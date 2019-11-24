---
title: ICorProfilerInfo4::RequestReJIT Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: eb4d5e1c4efd67914df95868b67ec5cc3fe6139a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444825"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="2386c-102">ICorProfilerInfo4::RequestReJIT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2386c-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="2386c-103">Requests a JIT recompilation of all instances of the specified functions.</span><span class="sxs-lookup"><span data-stu-id="2386c-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2386c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2386c-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2386c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2386c-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="2386c-106">[in] The number of functions to recompile.</span><span class="sxs-lookup"><span data-stu-id="2386c-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="2386c-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span><span class="sxs-lookup"><span data-stu-id="2386c-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="2386c-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span><span class="sxs-lookup"><span data-stu-id="2386c-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2386c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2386c-109">Return Value</span></span>  
 <span data-ttu-id="2386c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span><span class="sxs-lookup"><span data-stu-id="2386c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2386c-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2386c-111">HRESULT</span></span>|<span data-ttu-id="2386c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2386c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2386c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2386c-113">S_OK</span></span>|<span data-ttu-id="2386c-114">An attempt was made to mark all the methods for JIT recompilation.</span><span class="sxs-lookup"><span data-stu-id="2386c-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="2386c-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span><span class="sxs-lookup"><span data-stu-id="2386c-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="2386c-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="2386c-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="2386c-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span><span class="sxs-lookup"><span data-stu-id="2386c-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="2386c-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="2386c-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="2386c-119">JIT recompilation has not been enabled.</span><span class="sxs-lookup"><span data-stu-id="2386c-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="2386c-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span><span class="sxs-lookup"><span data-stu-id="2386c-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="2386c-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2386c-121">E_INVALIDARG</span></span>|<span data-ttu-id="2386c-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span><span class="sxs-lookup"><span data-stu-id="2386c-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="2386c-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2386c-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2386c-124">The CLR was unable to complete the request because it ran out of memory.</span><span class="sxs-lookup"><span data-stu-id="2386c-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2386c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2386c-125">Remarks</span></span>  
 <span data-ttu-id="2386c-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span><span class="sxs-lookup"><span data-stu-id="2386c-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="2386c-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span><span class="sxs-lookup"><span data-stu-id="2386c-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="2386c-128">This does not affect currently executing functions, only future function invocations.</span><span class="sxs-lookup"><span data-stu-id="2386c-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="2386c-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span><span class="sxs-lookup"><span data-stu-id="2386c-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="2386c-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span><span class="sxs-lookup"><span data-stu-id="2386c-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="2386c-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span><span class="sxs-lookup"><span data-stu-id="2386c-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="2386c-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span><span class="sxs-lookup"><span data-stu-id="2386c-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="2386c-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2386c-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="2386c-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span><span class="sxs-lookup"><span data-stu-id="2386c-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2386c-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2386c-135">Requirements</span></span>  
 <span data-ttu-id="2386c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2386c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2386c-137">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2386c-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2386c-138">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2386c-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2386c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2386c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2386c-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2386c-140">See also</span></span>

- [<span data-ttu-id="2386c-141">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2386c-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="2386c-142">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2386c-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2386c-143">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2386c-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
