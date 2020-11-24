---
title: IHostSemaphore Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
ms.openlocfilehash: cccbf9a28b16ffee14b3fd3ec43c376109d6ccec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683062"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="2f9e5-102">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f9e5-102">IHostSemaphore Interface</span></span>

<span data-ttu-id="2f9e5-103">Ana bilgisayarın iş parçacığı için semafor uygulamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2f9e5-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f9e5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2f9e5-104">Methods</span></span>  
  
|<span data-ttu-id="2f9e5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2f9e5-105">Method</span></span>|<span data-ttu-id="2f9e5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f9e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f9e5-107">ReleaseSemaphore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f9e5-107">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="2f9e5-108">Geçerli `IHostSemaphore` Örneğin sayısını belirtilen miktarda artırır.</span><span class="sxs-lookup"><span data-stu-id="2f9e5-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="2f9e5-109">Wait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f9e5-109">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="2f9e5-110">Geçerli örneğin, `IHostSemaphore` ait olana veya belirtilen süre geçtikten sonra beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f9e5-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f9e5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f9e5-111">Requirements</span></span>  

 <span data-ttu-id="2f9e5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f9e5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f9e5-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f9e5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f9e5-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2f9e5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f9e5-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f9e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9e5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f9e5-116">See also</span></span>

- [<span data-ttu-id="2f9e5-117">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f9e5-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2f9e5-118">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f9e5-118">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="2f9e5-119">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f9e5-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="2f9e5-120">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f9e5-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="2f9e5-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2f9e5-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
