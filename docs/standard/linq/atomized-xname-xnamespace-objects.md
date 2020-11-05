---
title: Atomlanmış XName ve XNamespace nesneleri-LINQ to XML
description: Aynı ada sahip atomlanmış XName ve XNamespace nesnelerinin bir örneği nasıl paylaştığından öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 05df7b5348fecebb7504ebb4e2623f688b6549e1
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400839"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml"></a>Atomlanmış XName ve XNamespace nesneleri (LINQ to XML)

<xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> nesneleri *atomlanmış* olur; diğer bir deyişle, aynı nitelikli adı içeriyorsa, aynı nesneye başvurur. Bu, sorgular için performans avantajları sağlar: iki atomılı adı eşitlik için karşılaştırdığınızda, temel alınan ara dilin yalnızca iki başvuruyu aynı nesneye işaret edip etmediğini belirlemesi gerekir. Temel alınan kodun dize karşılaştırmaları yapması gerekmez, bu da daha uzun sürer.

## <a name="atomization-semantics"></a>Atomleştirme semantiği

Atomleştirme, iki <xref:System.Xml.Linq.XName> nesnenin aynı yerel ada sahip olması ve aynı ad alanında olmaları durumunda aynı örneği paylaştıkları anlamına gelir. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesne aynı ad alanı URI 'sine sahip ise, aynı örneği paylaşır.

Atomlanmış nesneleri etkinleştirmek için bir sınıf için, sınıf için Oluşturucu genel değil, özel olmalıdır. Bunun nedeni, oluşturucunun genel olması, atomsuz olmayan bir nesne oluşturmanız olabilir. <xref:System.Xml.Linq.XName>Ve <xref:System.Xml.Linq.XNamespace> sınıfları bir dizeyi bir veya içine dönüştürmek için örtük bir dönüştürme işleci uygular <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> . Bu nesnelerin bir örneğini alma işlemi budur. Oluşturucuya erişilemediği için bir oluşturucuyu kullanarak bir örnek alamazsınız.

<xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>Ayrıca, karşılaştırılan iki nesnenin aynı örneğe başvuru olup olmadığını belirleyen eşitlik ve eşitsizlik işleçlerini da uygulayın.

## <a name="example-create-objects-and-show-that-identical-names-share-an-instance"></a>Örnek: nesne oluşturma ve özdeş adların bir örneği paylaştığı gösterme

Aşağıdaki kod bazı nesneler oluşturur <xref:System.Xml.Linq.XElement> ve aynı adların aynı örneği paylaşılacağını gösterir.

```csharp
var r1 = new XElement("Root", "data1");
XElement r2 = XElement.Parse("<Root>data2</Root>");

if ((object)r1.Name == (object)r2.Name)
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");
else
    Console.WriteLine("Different");

XName n = "Root";

if ((object)n == (object)r1.Name)
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");
else
    Console.WriteLine("Different");
```

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

Daha önce belirtildiği gibi, atomlanmış nesnelerin avantajı bir parametre olarak alan eksen yöntemlerinden birini kullandığınızda <xref:System.Xml.Linq.XName> , eksen yönteminin yalnızca iki adların istenen öğeleri seçmek için aynı örneğe başvurmadığını belirlemesi gerekir.

Aşağıdaki örnek, bir <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> ' ı yöntem çağrısına geçirir ve daha sonra atomleştirme düzeniyle daha iyi performansa sahiptir.

```csharp
var root = new XElement("Root",
    new XElement("C1", 1),
    new XElement("Z1",
        new XElement("C1", 2),
        new XElement("C1", 1)
    )
);

var query = from e in root.Descendants("C1")
            where (int)e == 1
            select e;

foreach (var z in query)
    Console.WriteLine(z);
```

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1

For Each z In query
    Console.WriteLine(z)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<C1>1</C1>
<C1>1</C1>
```
