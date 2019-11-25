---
title: <defaultHttpCachePolicy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: c5029a7d1e53c28d0abb232efdc3e0bd2c9658d4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088414"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="d97b3-102">\<defaultHttpCachePolicy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d97b3-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="d97b3-103">HTTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d97b3-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

<span data-ttu-id="d97b3-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d97b3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d97b3-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="d97b3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="d97b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d97b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>\
<span data-ttu-id="d97b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultHttpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="d97b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d97b3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d97b3-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d97b3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d97b3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d97b3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d97b3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d97b3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d97b3-111">Attributes</span></span>  
  
|<span data-ttu-id="d97b3-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d97b3-112">Attribute</span></span>|<span data-ttu-id="d97b3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d97b3-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="d97b3-114">Önbelleğe alınan bir nesnenin süresi dolmadan önce geçen maksimum zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d97b3-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="d97b3-115">Önbelleğe alınmış bir nesne, süresi dolmadan önce, hesaplanan yeniliği geçen en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d97b3-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="d97b3-116">Önbelleğe alınmış bir nesnenin yeni olarak kabul edileceği en kısa süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d97b3-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="d97b3-117">Önbelleğe alma ilkesinin otomatik olup olmadığını veya önbelleğin atlanıp atlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d97b3-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="d97b3-118">Varsayılan değer `BypassCache` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d97b3-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d97b3-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d97b3-119">Child Elements</span></span>  
 <span data-ttu-id="d97b3-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="d97b3-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d97b3-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d97b3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d97b3-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="d97b3-122">Element</span></span>|<span data-ttu-id="d97b3-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d97b3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d97b3-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="d97b3-124">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="d97b3-125">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="d97b3-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d97b3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d97b3-126">Remarks</span></span>  
 <span data-ttu-id="d97b3-127">`policyLevel` özniteliğinin değeri `BypassCache` veya `Default`.</span><span class="sxs-lookup"><span data-stu-id="d97b3-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="d97b3-128">`maximumAge`, `maximumStale`ve `minimumFresh` öğelerinin değerleri, *d*biçimindeki açık bir zaman aralığıdır. *SS*:*dd*:*SS* (gün, saat, dakika, saniye) veya `minValue` ya da `maxValue`sabitler uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="d97b3-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d97b3-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d97b3-129">Configuration Files</span></span>  
 <span data-ttu-id="d97b3-130">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d97b3-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d97b3-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d97b3-131">Example</span></span>  
 <span data-ttu-id="d97b3-132">Aşağıdaki örnek, en az altı saat, iki güne ait maksimum yaş süresi ve dört saatlik en fazla eski süreyi belirtmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d97b3-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d97b3-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d97b3-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="d97b3-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d97b3-134">Network Settings Schema</span></span>](index.md)
