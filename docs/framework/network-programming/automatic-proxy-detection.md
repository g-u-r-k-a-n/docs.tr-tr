---
title: Otomatik Ara Sunucu Algılama
description: Sistemin bir Web proxy sunucusu tanımladığı ve istemci adına istek göndermek için kullandığı otomatik proxy algılaması hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
ms.openlocfilehash: 8d1b904a8acc6d3960a076c54c2d5f5de54820c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250638"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="dadab-103">Otomatik Ara Sunucu Algılama</span><span class="sxs-lookup"><span data-stu-id="dadab-103">Automatic Proxy Detection</span></span>

<span data-ttu-id="dadab-104">Otomatik proxy algılama, sistem tarafından bir Web proxy sunucusunun tanımlandığı ve istemci adına istek göndermek için kullanılan bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="dadab-104">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="dadab-105">Bu özellik Web proxy otomatik bulma (WPAD) olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="dadab-105">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="dadab-106">Otomatik ara sunucu algılaması etkinleştirildiğinde, sistem, istek için kullanılabilecek proxy kümesini döndürmekten sorumlu bir ara sunucu yapılandırma betiği bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="dadab-106">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="dadab-107">Ara sunucu yapılandırma betiği bulunursa, bir örnek kullanan bir istek için proxy bilgileri, istek akışı veya yanıt elde edildiğinde, komut dosyası indirilir, derlenir ve yerel bilgisayarda çalıştırılır <xref:System.Net.WebProxy> .</span><span class="sxs-lookup"><span data-stu-id="dadab-107">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="dadab-108">Otomatik proxy algılama, sınıfı tarafından gerçekleştirilir <xref:System.Net.WebProxy> ve istek düzeyindeki ayarları, yapılandırma dosyalarındaki ayarları ve Internet Explorer **yerel ağ (LAN)** iletişim kutusu kullanılarak belirtilen ayarları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="dadab-108">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dadab-109">Internet Explorer ana menüsünden **Araçlar** ' ı seçip **Internet seçenekleri**' ni seçerek Internet Explorer **yerel alan ağı (LAN) ayarları** iletişim kutusunu görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dadab-109">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="dadab-110">Sonra, **Bağlantılar** sekmesini seçin ve **LAN ayarları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dadab-110">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="dadab-111">Otomatik ara sunucu algılaması etkinleştirildiğinde, <xref:System.Net.WebProxy> sınıfı proxy yapılandırma betiğini şu şekilde bulmaya çalışır:</span><span class="sxs-lookup"><span data-stu-id="dadab-111">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1. <span data-ttu-id="dadab-112">WinINet `InternetQueryOption` işlevi, Internet Explorer tarafından en son algılanan proxy yapılandırma betiğini bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dadab-112">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2. <span data-ttu-id="dadab-113">Betik bulunamıyorsa, <xref:System.Net.WebProxy> sınıf, betiği bulmak Için dinamik ana bilgisayar Yapılandırma Protokolü 'nü (DHCP) kullanır.</span><span class="sxs-lookup"><span data-stu-id="dadab-113">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="dadab-114">DHCP sunucusu, betiğin konumuyla (ana bilgisayar adıyla) veya komut dosyasının tam URL 'siyle yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="dadab-114">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3. <span data-ttu-id="dadab-115">DHCP, WPAD konağını tanımıyorsa, adı veya diğer adı olarak WPAD içeren bir konak için DNS sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="dadab-115">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4. <span data-ttu-id="dadab-116">Konak tanımlanmamışsa ve bir ara sunucu yapılandırma betiğinin konumu Internet Explorer LAN ayarları veya bir yapılandırma dosyası tarafından belirtilmişse, bu konum kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dadab-116">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dadab-117">NT hizmeti olarak veya ASP.NET kapsamında çalışan uygulamalar, çağıran kullanıcının Internet Explorer proxy sunucu ayarlarını (varsa) kullanır.</span><span class="sxs-lookup"><span data-stu-id="dadab-117">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="dadab-118">Bu ayarlar, tüm hizmet uygulamaları için kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="dadab-118">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="dadab-119">Proxy 'ler, connectoıd temelinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="dadab-119">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="dadab-120">Connectoıd, ağ bağlantısı iletişim kutusundaki bir öğedir ve bir fiziksel ağ aygıtı (bir modem veya Ethernet kartı) veya bir sanal arabirim (bir ağ aygıtı üzerinden çalışan VPN bağlantısı gibi) olabilir.</span><span class="sxs-lookup"><span data-stu-id="dadab-120">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="dadab-121">Bir connectoıd değiştiğinde (örneğin, bir kablosuz bağlantı bir erişim noktasını değiştirdiğinde veya VPN etkinleştirildiğinde), proxy algılama algoritması yeniden çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="dadab-121">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="dadab-122">Varsayılan olarak, Internet Explorer ara sunucu ayarları, proxy 'yi algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dadab-122">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="dadab-123">Uygulamanız etkileşimli olmayan bir hesap altında çalışıyorsa (IE proxy ayarlarını yapılandırmanın kolay bir yolu olmadan) veya IE ayarlarından farklı proxy ayarlarını kullanmak istiyorsanız, tanımlı [ \<defaultProxy> öğe (ağ ayarları)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) ve [ \<proxy> öğe (ağ ayarları)](../configure-apps/file-schema/network/proxy-element-network-settings.md) öğeleriyle bir yapılandırma dosyası oluşturarak proxy 'nizi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dadab-123">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="dadab-124">Oluşturduğunuz istekler için, <xref:System.Net.WebRequest.Proxy%2A> Aşağıdaki kod örneğinde gösterildiği gibi, isteğinize sahip bir null kullanarak istek düzeyinde otomatik proxy algılamayı devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dadab-124">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub
```  
  
 <span data-ttu-id="dadab-125">Proxy olmayan istekler, uygulama etki alanının varsayılan ara sunucusunu kullanır ve bu, <xref:System.Net.WebRequest.DefaultWebProxy%2A> özelliğinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dadab-125">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dadab-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dadab-126">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="dadab-127">\<system.Net> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="dadab-127">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
