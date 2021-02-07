---
description: ': ICorProfilerCallback:: FunctionUnloadStarted yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::FunctionUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 3dd5d46a224c0c51dfee251cf5d0c6ae9320b630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705969"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="74f27-103">ICorProfilerCallback::FunctionUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74f27-103">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>

<span data-ttu-id="74f27-104">Profil oluşturucuyu, çalışma zamanının bir işlevi kaldırmak için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="74f27-104">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f27-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74f27-105">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="74f27-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74f27-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="74f27-107">\[' de] kaldırılmakta olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="74f27-107">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="74f27-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74f27-108">Remarks</span></span>  

 <span data-ttu-id="74f27-109">`functionId`Bu yöntem çağırana döndüğünde parametrenin değeri artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="74f27-109">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74f27-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74f27-110">Requirements</span></span>  

 <span data-ttu-id="74f27-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74f27-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74f27-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74f27-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74f27-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74f27-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74f27-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74f27-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f27-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74f27-115">See also</span></span>

- [<span data-ttu-id="74f27-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74f27-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
