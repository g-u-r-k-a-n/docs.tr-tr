---
title: Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: 2ec958cc035ac62086cdd3e2844811accc181d47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048812"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="1d33d-102">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime</span><span class="sxs-lookup"><span data-stu-id="1d33d-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="1d33d-103">En yeni içeriğin istemci uygulamasına döndürülmesini sağlamak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en tutucu önbellek ilkesiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="1d33d-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="1d33d-104">Bu konudaki tüm örnekler, 1 Ocak'ta önbelleğe alınmış ve 4 Ocak'ta süresi dolan bir kaynağın önbellek ilkesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d33d-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="1d33d-105">Aşağıdaki örnekler, maksimum yaş ( ) ve minimum tazelik (`maxAge`)`minFresh`değerlerinin etkileşiminden kaynaklanan önbellek ilkesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1d33d-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="1d33d-106">Önbellek ilkesi = `maxAge` 2 gün `minFresh` belirler ve belirtilmemişse, içerik 3 Ocak'ta yeniden geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="1d33d-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="1d33d-107">Önbellek ilkesi = `maxAge` 2 gün `minFresh` ve = 1 `maxAge`gün olarak ayarlanırsa, içeriği 3 Ocak'a kadar tazedir.</span><span class="sxs-lookup"><span data-stu-id="1d33d-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="1d33d-108">Göre `minFresh`, içerik 3 Ocak'a kadar taze.</span><span class="sxs-lookup"><span data-stu-id="1d33d-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="1d33d-109">Bu nedenle, içeriğin 3 Ocak'ta yeniden onaylanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d33d-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="1d33d-110">Önbellek ilkesi = `maxAge` 2 gün `minFresh` ve = 2 `maxAge`gün olarak ayarlanırsa, içeriği 3 Ocak'a kadar tazedir.</span><span class="sxs-lookup"><span data-stu-id="1d33d-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="1d33d-111">İçeriä `minFresh` e günü2 Ocak' a kadar taze.</span><span class="sxs-lookup"><span data-stu-id="1d33d-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="1d33d-112">Bu nedenle, içeriğin 2 Ocak'ta yeniden onaylanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d33d-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d33d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d33d-113">See also</span></span>

- [<span data-ttu-id="1d33d-114">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="1d33d-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="1d33d-115">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="1d33d-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="1d33d-116">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="1d33d-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="1d33d-117">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="1d33d-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="1d33d-118">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1d33d-118">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="1d33d-119">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime</span><span class="sxs-lookup"><span data-stu-id="1d33d-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
