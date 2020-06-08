---
title: NTLM ve Kerberos Kimlik Doğrulaması
description: Varsayılan NTLM kimlik doğrulamasının ve Kerberos kimlik doğrulamasının .NET Framework bir uygulama için nasıl çalıştığını öğrenin ve varsayılan olmayan NTLM kimlik doğrulaması hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
ms.openlocfilehash: d91ebca084d84acd4eb8facb82ff08679ec35cd0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502242"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="315c3-103">NTLM ve Kerberos Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="315c3-103">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="315c3-104">Varsayılan NTLM kimlik doğrulaması ve Kerberos kimlik doğrulaması, sunucuyla kimlik doğrulamayı denemek için çağıran uygulamayla ilişkili Microsoft Windows NT Kullanıcı kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="315c3-104">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="315c3-105">Varsayılan olmayan NTLM kimlik doğrulaması kullanılırken, uygulama kimlik doğrulama türünü NTLM olarak ayarlar ve <xref:System.Net.NetworkCredential> Aşağıdaki örnekte gösterildiği gibi kullanıcı adını, parolayı ve etki alanını konağa geçirmek için bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="315c3-105">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 <span data-ttu-id="315c3-106">Uygulama kullanıcısının kimlik bilgilerini kullanarak Internet hizmetlerine bağlanması gereken uygulamalar, aşağıdaki örnekte gösterildiği gibi kullanıcının varsayılan kimlik bilgileriyle bunu yapabilir.</span><span class="sxs-lookup"><span data-stu-id="315c3-106">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 <span data-ttu-id="315c3-107">Negotiate kimlik doğrulama modülü, uzak sunucunun NTLM veya Kerberos kimlik doğrulaması kullanıp kullanmadığını belirler ve uygun yanıtı gönderir.</span><span class="sxs-lookup"><span data-stu-id="315c3-107">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="315c3-108">NTLM kimlik doğrulaması bir ara sunucu üzerinden çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="315c3-108">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315c3-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="315c3-109">See also</span></span>

- [<span data-ttu-id="315c3-110">Temel ve Özet kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="315c3-110">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="315c3-111">İnternet Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="315c3-111">Internet Authentication</span></span>](internet-authentication.md)
