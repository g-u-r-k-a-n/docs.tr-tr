---
title: ICorProfilerCallback5 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 02a690503d7b6323f19dcb66247d8a552b760b1c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499213"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="8cfcf-102">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cfcf-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="8cfcf-103">Bir profil oluşturucunun, ICorProfilerCallback:: [ObjectReferences](icorprofilercallback-objectreferences-method.md) ve [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) yöntemleriyle birlikte [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) veya [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) yöntemi ile birlikte kullanıldığında, canlı nesnelerin tam kapatılmasını belirlemesine yardımcı olmak için bilgileri tamamlar.</span><span class="sxs-lookup"><span data-stu-id="8cfcf-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="8cfcf-104">`ICorProfilerCallback5`bağımlı tanıtıcılarla ilgili bildirimlere abone olmak için yönetilen bir bellek Oluşturucu tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8cfcf-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cfcf-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cfcf-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8cfcf-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8cfcf-106">Methods</span></span>  
  
|<span data-ttu-id="8cfcf-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8cfcf-107">Method</span></span>|<span data-ttu-id="8cfcf-108">Description</span><span class="sxs-lookup"><span data-stu-id="8cfcf-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8cfcf-109">ConditionalWeakTableElementReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cfcf-109">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="8cfcf-110">Doğrudan üye alan başvuruları ve bağımlılıklar aracılığıyla bu köklerin başvurduğu nesnelerin geçişli kapanışını tanımlar `ConditionalWeakTable` .</span><span class="sxs-lookup"><span data-stu-id="8cfcf-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cfcf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cfcf-111">Requirements</span></span>  
 <span data-ttu-id="8cfcf-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cfcf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cfcf-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8cfcf-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8cfcf-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cfcf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfcf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cfcf-115">See also</span></span>

- [<span data-ttu-id="8cfcf-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8cfcf-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8cfcf-117">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cfcf-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
