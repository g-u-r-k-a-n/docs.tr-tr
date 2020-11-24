---
title: IHostControl::GetHostManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
ms.openlocfilehash: e340dcb5dc093f965e6c08a24a3d65ed0aa6e07a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680839"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="d1b94-102">IHostControl::GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1b94-102">IHostControl::GetHostManager Method</span></span>

<span data-ttu-id="d1b94-103">Konağın, belirtilen arabirim uygulamasına yönelik bir arabirim işaretçisini alır `IID` .</span><span class="sxs-lookup"><span data-stu-id="d1b94-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1b94-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d1b94-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1b94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1b94-105">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="d1b94-106">'ndaki `IID` Ortak dil çalışma zamanının (CLR) sorguladığını belirten arabirim.</span><span class="sxs-lookup"><span data-stu-id="d1b94-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="d1b94-107">dışı Konak tarafından uygulanan arabirime yönelik bir işaretçi veya konak bu arabirimi desteklemiyorsa NULL.</span><span class="sxs-lookup"><span data-stu-id="d1b94-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1b94-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1b94-108">Return Value</span></span>  
  
|<span data-ttu-id="d1b94-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1b94-109">HRESULT</span></span>|<span data-ttu-id="d1b94-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1b94-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1b94-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1b94-111">S_OK</span></span>|<span data-ttu-id="d1b94-112">`GetHostManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d1b94-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="d1b94-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1b94-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1b94-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d1b94-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d1b94-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1b94-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1b94-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d1b94-116">The call timed out.</span></span>|  
|<span data-ttu-id="d1b94-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1b94-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1b94-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d1b94-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1b94-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1b94-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1b94-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d1b94-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1b94-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1b94-121">E_FAIL</span></span>|<span data-ttu-id="d1b94-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d1b94-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1b94-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d1b94-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1b94-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1b94-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d1b94-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d1b94-125">E_INVALIDARG</span></span>|<span data-ttu-id="d1b94-126">İstenen `IID` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d1b94-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="d1b94-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="d1b94-127">E_NOINTERFACE</span></span>|<span data-ttu-id="d1b94-128">İstenen arabirim desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d1b94-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1b94-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1b94-129">Remarks</span></span>  

 <span data-ttu-id="d1b94-130">CLR, aşağıdaki arabirimlerden birini veya birkaçını destekleyip desteklemediğini öğrenmek için Konağı sorgular:</span><span class="sxs-lookup"><span data-stu-id="d1b94-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="d1b94-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="d1b94-131">IHostMemoryManager</span></span>](ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="d1b94-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d1b94-132">IHostTaskManager</span></span>](ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="d1b94-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="d1b94-133">IHostThreadPoolManager</span></span>](ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="d1b94-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="d1b94-134">IHostIoCompletionManager</span></span>](ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="d1b94-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="d1b94-135">IHostSyncManager</span></span>](ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="d1b94-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="d1b94-136">IHostAssemblyManager</span></span>](ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="d1b94-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="d1b94-137">IHostGCManager</span></span>](ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="d1b94-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="d1b94-138">IHostPolicyManager</span></span>](ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="d1b94-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="d1b94-139">IHostSecurityManager</span></span>](ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="d1b94-140">Ana bilgisayar belirtilen arabirimi destekliyorsa, `ppObject` Bu arabirimin uygulamasına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d1b94-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="d1b94-141">Aksi halde, `ppObject` null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d1b94-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="d1b94-142">Siz `Release` kapatsanız bile, clr konak yöneticilerinde çağrı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="d1b94-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1b94-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1b94-143">Requirements</span></span>  

 <span data-ttu-id="d1b94-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1b94-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1b94-145">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d1b94-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1b94-146">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d1b94-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1b94-147">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1b94-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b94-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1b94-148">See also</span></span>

- [<span data-ttu-id="d1b94-149">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1b94-149">IHostControl Interface</span></span>](ihostcontrol-interface.md)
