---
title: IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
ms.openlocfilehash: b70454cd1e2d6d38e6ca4d0ea0bd8974963c201c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136737"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="1600c-102">IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1600c-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="1600c-103">Ana bilgisayara ortak dil çalışma zamanının (CLR) belirtilen belleği işletim sisteminden almış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1600c-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1600c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1600c-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1600c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1600c-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="1600c-106">'ndaki Belleğin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="1600c-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="1600c-107">'ndaki Belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="1600c-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1600c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1600c-108">Remarks</span></span>  
 <span data-ttu-id="1600c-109">`AcquiredVirtualAddressSpace` yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1600c-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="1600c-110">CLR tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1600c-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1600c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1600c-111">Requirements</span></span>  
 <span data-ttu-id="1600c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1600c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1600c-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1600c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1600c-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1600c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1600c-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1600c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1600c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1600c-116">See also</span></span>

- [<span data-ttu-id="1600c-117">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1600c-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
