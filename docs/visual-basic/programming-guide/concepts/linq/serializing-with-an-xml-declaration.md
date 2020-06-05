---
title: XML Bildirimi ile Serileştirme
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: cd303a800efe42d3fa99d601f25d54320570bed3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411811"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="d2350-102">XML bildirimiyle serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2350-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="d2350-103">Bu konu, serileştirme 'in bir XML bildirimi oluşturup oluşturmayacağını nasıl denetleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d2350-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="d2350-104">XML bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2350-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="d2350-105"><xref:System.IO.File>Yöntemini veya yöntemini kullanarak bir veya öğesine serileştirmek BIR <xref:System.IO.TextWriter> <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> XML bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2350-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="d2350-106">' A serileştirçalıştığınızda <xref:System.Xml.XmlWriter> , yazıcı ayarları (bir <xref:System.Xml.XmlWriterSettings> nesnede belirtilir) bir XML bildiriminin oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2350-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="d2350-107">Yöntemini kullanarak bir dizeye serileştirme yapıyorsanız `ToString` , elde EDILEN XML BIR XML bildirimi içermez.</span><span class="sxs-lookup"><span data-stu-id="d2350-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="d2350-108">XML Bildirimi ile Serileştirme</span><span class="sxs-lookup"><span data-stu-id="d2350-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="d2350-109">Aşağıdaki örnek bir dosyası oluşturur <xref:System.Xml.Linq.XElement> , belgeyi bir dosyaya kaydeder ve sonra dosyayı konsola yazdırır:</span><span class="sxs-lookup"><span data-stu-id="d2350-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="d2350-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d2350-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="d2350-111">XML bildirimi olmadan serileştirme</span><span class="sxs-lookup"><span data-stu-id="d2350-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="d2350-112">Aşağıdaki örnekte, bir ' a nasıl kaydedileceği gösterilmektedir <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="d2350-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="d2350-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d2350-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2350-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2350-114">See also</span></span>

- [<span data-ttu-id="d2350-115">XML ağaçlarını serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2350-115">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
