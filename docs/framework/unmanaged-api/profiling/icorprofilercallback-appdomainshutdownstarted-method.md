---
description: ': ICorProfilerCallback:: AppDomainShutdownStarted Yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorProfilerCallback:: AppDomainShutdownStarted Yöntemi'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: 16545142a512ca1c5f4167f61b81ea949e3d14e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648122"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="51c19-103">ICorProfilerCallback:: AppDomainShutdownStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51c19-103">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>

<span data-ttu-id="51c19-104">Profil Oluşturucu bir uygulama etki alanının bir işlemden kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="51c19-104">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51c19-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51c19-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51c19-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51c19-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="51c19-107">\[' de], uygulamanın derlemelerinin depolandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="51c19-107">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="51c19-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51c19-108">Remarks</span></span>  

 <span data-ttu-id="51c19-109">Değeri, `appDomainId` Yöntem çağrıldıktan sonra herhangi bir bilgi isteği için geçerli değildir `AppDomainShutdownStarted` ; Bu, profil oluşturucunun bu uygulama etki alanı hakkında bilgi almak için en son şansınız olur.</span><span class="sxs-lookup"><span data-stu-id="51c19-109">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51c19-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51c19-110">Requirements</span></span>  

 <span data-ttu-id="51c19-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51c19-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51c19-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="51c19-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="51c19-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="51c19-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51c19-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51c19-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c19-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51c19-115">See also</span></span>

- [<span data-ttu-id="51c19-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51c19-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
