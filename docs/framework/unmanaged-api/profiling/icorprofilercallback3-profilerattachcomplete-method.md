---
title: ICorProfilerCallback3::ProfilerAttachComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 4c5b8f18424ba54d9e8e14ba0a518a89e0d54796
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439472"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="a1e02-102">ICorProfilerCallback3::ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1e02-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="a1e02-103">Profil oluşturucunun artık [ICorProfilerInfo3:: EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) ve [ICorProfilerInfo3:: EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) yakalama yöntemlerini çağırabelirtemeyeceğini belirtmek için ortak DIL çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a1e02-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1e02-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1e02-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1e02-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1e02-105">Remarks</span></span>  
 <span data-ttu-id="a1e02-106">`ProfilerAttachComplete` geri çağırma, [ICorProfilerCallback3:: InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi çağrıldıktan sonra verilir.</span><span class="sxs-lookup"><span data-stu-id="a1e02-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="a1e02-107">Şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="a1e02-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="a1e02-108">`InitializeForAttach` içinde profil oluşturucu tarafından istenen geri çağrılar etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="a1e02-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="a1e02-109">Profil Oluşturucu artık eksik bildirimlerle ilgilenmeden ilişkili kimliklerde catch gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a1e02-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="a1e02-110">CLR bu geri aramadan döndürülen değeri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="a1e02-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1e02-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1e02-111">Requirements</span></span>  
 <span data-ttu-id="a1e02-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1e02-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1e02-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a1e02-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1e02-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a1e02-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1e02-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1e02-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e02-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1e02-116">See also</span></span>

- [<span data-ttu-id="a1e02-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1e02-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a1e02-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1e02-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a1e02-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a1e02-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a1e02-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a1e02-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
