---
title: ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
ms.openlocfilehash: fcf034d93ceb7ececd5f6c71708d442f62a00f65
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092259"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="768db-102">ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="768db-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="768db-103">Ortak dil çalışma zamanının (CLR), bir okuyucu-yazıcı kilidinde bekleyen görev kümesini belirlemede kullanacağı konak için bir yineleyici oluşturmasını ister.</span><span class="sxs-lookup"><span data-stu-id="768db-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="768db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="768db-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="768db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="768db-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="768db-106">'ndaki İstenen okuyucu-yazıcı kilidi ile ilişkili tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="768db-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="768db-107">dışı [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) ve [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemlerine geçirilebileceğini bir yineleyici işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="768db-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="768db-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="768db-108">Return Value</span></span>  
  
|<span data-ttu-id="768db-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="768db-109">HRESULT</span></span>|<span data-ttu-id="768db-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="768db-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="768db-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="768db-111">S_OK</span></span>|<span data-ttu-id="768db-112">`CreateRWLockOwnerIterator` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="768db-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="768db-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="768db-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="768db-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="768db-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="768db-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="768db-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="768db-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="768db-116">The call timed out.</span></span>|  
|<span data-ttu-id="768db-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="768db-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="768db-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="768db-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="768db-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="768db-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="768db-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="768db-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="768db-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="768db-121">E_FAIL</span></span>|<span data-ttu-id="768db-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="768db-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="768db-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="768db-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="768db-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="768db-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="768db-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="768db-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="768db-126">`CreateRWLockOwnerIterator`, şu anda yönetilen kodu çalıştıran bir iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="768db-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="768db-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="768db-127">Remarks</span></span>  
 <span data-ttu-id="768db-128">Konaklar genellikle kilitlenme algılaması sırasında `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`ve `GetRWLockOwnerNext` yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="768db-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="768db-129">CLR, okuyucu-yazıcı kilidini canlı tutmaya hiçbir girişim olmadığından, okuyucu-yazıcı kilidinin hala geçerli olduğundan emin olmak için ana bilgisayar sorumludur.</span><span class="sxs-lookup"><span data-stu-id="768db-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="768db-130">Kilit geçerliliğini sağlamak için ana bilgisayar için birkaç strateji mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="768db-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="768db-131">Ana bilgisayar okuyucu-yazıcı kilidinde (örneğin, [ıhostsemafor:: releasesemafor](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) yayın çağrılarını engelleyebilir, bu da bloğun kilitlenmeye neden olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="768db-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="768db-132">Ana bilgisayar, okuyucu-yazıcı kilidi ile ilişkili olay nesnesi üzerinde beklemeyi, bu bloğun kilitlenmeye neden olmamasını sağlamak üzere engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="768db-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="768db-133">`CreateRWLockOwnerIterator`, yalnızca şu anda yönetilmeyen kodu yürüten iş parçacıklarında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="768db-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="768db-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="768db-134">Requirements</span></span>  
 <span data-ttu-id="768db-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="768db-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="768db-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="768db-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="768db-137">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="768db-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="768db-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="768db-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768db-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="768db-139">See also</span></span>

- [<span data-ttu-id="768db-140">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="768db-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="768db-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="768db-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
