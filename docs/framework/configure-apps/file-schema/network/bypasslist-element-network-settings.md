---
title: <bypasslist> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154952"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="5e29d-102">\<bypasslist> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="5e29d-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="5e29d-103">Proxy kullanmayan adresleri açıklayan bir dizi düzenli ifade sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e29d-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="5e29d-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5e29d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5e29d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5e29d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="5e29d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5e29d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="5e29d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span><span class="sxs-lookup"><span data-stu-id="5e29d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5e29d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e29d-108">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e29d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e29d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5e29d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e29d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e29d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e29d-111">Attributes</span></span>  
 <span data-ttu-id="5e29d-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="5e29d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5e29d-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e29d-113">Child Elements</span></span>  
  
|<span data-ttu-id="5e29d-114">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5e29d-114">**Element**</span></span>|<span data-ttu-id="5e29d-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5e29d-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5e29d-116">Ekle</span><span class="sxs-lookup"><span data-stu-id="5e29d-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="5e29d-117">Proxy bypass listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="5e29d-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="5e29d-118">Temizleyin</span><span class="sxs-lookup"><span data-stu-id="5e29d-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="5e29d-119">Bypass listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="5e29d-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="5e29d-120">Kaldırmak</span><span class="sxs-lookup"><span data-stu-id="5e29d-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="5e29d-121">Proxy bypass listesinden bir IP adresi veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5e29d-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e29d-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e29d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5e29d-123">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5e29d-123">**Element**</span></span>|<span data-ttu-id="5e29d-124">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5e29d-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5e29d-125">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="5e29d-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="5e29d-126">Hypertext Transfer Protocol (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5e29d-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e29d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e29d-127">Remarks</span></span>  
 <span data-ttu-id="5e29d-128">Baypas listesi, proxy sunucusu yerine doğrudan <xref:System.Net.WebRequest> erişim örnekleri uris açıklayan düzenli ifadeler içerir.</span><span class="sxs-lookup"><span data-stu-id="5e29d-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="5e29d-129">Bu öğe için düzenli bir ifade belirtirken dikkatli olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="5e29d-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="5e29d-130">Normal ifade "[a-z]+\\.contoso\\.com" contoso.com etki alanında herhangi bir ana bilgisayar eşleşir, ancak aynı zamanda contoso.com.cpandl.com etki alanında herhangi bir ana bilgisayar eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5e29d-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="5e29d-131">Yalnızca contoso.com etki alanında bir ana bilgisayarla eşleştirmek için bir bağlantı ("$"): "[a-z]+\\.contoso\\.com$" kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e29d-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="5e29d-132">Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET Framework Düzenli İfadeler](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5e29d-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5e29d-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5e29d-133">Configuration Files</span></span>  
 <span data-ttu-id="5e29d-134">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e29d-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e29d-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e29d-135">Example</span></span>  
 <span data-ttu-id="5e29d-136">Aşağıdaki örnek, baypas listesine iki adres ekler.</span><span class="sxs-lookup"><span data-stu-id="5e29d-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="5e29d-137">İlki, contoso.com etki alanında bulunan tüm sunucular için proxy'yi atlar; ikincisi, IP adresleri 192.168 ile başlayan tüm sunucular için proxy'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="5e29d-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e29d-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e29d-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="5e29d-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5e29d-139">Network Settings Schema</span></span>](index.md)
