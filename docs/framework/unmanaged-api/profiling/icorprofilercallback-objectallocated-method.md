---
title: ICorProfilerCallback::ObjectAllocated Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: fda234a6a280aeea1f497ad195d6d41efb6aa951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674352"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="3df3a-102">ICorProfilerCallback::ObjectAllocated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3df3a-102">ICorProfilerCallback::ObjectAllocated Method</span></span>

<span data-ttu-id="3df3a-103">Profil oluşturucuya, yığın içindeki belleğin bir nesne için ayrıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="3df3a-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df3a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3df3a-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3df3a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3df3a-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="3df3a-106">'ndaki Belleğin ayrıldığı nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3df3a-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="3df3a-107">'ndaki Nesnenin bir örnek olduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3df3a-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3df3a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3df3a-108">Remarks</span></span>  

 <span data-ttu-id="3df3a-109">`ObjectedAllocated`Yöntemi, yığından veya yönetilmeyen bellekten ayırmalar için çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="3df3a-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="3df3a-110">`classId`Parametresi, henüz yüklenmemiş Yönetilen koddaki bir sınıfa başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="3df3a-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="3df3a-111">Profil Oluşturucu, geri aramadan hemen sonra bu sınıf için bir sınıf yükü geri çağırması alır `ObjectAllocated` .</span><span class="sxs-lookup"><span data-stu-id="3df3a-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3df3a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3df3a-112">Requirements</span></span>  

 <span data-ttu-id="3df3a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3df3a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df3a-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3df3a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3df3a-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3df3a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3df3a-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3df3a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df3a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3df3a-117">See also</span></span>

- [<span data-ttu-id="3df3a-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3df3a-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3df3a-119">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3df3a-119">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="3df3a-120">ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3df3a-120">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
