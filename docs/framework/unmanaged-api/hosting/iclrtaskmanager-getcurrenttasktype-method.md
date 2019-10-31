---
title: ICLRTaskManager::GetCurrentTaskType Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 848255d44ce8637182f18288d30151a3f0df0912
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092160"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="a3e04-102">ICLRTaskManager::GetCurrentTaskType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3e04-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="a3e04-103">Şu anda yürütülmekte olan görevin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="a3e04-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3e04-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3e04-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3e04-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3e04-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="a3e04-106">dışı Şu anda yürütülmekte olan görevin türünü gösteren [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3e04-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3e04-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3e04-107">Requirements</span></span>  
 <span data-ttu-id="a3e04-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3e04-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3e04-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a3e04-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3e04-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a3e04-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3e04-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3e04-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3e04-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3e04-112">See also</span></span>

- [<span data-ttu-id="a3e04-113">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3e04-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
