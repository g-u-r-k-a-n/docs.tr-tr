---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: nesne verilerini bir XML dosyasına yazma (Visual Basic)'
title: 'Nasıl Yapılır: Nesne Verilerini bir XML Dosyasına Yazma'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: c6935fa97ed8813528630f5794e0a8e3e7e77b4d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486842"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="d2efa-103">Nasıl yapılır: nesne verilerini bir XML dosyasına yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2efa-103">How to: Write Object Data to an XML File (Visual Basic)</span></span>

<span data-ttu-id="d2efa-104">Bu örnek, sınıfını kullanarak bir sınıftan bir XML dosyasına nesne yazar <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="d2efa-104">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2efa-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2efa-105">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="d2efa-106">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="d2efa-106">Compile the code</span></span>  

 <span data-ttu-id="d2efa-107">Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2efa-107">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d2efa-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d2efa-108">Robust Programming</span></span>  

 <span data-ttu-id="d2efa-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d2efa-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d2efa-110">Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="d2efa-110">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="d2efa-111">Dosya var ve salt okunurdur ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="d2efa-111">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="d2efa-112">Yol çok uzun ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="d2efa-112">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d2efa-113">Disk dolu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="d2efa-113">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d2efa-114">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d2efa-114">.NET Framework Security</span></span>  

 <span data-ttu-id="d2efa-115">Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2efa-115">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="d2efa-116">Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın `Create` klasöre erişmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2efa-116">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="d2efa-117">Dosya zaten mevcutsa, uygulamanın yalnızca daha `Write` az bir ayrıcalığa erişmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2efa-117">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="d2efa-118">Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve `Read` `Create` bir klasör için erişim yerine yalnızca tek bir dosyaya erişim izni verir.</span><span class="sxs-lookup"><span data-stu-id="d2efa-118">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2efa-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2efa-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="d2efa-120">Nasıl yapılır: bir XML dosyasından nesne verilerini okuma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2efa-120">How to: Read Object Data from an XML File (Visual Basic)</span></span>](how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="d2efa-121">Serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2efa-121">Serialization (Visual Basic)</span></span>](index.md)
