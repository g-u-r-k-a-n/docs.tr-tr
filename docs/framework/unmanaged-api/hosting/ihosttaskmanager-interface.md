---
title: IHostTaskManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: deb14d291bfd511e8f3534f3c5e32787c259c5e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673117"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="0a107-102">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a107-102">IHostTaskManager Interface</span></span>

<span data-ttu-id="0a107-103">Ortak dil çalışma zamanının (CLR) standart işletim sistemi iş parçacığı veya fiber işlevlerini kullanmak yerine ana bilgisayar aracılığıyla görevlerle çalışmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a107-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a107-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0a107-104">Methods</span></span>  
  
|<span data-ttu-id="0a107-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0a107-105">Method</span></span>|<span data-ttu-id="0a107-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a107-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a107-107">BeginDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-107">BeginDelayAbort Method</span></span>](ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="0a107-108">Ana bilgisayara, yönetilen kodun geçerli görevin durdurulmayan bir dönem girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="0a107-109">BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-109">BeginThreadAffinity Method</span></span>](ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="0a107-110">Yönetilen koda, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken bir dönem girmediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="0a107-111">CallNeedsHostHook Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-111">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="0a107-112">Ana bilgisayarın, ortak dil çalışma zamanının yönetilmeyen bir işleve belirtilen çağrıyı satır içinde yapıp gerçekleştiremeyeceğini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a107-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="0a107-113">CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-113">CreateTask Method</span></span>](ihosttaskmanager-createtask-method.md)|<span data-ttu-id="0a107-114">Konağın yeni bir görev oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="0a107-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="0a107-115">EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-115">EndDelayAbort Method</span></span>](ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="0a107-116">Daha önceki bir çağrısından sonra, yönetilen kodun geçerli görevin durdurulmadıkları dönemden çıkış yaptığını ana bilgisayara bildirir `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="0a107-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="0a107-117">EndThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-117">EndThreadAffinity Method</span></span>](ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="0a107-118">Yönetilen kodun, önceki bir çağrısından sonra geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken dönemden çıkış olduğunu bildirir `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="0a107-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="0a107-119">EnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-119">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="0a107-120">Ana bilgisayara platform çağırma yöntemi gibi yönetilmeyen bir yönteme yapılan çağrının, CLR 'ye yürütme denetimi döndürdüğünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="0a107-121">GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-121">GetCurrentTask Method</span></span>](ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="0a107-122">Bu çağrının yapıldığı işletim sistemi iş parçacığında yürütülmekte olan göreve yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="0a107-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="0a107-123">GetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-123">GetStackGuarantee Method</span></span>](ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="0a107-124">Bir yığın işlemi tamamlandıktan sonra, ancak bir işlemin kapatılmadan önce kullanılabilir olması garanti edilen yığın alanı miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="0a107-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="0a107-125">LeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-125">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="0a107-126">Yönetilmeyen bir işleve çağrı yapmak için yönetilen kodun ilgili olduğu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="0a107-127">ReverseEnterRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-127">ReverseEnterRuntime Method</span></span>](ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="0a107-128">Ana bilgisayara, yönetilmeyen koddan ortak dil çalışma zamanı (CLR) için bir çağrının yapıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="0a107-129">ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-129">ReverseLeaveRuntime Method</span></span>](ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="0a107-130">Denetimin CLR 'den ayrıldığını ve yönetilen koddan çağrılan yönetilmeyen bir işlevi girdiğini ana bilgisayara bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="0a107-131">SetCLRTaskManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-131">SetCLRTaskManager Method</span></span>](ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="0a107-132">Bir konağa, CLR tarafından uygulanan bir [ICLRTaskManager](iclrtaskmanager-interface.md) örneğine yönelik arabirim işaretçisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a107-132">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="0a107-133">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-133">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="0a107-134">Konağa CLR 'nin geçerli görevdeki yerel ayarı değiştirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="0a107-135">SetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-135">SetStackGuarantee Method</span></span>](ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="0a107-136">Yalnızca iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0a107-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="0a107-137">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-137">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="0a107-138">Ana bilgisayara, geçerli görevde Kullanıcı arabirimi yerel ayarının değiştirildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="0a107-139">Sleep Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-139">Sleep Method</span></span>](ihosttaskmanager-sleep-method.md)|<span data-ttu-id="0a107-140">Ana bilgisayara geçerli görevin uykuya geçmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="0a107-141">SwitchToTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a107-141">SwitchToTask Method</span></span>](ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="0a107-142">Ana bilgisayara geçerli görevi geçiş yapmak zorunda olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0a107-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a107-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a107-143">Remarks</span></span>  

 <span data-ttu-id="0a107-144">`IHostTaskManager` , yönetilen sunucudan yönetilmeyen koddan ve tam tersi yönde aktarım yapıldığında ve ana bilgisayarın kod yürütmesi sırasında gerçekleştirebileceği belirli eylemleri belirtmek için, CLR 'nin görev oluşturmasına ve yönetmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="0a107-144">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a107-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a107-145">Requirements</span></span>  

 <span data-ttu-id="0a107-146">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a107-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a107-147">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a107-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a107-148">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0a107-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a107-149">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a107-149">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a107-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a107-150">See also</span></span>

- [<span data-ttu-id="0a107-151">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a107-151">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="0a107-152">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a107-152">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0a107-153">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a107-153">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0a107-154">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0a107-154">Hosting Interfaces</span></span>](hosting-interfaces.md)
