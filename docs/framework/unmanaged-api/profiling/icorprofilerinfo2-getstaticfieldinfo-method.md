---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo2:: GetStaticFieldInfo yöntemi'
title: ICorProfilerInfo2::GetStaticFieldInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: 1acde9d5ad1a35b11cb036bced99c1909f0b6b04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716365"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="e841d-103">ICorProfilerInfo2::GetStaticFieldInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e841d-103">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>

<span data-ttu-id="e841d-104">Belirtilen alan için geçerli olan statik türünü gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e841d-104">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e841d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e841d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e841d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e841d-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="e841d-107">'ndaki Statik alanın tanımlandığı sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e841d-107">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e841d-108">'ndaki Statik alan için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="e841d-108">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="e841d-109">dışı Belirtilen alanın statik olup olmadığını belirten [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) sabit değerinin bir işaretçisi ve bu durumda, alan için geçerli olan statik türü.</span><span class="sxs-lookup"><span data-stu-id="e841d-109">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e841d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e841d-110">Remarks</span></span>  

 <span data-ttu-id="e841d-111">Bu bilgiler, statik alanın adresini almak için hangi işlevin çağrılacağını belirlemede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e841d-111">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="e841d-112">Profil Oluşturucu kodu, gerçekten bir adresi olduğundan emin olmak için statik bir alana ait meta verileri denetlemelidir.</span><span class="sxs-lookup"><span data-stu-id="e841d-112">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="e841d-113">Statik sabit değerler (diğer bir deyişle, sabitler) yalnızca meta verilerde bulunur ve bir adrese sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="e841d-113">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e841d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e841d-114">Requirements</span></span>  

 <span data-ttu-id="e841d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e841d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e841d-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e841d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e841d-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e841d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e841d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e841d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e841d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e841d-119">See also</span></span>

- [<span data-ttu-id="e841d-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e841d-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e841d-121">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e841d-121">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
