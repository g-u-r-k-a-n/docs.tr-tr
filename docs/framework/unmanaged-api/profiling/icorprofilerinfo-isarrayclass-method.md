---
description: ': ICorProfilerInfo:: IsArrayClass yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerInfo::IsArrayClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 1eee0b834c63c3cfe15bd08776214ca8b2ba3f69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687239"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="7cc68-103">ICorProfilerInfo::IsArrayClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7cc68-103">ICorProfilerInfo::IsArrayClass Method</span></span>

<span data-ttu-id="7cc68-104">Belirtilen sınıfın bir dizi sınıfı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="7cc68-104">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc68-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cc68-105">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cc68-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cc68-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="7cc68-107">'ndaki İnceedilecek sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7cc68-107">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="7cc68-108">dışı Dizi öğelerinin türünü gösteren CorElementType numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7cc68-108">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="7cc68-109">dışı Kullanılabilir olduğunda dizi öğelerinin sınıf KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7cc68-109">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="7cc68-110">dışı Dizinin derecesini (yani boyut sayısını) gösteren bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7cc68-110">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cc68-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cc68-111">Remarks</span></span>  

 <span data-ttu-id="7cc68-112">Belirtilen sınıf bir dizi sınıfınse, `IsArrayClass` Yöntem bir S_OK HRESULT ve null olmayan herhangi bir çıkış parametresi için değerler döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cc68-112">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="7cc68-113">Aksi takdirde, S_FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cc68-113">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cc68-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cc68-114">Requirements</span></span>  

 <span data-ttu-id="7cc68-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cc68-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cc68-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7cc68-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cc68-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7cc68-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cc68-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cc68-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc68-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cc68-119">See also</span></span>

- [<span data-ttu-id="7cc68-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cc68-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
