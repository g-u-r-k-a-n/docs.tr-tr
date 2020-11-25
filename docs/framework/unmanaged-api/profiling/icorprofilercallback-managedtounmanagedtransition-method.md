---
title: ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: ef65ed908c71bcc2755aaf42070439fd7dab3f6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733147"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="8fe27-102">ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fe27-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>

<span data-ttu-id="8fe27-103">Profil oluşturucuyu yönetilen koddan yönetilmeyen koda geçişin oluştuğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8fe27-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe27-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8fe27-104">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fe27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8fe27-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="8fe27-106">'ndaki Çağrılmakta olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8fe27-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="8fe27-107">'ndaki Yönetilen koddan yönetilmeyen koda yapılan bir çağrı nedeniyle veya yönetilmeyen bir işlevden gelen bir dönüş nedeniyle geçiş yapılıp yapılmayacağını belirten [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="8fe27-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fe27-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fe27-108">Remarks</span></span>  

 <span data-ttu-id="8fe27-109">Değeri `reason` COR_PRF_TRANSITION_CALL ise, Işlev kimliği yönetilmeyen işlevin değildir ve bu, hiçbir zaman tam zamanında derleyici kullanılarak derlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="8fe27-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="8fe27-110">Yönetilmeyen işlevlerde, bir ad ve bazı meta veriler gibi kendileriyle ilişkili temel bilgiler vardır.</span><span class="sxs-lookup"><span data-stu-id="8fe27-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="8fe27-111">Yönetilmeyen işlev örtük platform çağırma (PInvoke) kullanılarak çağrılırsa, çalışma zamanı çağrının hedefini belirleyemez ve değeri `functionId` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8fe27-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="8fe27-112">Örtük PInvoke hakkında daha fazla bilgi için bkz. [C++ birlikte çalışabilirliği kullanma (örtük PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="8fe27-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe27-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fe27-113">Requirements</span></span>  

 <span data-ttu-id="8fe27-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe27-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe27-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8fe27-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fe27-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8fe27-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe27-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe27-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe27-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fe27-118">See also</span></span>

- [<span data-ttu-id="8fe27-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fe27-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8fe27-120">UnmanagedToManagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fe27-120">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="8fe27-121">C++ ' ta açık PInvoke kullanma (DllImport özniteliği)</span><span class="sxs-lookup"><span data-stu-id="8fe27-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
