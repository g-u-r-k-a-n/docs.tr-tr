---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: 2ae4b35feb2441fdd66fb68ba9bb3649269a983c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697824"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="6d88f-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d88f-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>

<span data-ttu-id="6d88f-103">Yönetilen işlevlerin [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) kancaları üzerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d88f-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d88f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6d88f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d88f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d88f-105">Parameters</span></span>  

 `pFuncEnter3`  
 <span data-ttu-id="6d88f-106">'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionEnter3WithInfo` .</span><span class="sxs-lookup"><span data-stu-id="6d88f-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="6d88f-107">'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionLeave3WithInfo` .</span><span class="sxs-lookup"><span data-stu-id="6d88f-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="6d88f-108">'ndaki Geri çağırma olarak kullanılacak uygulamaya yönelik bir işaretçi `FunctionTailcall3WithInfo` .</span><span class="sxs-lookup"><span data-stu-id="6d88f-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d88f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d88f-109">Remarks</span></span>  

 <span data-ttu-id="6d88f-110">[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) kancaları yığın çerçevesi ve bağımsız değişken incelemesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d88f-110">The [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="6d88f-111">Bu bilgilere erişmek için,, `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` ve/veya `COR_PRF_ENABLE_FRAME_INFO` bayraklarının ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d88f-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="6d88f-112">Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir ve sonra `SetEnterLeaveFunctionHooks3WithInfo` Bu işlevin uygulamanızı kaydetmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6d88f-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="6d88f-113">Tek seferde yalnızca bir geri çağırma kümesi etkin olabilir ve en yeni sürüm öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="6d88f-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="6d88f-114">Bu nedenle, bir profil oluşturucu hem [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) hem de `SetEnterLeaveFunctionHooks3WithInfo` ' i çağırırsa, `SetEnterLeaveFunctionHooks3WithInfo` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d88f-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="6d88f-115">`SetEnterLeaveFunctionHooks3WithInfo`Yöntemi yalnızca Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d88f-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d88f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d88f-116">Requirements</span></span>  

 <span data-ttu-id="6d88f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d88f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d88f-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6d88f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d88f-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6d88f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d88f-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d88f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d88f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d88f-121">See also</span></span>

- [<span data-ttu-id="6d88f-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="6d88f-122">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="6d88f-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="6d88f-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="6d88f-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="6d88f-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="6d88f-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="6d88f-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="6d88f-126">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="6d88f-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="6d88f-127">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="6d88f-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="6d88f-128">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="6d88f-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="6d88f-129">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6d88f-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="6d88f-130">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d88f-130">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="6d88f-131">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6d88f-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6d88f-132">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d88f-132">Profiling</span></span>](index.md)
