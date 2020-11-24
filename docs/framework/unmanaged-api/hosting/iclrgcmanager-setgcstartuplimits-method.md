---
title: ICLRGCManager::SetGCStartupLimits Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
ms.openlocfilehash: 169d344975762b97f89e8dc32d72f2b9c95fea11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678187"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="b189e-102">ICLRGCManager::SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b189e-102">ICLRGCManager::SetGCStartupLimits Method</span></span>

<span data-ttu-id="b189e-103">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b189e-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b189e-104">4,5 .NET Framework başlayarak, segment boyutunu ve en fazla nesil 0 boyutunu `DWORD` [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini kullanarak daha büyük değerlere ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b189e-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b189e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b189e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b189e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b189e-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="b189e-107">'ndaki Bir çöp toplama kesiminin belirtilen boyutu.</span><span class="sxs-lookup"><span data-stu-id="b189e-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="b189e-108">En küçük kesim boyutu 4 MB 'tır.</span><span class="sxs-lookup"><span data-stu-id="b189e-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="b189e-109">Segmentler, 1 MB veya daha büyük artışlarla artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b189e-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="b189e-110">'ndaki Oluşturma 0 için belirtilen en büyük boyut.</span><span class="sxs-lookup"><span data-stu-id="b189e-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="b189e-111">Minimum nesil 0 boyutu 64 KB 'tır.</span><span class="sxs-lookup"><span data-stu-id="b189e-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b189e-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b189e-112">Return Value</span></span>  
  
|<span data-ttu-id="b189e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b189e-113">HRESULT</span></span>|<span data-ttu-id="b189e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b189e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b189e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b189e-115">S_OK</span></span>|<span data-ttu-id="b189e-116">`SetGCStartupLimits` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b189e-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="b189e-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b189e-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b189e-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b189e-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b189e-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b189e-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b189e-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b189e-120">The call timed out.</span></span>|  
|<span data-ttu-id="b189e-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b189e-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b189e-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b189e-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b189e-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b189e-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b189e-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b189e-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b189e-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b189e-125">E_FAIL</span></span>|<span data-ttu-id="b189e-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b189e-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b189e-127">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b189e-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b189e-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b189e-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b189e-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b189e-129">Remarks</span></span>  

 <span data-ttu-id="b189e-130">`SetGCStartupLimits`Ayarlayan değerler yalnızca bir kez belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b189e-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="b189e-131">Daha sonraki çağrıları `SetGCStartupLimits` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="b189e-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b189e-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b189e-132">Requirements</span></span>  

 <span data-ttu-id="b189e-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b189e-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b189e-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b189e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b189e-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b189e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b189e-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b189e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b189e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b189e-137">See also</span></span>

- [<span data-ttu-id="b189e-138">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="b189e-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="b189e-139">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="b189e-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="b189e-140">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b189e-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b189e-141">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b189e-141">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
