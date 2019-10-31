---
title: DOM’da XML Belgesi Okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 2e61a9ed1a1ccaa2f9f1543efa1d33c3fcf00061
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130841"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="99be3-102">DOM’da XML Belgesi Okuma</span><span class="sxs-lookup"><span data-stu-id="99be3-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="99be3-103">XML bilgileri farklı biçimlerden belleğe okundu.</span><span class="sxs-lookup"><span data-stu-id="99be3-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="99be3-104">Dize, akış, URL, metin okuyucu veya <xref:System.Xml.XmlReader>türetilmiş bir sınıftan okunabilir.</span><span class="sxs-lookup"><span data-stu-id="99be3-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="99be3-105"><xref:System.Xml.XmlDocument.Load%2A> yöntemi, belgeyi belleğe getirir ve farklı biçimlerden her birinden veri almak için kullanılabilir yöntemler daha fazla bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="99be3-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="99be3-106">Ayrıca, bir dizeden XML okuyan bir <xref:System.Xml.XmlDocument.LoadXml%2A> yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="99be3-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="99be3-107">Farklı <xref:System.Xml.XmlDocument.Load%2A> yöntemleri, XML Belge Nesne Modeli (DOM) yüklendiğinde hangi düğümlerin oluşturulduğunu etkiler.</span><span class="sxs-lookup"><span data-stu-id="99be3-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="99be3-108">Aşağıdaki tabloda, bazı <xref:System.Xml.XmlDocument.Load%2A> yöntemleri ve bunları ele alan konular arasındaki farklılıklar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="99be3-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="99be3-109">Konu</span><span class="sxs-lookup"><span data-stu-id="99be3-109">Subject</span></span>|<span data-ttu-id="99be3-110">Konu</span><span class="sxs-lookup"><span data-stu-id="99be3-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="99be3-111">Boşluk düğümleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="99be3-111">Creation of white space nodes</span></span>|<span data-ttu-id="99be3-112">DOM 'ı yüklemek için kullanılan nesnenin, DOM 'da oluşturulan, boşluk ve önemli boşluk düğümleri üzerinde bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="99be3-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="99be3-113">Daha fazla bilgi için bkz. [Dom yüklenirken beyaz boşluk ve önemli boşluk işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="99be3-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="99be3-114">Belirli bir düğümden başlayarak XML yükleme veya tüm XML belgesi yükleme</span><span class="sxs-lookup"><span data-stu-id="99be3-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="99be3-115"><xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> yöntemi verileri kullanmak belirli bir düğümden DOM 'a yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="99be3-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="99be3-116">Daha fazla bilgi için bkz. [okuyucudan veri yükleme](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="99be3-116">For more information, see [Load Data from a Reader](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="99be3-117">XML yüklendiği için doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="99be3-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="99be3-118">DOM 'a yüklenen XML verileri, yüklendiği için doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="99be3-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="99be3-119">Bu, doğrulama <xref:System.Xml.XmlReader>kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="99be3-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="99be3-120">XML 'nin yüklendiği şekilde doğrulanması hakkında daha fazla bilgi için bkz. [Dom 'da BIR XML belgesini doğrulama](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="99be3-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="99be3-121">Aşağıdaki örnek, <xref:System.Xml.XmlDocument.LoadXml%2A> yöntemiyle yüklenmekte olan XML ve daha sonra `data.xml`adlı bir metin dosyasına kaydedilen verileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="99be3-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="99be3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99be3-122">See also</span></span>

- [<span data-ttu-id="99be3-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="99be3-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
