---
title: Konum Temelli Önbellek İlkeleri
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
ms.openlocfilehash: 22d99111cd22ef24603f3cdd213c9c9afac5a974
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242207"
---
# <a name="location-based-cache-policies"></a><span data-ttu-id="0944d-102">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="0944d-102">Location-Based Cache Policies</span></span>

<span data-ttu-id="0944d-103">Konum tabanlı önbellek ilkesi, istenen kaynağın nereden alınabileceğini temel alarak geçerli önbelleğe alınmış girişlerin yeniliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0944d-103">A location-based cache policy defines the freshness of valid cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="0944d-104">Önbelleğe alınmış bir kaynak, kullanılması durumunda sunucu tarafından belirtilen yeniden doğrulama gereksinimlerini ihlal etmezse geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="0944d-104">A cached resource is valid if using it does not does not violate server-specified revalidation requirements.</span></span> <span data-ttu-id="0944d-105">Konum tabanlı önbellek ilkesi, <xref:System.Net.Cache.RequestCachePolicy> veya sınıf oluşturucusu kullanılarak programlı bir şekilde oluşturulur <xref:System.Net.Cache.HttpRequestCachePolicy> .</span><span class="sxs-lookup"><span data-stu-id="0944d-105">A location-based cache policy is created programmatically by using a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class constructor.</span></span> <span data-ttu-id="0944d-106">Konum tabanlı ilke türü, bir <xref:System.Net.Cache.RequestCacheLevel> veya numaralandırma değeri kullanılarak oluşturucuya geçirilir <xref:System.Net.Cache.HttpRequestCacheLevel> .</span><span class="sxs-lookup"><span data-stu-id="0944d-106">The type of location-based policy is passed to the constructor using a <xref:System.Net.Cache.RequestCacheLevel> or <xref:System.Net.Cache.HttpRequestCacheLevel> enumeration value.</span></span> <span data-ttu-id="0944d-107">Konum tabanlı önbellek ilkeleri oluşturan kod örnekleri için bkz. [nasıl yapılır: bir uygulama için Location-Based önbellek Ilkesi ayarlama](how-to-set-a-location-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="0944d-107">For code examples that create location-based cache policies, see [How to: Set a Location-Based Cache Policy for an Application](how-to-set-a-location-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="0944d-108">Aşağıdaki bölümlerde, Köprü Metni Aktarım Protokolü (http ve https) kaynakları için her konum tabanlı önbellek ilkesi türü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0944d-108">The following sections explain each type of location-based cache policy for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
## <a name="cache-if-available-policy"></a><span data-ttu-id="0944d-109">Kullanılabilir Ilke varsa önbelleğe al</span><span class="sxs-lookup"><span data-stu-id="0944d-109">Cache If Available Policy</span></span>  

 <span data-ttu-id="0944d-110">Geçerli bir istenen kaynak yerel önbellekte ise, önbelleğe alınmış kaynak kullanılır; Aksi takdirde, kaynak isteği sunucuya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0944d-110">If a valid requested resource is in the local cache, the cached resource is used; otherwise, the request for the resource is sent to the server.</span></span> <span data-ttu-id="0944d-111">İstenen kaynak, istemci ve sunucu arasındaki herhangi bir önbellekte kullanılabiliyorsa, istek bir ara önbellek tarafından karşılanabilir.</span><span class="sxs-lookup"><span data-stu-id="0944d-111">If the requested resource is available in any cache between the client and the server, the request can be satisfied by an intermediate cache.</span></span>  
  
## <a name="cache-only-policy"></a><span data-ttu-id="0944d-112">Yalnızca önbellek Ilkesi</span><span class="sxs-lookup"><span data-stu-id="0944d-112">Cache Only Policy</span></span>  

 <span data-ttu-id="0944d-113">Geçerli bir istenen kaynak yerel önbellekte ise, önbelleğe alınmış kaynak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0944d-113">If a valid requested resource is in the local cache, the cached resource is used.</span></span> <span data-ttu-id="0944d-114">Bu önbellek ilkesi düzeyi belirtildiğinde, <xref:System.Net.WebException> öğe yerel önbellekte değilse bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0944d-114">When this cache policy level is specified, a <xref:System.Net.WebException> exception is thrown if the item is not in the local cache.</span></span>  
  
## <a name="cache-or-next-cache-only-policy"></a><span data-ttu-id="0944d-115">Yalnızca önbellek veya sonraki önbellek Ilkesi</span><span class="sxs-lookup"><span data-stu-id="0944d-115">Cache Or Next Cache Only Policy</span></span>  

 <span data-ttu-id="0944d-116">Geçerli bir istenen kaynak yerel önbellekte veya yerel alan ağı üzerindeki ara önbellekte ise, önbelleğe alınmış kaynak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0944d-116">If a valid requested resource is in the local cache or an intermediate cache on the local area network, the cached resource is used.</span></span> <span data-ttu-id="0944d-117">Aksi takdirde, bir <xref:System.Net.WebException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0944d-117">Otherwise, a <xref:System.Net.WebException> exception is thrown.</span></span> <span data-ttu-id="0944d-118">HTTP önbelleğe alma protokolünde, bu, tek-if-önbelleğe alınmış önbellek denetim yönergesi kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0944d-118">In the HTTP caching protocol, this is achieved using the only-if-cached cache control directive.</span></span>  
  
## <a name="no-cache-no-store-policy"></a><span data-ttu-id="0944d-119">Önbellekte depolama Ilkesi yok</span><span class="sxs-lookup"><span data-stu-id="0944d-119">No Cache No Store Policy</span></span>  

 <span data-ttu-id="0944d-120">İstenen bir kaynak herhangi bir önbellekten hiçbir şekilde kullanılmaz ve hiçbir şekilde hiçbir önbelleğe yerleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="0944d-120">A requested resource is never used from any cache and is never placed in any cache.</span></span> <span data-ttu-id="0944d-121">İstenen bir kaynak yerel önbellekte mevcutsa, kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="0944d-121">If a requested resource is present in the local cache, it is removed.</span></span> <span data-ttu-id="0944d-122">Bu ilke düzeyi ara önbelleklerin kaynağı kaldırması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0944d-122">This policy level indicates to intermediate caches that they should also remove the resource.</span></span> <span data-ttu-id="0944d-123">HTTP önbelleğe alma protokolünde, bu, depolama önbelleği denetim yönergesi kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0944d-123">In the HTTP caching protocol, this is achieved using the no-store cache control directive.</span></span>  
  
## <a name="refresh-policy"></a><span data-ttu-id="0944d-124">Ilkeyi Yenile</span><span class="sxs-lookup"><span data-stu-id="0944d-124">Refresh Policy</span></span>  

 <span data-ttu-id="0944d-125">İstenen kaynak, sunucudan elde edilmişse veya yerel önbellek dışında bir önbellekte bulunursa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0944d-125">A requested resource can be used if it is obtained from the server or found in a cache other than the local cache.</span></span> <span data-ttu-id="0944d-126">İstek bir ara önbellek tarafından karşılanmadan önce, bu önbelleğin sunucu ile önbelleğe alınmış girişini yeniden doğrulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0944d-126">Before the request can be satisfied by an intermediate cache, that cache must revalidate its cached entry with the server.</span></span> <span data-ttu-id="0944d-127">HTTP önbelleğe alma protokolünde, bu, maksimum yaş = 0 önbellek denetim yönergesi ve No-Cache pragma üst bilgisi kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0944d-127">In the HTTP caching protocol, this is achieved using the max-age = 0 cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="reload-policy"></a><span data-ttu-id="0944d-128">Ilkeyi yeniden yükle</span><span class="sxs-lookup"><span data-stu-id="0944d-128">Reload Policy</span></span>  

 <span data-ttu-id="0944d-129">İstenen kaynaklar sunucudan alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0944d-129">Requested resources must be obtained from the server.</span></span> <span data-ttu-id="0944d-130">Yanıt, yerel önbellekte kaydedilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="0944d-130">The response might be saved in the local cache.</span></span> <span data-ttu-id="0944d-131">HTTP önbelleğe alma protokolünde, bu, önbellek önbelleği denetim yönergesi ve No-Cache pragma üst bilgisi kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0944d-131">In the HTTP caching protocol, this is achieved using the no-cache cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="revalidate-policy"></a><span data-ttu-id="0944d-132">Ilkeyi yeniden doğrula</span><span class="sxs-lookup"><span data-stu-id="0944d-132">Revalidate Policy</span></span>  

 <span data-ttu-id="0944d-133">Önbellekteki kaynağın kopyasını sunucudaki kopyayla karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="0944d-133">Compares the copy of the resource in the cache with the copy on the server.</span></span> <span data-ttu-id="0944d-134">Sunucu üzerindeki kopya yeniyse, isteği karşılamak için kullanılır ve önbellekteki kopyayı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0944d-134">If the copy on the server is newer, it is used to satisfy the request and replaces the copy in the cache.</span></span> <span data-ttu-id="0944d-135">Önbellekteki kopya sunucu kopyasıyla aynıysa, önbelleğe alınan kopya kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0944d-135">If the copy in the cache is the same as the server copy, the cached copy is used.</span></span> <span data-ttu-id="0944d-136">HTTP önbelleğe alma protokolünde bu, koşullu bir istek kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0944d-136">In the HTTP caching protocol, this is achieved using a conditional request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0944d-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0944d-137">See also</span></span>

- [<span data-ttu-id="0944d-138">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="0944d-138">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="0944d-139">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="0944d-139">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="0944d-140">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="0944d-140">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="0944d-141">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0944d-141">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="0944d-142">\<requestCaching> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="0944d-142">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
