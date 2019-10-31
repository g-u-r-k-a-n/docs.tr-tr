---
title: IGCHostControl::RequestVirtualMemLimit Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
ms.openlocfilehash: ccff575974093de0bf00b257cba78c509f9cbd92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134768"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="0f483-102">IGCHostControl::RequestVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f483-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="0f483-103">Konağı, sanal bellek sınırlarını değiştirecek şekilde ister.</span><span class="sxs-lookup"><span data-stu-id="0f483-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f483-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f483-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f483-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f483-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="0f483-106">'ndaki Ayrılacak belleğin istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="0f483-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="0f483-107">[in, out] Ayrılan belleğin gerçek boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0f483-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f483-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f483-108">Requirements</span></span>  
 <span data-ttu-id="0f483-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f483-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f483-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f483-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f483-111">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0f483-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f483-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f483-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f483-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f483-113">See also</span></span>

- [<span data-ttu-id="0f483-114">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f483-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
