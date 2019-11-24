---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: b6ef54297b69892f07df1aa92a92600fb20756e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445308"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="21db6-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21db6-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="21db6-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span><span class="sxs-lookup"><span data-stu-id="21db6-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21db6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21db6-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="21db6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21db6-105">Remarks</span></span>  
 <span data-ttu-id="21db6-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span><span class="sxs-lookup"><span data-stu-id="21db6-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="21db6-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span><span class="sxs-lookup"><span data-stu-id="21db6-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="21db6-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span><span class="sxs-lookup"><span data-stu-id="21db6-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21db6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21db6-109">Requirements</span></span>  
 <span data-ttu-id="21db6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21db6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21db6-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21db6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21db6-112">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21db6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21db6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21db6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21db6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21db6-114">See also</span></span>

- [<span data-ttu-id="21db6-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21db6-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="21db6-116">ExceptionUnwindFinallyEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21db6-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
