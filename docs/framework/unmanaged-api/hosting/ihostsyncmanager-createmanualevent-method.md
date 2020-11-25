---
title: IHostSyncManager::CreateManualEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 67af8f125b2be39138bac5d51148215f3a3acf86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723876"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="a280c-102">IHostSyncManager::CreateManualEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a280c-102">IHostSyncManager::CreateManualEvent Method</span></span>

<span data-ttu-id="a280c-103">El ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a280c-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a280c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a280c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a280c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a280c-105">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="a280c-106">[in] `true` , nesne sinyalse, aksi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="a280c-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="a280c-107">dışı Bir [IHostManualEvent](ihostmanualevent-interface.md) örneğinin adresine yönelik bir işaretçi ya da olay oluşturuoluşturulamadığı takdirde null.</span><span class="sxs-lookup"><span data-stu-id="a280c-107">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a280c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a280c-108">Return Value</span></span>  
  
|<span data-ttu-id="a280c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a280c-109">HRESULT</span></span>|<span data-ttu-id="a280c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a280c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a280c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a280c-111">S_OK</span></span>|<span data-ttu-id="a280c-112">`CreateManualEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a280c-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="a280c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a280c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a280c-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a280c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a280c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a280c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a280c-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a280c-116">The call timed out.</span></span>|  
|<span data-ttu-id="a280c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a280c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a280c-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a280c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a280c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a280c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a280c-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a280c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a280c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a280c-121">E_FAIL</span></span>|<span data-ttu-id="a280c-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a280c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a280c-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a280c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a280c-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a280c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a280c-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a280c-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a280c-126">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="a280c-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a280c-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a280c-127">Remarks</span></span>  

 <span data-ttu-id="a280c-128">`CreateManualEvent``IHostManualEvent` [IHostManualEvent:: Reset](ihostmanualevent-reset-method.md) yöntemine çağrı gerektiren, sinyal olmayan bir duruma ayarlamak için bir el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a280c-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="a280c-129">`CreateManualEvent``CreateEvent`parametresi için belirtilen bir değere sahip Win32 işlevini yansıtır `true` `bManualReset` .</span><span class="sxs-lookup"><span data-stu-id="a280c-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a280c-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a280c-130">Requirements</span></span>  

 <span data-ttu-id="a280c-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a280c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a280c-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a280c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a280c-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a280c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a280c-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a280c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a280c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a280c-135">See also</span></span>

- [<span data-ttu-id="a280c-136">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a280c-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a280c-137">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a280c-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="a280c-138">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a280c-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
