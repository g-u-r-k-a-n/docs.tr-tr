---
title: Paragrafların metnini alma (C#)
description: Bir WordprocessingML belgesindeki her bir paragrafın metnini C# dilinde bir dize olarak almak için LINQ sorgularını nasıl kullanacağınızı öğrenin. Bu örnek, zincirleme sorguları kullanır.
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 58a07ab848307c886927815e4e49e90806f61346
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302600"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Paragrafların metnini alma (C#)
Bu örnek, önceki örnekte yer alan [ve paragrafları ve stillerini alma (C#) ile](./retrieving-the-paragraphs-and-their-styles.md)oluşturulur. Bu yeni örnek, her bir paragrafın metnini dize olarak alır.  
  
 Bu örnek, metni almak için anonim türler koleksiyonu ve proje, yeni bir üyenin eklenmesiyle anonim bir türün yeni bir koleksiyonu aracılığıyla yinelenen ek bir sorgu ekler `Text` . <xref:System.Linq.Enumerable.Aggregate%2A>Birden çok dizeyi tek bir dizede birleştirmek için standart sorgu işlecini kullanır.  
  
 Bu teknik (yani, ilk olarak anonim bir türün koleksiyonuna yansıtırken, daha sonra bu koleksiyonun yeni bir anonim tür koleksiyonuna proje için kullanılması) ortak ve kullanışlı bir derlemedir. Bu sorgu, ilk anonim türe yansıtılamadan yazılmış olabilir. Ancak, yavaş değerlendirme nedeniyle bunu yapmak çok daha fazla işlem gücü kullanmaz. Deyim yığında daha kısa süreli nesneler oluşturur, ancak bu durum performansı önemli ölçüde düşürür.  
  
 Tabii ki, paragrafları alma işlevini, her bir paragrafın stilini ve her bir paragrafın metnini içeren tek bir sorgu yazmak mümkün olacaktır. Ancak, sonuçta elde edilen kod daha modüler ve bakımını daha kolay olduğundan, genellikle daha karmaşık bir sorguyu birden çok sorguya bölmek faydalı olur. Ayrıca, sorgunun bir bölümünü yeniden kullanmanız gerekiyorsa, sorgular bu şekilde yazılmışsa yeniden düzenleme daha kolay olur.  
  
 Birlikte zincirleme olan bu sorgular, konu öğreticisinde ayrıntılı olarak incelenen işleme modelini kullanın [: sorguları birlikte zincirleme (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir WordprocessingML belgesi işlenir, öğe düğümü, stil adı ve her paragrafın metni belirlenir. Bu örnekte, bu öğreticideki önceki örneklerde derleme yapılır. Yeni sorgu, aşağıdaki koddaki açıklamalarda çağrılır.  
  
 Bu örnek için kaynak belge oluşturmaya ilişkin yönergeler için bkz. [kaynak Office Open XML belgesi oluşturma (C#)](./creating-the-source-office-open-xml-document.md).  
  
 Bu örnek, WindowsBase derlemesinden sınıfları kullanır. <xref:System.IO.Packaging?displayProperty=nameWithType>Ad alanındaki türleri kullanır.  
  
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
  
 Bu örnek, [kaynak Office Open XML belgesi (C#) oluşturma](./creating-the-source-office-open-xml-document.md)bölümünde açıklanan belgeye uygulandığında aşağıdaki çıktıyı üretir.  
  
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
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki örnek, <xref:System.Linq.Enumerable.Aggregate%2A> birden çok dizeyi tek bir dizeye birleştirmek için yerine bir genişletme yönteminin nasıl kullanılacağını gösterir.  
  
- [Genişletme yöntemi kullanarak yeniden düzenleme (C#)](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (C#)](shape-of-wordprocessingml-documents.md)
- [LINQ to XML ertelenmiş yürütme ve geç değerlendirme (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
