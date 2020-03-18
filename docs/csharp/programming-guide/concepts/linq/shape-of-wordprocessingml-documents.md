---
title: WordprocessingML Belgelerin şekli (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 58c028fed465f45fdcf8f63f2119eb8e8b201e32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76732678"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="dd6f2-102">WordprocessingML Belgelerin şekli (C#)</span><span class="sxs-lookup"><span data-stu-id="dd6f2-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="dd6f2-103">Bu konu, WordprocessingML belgesinin XML şeklini tanır.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="dd6f2-104">Microsoft Office Biçimleri</span><span class="sxs-lookup"><span data-stu-id="dd6f2-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="dd6f2-105">2007 Microsoft Office sisteminin yerel dosya biçimi Office Open XML 'dir (genellikle Açık XML olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="dd6f2-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="dd6f2-106">Open XML, Bir Ecma standardı olan ve şu anda ISO-IEC standart sürecinden geçmekte olan XML tabanlı bir biçimdir.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="dd6f2-107">Açık XML içindeki sözcük işleme dosyalarının biçimlendirme dili WordprocessingML olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="dd6f2-108">Bu öğretici, örnekler için giriş olarak WordprocessingML kaynak dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="dd6f2-109">Microsoft Office 2003 kullanıyorsanız, Word, Excel ve PowerPoint 2007 Dosya Biçimleri için Microsoft Office Uyumluluk Paketi yüklediyseniz Belgeleri Office Open XML biçiminde kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="dd6f2-110">WordprocessingML Belgelerin Şekli</span><span class="sxs-lookup"><span data-stu-id="dd6f2-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="dd6f2-111">Anlamak için ilk şey WordprocessingML belgelerin şeklidir.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="dd6f2-112">WordprocessingML belgesi, belgenin paragraflarını içeren bir gövde öğesi (adlandırılmış) `w:body`içerir.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="dd6f2-113">Her paragraf bir veya daha `w:r`fazla metin çalışır (adlandırılmış) içerir.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="dd6f2-114">Her metin çalıştırıcı bir veya `w:t`daha fazla metin parçaları (adlandırılmış) içerir.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="dd6f2-115">Aşağıdaki çok basit bir WordprocessingML belgedir:</span><span class="sxs-lookup"><span data-stu-id="dd6f2-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="dd6f2-116">Bu belge iki paragraf içerir.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-116">This document contains two paragraphs.</span></span> <span data-ttu-id="dd6f2-117">Her ikisi de tek bir metin çalışması içerir ve her metin çalışması tek bir metin parçası içerir.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="dd6f2-118">Bir WordprocessingML belgesinin içeriğini XML formunda görmenin en kolay yolu, Microsoft Word'ü kullanarak bir belge oluşturmak, kaydetmek ve ardından XML'yi konsola yazdıran aşağıdaki programı çalıştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="dd6f2-119">Bu örnek, WindowsBase derlemesinde bulunan sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="dd6f2-120"><xref:System.IO.Packaging?displayProperty=nameWithType> Ad alanında türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="dd6f2-121">Dış kaynaklar</span><span class="sxs-lookup"><span data-stu-id="dd6f2-121">External resources</span></span>

- [<span data-ttu-id="dd6f2-122">Office Tanıtımı (2007) Açık XML Dosya Biçimleri</span><span class="sxs-lookup"><span data-stu-id="dd6f2-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [<span data-ttu-id="dd6f2-123">WordprocessingML'e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd6f2-123">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [<span data-ttu-id="dd6f2-124">Bir WordProcessingML Dosyaanatomisi</span><span class="sxs-lookup"><span data-stu-id="dd6f2-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="dd6f2-125">WordprocessingML'e Giriş</span><span class="sxs-lookup"><span data-stu-id="dd6f2-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a><span data-ttu-id="dd6f2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd6f2-126">See also</span></span>

- [<span data-ttu-id="dd6f2-127">Öğretici: WordprocessingML Belgesinde İçeriği Manipüle Etme (C#)</span><span class="sxs-lookup"><span data-stu-id="dd6f2-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
