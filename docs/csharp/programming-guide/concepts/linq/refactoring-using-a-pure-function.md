---
title: Saf Işlev kullanarak yeniden düzenleme (C#)
description: Saf bir işlev kullanarak kodu yeniden düzenleme hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
ms.assetid: a3416a45-9e12-4e4a-9747-897f06eef510
ms.openlocfilehash: a3f0084d9de27f3f215cc3ba527ada93f7a3d61a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300117"
---
# <a name="refactoring-using-a-pure-function-c"></a><span data-ttu-id="b14bd-104">Saf Işlev kullanarak yeniden düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="b14bd-104">Refactoring Using a Pure Function (C#)</span></span>
<span data-ttu-id="b14bd-105">Aşağıdaki örnek, bir [genişletme yöntemi (C#) kullanarak](./refactoring-using-an-extension-method.md)saf bir işlevi kullanmak için önceki örneği şunların.</span><span class="sxs-lookup"><span data-stu-id="b14bd-105">The following example refactors the previous example, [Refactoring Using an Extension Method (C#)](./refactoring-using-an-extension-method.md), to use a pure function.</span></span> <span data-ttu-id="b14bd-106">Bu örnekte, bir paragrafın metnini bulmak için kod saf statik metoda taşınır `ParagraphText` .</span><span class="sxs-lookup"><span data-stu-id="b14bd-106">In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b14bd-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b14bd-107">Example</span></span>  
 <span data-ttu-id="b14bd-108">Bu örnek, WordprocessingML belgesinden paragraf düğümlerini alarak bir WordprocessingML belgesini işler.</span><span class="sxs-lookup"><span data-stu-id="b14bd-108">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="b14bd-109">Ayrıca her bir paragrafın stilini belirler.</span><span class="sxs-lookup"><span data-stu-id="b14bd-109">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="b14bd-110">Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır.</span><span class="sxs-lookup"><span data-stu-id="b14bd-110">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="b14bd-111">Yeniden düzenlenmiş kodu, aşağıdaki koddaki açıklamalarda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b14bd-111">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="b14bd-112">Bu örnek için kaynak belge oluşturmaya ilişkin yönergeler için bkz. [kaynak Office Open XML belgesi oluşturma (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b14bd-112">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="b14bd-113">Bu örnek, WindowsBase derlemesinden sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="b14bd-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="b14bd-114"><xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="b14bd-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    // This is a new method that assembles the paragraph text.  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
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
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri,  
                      styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
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
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="b14bd-115">Bu örnek, yeniden düzenlemeden önceki ile aynı çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b14bd-115">This example produces the same output as before the refactoring:</span></span>  
  
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
  
### <a name="next-steps"></a><span data-ttu-id="b14bd-116">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b14bd-116">Next Steps</span></span>  
 <span data-ttu-id="b14bd-117">Sonraki örnekte, XML 'in farklı bir şekle nasıl proje yapılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b14bd-117">The next example shows how to project XML into a different shape:</span></span>  
  
- [<span data-ttu-id="b14bd-118">XML 'i farklı bir şekilde yansıtma (C#)</span><span class="sxs-lookup"><span data-stu-id="b14bd-118">Projecting XML in a Different Shape (C#)</span></span>](./projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="b14bd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b14bd-119">See also</span></span>

- [<span data-ttu-id="b14bd-120">Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="b14bd-120">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="b14bd-121">Genişletme yöntemi kullanarak yeniden düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="b14bd-121">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)
- [<span data-ttu-id="b14bd-122">Saf IŞLEVLERE yeniden düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="b14bd-122">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
