---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback8 Interface'
title: ICorProfilerCallback8 Arabirimi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 8dd9b8eea82f38b7598d578bd718743af826070d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781681"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="817ba-103">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="817ba-103">ICorProfilerCallback8 Interface</span></span>

<span data-ttu-id="817ba-104">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="817ba-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="817ba-105">Ortak dil çalışma zamanı tarafından, bir dinamik yöntemin JıT derlemesinin başlatıldığını ve tamamlandığını bildiren profil oluşturucu bildirmek için kullanılan geri çağırma yöntemleri sağlayan bir [ICorProfilerCallback7](icorprofilercallback7-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="817ba-105">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="817ba-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="817ba-106">Methods</span></span>  
  
|<span data-ttu-id="817ba-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="817ba-107">Method</span></span>|<span data-ttu-id="817ba-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="817ba-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="817ba-109">DynamicMethodJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="817ba-109">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="817ba-110">Profiler öğesine dinamik bir yöntemin JıT derlemesinin başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="817ba-110">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="817ba-111">DynamicMethodJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="817ba-111">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="817ba-112">Profiler öğesine dinamik bir yöntemin JıT derlemesinin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="817ba-112">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="817ba-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="817ba-113">Requirements</span></span>  

 <span data-ttu-id="817ba-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="817ba-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="817ba-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="817ba-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="817ba-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="817ba-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="817ba-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="817ba-117">See also</span></span>

- [<span data-ttu-id="817ba-118">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="817ba-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="817ba-119">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="817ba-119">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
