---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 46a25fc6e9119481f728275e0569429cc6c46dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725436"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="59ff5-102">ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="59ff5-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>

<span data-ttu-id="59ff5-103">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="59ff5-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="59ff5-104">Dinamik bir yöntemin JıT derlemesi başladığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="59ff5-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ff5-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="59ff5-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59ff5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59ff5-106">Parameters</span></span>  

<span data-ttu-id="59ff5-107">'ndaki `functionId`</span><span class="sxs-lookup"><span data-stu-id="59ff5-107">[in] `functionId`</span></span>  
<span data-ttu-id="59ff5-108">JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="59ff5-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="59ff5-109">[in] `fIsSafeToBlock` 
 `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false`engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="59ff5-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="59ff5-110">[in] `pILHeader` Metodun Il üstbilgisinin ilk baytına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="59ff5-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="59ff5-111">[in] `cbILHeader` Il üstbilgisindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="59ff5-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="59ff5-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59ff5-112">Remarks</span></span>  

<span data-ttu-id="59ff5-113">Bu geri çağırma, dinamik bir yöntem JıT olarak derlendiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="59ff5-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="59ff5-114">Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="59ff5-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="59ff5-115">Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="59ff5-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="59ff5-116">`functionId` Dinamik metotların meta verisi olmadığından, meta veri belirteçlerine çözümlemek için değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="59ff5-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="59ff5-117">`pILHeader`İşaretçi yalnızca geri çağırma sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="59ff5-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="59ff5-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59ff5-118">Requirements</span></span>  

 <span data-ttu-id="59ff5-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ff5-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ff5-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="59ff5-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59ff5-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="59ff5-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59ff5-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="59ff5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ff5-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59ff5-123">See also</span></span>

- [<span data-ttu-id="59ff5-124">DynamicMethodJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59ff5-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="59ff5-125">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59ff5-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
