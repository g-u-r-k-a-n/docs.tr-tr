---
title: ICLRTask::SetTaskIdentifier Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
ms.openlocfilehash: d1f731e00d4917b997dfba392cb9b6ce2afc082e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690752"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="a300e-102">ICLRTask::SetTaskIdentifier Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a300e-102">ICLRTask::SetTaskIdentifier Method</span></span>

<span data-ttu-id="a300e-103">Ortak dil çalışma zamanını (CLR), belirtilen tanımlayıcı değerini geçerli [ICLRTask](iclrtask-interface.md) örneğiyle temsil edilen görevle ilişkilendider.</span><span class="sxs-lookup"><span data-stu-id="a300e-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a300e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a300e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a300e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a300e-105">Parameters</span></span>  

 `Asked`  
 <span data-ttu-id="a300e-106">'ndaki Geçerli örnek tarafından temsil edilen görevle ilişkilendirilecek ortak dil çalışma zamanı için benzersiz tanımlayıcı `ICLRTask` .</span><span class="sxs-lookup"><span data-stu-id="a300e-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a300e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a300e-107">Return Value</span></span>  
  
|<span data-ttu-id="a300e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a300e-108">HRESULT</span></span>|<span data-ttu-id="a300e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a300e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a300e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a300e-110">S_OK</span></span>|<span data-ttu-id="a300e-111">`SetTaskIdentifier` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a300e-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="a300e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a300e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a300e-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a300e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a300e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a300e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a300e-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a300e-115">The call timed out.</span></span>|  
|<span data-ttu-id="a300e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a300e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a300e-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a300e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a300e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a300e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a300e-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a300e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a300e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a300e-120">E_FAIL</span></span>|<span data-ttu-id="a300e-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a300e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a300e-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a300e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a300e-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a300e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a300e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a300e-124">Remarks</span></span>  

 <span data-ttu-id="a300e-125">Konak, bir tanıtıcıyı bir tanıtıcı ile ilişkilendirebilir ve bir hata ayıklama ortamında CLR ve Konağı tümleştirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a300e-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="a300e-126">Tanımlayıcının CLR için anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="a300e-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="a300e-127">CLR onu bir hata ayıklayıcı uygulamasına geçirir.</span><span class="sxs-lookup"><span data-stu-id="a300e-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="a300e-128">Hata ayıklayıcı, bir CLR çağrı yığınını bir konak çağrı yığını ile ilişkilendirmek için bu tanımlayıcıyı kullanabilir ve hata ayıklayıcının Kullanıcı arabiriminde görüntülendiklerinde kendi izleme bilgilerini Birleşik hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a300e-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a300e-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a300e-129">Requirements</span></span>  

 <span data-ttu-id="a300e-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a300e-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a300e-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a300e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a300e-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a300e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a300e-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a300e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a300e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a300e-134">See also</span></span>

- [<span data-ttu-id="a300e-135">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a300e-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a300e-136">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a300e-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a300e-137">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a300e-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a300e-138">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a300e-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
