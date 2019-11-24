---
title: ICorProfilerCallback::AssemblyUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
ms.openlocfilehash: 3abf944df3619256791882bf61dfc4072b642c54
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445134"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="fddb7-102">ICorProfilerCallback::AssemblyUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fddb7-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="fddb7-103">Notifies the profiler that an assembly is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="fddb7-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fddb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fddb7-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fddb7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fddb7-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="fddb7-106">[in] Identifies the assembly that is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="fddb7-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fddb7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fddb7-107">Remarks</span></span>  
 <span data-ttu-id="fddb7-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span><span class="sxs-lookup"><span data-stu-id="fddb7-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fddb7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fddb7-109">Requirements</span></span>  
 <span data-ttu-id="fddb7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fddb7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fddb7-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fddb7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fddb7-112">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fddb7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fddb7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fddb7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fddb7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fddb7-114">See also</span></span>

- [<span data-ttu-id="fddb7-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fddb7-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="fddb7-116">AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fddb7-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
