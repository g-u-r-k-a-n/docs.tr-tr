---
title: Eşdüzey düğümleri bulma (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 24bad37151f3d63b03ec28c0fbea95bef02ab614
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141017"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="7ba98-102">Eşdüzey düğümleri bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ba98-102">How to find sibling nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="7ba98-103">Belirli bir ada sahip bir düğümün tüm eşdüzey düzeylerini bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ba98-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="7ba98-104">Bağlam düğümü de belirli bir ada sahipse, sonuçta elde edilen koleksiyon bağlam düğümünü içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7ba98-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="7ba98-105">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="7ba98-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="7ba98-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ba98-106">Example</span></span>  
 <span data-ttu-id="7ba98-107">Bu örnek önce bir `Book` öğesi bulur ve sonra `Book`adlı tüm eşdüzey öğeleri bulur.</span><span class="sxs-lookup"><span data-stu-id="7ba98-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="7ba98-108">Elde edilen koleksiyon, bağlam düğümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="7ba98-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="7ba98-109">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7ba98-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Elements("Book")  
    .Skip(1)  
    .First();  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    book  
    .Parent  
    .Elements("Book");  
  
// XPath expression  
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="7ba98-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7ba98-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
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
```  
