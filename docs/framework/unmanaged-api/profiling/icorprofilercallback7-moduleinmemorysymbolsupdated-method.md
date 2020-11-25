---
title: 'ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: 248d2f749ddcbd772313558af2b2721f4d1c0f58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723096"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="17fca-102">ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi</span><span class="sxs-lookup"><span data-stu-id="17fca-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>

<span data-ttu-id="17fca-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="17fca-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="17fca-104">Bellek içi modülle ilişkili sembol akışı güncelleştirildiğinde profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="17fca-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17fca-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="17fca-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17fca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17fca-106">Parameters</span></span>  

 <span data-ttu-id="17fca-107">'ndaki `moduleId`</span><span class="sxs-lookup"><span data-stu-id="17fca-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="17fca-108">Sembol akışı güncelleştirilmiş olan bellek içi modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="17fca-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17fca-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17fca-109">Remarks</span></span>  

 <span data-ttu-id="17fca-110">Bu geri çağırma, [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemi çağrılırken [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) Event Mask bayrağı ayarlanarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="17fca-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17fca-111">Bu olay şu anda, API 'ler aracılığıyla örtük olarak oluşturulan veya değiştirilen semboller için çıkarılmamaktadır <xref:System.Reflection.Emit> .</span><span class="sxs-lookup"><span data-stu-id="17fca-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="17fca-112">Semboller, derleme için sembolleri belirtmek üzere bir bağımsız değişken içeren yönetilen yöntemlerin aşırı yüklerinden birine yapılan bir çağrıda önde gelen olsa bile <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> `rawSymbolStore` , [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması gerçekleşene kadar çalışma zamanı aslında sembolik verileri modülle ilişkilendirmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="17fca-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="17fca-113">Bu olay, bu tür modüller için sembolleri toplamaya yönelik daha sonraki bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="17fca-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17fca-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17fca-114">Requirements</span></span>  

 <span data-ttu-id="17fca-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17fca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17fca-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="17fca-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17fca-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="17fca-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17fca-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17fca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17fca-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17fca-119">See also</span></span>

- [<span data-ttu-id="17fca-120">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17fca-120">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="17fca-121">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17fca-121">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
- [<span data-ttu-id="17fca-122">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17fca-122">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)
