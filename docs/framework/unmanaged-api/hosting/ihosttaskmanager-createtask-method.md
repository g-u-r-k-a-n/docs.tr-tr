---
title: IHostTaskManager::CreateTask Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: 7fdf25d44bdf630e306cf0f5dcb3387a3b0f7c76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731689"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="883d3-102">IHostTaskManager::CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="883d3-102">IHostTaskManager::CreateTask Method</span></span>

<span data-ttu-id="883d3-103">Konağın yeni bir görev oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="883d3-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="883d3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="883d3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="883d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="883d3-105">Parameters</span></span>  

 `stacksize`  
 <span data-ttu-id="883d3-106">'ndaki İstenen yığının bayt cinsinden istenen boyutu veya varsayılan boyut için 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="883d3-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="883d3-107">'ndaki Görevin yürütüleceği işleve yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="883d3-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="883d3-108">'ndaki İşleve geçirilecek Kullanıcı verilerine yönelik bir işaretçi veya işlev hiçbir parametre alırsa null.</span><span class="sxs-lookup"><span data-stu-id="883d3-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="883d3-109">dışı Konak tarafından oluşturulan bir [IHostTask](ihosttask-interface.md) örneğinin adresine yönelik bir işaretçi veya görev oluşturulanmadıysa null.</span><span class="sxs-lookup"><span data-stu-id="883d3-109">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="883d3-110">Görev, [IHostTask:: Start](ihosttask-start-method.md)çağrısıyla açıkça başlatılana kadar askıya alınmış durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="883d3-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="883d3-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="883d3-111">Return Value</span></span>  
  
|<span data-ttu-id="883d3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="883d3-112">HRESULT</span></span>|<span data-ttu-id="883d3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="883d3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="883d3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="883d3-114">S_OK</span></span>|<span data-ttu-id="883d3-115">`CreateTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="883d3-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="883d3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="883d3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="883d3-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="883d3-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="883d3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="883d3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="883d3-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="883d3-119">The call timed out.</span></span>|  
|<span data-ttu-id="883d3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="883d3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="883d3-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="883d3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="883d3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="883d3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="883d3-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="883d3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="883d3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="883d3-124">E_FAIL</span></span>|<span data-ttu-id="883d3-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="883d3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="883d3-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="883d3-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="883d3-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="883d3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="883d3-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="883d3-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="883d3-129">İstenen görevi oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="883d3-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="883d3-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="883d3-130">Remarks</span></span>  

 <span data-ttu-id="883d3-131">CLR, `CreateTask` konağın yeni bir görev oluşturmasını istemek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="883d3-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="883d3-132">Konak, bir örneğe bir arabirim işaretçisi döndürür `IHostTask` .</span><span class="sxs-lookup"><span data-stu-id="883d3-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="883d3-133">Döndürülen görev, öğesine yapılan bir çağrı tarafından açıkça başlatılana kadar askıya alınmalıdır `IHostTask::Start` .</span><span class="sxs-lookup"><span data-stu-id="883d3-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="883d3-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="883d3-134">Requirements</span></span>  

 <span data-ttu-id="883d3-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="883d3-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="883d3-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="883d3-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="883d3-137">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="883d3-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="883d3-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="883d3-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="883d3-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="883d3-139">See also</span></span>

- [<span data-ttu-id="883d3-140">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="883d3-140">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="883d3-141">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="883d3-141">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="883d3-142">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="883d3-142">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="883d3-143">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="883d3-143">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
