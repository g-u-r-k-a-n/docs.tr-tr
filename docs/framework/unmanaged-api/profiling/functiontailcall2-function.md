---
title: FunctionTailcall2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: 2d99c6d8bd2af02456c6a90143b524c337483868
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866901"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="51e54-102">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="51e54-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="51e54-103">Şu anda yürütülmekte olan işlevin başka bir işleve bir tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesi hakkında bilgi sağladığını bildiren Profiler öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="51e54-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51e54-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51e54-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51e54-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51e54-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="51e54-106">\[in] Şu anda yürütülmekte olan işlevin tanıtıcısı, kuyruk çağrısını yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51e54-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="51e54-107">\[içinde] ' de, bir kuyruk çağrısını yapmak üzere olan şu anda yürütülmekte olan işlevin [FunctionIDMapper](functionidmapper-function.md)aracılığıyla belirtilen profil oluşturucunun yeniden eşlenen işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="51e54-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="51e54-108">\[içinde, yığın çerçevesi hakkındaki bilgileri gösteren bir `COR_PRF_FRAME_INFO` değeri.</span><span class="sxs-lookup"><span data-stu-id="51e54-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="51e54-109">Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="51e54-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="51e54-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51e54-110">Remarks</span></span>  
 <span data-ttu-id="51e54-111">Tail çağrısının hedef işlevi geçerli yığın çerçevesini kullanır ve doğrudan kuyruk çağrısını yapan işlevin çağıranına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="51e54-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="51e54-112">Bu, bir kuyruk çağrısının hedefi olan bir işlev için [FunctionLeave2](functionleave2-function.md) geri çağrısının yayımlanmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="51e54-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="51e54-113">`func` parametresinin değeri, `FunctionTailcall2` işlevi döndürüldüğünden geçerli değildir çünkü değer değişebilir veya yok edilir.</span><span class="sxs-lookup"><span data-stu-id="51e54-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="51e54-114">`FunctionTailcall2` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51e54-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="51e54-115">Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51e54-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="51e54-116">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="51e54-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="51e54-117">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="51e54-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="51e54-118">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="51e54-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="51e54-119">`FunctionTailcall2` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="51e54-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="51e54-120">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="51e54-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="51e54-121">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall2` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="51e54-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="51e54-122">Ayrıca, `FunctionTailcall2` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="51e54-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51e54-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51e54-123">Requirements</span></span>  
 <span data-ttu-id="51e54-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51e54-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51e54-125">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="51e54-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="51e54-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="51e54-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51e54-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51e54-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51e54-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51e54-128">See also</span></span>

- [<span data-ttu-id="51e54-129">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="51e54-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="51e54-130">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="51e54-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="51e54-131">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51e54-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="51e54-132">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="51e54-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
