---
title: IHostIoCompletionManager::GetMaxThreads Metodu
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
ms.openlocfilehash: d35fd91f2a28c392176a6dd87bd21baa964ee9a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133808"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="104dd-102">IHostIoCompletionManager::GetMaxThreads Metodu</span><span class="sxs-lookup"><span data-stu-id="104dd-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="104dd-103">Ana bilgisayarın g/ç isteklerine hizmet vermek için lot olarak barındırabileceği en fazla iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="104dd-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="104dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="104dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="104dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="104dd-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="104dd-106">dışı İş parçacığı havuzunda ana bilgisayarın g/ç isteklerine hizmet verecek en fazla iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="104dd-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="104dd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="104dd-107">Return Value</span></span>  
  
|<span data-ttu-id="104dd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="104dd-108">HRESULT</span></span>|<span data-ttu-id="104dd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="104dd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="104dd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="104dd-110">S_OK</span></span>|<span data-ttu-id="104dd-111">`GetMaxThreads` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="104dd-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="104dd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="104dd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="104dd-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="104dd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="104dd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="104dd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="104dd-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="104dd-115">The call timed out.</span></span>|  
|<span data-ttu-id="104dd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="104dd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="104dd-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="104dd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="104dd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="104dd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="104dd-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="104dd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="104dd-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="104dd-120">E_FAIL</span></span>|<span data-ttu-id="104dd-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="104dd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="104dd-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="104dd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="104dd-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="104dd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="104dd-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="104dd-124">E_NOTIMPL</span></span>|<span data-ttu-id="104dd-125">Ana bilgisayar `GetMaxThreads`bir uygulamasını sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="104dd-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="104dd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="104dd-126">Remarks</span></span>  
 <span data-ttu-id="104dd-127">Bir ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç isteklerini işlemek için ayrılan iş parçacığı sayısı üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="104dd-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="104dd-128">Bu nedenle, konağın `GetMaxThreads`uygulamak için konak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="104dd-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="104dd-129">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="104dd-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="104dd-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="104dd-130">Requirements</span></span>  
 <span data-ttu-id="104dd-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="104dd-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="104dd-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="104dd-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="104dd-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="104dd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="104dd-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="104dd-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="104dd-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="104dd-135">See also</span></span>

- [<span data-ttu-id="104dd-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="104dd-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="104dd-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="104dd-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
