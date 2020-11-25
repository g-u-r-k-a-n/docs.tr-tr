---
title: ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 446de663d437c950f3a9be968e7dcbe8d25ed2b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717296"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="264c3-102">ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="264c3-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>

<span data-ttu-id="264c3-103">Profil oluşturucuyu yönetilmeyen koddan yönetilen koda geçiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="264c3-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="264c3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="264c3-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="264c3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="264c3-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="264c3-106">'ndaki Çağrılmakta olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="264c3-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="264c3-107">'ndaki Yönetilmeyen koddan yönetilen koda yapılan bir çağrı nedeniyle veya yönetilen bir işlev tarafından çağrılan yönetilmeyen bir işlevden dönüş nedeniyle geçişin yapılıp yapılmayacağını belirten [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="264c3-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="264c3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="264c3-108">Remarks</span></span>  

 <span data-ttu-id="264c3-109">Değeri `reason` COR_PRF_TRANSITION_RETURN ise ve `functionId` null değilse, işlev kimliği yönetilmeyen işlevin değeridir ve hiçbir zaman tam ZAMANıNDA (JIT) derleyici kullanılarak derlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="264c3-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="264c3-110">Yönetilmeyen işlevlerde, bunlarla ilişkili bazı temel bilgiler (örneğin, bir ad ve bazı meta veriler) vardır.</span><span class="sxs-lookup"><span data-stu-id="264c3-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="264c3-111">Değeri `reason` COR_PRF_TRANSITION_CALL ise, çağrılan işlevin (yani, yönetilen işlev) henüz JIT derlenmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="264c3-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="264c3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="264c3-112">Requirements</span></span>  

 <span data-ttu-id="264c3-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="264c3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="264c3-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="264c3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="264c3-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="264c3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="264c3-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="264c3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264c3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="264c3-117">See also</span></span>

- [<span data-ttu-id="264c3-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="264c3-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="264c3-119">ManagedToUnmanagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="264c3-119">ManagedToUnmanagedTransition Method</span></span>](icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="264c3-120">C++ ' ta açık PInvoke kullanma (DllImport özniteliği)</span><span class="sxs-lookup"><span data-stu-id="264c3-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="264c3-121">C++ birlikte çalışabilirliği kullanma (örtük PInvoke)</span><span class="sxs-lookup"><span data-stu-id="264c3-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
