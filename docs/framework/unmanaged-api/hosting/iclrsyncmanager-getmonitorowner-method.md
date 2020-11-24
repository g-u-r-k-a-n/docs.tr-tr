---
title: ICLRSyncManager::GetMonitorOwner Metodu
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
ms.openlocfilehash: a2cb82d8071518af4d4bc3276871f3846a5a5693
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687105"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="d3930-102">ICLRSyncManager::GetMonitorOwner Metodu</span><span class="sxs-lookup"><span data-stu-id="d3930-102">ICLRSyncManager::GetMonitorOwner Method</span></span>

<span data-ttu-id="d3930-103">Belirtilen tanımlama bilgisi tarafından tanımlanan izleyicinin sahibi olan [IHostTask](ihosttask-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="d3930-103">Gets the [IHostTask](ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3930-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d3930-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3930-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3930-105">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="d3930-106">'ndaki İzleyiciyle ilişkili tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="d3930-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="d3930-107">dışı `IHostTask` Şu anda izleyicisine sahip olan bir işaretçi veya hiçbir görevin sahipliği yoksa null.</span><span class="sxs-lookup"><span data-stu-id="d3930-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3930-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d3930-108">Return Value</span></span>  
  
|<span data-ttu-id="d3930-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3930-109">HRESULT</span></span>|<span data-ttu-id="d3930-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3930-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3930-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3930-111">S_OK</span></span>|<span data-ttu-id="d3930-112">`GetMonitorOwner` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d3930-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="d3930-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d3930-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d3930-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d3930-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d3930-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d3930-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d3930-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d3930-116">The call timed out.</span></span>|  
|<span data-ttu-id="d3930-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d3930-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d3930-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d3930-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d3930-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d3930-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d3930-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d3930-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d3930-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d3930-121">E_FAIL</span></span>|<span data-ttu-id="d3930-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d3930-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d3930-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d3930-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d3930-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3930-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3930-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3930-125">Remarks</span></span>  

 <span data-ttu-id="d3930-126">Ana bilgisayar genellikle `GetMonitorOwner` kilitlenme algılama mekanizmanın bir parçası olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="d3930-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="d3930-127">Tanımlama bilgisi [IHostSyncManager:: CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md)çağrısı kullanılarak oluşturulduğunda bir izleyici ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="d3930-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3930-128">İzlemeyi izleyen olayı serbest bırakma çağrısı, bu yönteme yönelik bir çağrı Şu anda bu izleyiciyle ilişkili tanımlama bilgisinde etkinse engelleyebilir, ancak kilitlenmeyecektir —.</span><span class="sxs-lookup"><span data-stu-id="d3930-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="d3930-129">Diğer görevler de bu izleyiciyi almayı deneseler de engelleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="d3930-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="d3930-130">`GetMonitorOwner` her zaman hemen döndürür ve çağrısından sonra herhangi bir zaman çağrılabilir `CreateMonitorEvent` .</span><span class="sxs-lookup"><span data-stu-id="d3930-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="d3930-131">Konağın, bir görevin olayda beklenene kadar beklemesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d3930-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3930-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3930-132">Requirements</span></span>  

 <span data-ttu-id="d3930-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3930-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3930-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3930-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3930-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d3930-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3930-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3930-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3930-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3930-137">See also</span></span>

- [<span data-ttu-id="d3930-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3930-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d3930-139">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3930-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
