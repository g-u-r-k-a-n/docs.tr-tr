---
title: XmlReader-LINQ to XML ağaç oluşturma
description: C# veya Visual Basic XML 'yi okumak ve bir XML ağacı oluşturmak için bir XmlReader kullanabilirsiniz. XmlReader 'yi bir öğe düğümüne doğru bir şekilde konumlandırmalısınız.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 659135ae9930d4ba63b13e436ebd278807e4256b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553198"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-linq-to-xml"></a><span data-ttu-id="dc907-104">XmlReader 'dan ağaç oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="dc907-104">How to create a tree from an XmlReader (LINQ to XML)</span></span>

<span data-ttu-id="dc907-105">Bu makalede <xref:System.Xml.XmlReader> , C# veya Visual Basic doğrudan BIR XML ağacının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc907-105">This article shows how to create an XML tree directly from an <xref:System.Xml.XmlReader> in C# or Visual Basic.</span></span> <span data-ttu-id="dc907-106">Bir öğesinden oluşturmak için <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlReader> , öğesini bir <xref:System.Xml.XmlReader> öğe düğümüne yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc907-106">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="dc907-107"><xref:System.Xml.XmlReader>Açıklamaları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümüne yerleştirilse bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="dc907-107">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="dc907-108">Bu tür hatalardan kaçınmak için, <xref:System.Xml.XmlReader> öğesinden BIR XML ağacı oluşturmadan önce öğesini bir öğesine konumlandırın <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="dc907-108">To avoid such errors, position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example-load-xelement-object-from-an-xmlreader-object"></a><span data-ttu-id="dc907-109">Örnek: bir XmlReader nesnesinden XElement nesnesini yükle</span><span class="sxs-lookup"><span data-stu-id="dc907-109">Example: Load XElement object from an XmlReader object</span></span>

<span data-ttu-id="dc907-110">Bu örnek XML belgesi [örnek xml dosyasını kullanır: kitaplar](sample-xml-file-books.md).</span><span class="sxs-lookup"><span data-stu-id="dc907-110">This example uses the XML document [Sample XML file: Books](sample-xml-file-books.md).</span></span>

<span data-ttu-id="dc907-111">Aşağıdaki kod bir nesne oluşturur <xref:System.Xml.XmlReader> , ilk öğe düğümünü bulana kadar düğümleri okur ve <xref:System.Xml.Linq.XElement> nesneyi yükler.</span><span class="sxs-lookup"><span data-stu-id="dc907-111">The following code creates a <xref:System.Xml.XmlReader> object, reads nodes until it finds the first element node, and loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```csharp
XmlReader r = XmlReader.Create("books.xml");
while (r.NodeType != XmlNodeType.Element)
    r.Read();
XElement e = XElement.Load(r);
Console.WriteLine(e);
```

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="dc907-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="dc907-112">This example produces the following output:</span></span>

```xml
<Catalog>
   <Book id="bk101">
      <Author>Garghentini, Davide</Author>
      <Title>XML Developer's Guide</Title>
      <Genre>Computer</Genre>
      <Price>44.95</Price>
      <PublishDate>2000-10-01</PublishDate>
      <Description>An in-depth look at creating applications
      with XML.</Description>
   </Book>
   <Book id="bk102">
      <Author>Garcia, Debra</Author>
      <Title>Midnight Rain</Title>
      <Genre>Fantasy</Genre>
      <Price>5.95</Price>
      <PublishDate>2000-12-16</PublishDate>
      <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
   </Book>
</Catalog>
```

## <a name="see-also"></a><span data-ttu-id="dc907-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc907-113">See also</span></span>

- [<span data-ttu-id="dc907-114">XML 'yi Ayrıştır</span><span class="sxs-lookup"><span data-stu-id="dc907-114">Parse XML</span></span>](parse-string.md)
