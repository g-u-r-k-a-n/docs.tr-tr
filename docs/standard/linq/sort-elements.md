---
title: Öğeleri sıralama-LINQ to XML
description: Sonuçlarını sıralayan bir sorgu yazmayı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 0e93add12e39c71c7312036917d42dd53450b712
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550071"
---
# <a name="how-to-sort-elements-linq-to-xml"></a>Öğeleri sıralama (LINQ to XML)

XML 'yi sorguladığınızda sonuçlarınızı sıralayabilirsiniz. Bu makalede iki örnek sunulmaktadır: ilki, bir ad alanında *olmayan* XML için sonuçları sıralar, *ikincisi ise bir ad alanında olan XML* için de aynı sıralamayı yapar.

## <a name="example-write-a-query-that-sorts-its-results"></a>Örnek: sonuçlarını sıralayan bir sorgu yazın

Bu örnek, sonuçlarını sıralayan bir sorgunun nasıl yazılacağını gösterir. XML belgesi [örnek xml dosyası kullanır: sayısal veri](sample-xml-file-numerical-data.md).

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> prices =
    from el in root.Elements("Data")
    let price = (decimal)el.Element("Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim prices As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let price = Convert.ToDecimal(el.<Price>.Value) _
    Order By (price) _
    Select price
For Each el As Decimal In prices
    Console.WriteLine(el)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="example-write-a-query-in-a-namespace-that-sorts-its-results"></a>Örnek: bir ad alanına sonuçlarını sıralayan bir sorgu yazma

Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir. XML belgesi [örnek xml dosyası kullanır: bir ad alanında sayısal veri](sample-xml-file-numerical-data-namespace.md).

Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace aw = "http://www.adatum.com";
IEnumerable<decimal> prices =
    from el in root.Elements(aw + "Data")
    let price = (decimal)el.Element(aw + "Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim prices As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let price = Convert.ToDecimal(el.<Price>.Value) _
            Order By (price) _
            Select price
        For Each el As Decimal In prices
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri sıralama (C#)](../../csharp/programming-guide/concepts/linq/sorting-data.md)
- [Verileri sıralama (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [Temel sorgular (LINQ to XML) (Visual Basic)](./find-element-specific-attribute.md)
