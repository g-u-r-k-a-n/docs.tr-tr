---
title: ICorProfilerCallback2::HandleCreated Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
ms.openlocfilehash: 594d970dbe0a176a5ec49015e105f89ff64bdfac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439765"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="22844-102">ICorProfilerCallback2::HandleCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22844-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="22844-103">Kod Profilcisi bir çöp toplama tutamacının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="22844-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22844-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22844-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22844-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22844-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="22844-106">'ndaki Çöp toplama tanıtıcısının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="22844-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="22844-107">'ndaki Çöp toplama tanıtıcısının oluşturulduğu nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="22844-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22844-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22844-108">Requirements</span></span>  
 <span data-ttu-id="22844-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22844-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22844-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="22844-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22844-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="22844-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22844-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22844-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22844-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22844-113">See also</span></span>

- [<span data-ttu-id="22844-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22844-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="22844-115">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22844-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
