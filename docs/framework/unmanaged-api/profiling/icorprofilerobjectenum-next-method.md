---
title: ICorProfilerObjectEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type:
- apiref
ms.openlocfilehash: 0c833416cca965f2655266152c5bdf5f11624d14
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861144"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="c5c0b-102">ICorProfilerObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5c0b-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="c5c0b-103">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı nesne koleksiyonundan belirtilen sayıda bitişik nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="c5c0b-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5c0b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5c0b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5c0b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c5c0b-106">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="c5c0b-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="c5c0b-107">dışı Her biri alınan bir nesneyi temsil eden `ObjectID` değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="c5c0b-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c5c0b-108">dışı `objects` dizisinde aslında döndürülen öğe sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5c0b-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c0b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5c0b-109">Requirements</span></span>  
 <span data-ttu-id="c5c0b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5c0b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c0b-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c5c0b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5c0b-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c5c0b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5c0b-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5c0b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c0b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5c0b-114">See also</span></span>

- [<span data-ttu-id="c5c0b-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5c0b-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
