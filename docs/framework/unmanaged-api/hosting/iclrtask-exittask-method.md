---
title: ICLRTask::ExitTask Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
ms.openlocfilehash: 9294f149e020cfb22512b4f110d64c5dabb5e777
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762460"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="40f48-102">ICLRTask::ExitTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40f48-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="40f48-103">Geçerli [ICLRTask](iclrtask-interface.md) örneği tarafından temsil edilen görevin sona erme olduğunu ve görevi düzgün bir şekilde kapatmayı denediğinde ortak dil çalışma ZAMANıNı (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="40f48-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f48-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="40f48-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="40f48-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="40f48-105">Return Value</span></span>  
  
|<span data-ttu-id="40f48-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40f48-106">HRESULT</span></span>|<span data-ttu-id="40f48-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40f48-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40f48-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="40f48-108">S_OK</span></span>|<span data-ttu-id="40f48-109">`ExitTask`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="40f48-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="40f48-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="40f48-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="40f48-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="40f48-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="40f48-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="40f48-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="40f48-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="40f48-113">The call timed out.</span></span>|  
|<span data-ttu-id="40f48-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="40f48-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="40f48-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="40f48-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="40f48-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="40f48-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="40f48-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="40f48-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="40f48-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="40f48-118">E_FAIL</span></span>|<span data-ttu-id="40f48-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="40f48-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="40f48-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="40f48-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="40f48-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="40f48-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40f48-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40f48-122">Remarks</span></span>  
 <span data-ttu-id="40f48-123">`ExitTask`bir görevi, yönetilmeyen bir tür kitaplığından bir iş parçacığını ayırmaya benzer şekilde, temiz bir şekilde kapanmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="40f48-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40f48-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40f48-124">Requirements</span></span>  
 <span data-ttu-id="40f48-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40f48-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40f48-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40f48-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40f48-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="40f48-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40f48-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40f48-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f48-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40f48-129">See also</span></span>

- [<span data-ttu-id="40f48-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40f48-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="40f48-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40f48-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="40f48-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40f48-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="40f48-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40f48-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
