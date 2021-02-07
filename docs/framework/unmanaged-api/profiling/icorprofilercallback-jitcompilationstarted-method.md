---
description: ': ICorProfilerCallback:: JITCompilationStarted Yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::JITCompilationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 984c19e1601f83cc0f52145403ad85affc158050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705752"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="8285f-103">ICorProfilerCallback::JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8285f-103">ICorProfilerCallback::JITCompilationStarted Method</span></span>

<span data-ttu-id="8285f-104">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemek için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="8285f-104">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8285f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8285f-105">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8285f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8285f-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="8285f-107">'ndaki Derlemenin başladığı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8285f-107">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="8285f-108">'ndaki Profiler 'ın çalışma zamanının işlemini etkilemesinin ne olmayacağını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="8285f-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="8285f-109">Bu değer, `true` engelleme çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini, aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="8285f-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="8285f-110">Bir değeri `true` çalışma zamanına zarar verse de, profil oluşturma sonuçlarını çarpıtmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8285f-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8285f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8285f-111">Remarks</span></span>  

 <span data-ttu-id="8285f-112">`JITCompilationStarted`Çalışma zamanının sınıf oluşturucularını işleme biçimi nedeniyle her bir işlev için birden fazla çift ve [ICorProfilerCallback:: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) çağrısı almak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8285f-112">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="8285f-113">Örneğin, çalışma zamanı JıT-Compile yöntemine başlar, ancak B sınıfı için sınıf oluşturucusunun çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8285f-113">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="8285f-114">Bu nedenle, çalışma zamanı JıT-oluşturucuyu B sınıfı için derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="8285f-114">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="8285f-115">Oluşturucu çalışırken, a yöntemine bir çağrı yapar ve bu, yönteminin JıT olarak derlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="8285f-115">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="8285f-116">Bu senaryoda, A yönteminin ilk JıT derlemesi durdurulur.</span><span class="sxs-lookup"><span data-stu-id="8285f-116">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="8285f-117">Ancak, JIT-Compile yöntemine her ikisi de JıT derleme olayları ile bildirilir.</span><span class="sxs-lookup"><span data-stu-id="8285f-117">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="8285f-118">Profil Oluşturucu, [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) metodunu çağırarak bir yöntemi için Microsoft ara DILI (MSIL) kodunu değiştirmek için her iki olay için de bunu yapması gerekir `JITCompilationStarted` , ancak her IKISI için aynı MSIL bloğunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8285f-118">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="8285f-119">Profil oluşturucular, iki iş parçacığının aynı anda geri çağırma yapmakta olduğu durumlarda JıT geri çağırmaları dizisini desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="8285f-119">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="8285f-120">Örneğin, bir çağrı iş parçacığı `JITCompilationStarted` .</span><span class="sxs-lookup"><span data-stu-id="8285f-120">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="8285f-121">Bununla birlikte, bir çağrı iş parçacığından önce `JITCompilationFinished` , B iş parçacığı [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) ' i iş parçacığı A 'nın `JITCompilationStarted` GERI çağırmasında işlev kimliğiyle çağırır.</span><span class="sxs-lookup"><span data-stu-id="8285f-121">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="8285f-122">Bir çağrı `JITCompilationFinished` Profil Oluşturucu tarafından henüz alınmadığı için Işlev kimliğinin henüz geçerli olmaması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8285f-122">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="8285f-123">Ancak, bunun gibi bir durumda, işlev KIMLIĞI geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="8285f-123">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8285f-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8285f-124">Requirements</span></span>  

 <span data-ttu-id="8285f-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8285f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8285f-126">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8285f-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8285f-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8285f-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8285f-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8285f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8285f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8285f-129">See also</span></span>

- [<span data-ttu-id="8285f-130">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8285f-130">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8285f-131">JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8285f-131">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
