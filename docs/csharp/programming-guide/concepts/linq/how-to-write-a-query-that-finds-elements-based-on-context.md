---
title: Bağlam temelinde öğeleri bulan bir sorgu yazma (C#)
description: Bağlam temelinde öğeleri bulan bir sorgu yazmayı öğrenin. Kod örneklerine bakın ve ek kaynakları görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 64f09a41c2c1d01b0be8f776461f9be9df9ecb5f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303198"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="1c631-104">Bağlam temelinde öğeleri bulan bir sorgu yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="1c631-104">How to write a query that finds elements based on context (C#)</span></span>
<span data-ttu-id="1c631-105">Bazen, bağlamlarına göre öğeleri seçen bir sorgu yazmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1c631-105">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="1c631-106">Önceki veya sonraki eşdüzey öğelere göre filtrelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c631-106">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="1c631-107">Alt veya üst öğe öğelerine göre filtrelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c631-107">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="1c631-108">Bunu, bir sorgu yazarak ve yan tümcesindeki sorgunun sonuçlarını kullanarak yapabilirsiniz `where` .</span><span class="sxs-lookup"><span data-stu-id="1c631-108">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="1c631-109">İlk olarak null ile test etmeniz ve sonra değeri test etmeniz gerekiyorsa, bir yan tümce içinde sorgu yapmak daha uygundur `let` ve sonra sonuçları `where` yan tümce içinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c631-109">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c631-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c631-110">Example</span></span>  
 <span data-ttu-id="1c631-111">Aşağıdaki örnek, `p` hemen arkasından bir öğesi olan tüm öğeleri seçer `ul` .</span><span class="sxs-lookup"><span data-stu-id="1c631-111">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="1c631-112">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1c631-112">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="1c631-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c631-113">Example</span></span>  
 <span data-ttu-id="1c631-114">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c631-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1c631-115">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1c631-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="1c631-116">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1c631-116">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c631-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c631-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
