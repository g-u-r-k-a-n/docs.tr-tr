---
title: ICLRDebugManager::BeginConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: c5b41e4209141c0396ec8a1da766b80043be8807
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726164"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="097d7-102">ICLRDebugManager::BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="097d7-102">ICLRDebugManager::BeginConnection Method</span></span>

<span data-ttu-id="097d7-103">Bir görev listesini tanımlayıcı ve kolay bir ad ile ilişkilendirmek için ana bilgisayar ile hata ayıklayıcı arasında yeni bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="097d7-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="097d7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="097d7-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="097d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="097d7-105">Parameters</span></span>  

 `dwConnectionId`  
 <span data-ttu-id="097d7-106">'ndaki Ortak dil çalışma zamanı (CLR) görevlerinin listesiyle ilişkilendirilecek tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="097d7-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="097d7-107">'ndaki CLR görevlerinin listesiyle ilişkilendirilecek kolay ad.</span><span class="sxs-lookup"><span data-stu-id="097d7-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="097d7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="097d7-108">Return Value</span></span>  
  
|<span data-ttu-id="097d7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="097d7-109">HRESULT</span></span>|<span data-ttu-id="097d7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="097d7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="097d7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="097d7-111">S_OK</span></span>|<span data-ttu-id="097d7-112">`BeginConnection` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="097d7-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="097d7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="097d7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="097d7-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="097d7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="097d7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="097d7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="097d7-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="097d7-116">The call timed out.</span></span>|  
|<span data-ttu-id="097d7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="097d7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="097d7-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="097d7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="097d7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="097d7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="097d7-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="097d7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="097d7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="097d7-121">E_FAIL</span></span>|<span data-ttu-id="097d7-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="097d7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="097d7-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="097d7-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="097d7-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="097d7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="097d7-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="097d7-125">E_INVALIDARG</span></span>|<span data-ttu-id="097d7-126">`dwConnectionId` sıfır veya `BeginConnection` Bu değeri kullanarak zaten çağırıldı ya da `dwConnectionId` `szConnectionName` null idi.</span><span class="sxs-lookup"><span data-stu-id="097d7-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="097d7-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="097d7-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="097d7-128">Bu bağlantıyla ilişkili görevlerin listesini tutmak için yeterli bellek ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="097d7-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="097d7-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="097d7-129">Remarks</span></span>  

 <span data-ttu-id="097d7-130">[ICLRDebugManager](iclrdebugmanager-interface.md) , `BeginConnection` görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)ve [EndConnection](iclrdebugmanager-endconnection-method.md)olmak üzere üç yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="097d7-130">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="097d7-131">Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="097d7-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="097d7-132">`BeginConnection` İlk olarak yeni bir bağlantı kurmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="097d7-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="097d7-133">`SetConnectionTasks` ileri, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="097d7-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="097d7-134">`EndConnection` , görev listesi ile tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="097d7-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="097d7-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="097d7-135">Requirements</span></span>  

 <span data-ttu-id="097d7-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="097d7-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="097d7-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="097d7-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="097d7-138">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="097d7-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="097d7-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="097d7-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097d7-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="097d7-140">See also</span></span>

- [<span data-ttu-id="097d7-141">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="097d7-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="097d7-142">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="097d7-142">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="097d7-143">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="097d7-143">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="097d7-144">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="097d7-144">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="097d7-145">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="097d7-145">IHostControl Interface</span></span>](ihostcontrol-interface.md)
