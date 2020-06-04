---
title: Statik Olarak Derlenmiş Sorgular (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f020c1ed8627df8c8386a059f0cea372e8df363e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406774"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Statik olarak derlenen sorgular (LINQ to XML) (Visual Basic)

En önemli performans avantajlarından biri de LINQ to XML, <xref:System.Xml.XmlDocument> LINQ to XML içindeki sorguların statik olarak derlenmesine karşın XPath sorgularının çalışma zamanında yorumlanması gerekir. Bu özellik LINQ to XML ' de yerleşiktir. bu nedenle, bundan faydalanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken farkın anlaşılması yararlı olur. Bu konu, farkı açıklamaktadır.

## <a name="statically-compiled-queries-vs-xpath"></a>Statik olarak derlenen sorgular ve XPath karşılaştırması

Aşağıdaki örnek, belirtilen bir ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını gösterir.

Eşdeğer XPath ifadesi aşağıda verilmiştir:

```vb
//Address[@Type='Shipping']
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

Bu örnekteki sorgu ifadesi derleyici tarafından Yöntem tabanlı sorgu söz dizimine yeniden yazılır. Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<xref:System.Linq.Enumerable.Where%2A>Yöntemi bir genişletme yöntemidir. Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). <xref:System.Linq.Enumerable.Where%2A>Bir genişletme yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir. Bu, sorguların statik olarak bağlı yöntem çağrılarına etkin bir şekilde derlendiğini gösterir. Yineleyicilerin ertelenmiş yürütme semantiği ile birlikte, performansı geliştirir. Yineleyicilerin ertelenmiş yürütme semantiği hakkında daha fazla bilgi için bkz. [LINQ to XML ertelenmiş yürütme ve geç değerlendirme (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

> [!NOTE]
> Bu örnekler, derleyicinin yazabilmesi için kod temsilcisidir. Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak performans aynı veya bu örneklere benzer olacaktır.

## <a name="executing-xpath-expressions-with-xmldocument"></a>XmlDocument ile XPath Ifadeleri yürütme

Aşağıdaki örnek, <xref:System.Xml.XmlDocument> önceki örneklerle aynı sonuçları başarmak için kullanır:

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

Bu sorgu, LINQ to XML kullanan örneklerle aynı çıktıyı döndürür; Tek fark, LINQ to XML yazdırılan XML 'nin girintilebilirken, bunun farklılığı değildir <xref:System.Xml.XmlDocument> .

Ancak, <xref:System.Xml.XmlDocument> yaklaşım genellikle LINQ to XML, ve yöntemi her çağrıldığında aşağıdaki işlemleri yapması gerektiğinden, <xref:System.Xml.XmlNode.SelectNodes%2A> her zaman yaklaşım uygulanmaz:

- XPath ifadesini içeren dizeyi ayrıştırır ve dizeyi belirteçlere ayırır.

- XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrular.

- İfadeyi bir iç ifade ağacına çevirir.

- İfadenin değerlendirmesine bağlı olarak sonuç kümesi düğümlerini uygun şekilde seçerek düğümleri üzerinde dolaşır.

Bu, karşılık gelen LINQ to XML sorgusu tarafından gerçekleştirilen işin önemli ölçüde daha yüksektir. Belirli performans farkı farklı sorgu türleri için farklılık gösterir, ancak genel LINQ to XML sorgularında daha az iş olur ve bu nedenle, kullanarak XPath ifadelerini değerlendirmeden daha iyi gerçekleştirilir <xref:System.Xml.XmlDocument> .

## <a name="see-also"></a>Ayrıca bkz.

- [Performans (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
