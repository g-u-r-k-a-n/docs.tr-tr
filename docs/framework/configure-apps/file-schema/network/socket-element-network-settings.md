---
title: <socket> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 0e2b369eccfbc658a790ef61a961315a88361669
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089082"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="0f337-102">\<socket> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="0f337-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="0f337-103">Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f337-103">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="0f337-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f337-104">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f337-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f337-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0f337-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f337-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f337-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0f337-107">Attributes</span></span>  
  
|<span data-ttu-id="0f337-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="0f337-108">**Attribute**</span></span>|<span data-ttu-id="0f337-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0f337-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="0f337-110">Yuvanın Yöntem çağrılarını kabul etmek için her zaman tamamlama bağlantı noktalarını kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f337-110">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="0f337-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="0f337-111">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="0f337-112">Yuvanın, bağlantı yöntemi çağrıları için her zaman tamamlama bağlantı noktaları kullanması gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f337-112">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="0f337-113">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="0f337-113">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="0f337-114"><xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>Yuva için kullanılacak varsayılanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f337-114">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="0f337-115">Varsayılan değer, Windows sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0f337-115">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f337-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f337-116">Child Elements</span></span>  
 <span data-ttu-id="0f337-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="0f337-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f337-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f337-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0f337-119">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="0f337-119">**Element**</span></span>|<span data-ttu-id="0f337-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0f337-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0f337-121">ayarlar</span><span class="sxs-lookup"><span data-stu-id="0f337-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="0f337-122">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="0f337-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f337-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f337-123">Remarks</span></span>  
 <span data-ttu-id="0f337-124">`alwaysUseCompletionPortsForAccept`Ve `alwaysUseCompletionPortsForConnect` öznitelikleri,. Namespace içindeki sınıflar tarafından tamamlama bağlantı noktalarının kullanımıyla ilgili varsayılan davranışı belirtmek için kullanılır <xref:System.Net.Sockets?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0f337-124">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="0f337-125">Tamamlanma bağlantı noktaları, yüksek performanslı sunucu uygulamaları için önerilir.</span><span class="sxs-lookup"><span data-stu-id="0f337-125">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="0f337-126">Ve öznitelikleri için varsayılan değer `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="0f337-126">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="0f337-127">, <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> İlgili yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `alwaysUseCompletionPortsForAccept` .</span><span class="sxs-lookup"><span data-stu-id="0f337-127">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="0f337-128">, <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> İlgili yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `alwaysUseCompletionPortsForConnect` .</span><span class="sxs-lookup"><span data-stu-id="0f337-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="0f337-129">`ipProtectionLevel`Öznitelik, <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> bir yuva için kullanılacak varsayılan değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f337-129">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="0f337-130"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Özelliği, aynı bağlantı yerel veya site yerel ön ekine sahip adresler gibi, IPv6 soketi için belirtilen kapsama yönelik bir kısıtlama yapılandırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f337-130">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="0f337-131">Bu seçenek, uygulamaların IPv6 yuvaları üzerinde erişim kısıtlamaları yerleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f337-131">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="0f337-132">Bu tür kısıtlamalar, özel bir LAN üzerinde çalışan bir uygulamanın kendisini dış saldırılara karşı tek ve robustly bir şekilde kendi kendine ister.</span><span class="sxs-lookup"><span data-stu-id="0f337-132">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="0f337-133">Bu seçenek, bir dinleme yuvasının kapsamını widens veya daraltır, uygun olduğunda genel ve özel kullanıcılardan Kısıtlanmamış erişimi etkinleştirir ya da gerektiğinde erişimi yalnızca aynı siteye kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="0f337-133">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="0f337-134">Bu `ipProtectionLevel` öznitelik ayarı yalnızca ilk gelen trafiği etkiler:</span><span class="sxs-lookup"><span data-stu-id="0f337-134">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="0f337-135">Bir yuvada gelen bağlantıları dinleyen bir TCP sunucusu.</span><span class="sxs-lookup"><span data-stu-id="0f337-135">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="0f337-136">Bir yuvada paket alan UDP uygulaması.</span><span class="sxs-lookup"><span data-stu-id="0f337-136">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="0f337-137">Bu yapılandırma ayarı, zaten kurulu olan TCP bağlantılarını etkilemez (trafik her iki yönde kısıtlanır) ve UDP paketleri gönderen bir uygulamayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="0f337-137">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="0f337-138">Öznitelik ayarı için olası değerler, `ipProtectionLevel` numaralandırmada belirtilen tanımlı koruma düzeylerine karşılık gelir ve <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="0f337-138">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="0f337-139">**Öznitelik değeri**</span><span class="sxs-lookup"><span data-stu-id="0f337-139">**Attribute Value**</span></span>|<span data-ttu-id="0f337-140">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0f337-140">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="0f337-141">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="0f337-141">EdgeRestricted</span></span>|<span data-ttu-id="0f337-142">IP koruma düzeyi kenar kısıtlanıyor.</span><span class="sxs-lookup"><span data-stu-id="0f337-142">The IP protection level is edge restricted.</span></span> <span data-ttu-id="0f337-143">Bu değer, Internet 'te çalışacak şekilde tasarlanan uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f337-143">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="0f337-144">Bu ayar, Windows Teredo uygulamasını kullanarak ağ adresi çevirisi (NAT) çapraz geçişine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0f337-144">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="0f337-145">Bu uygulamalar IPv4 güvenlik duvarlarını atlayabilir, bu nedenle uygulamaların açılan bağlantı noktasına yöneltilen Internet saldırılarına karşı sağlamlaştırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f337-145">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="0f337-146">Windows Server 2003 ve Windows XP 'de, bir yuvada IP koruma düzeyi için varsayılan değer kenar kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="0f337-146">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="0f337-147">Kısıtlı</span><span class="sxs-lookup"><span data-stu-id="0f337-147">Restricted</span></span>|<span data-ttu-id="0f337-148">IP koruması düzeyi kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="0f337-148">The IP protection level is restricted.</span></span> <span data-ttu-id="0f337-149">Bu değer, Internet senaryoları uygulamayan intranet uygulamaları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f337-149">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="0f337-150">Bu uygulamalar genellikle Internet stili saldırılara karşı sınanmamıştır veya sağlamlamazlar.</span><span class="sxs-lookup"><span data-stu-id="0f337-150">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="0f337-151">Bu ayar, alınan trafiği yalnızca bağlantı yerel ile sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="0f337-151">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="0f337-152">Sınırsız</span><span class="sxs-lookup"><span data-stu-id="0f337-152">Unrestricted</span></span>|<span data-ttu-id="0f337-153">IP koruması düzeyi Kısıtlanmamış.</span><span class="sxs-lookup"><span data-stu-id="0f337-153">The IP protection level is unrestricted.</span></span> <span data-ttu-id="0f337-154">Bu değer, Windows 'da yerleşik olarak bulunan IPv6 NAT çapraz geçiş özelliğinden faydalanan uygulamalar da dahil olmak üzere tasarlanan uygulamalar tarafından kullanılır (örneğin, Teredo).</span><span class="sxs-lookup"><span data-stu-id="0f337-154">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="0f337-155">Bu uygulamalar IPv4 güvenlik duvarlarını atlayabilir, bu nedenle uygulamaların açılan bağlantı noktasına yöneltilen Internet saldırılarına karşı sağlamlaştırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f337-155">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="0f337-156">Windows Server 2008 R2 ve Windows Vista 'da, bir yuvada IP koruma düzeyi için varsayılan değer Kısıtlamasız olur.</span><span class="sxs-lookup"><span data-stu-id="0f337-156">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="0f337-157">Belirtilmemiş</span><span class="sxs-lookup"><span data-stu-id="0f337-157">Unspecified</span></span>|<span data-ttu-id="0f337-158">IP koruması düzeyi belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="0f337-158">The IP protection level is unspecified.</span></span> <span data-ttu-id="0f337-159">Windows 7 ve Windows Server 2008 R2 'de, bir yuvada IP koruma düzeyi için varsayılan değer belirtilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="0f337-159">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="0f337-160">Öznitelik için varsayılan değer `ipProtectionLevel` **belirtilmemiş**.</span><span class="sxs-lookup"><span data-stu-id="0f337-160">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="0f337-161"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Özelliği, geçerli yapılandırma dosyalarından özniteliğin geçerli değerini almak için kullanılabilir `ipProtectionLevel` .</span><span class="sxs-lookup"><span data-stu-id="0f337-161">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0f337-162">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="0f337-162">Configuration Files</span></span>  
 <span data-ttu-id="0f337-163">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f337-163">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f337-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f337-164">Example</span></span>  
 <span data-ttu-id="0f337-165">Aşağıdaki örnek, tamamlama bağlantı noktalarının kullanılması gerektiğini ve varsayılan değer <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> Kısıtlanmamış olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f337-165">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f337-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f337-166">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="0f337-167">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0f337-167">Network Settings Schema</span></span>](index.md)
