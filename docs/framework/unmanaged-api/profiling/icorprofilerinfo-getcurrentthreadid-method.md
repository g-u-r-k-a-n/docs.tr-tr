---
title: ICorProfilerInfo::GetCurrentThreadID Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: fc5356f097f869403212cd234a508f1f29c5ec94
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450392"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="304e8-102">ICorProfilerInfo::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="304e8-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="304e8-103">Yönetilen bir iş parçacığı ise, geçerli iş parçacığının KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="304e8-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="304e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="304e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="304e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="304e8-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="304e8-106">dışı Yönetilen iş parçacığının döndürülen KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="304e8-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="304e8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="304e8-107">Remarks</span></span>  
 <span data-ttu-id="304e8-108">Geçerli iş parçacığı bir iç çalışma zamanı iş parçacığı veya diğer yönetilmeyen iş parçacığıdır, `GetCurrentThreadID` HRESULT olarak CORPROF_E_NOT_MANAGED_THREAD döndürür ve `pThreadId` parametresinin döndürülen değeri null olur.</span><span class="sxs-lookup"><span data-stu-id="304e8-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="304e8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="304e8-109">Requirements</span></span>  
 <span data-ttu-id="304e8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="304e8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="304e8-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="304e8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="304e8-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="304e8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="304e8-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="304e8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="304e8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="304e8-114">See also</span></span>

- [<span data-ttu-id="304e8-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="304e8-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
