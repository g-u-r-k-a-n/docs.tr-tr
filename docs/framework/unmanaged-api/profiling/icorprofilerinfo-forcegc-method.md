---
title: ICorProfilerInfo::ForceGC Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: 9f97da4e68d4b76178198e91c3fb8f08b56dda7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448192"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="5d6ad-102">ICorProfilerInfo::ForceGC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d6ad-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="5d6ad-103">Çöp toplamayı ortak dil çalışma zamanı (CLR) içinde gerçekleşmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="5d6ad-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d6ad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d6ad-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5d6ad-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d6ad-105">Remarks</span></span>  
 <span data-ttu-id="5d6ad-106">`ForceGC` yöntemi yalnızca yönetilen kodu çalıştırmayan bir iş parçacığından çağrılmalıdır ve yığınında hiçbir profil oluşturucu geri çağırmaları yok.</span><span class="sxs-lookup"><span data-stu-id="5d6ad-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="5d6ad-107">En kullanışlı uygulama, bir profil oluşturucu içinde, sinyal edildiğinde `ForceGC` çağıran ayrı bir iş parçacığı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="5d6ad-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d6ad-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d6ad-108">Requirements</span></span>  
 <span data-ttu-id="5d6ad-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ad-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d6ad-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5d6ad-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d6ad-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5d6ad-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d6ad-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d6ad-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d6ad-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d6ad-113">See also</span></span>

- [<span data-ttu-id="5d6ad-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d6ad-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
