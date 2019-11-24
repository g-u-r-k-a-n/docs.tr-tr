---
title: COR_PRF_MISC Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: 8105ba34ca400771fbc4273630f20941a4a9557d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432282"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="9cddf-102">COR_PRF_MISC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9cddf-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="9cddf-103">Contains constant values that specify special identifiers.</span><span class="sxs-lookup"><span data-stu-id="9cddf-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cddf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9cddf-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="9cddf-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9cddf-105">Members</span></span>  
  
|<span data-ttu-id="9cddf-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9cddf-106">Member</span></span>|<span data-ttu-id="9cddf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cddf-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="9cddf-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span><span class="sxs-lookup"><span data-stu-id="9cddf-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="9cddf-109">The default class identifier for global constants that do not belong to a class.</span><span class="sxs-lookup"><span data-stu-id="9cddf-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="9cddf-110">The default module identifier for global objects that do not belong to a module.</span><span class="sxs-lookup"><span data-stu-id="9cddf-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9cddf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9cddf-111">Requirements</span></span>  
 <span data-ttu-id="9cddf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cddf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cddf-113">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9cddf-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9cddf-114">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cddf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cddf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cddf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cddf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cddf-116">See also</span></span>

- [<span data-ttu-id="9cddf-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9cddf-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
