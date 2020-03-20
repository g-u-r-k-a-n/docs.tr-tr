---
title: Güvenli Yuva Katmanı Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
ms.openlocfilehash: ef2abc7574aea1b4f77ff93545ad84678c66ce48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046898"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="83353-102">Güvenli Yuva Katmanı Kullanma</span><span class="sxs-lookup"><span data-stu-id="83353-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="83353-103">Sınıflar, <xref:System.Net> çeşitli ağ protokolleri için bağlantıyı şifrelemek için Güvenli Soketkatmanını (SSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="83353-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="83353-104">Http bağlantıları için <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar, SSL'yi destekleyen web ana bilgisayarlarıyla iletişim kurmak için SSL'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="83353-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="83353-105">SSL'yi kullanma kararı, <xref:System.Net.WebRequest> verilen URI'ye göre sınıf tarafından verilir.</span><span class="sxs-lookup"><span data-stu-id="83353-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="83353-106">URI "https:" ile başlarsa, SSL kullanılır; URI "http:" ile başlarsa, şifrelenmemiş bir bağlantı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="83353-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="83353-107">Dosya Aktarım Protokolü (FTP) ile SSL'yi kullanmak <xref:System.Net.FtpWebRequest.GetResponse>için, aramadan önce <xref:System.Net.FtpWebRequest.EnableSsl> özelliği doğru olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="83353-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="83353-108">Benzer şekilde, Basit Posta Aktarım Protokolü (SMTP) <xref:System.Net.Mail.SmtpClient.EnableSsl> ile SSL kullanmak için, e-posta göndermeden önce gerçek özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="83353-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="83353-109">Sınıf, <xref:System.Net.Security.SslStream> SSL için akış tabanlı bir soyutlama sağlar ve SSL el sıkışmasını yapılandırmanın birçok yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="83353-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83353-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="83353-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="83353-111">Kod</span><span class="sxs-lookup"><span data-stu-id="83353-111">Code</span></span>  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83353-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="83353-112">Compiling the Code</span></span>  
 <span data-ttu-id="83353-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="83353-113">This example requires:</span></span>  
  
- <span data-ttu-id="83353-114">**System.Net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="83353-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83353-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83353-115">See also</span></span>

- [<span data-ttu-id="83353-116">Ağ Programlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="83353-116">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="83353-117">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="83353-117">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="83353-118">Sertifika Seçimi ve Doğrulama</span><span class="sxs-lookup"><span data-stu-id="83353-118">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
