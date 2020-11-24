---
title: COR_PRF_GC_ROOT_KIND Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: e86074031b8fc2c82636e7aef2177eaf04a9db14
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682373"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="3d7f4-102">COR_PRF_GC_ROOT_KIND Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3d7f4-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>

<span data-ttu-id="3d7f4-103">[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplama kökünün türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d7f4-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d7f4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d7f4-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="3d7f4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3d7f4-105">Members</span></span>  
  
|<span data-ttu-id="3d7f4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3d7f4-106">Member</span></span>|<span data-ttu-id="3d7f4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d7f4-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="3d7f4-108">Kök, yığındaki bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="3d7f4-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="3d7f4-109">Kök, Sonlandırıcı sırasındaki bir giriştir.</span><span class="sxs-lookup"><span data-stu-id="3d7f4-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="3d7f4-110">Kök bir atık toplama tanıtıcıdır.</span><span class="sxs-lookup"><span data-stu-id="3d7f4-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="3d7f4-111">Kök türü belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="3d7f4-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d7f4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d7f4-112">Requirements</span></span>  

 <span data-ttu-id="3d7f4-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d7f4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d7f4-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3d7f4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d7f4-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3d7f4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d7f4-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d7f4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d7f4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d7f4-117">See also</span></span>

- [<span data-ttu-id="3d7f4-118">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="3d7f4-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
