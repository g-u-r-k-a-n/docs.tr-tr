---
title: Saat Temelli Önbellek İlkeleri
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
ms.openlocfilehash: 372621ce55891cb87594e6d059c7bbeeb99f6468
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239425"
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="395c2-102">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="395c2-102">Time-Based Cache Policies</span></span>

<span data-ttu-id="395c2-103">Zaman tabanlı önbellek ilkesi, kaynağın alındığı zamanı, kaynakla döndürülen üstbilgileri ve geçerli saati kullanarak önbelleğe alınmış girişlerin yeniliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="395c2-103">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="395c2-104">Zaman tabanlı bir önbellek ilkesi ayarlarken, <xref:System.Net.Cache.HttpRequestCacheLevel.Default> zaman tabanlı ilkeyi kullanabilir veya özelleştirilmiş zaman tabanlı bir ilke oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="395c2-104">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="395c2-105">Köprü Metni Aktarım Protokolü (HTTP) kullanılarak elde edilen kaynaklar için varsayılan zaman tabanlı ilkeyi kullanırken, tam önbellek davranışı, önbelleğe alınan yanıtta yer alan üst bilgiler ve [Internet Mühendisliği görev zorlaması (IETF)](https://www.ietf.org/) Web sitesinde bulunabilir 2616 ve 13. bölümde belirtilen davranışlar tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="395c2-105">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="395c2-106">HTTP kaynakları için varsayılan zaman tabanlı ilkeyi ayarlamayı gösteren bir kod örneği için, bkz. [nasıl yapılır: bir uygulama Için varsayılan Time-Based önbellek Ilkesini ayarlama](how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="395c2-106">For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="395c2-107">Önbellek ilkeleri oluşturmayı ve kullanmayı gösteren kod örnekleri için bkz. [Ağ uygulamalarında önbelleğe alma yapılandırma](configuring-caching-in-network-applications.md).</span><span class="sxs-lookup"><span data-stu-id="395c2-107">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="395c2-108">Önbelleğe alınmış girişlerin yeniliği belirleme ölçütleri</span><span class="sxs-lookup"><span data-stu-id="395c2-108">Criteria to Determine Freshness of Cached Entries</span></span>  

 <span data-ttu-id="395c2-109">Zaman tabanlı bir önbellek ilkesini özelleştirmek için, aşağıdaki ölçütlerden birini veya daha fazlasını, önbelleğe alınmış girişlerin yeniliği belirlemek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="395c2-109">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
- <span data-ttu-id="395c2-110">Maksimum yaş</span><span class="sxs-lookup"><span data-stu-id="395c2-110">Maximum age</span></span>  
  
- <span data-ttu-id="395c2-111">Maksimum Eskime durumu</span><span class="sxs-lookup"><span data-stu-id="395c2-111">Maximum staleness</span></span>  
  
- <span data-ttu-id="395c2-112">En düşük yenilik</span><span class="sxs-lookup"><span data-stu-id="395c2-112">Minimum freshness</span></span>  
  
- <span data-ttu-id="395c2-113">Önbellek eşitleme tarihi</span><span class="sxs-lookup"><span data-stu-id="395c2-113">Cache synchronization date</span></span>  
  
> [!NOTE]
> <span data-ttu-id="395c2-114">Varsayılan süre tabanlı önbellek ilkesinin kullanılması, uygulamanız için varsayılan önbellek ilkesi ayarlanarak karıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="395c2-114">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="395c2-115">Varsayılan zaman tabanlı ilke, istek veya uygulama düzeyinde kullanılabilen belirli bir ilkedir.</span><span class="sxs-lookup"><span data-stu-id="395c2-115">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="395c2-116">Uygulamanız için varsayılan önbellek ilkesi, bir istekte hiçbir ilke ayarlanmamışsa geçerli olan bir ilkedir (konum tabanlı veya zaman tabanlı).</span><span class="sxs-lookup"><span data-stu-id="395c2-116">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="395c2-117">Uygulamanız için varsayılan önbellek ilkesi ayarlama hakkında daha fazla bilgi için bkz <xref:System.Net.WebRequest.DefaultCachePolicy%2A> ..</span><span class="sxs-lookup"><span data-stu-id="395c2-117">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="395c2-118">Maksimum yaş</span><span class="sxs-lookup"><span data-stu-id="395c2-118">Maximum Age</span></span>  

 <span data-ttu-id="395c2-119">Maksimum yaş ilkesi ölçütü, bir kaynağın önbelleğe alınmış kopyasının kullanılabileceği süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="395c2-119">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="395c2-120">Kaynağın önbelleğe alınmış kopyası belirtilen süreden daha eskiyse, kaynak sunucu üzerindeki içeriğe karşı denetlenerek yeniden doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="395c2-120">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="395c2-121">En fazla yaş kaynağın süresi dolduktan sonra kullanılmasına izin veracaksa, en yüksek bir stalet değeri de belirtilmediği takdirde bu ölçüt kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="395c2-121">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="395c2-122">Maksimum Eskime durumu</span><span class="sxs-lookup"><span data-stu-id="395c2-122">Maximum Staleness</span></span>  

 <span data-ttu-id="395c2-123">En yüksek stalet ilkesi ölçütü, kaynağın önbelleğe alınmış kopyasının kullanılabileceği içerik süresi dolduktan sonraki sürenin uzunluğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="395c2-123">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="395c2-124">Bu, kaynakların süre dolduktan sonra kullanılmasına izin veren tek önbellek ilkesi ölçütünüz.</span><span class="sxs-lookup"><span data-stu-id="395c2-124">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="395c2-125">En düşük yenilik</span><span class="sxs-lookup"><span data-stu-id="395c2-125">Minimum Freshness</span></span>  

 <span data-ttu-id="395c2-126">Minimum yeniliği ilke ölçütü, kaynağın önbelleğe alınmış kopyasının kullanılabileceği içerik süresinin dolması için geçen sürenin uzunluğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="395c2-126">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="395c2-127">Bu ilke, bir önbellek girişinin süre sonu tarihinden önce sona ermesine neden olan etkileri sağlar; Bu nedenle, en düşük yenilik ve en yüksek stalet ayarları birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="395c2-127">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="395c2-128">Önbellek eşitleme tarihi</span><span class="sxs-lookup"><span data-stu-id="395c2-128">Cache Synchronization Date</span></span>  

 <span data-ttu-id="395c2-129">Önbellek eşitleme tarihi ilke ölçütü, bir kaynağın önbelleğe alınmış kopyasının, sunucudaki içeriğe karşı denetlenerek yeniden doğrulanması gerektiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="395c2-129">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="395c2-130">İçerik, öğe önbelleğe alındıktan sonra değiştirildiyse, sunucudan alınır, önbellekte depolanır ve uygulamaya döndürülür.</span><span class="sxs-lookup"><span data-stu-id="395c2-130">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="395c2-131">İçerik değiştirilmediyse, zaman damgası güncellenir ve uygulama önbelleğe alınmış içeriği alır.</span><span class="sxs-lookup"><span data-stu-id="395c2-131">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="395c2-132">Önbellek eşitleme tarihi, önbelleğe alınmış içeriklerin yeniden doğrulanması gerektiğinde mutlak bir tarih belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="395c2-132">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="395c2-133">Önbellek eşitleme tarihinden önce yeni bir önbellek girişinin yeniden doğrulanması durumunda sunucu ile yeniden doğrulama işlemi devam eder.</span><span class="sxs-lookup"><span data-stu-id="395c2-133">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="395c2-134">Önbellek girişi önbellek eşitleme tarihinden sonra yeniden doğrulandıysa ve önbellekteki girişi geçersiz kılan ek bir yenilik veya sunucu yeniden doğrulama gereksinimi yoksa, önbellekten gelen giriş kullanılır.</span><span class="sxs-lookup"><span data-stu-id="395c2-134">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="395c2-135">Önbellek eşitleme tarihi gelecek bir tarih olarak ayarlandıysa, önbellek eşitleme tarihi geçirilmeden, giriş her istendiğinde yeniden onaylanır.</span><span class="sxs-lookup"><span data-stu-id="395c2-135">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="395c2-136">Aşağıdaki konular, zaman tabanlı önbellek ilkesi ölçütlerini birleştirmenin etkileri hakkında bilgi sağlar:</span><span class="sxs-lookup"><span data-stu-id="395c2-136">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
- [<span data-ttu-id="395c2-137">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime</span><span class="sxs-lookup"><span data-stu-id="395c2-137">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [<span data-ttu-id="395c2-138">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime</span><span class="sxs-lookup"><span data-stu-id="395c2-138">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="395c2-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="395c2-139">See also</span></span>

- [<span data-ttu-id="395c2-140">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="395c2-140">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="395c2-141">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="395c2-141">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="395c2-142">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="395c2-142">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="395c2-143">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="395c2-143">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="395c2-144">\<requestCaching> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="395c2-144">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
