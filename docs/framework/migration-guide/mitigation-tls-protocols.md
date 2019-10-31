---
title: 'Azaltma: TLS Protokolleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 2a2f95be92ec08185f627e862b0f62e40a1d764b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126136"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="75494-102">Azaltma: TLS Protokolleri</span><span class="sxs-lookup"><span data-stu-id="75494-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="75494-103">.NET Framework 4,6 ' den başlayarak, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıflarının şu üç protokolden birini kullanmasına izin verilir: TLS 1.0, TLS 1.1 veya TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="75494-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="75494-104">SSL 3.0 protokol ve RC4 şifresi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="75494-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="75494-105">Etki</span><span class="sxs-lookup"><span data-stu-id="75494-105">Impact</span></span>  
 <span data-ttu-id="75494-106">Bu değişiklik şunları etkiler:</span><span class="sxs-lookup"><span data-stu-id="75494-106">This change affects:</span></span>  
  
- <span data-ttu-id="75494-107">SSL kullanan herhangi bir uygulama, şu türlerden birini kullanarak bir HTTPS sunucusu ya da bir yuva sunucusu ile konuşmak için: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>ve <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="75494-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="75494-108">TLS 1.0, TLS 1.1 veya TLS 1,2 desteği için yükseltilemeyen herhangi bir sunucu tarafı uygulama.</span><span class="sxs-lookup"><span data-stu-id="75494-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="75494-109">Azaltma</span><span class="sxs-lookup"><span data-stu-id="75494-109">Mitigation</span></span>  
 <span data-ttu-id="75494-110">Önerilen risk azaltma, sunucu tarafı uygulamayı TLS 1.0, TLS 1.1 veya TLS 1,2 sürümüne yükseltmekle birlikte önerilir.</span><span class="sxs-lookup"><span data-stu-id="75494-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="75494-111">Bu uygun değilse veya istemci uygulamaları bozulur, <xref:System.AppContext> sınıfı iki şekilde bu özelliği devre dışı bırakmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="75494-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="75494-112">Programlı olarak, aşağıdaki gibi bir kod parçacığı kullanarak:</span><span class="sxs-lookup"><span data-stu-id="75494-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="75494-113"><xref:System.Net.ServicePointManager> nesnesi yalnızca bir kez başlatıldığından, bu uyumluluk ayarlarının tanımlanması uygulamanın ilk tarafından yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="75494-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="75494-114">Aşağıdaki satırı App. config dosyanızın [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="75494-114">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="75494-115">Ancak, uygulamayı daha az güvenli hale yaptığından varsayılan davranışın yerine geçen önerilmez.</span><span class="sxs-lookup"><span data-stu-id="75494-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75494-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75494-116">See also</span></span>

- [<span data-ttu-id="75494-117">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="75494-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
