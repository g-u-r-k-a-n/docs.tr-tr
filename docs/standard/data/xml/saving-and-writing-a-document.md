---
title: Belge Kaydetme ve Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 0cb83935b4175060a04f4be48e6b4eee2f44ed7d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823504"
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="86373-102">Belge Kaydetme ve Yazma</span><span class="sxs-lookup"><span data-stu-id="86373-102">Saving and Writing a Document</span></span>
<span data-ttu-id="86373-103">Yüklediğinizde ve kaydettiğinizde <xref:System.Xml.XmlDocument> , kaydedilen belge orijinalden aşağıdaki yollarla farklılık gösterebilir:</span><span class="sxs-lookup"><span data-stu-id="86373-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
- <span data-ttu-id="86373-104"><xref:System.Xml.XmlDocument.PreserveWhitespace%2A>Özelliği `true` yöntemi çağrılmadan önce olarak ayarlandıysa <xref:System.Xml.XmlDocument.Save%2A> , çıktıda boşluk korunur; Bu özellik ise `false` <xref:System.Xml.XmlDocument> çıktıyı otomatik olarak girintiler.</span><span class="sxs-lookup"><span data-stu-id="86373-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
- <span data-ttu-id="86373-105">Öznitelikler arasındaki tüm boşluklar, tek bir boşluk karakteriyle azaltılır.</span><span class="sxs-lookup"><span data-stu-id="86373-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
- <span data-ttu-id="86373-106">Öğeler arasındaki boşluk değişir.</span><span class="sxs-lookup"><span data-stu-id="86373-106">The white space between elements is changed.</span></span> <span data-ttu-id="86373-107">Önemli boşluk korunur ve çok önemli boşluk değildir.</span><span class="sxs-lookup"><span data-stu-id="86373-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="86373-108">Ancak belge kaydedildiğinde, <xref:System.Xml.XmlTextWriter> çıktıyı daha okunabilir hale getirmek için varsayılan olarak, **girintilemeyi** seçerek yazdırmak için varsayılan olarak girintileme modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="86373-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
- <span data-ttu-id="86373-109">Öznitelik değerleri etrafında kullanılan tırnak karakteri varsayılan olarak çift tırnak olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="86373-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="86373-110"><xref:System.Xml.XmlTextReader.QuoteChar%2A> <xref:System.Xml.XmlTextWriter> Tırnak karakterini çift tırnak ya da tek tırnak olarak ayarlamak için üzerinde özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86373-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
- <span data-ttu-id="86373-111">Varsayılan olarak, benzer sayısal karakter varlıkları `{` genişletilir.</span><span class="sxs-lookup"><span data-stu-id="86373-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
- <span data-ttu-id="86373-112">Giriş belgesinde bulunan bayt düzeni işareti korunmaz.</span><span class="sxs-lookup"><span data-stu-id="86373-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="86373-113">Özel olarak farklı bir kodlama belirten bir XML bildirimi oluşturmadığınız sürece, UCS-2 UTF-8 olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="86373-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
- <span data-ttu-id="86373-114"><xref:System.Xml.XmlDocument>' I bir dosyaya veya akışa yazmak isterseniz, yazılan çıkış belgenin içeriğiyle aynı olur.</span><span class="sxs-lookup"><span data-stu-id="86373-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="86373-115">Diğer bir deyişle, <xref:System.Xml.XmlDeclaration> yalnızca belgede bulunan bir belge varsa yazılır ve belgeyi yazarken kullanılan kodlama, bildirim düğümünde belirtilen kodlamayla aynı olur.</span><span class="sxs-lookup"><span data-stu-id="86373-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="86373-116">XmlDeclaration yazma</span><span class="sxs-lookup"><span data-stu-id="86373-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="86373-117">, <xref:System.Xml.XmlDocument> Ve <xref:System.Xml.XmlDeclaration> <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlNode.InnerXml%2A> <xref:System.Xml.XmlNode.WriteTo%2A> yöntemlerinin yanı sıra <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.WriteContentTo%2A> bir XML bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86373-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="86373-118">, Ve, <xref:System.Xml.XmlDocument> ve yöntemlerinin özellikleri için, <xref:System.Xml.XmlNode.OuterXml%2A> <xref:System.Xml.XmlDocument.InnerXml%2A> <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.WriteTo%2A> <xref:System.Xml.XmlDocument.WriteContentTo%2A> XML bildiriminde yazılan kodlama <xref:System.Xml.XmlDeclaration> düğümden alınır.</span><span class="sxs-lookup"><span data-stu-id="86373-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="86373-119"><xref:System.Xml.XmlDeclaration>Düğüm yoksa, <xref:System.Xml.XmlDeclaration> yazılmaz. Düğümde bir kodlama yoksa <xref:System.Xml.XmlDeclaration> , kodlama XML bildiriminde yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="86373-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="86373-120"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType>Ve <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> yöntemleri her zaman bir yazar <xref:System.Xml.XmlDeclaration> .</span><span class="sxs-lookup"><span data-stu-id="86373-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="86373-121">Bu yöntemler, yazma yaptığı yazarın kodlamasını alır.</span><span class="sxs-lookup"><span data-stu-id="86373-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="86373-122">Diğer bir deyişle, yazıcı üzerindeki kodlama değeri belgedeki ve içindeki kodlamayı geçersiz kılar <xref:System.Xml.XmlDeclaration> .</span><span class="sxs-lookup"><span data-stu-id="86373-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="86373-123">Örneğin, aşağıdaki kod çıkış dosyasında bulunan XML bildiriminde bir kodlama yazmıyor `out.xml` .</span><span class="sxs-lookup"><span data-stu-id="86373-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="86373-124">Yöntemi için <xref:System.Xml.XmlDocument.Save%2A> , XML bildirimi <xref:System.Xml.XmlWriter.WriteStartDocument%2A> sınıfında yöntemi kullanılarak yazılır <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="86373-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="86373-125">Bu nedenle, yöntemin üzerine yazılması <xref:System.Xml.XmlWriter.WriteStartDocument%2A> belgenin başlangıcını nasıl yazıldığı değişir.</span><span class="sxs-lookup"><span data-stu-id="86373-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="86373-126">, <xref:System.Xml.XmlDeclaration> Ve üyeleri için <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDeclaration.WriteTo%2A> <xref:System.Xml.XmlNode.InnerXml%2A> <xref:System.Xml.XmlDeclaration.Encoding%2A> özelliği ayarlanmamışsa, hiçbir kodlama yazılmaz. Aksi halde, XML bildiriminde yazılan kodlama, özelliğinde bulunan kodlamayla aynı olur <xref:System.Xml.XmlDeclaration.Encoding%2A> .</span><span class="sxs-lookup"><span data-stu-id="86373-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="86373-127">OuterXml özelliğini kullanarak belge Içeriği yazma</span><span class="sxs-lookup"><span data-stu-id="86373-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="86373-128"><xref:System.Xml.XmlNode.OuterXml%2A>Özelliği, World Wide Web Konsorsiyumu (W3C) XML belge nesne modeli (DOM) standartlarına yönelik bir Microsoft uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="86373-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="86373-129"><xref:System.Xml.XmlNode.OuterXml%2A>Özelliği tüm XML belgesinin işaretlemesini veya yalnızca tek bir düğümün ve onun alt düğümlerinin işaretlemesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86373-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="86373-130"><xref:System.Xml.XmlNode.OuterXml%2A> verilen düğümü ve onun tüm alt düğümlerini temsil eden biçimlendirmeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="86373-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="86373-131">Aşağıdaki kod örneği, bir belgenin tamamen dize olarak nasıl kaydedileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="86373-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="86373-132">Aşağıdaki kod örneğinde, yalnızca belge öğesinin nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="86373-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="86373-133">Buna karşılık, <xref:System.Xml.XmlNode.InnerText%2A> alt düğümlerin içeriğini istiyorsanız özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86373-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86373-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86373-134">See also</span></span>

- [<span data-ttu-id="86373-135">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="86373-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
