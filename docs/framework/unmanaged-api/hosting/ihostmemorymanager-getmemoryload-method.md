---
title: IHostMemoryManager::GetMemoryLoad Metodu
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 0611b82e22ec9d5d2cde2a7f46e65b5e25733610
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731364"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="a6204-102">IHostMemoryManager::GetMemoryLoad Metodu</span><span class="sxs-lookup"><span data-stu-id="a6204-102">IHostMemoryManager::GetMemoryLoad Method</span></span>

<span data-ttu-id="a6204-103">Şu anda kullanımda olan fiziksel bellek miktarını ve bu nedenle ana bilgisayar tarafından bildirilen kullanım sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a6204-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6204-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a6204-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6204-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6204-105">Parameters</span></span>  

 `pMemoryLoad`  
 <span data-ttu-id="a6204-106">dışı Şu anda kullanımda olan toplam fiziksel belleğin yaklaşık yüzdesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6204-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="a6204-107">dışı Ortak dil çalışma zamanı (CLR) için kullanılabilen bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6204-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6204-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a6204-108">Return Value</span></span>  
  
|<span data-ttu-id="a6204-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6204-109">HRESULT</span></span>|<span data-ttu-id="a6204-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6204-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6204-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6204-111">S_OK</span></span>|<span data-ttu-id="a6204-112">`GetMemoryLoad` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a6204-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="a6204-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a6204-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6204-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a6204-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a6204-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a6204-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a6204-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a6204-116">The call timed out.</span></span>|  
|<span data-ttu-id="a6204-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a6204-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a6204-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a6204-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a6204-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a6204-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a6204-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a6204-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a6204-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6204-121">E_FAIL</span></span>|<span data-ttu-id="a6204-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a6204-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a6204-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a6204-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a6204-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a6204-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6204-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6204-125">Remarks</span></span>  

 <span data-ttu-id="a6204-126">`GetMemoryLoad` Win32 işlevini kaydırır `GlobalMemoryStatus` .</span><span class="sxs-lookup"><span data-stu-id="a6204-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="a6204-127">Değeri, `pMemoryLoad` `dwMemoryLoad` `MEMORYSTATUS` öğesinden döndürülen yapıdaki alanın eşdeğeridir `GlobalMemoryStatus` .</span><span class="sxs-lookup"><span data-stu-id="a6204-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="a6204-128">Çalışma zamanı, çöp toplayıcı için bir buluşsal yöntem olarak dönüş değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6204-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="a6204-129">Örneğin, ana bilgisayar belleğin çoğunluğunun kullanımda olduğunu bildirirse çöp toplayıcı, kullanılabilir olabilecek bellek miktarını artırmak için birden çok nesden toplamayı tercih edebilir.</span><span class="sxs-lookup"><span data-stu-id="a6204-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6204-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6204-130">Requirements</span></span>  

 <span data-ttu-id="a6204-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6204-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6204-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a6204-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6204-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a6204-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6204-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6204-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6204-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6204-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="a6204-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6204-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
