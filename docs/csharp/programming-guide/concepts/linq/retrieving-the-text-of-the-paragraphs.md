---
title: Paragrafmetninin Alınması (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 7c47420045def3fe973169e01143646c0f60a8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168251"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="26564-102">Paragrafmetninin Alınması (C#)</span><span class="sxs-lookup"><span data-stu-id="26564-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="26564-103">Bu örnek, önceki örnekte, [Paragrafları ve Stilleri (C#) alma](./retrieving-the-paragraphs-and-their-styles.md)üzerine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26564-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="26564-104">Bu yeni örnek, her paragrafın metnini bir dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="26564-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="26564-105">Metni almak için, bu örnek, anonim türlerin toplanması yoluyla yineleyen ek bir sorgu ekler ve yeni bir üye `Text`nin eklenmesiyle anonim bir türden oluşan yeni bir koleksiyon projeleri, .</span><span class="sxs-lookup"><span data-stu-id="26564-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="26564-106">Birden çok <xref:System.Linq.Enumerable.Aggregate%2A> dizeyi tek bir dize ye dönüştürmek için standart sorgu işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="26564-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="26564-107">Bu teknik (yani, ilk anonim bir tür bir koleksiyona yansıtma, daha sonra anonim bir tür yeni bir koleksiyona proje için bu koleksiyonu kullanarak) yaygın ve yararlı bir deyimdir.</span><span class="sxs-lookup"><span data-stu-id="26564-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="26564-108">Bu sorgu, ilk anonim türe yansıtılmadan yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="26564-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="26564-109">Ancak, tembel değerlendirme nedeniyle, bunu yapmak çok ek işlem gücü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="26564-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="26564-110">Deyim yığın üzerinde daha kısa ömürlü nesneler oluşturur, ancak bu önemli ölçüde performansı düşürmez.</span><span class="sxs-lookup"><span data-stu-id="26564-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="26564-111">Elbette, paragrafları, her paragrafın stilini ve her paragrafın metnini almak için işlevselliği içeren tek bir sorgu yazmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="26564-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="26564-112">Ancak, ortaya çıkan kod daha modüler ve bakımı daha kolay olduğundan, daha karmaşık bir sorguyu birden çok sorguya ayırmak genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="26564-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="26564-113">Ayrıca, sorgunun bir bölümünü yeniden kullanmanız gerekiyorsa, sorgular bu şekilde yazılmışsa yeniden düzenlemeyapmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="26564-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="26564-114">Birlikte zincirlenmiş olan bu sorgular, konu Öğretici ayrıntılı olarak incelenir işleme modeli kullanın: Birlikte [Sorguları Zincirleme (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="26564-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26564-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="26564-115">Example</span></span>  
 <span data-ttu-id="26564-116">Bu örnek, öğe düğümü, stil adı ve her paragrafın metnini belirleyerek bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="26564-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="26564-117">Bu örnek, bu öğreticide önceki örneklere dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="26564-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="26564-118">Yeni sorgu aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="26564-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="26564-119">Bu örnek için kaynak belge oluşturma yönergeleri için [bkz.](./creating-the-source-office-open-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="26564-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="26564-120">Bu örnek, WindowsBase derlemesi sınıflarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="26564-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="26564-121"><xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="26564-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
string defaultStyle =
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Find all paragraphs in the document.  
var paragraphs =  
    from para in xDoc  
                 .Root  
                 .Element(w + "body")  
                 .Descendants(w + "p")  
    let styleNode = para  
                    .Elements(w + "pPr")  
                    .Elements(w + "pStyle")  
                    .FirstOrDefault()  
    select new  
    {  
        ParagraphNode = para,  
        StyleName = styleNode != null ?  
            (string)styleNode.Attribute(w + "val") :  
            defaultStyle  
    };  
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 <span data-ttu-id="26564-122">Bu örnek, [Kaynak Office Açık XML Belgesi (C#) oluşturma'da](./creating-the-source-office-open-xml-document.md)açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="26564-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```output  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="26564-123">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="26564-123">Next Steps</span></span>  
 <span data-ttu-id="26564-124">Sonraki örnek, birden çok dizeyi <xref:System.Linq.Enumerable.Aggregate%2A>tek bir dize içine dönüştürmek yerine bir uzantı yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="26564-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="26564-125">Uzantı Yöntemini Kullanarak Yeniden Düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="26564-125">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="26564-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26564-126">See also</span></span>

- [<span data-ttu-id="26564-127">Öğretici: WordprocessingML Belgesinde İçeriği Manipüle Etme (C#)</span><span class="sxs-lookup"><span data-stu-id="26564-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="26564-128">Linq'te Ertelenmiş Yürütme ve Tembel Değerlendirme XML 'ye (C#)</span><span class="sxs-lookup"><span data-stu-id="26564-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
