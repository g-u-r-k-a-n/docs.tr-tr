---
title: IHostTask::Alert Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: b2fc1d6c45eb72410ccfa1071064aa1a31ae46e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121401"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="9c624-102">IHostTask::Alert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c624-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="9c624-103">Konağın geçerli [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tarafından temsil edilen görevi uyandırmasını ve bu nedenle görevin iptal edileceğini ister.</span><span class="sxs-lookup"><span data-stu-id="9c624-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c624-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c624-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9c624-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c624-105">Return Value</span></span>  
  
|<span data-ttu-id="9c624-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c624-106">HRESULT</span></span>|<span data-ttu-id="9c624-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c624-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c624-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c624-108">S_OK</span></span>|<span data-ttu-id="9c624-109">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9c624-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="9c624-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c624-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c624-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9c624-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c624-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c624-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c624-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9c624-113">The call timed out.</span></span>|  
|<span data-ttu-id="9c624-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c624-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c624-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9c624-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c624-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c624-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c624-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9c624-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c624-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="9c624-118">E_FAIL</span></span>|<span data-ttu-id="9c624-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9c624-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c624-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9c624-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c624-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c624-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c624-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c624-122">Remarks</span></span>  
 <span data-ttu-id="9c624-123">CLR, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> kullanıcı kodundan çağrıldığında veya geçerli <xref:System.Threading.Thread> ilişkili <xref:System.AppDomain> kapandığında `Alert` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="9c624-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="9c624-124">Çağrı zaman uyumsuz olarak yapıldığından, konağın hemen dönmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c624-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="9c624-125">Ana bilgisayar, görevi hemen uyarçıkaramaz, uyarı almak için bir sonraki duruma girmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c624-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c624-126">`Alert`, yalnızca çalışma zamanının [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerini [JOIN](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)gibi yöntemlere geçirdiğine yönelik görevleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="9c624-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c624-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c624-127">Requirements</span></span>  
 <span data-ttu-id="9c624-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c624-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c624-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9c624-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c624-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9c624-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c624-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c624-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c624-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c624-132">See also</span></span>

- [<span data-ttu-id="9c624-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c624-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9c624-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c624-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9c624-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c624-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9c624-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c624-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
