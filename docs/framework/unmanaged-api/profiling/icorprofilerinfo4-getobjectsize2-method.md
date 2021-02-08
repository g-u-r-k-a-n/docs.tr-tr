---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo4:: GetObjectSize2 yöntemi'
title: ICorProfilerInfo4::GetObjectSize2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: 986c3d99501e21feec95dd3b6014f8d11d809704
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794531"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="64d2e-103">ICorProfilerInfo4::GetObjectSize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64d2e-103">ICorProfilerInfo4::GetObjectSize2 Method</span></span>

<span data-ttu-id="64d2e-104">Belirtilen nesnenin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="64d2e-104">Returns the size of a specified object.</span></span> <span data-ttu-id="64d2e-105">[ICorProfilerInfo:: GetObjectSize](icorprofilerinfo-getobjectsize-method.md) yöntemini, içinde belirtilebilenden daha büyük nesnelerin raporlama boyutlarına göre değiştirir `ULONG` .</span><span class="sxs-lookup"><span data-stu-id="64d2e-105">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d2e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64d2e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d2e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64d2e-107">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="64d2e-108">'ndaki Nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="64d2e-108">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="64d2e-109">dışı Nesnenin boyutunun bayt cinsinden işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="64d2e-109">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64d2e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64d2e-110">Remarks</span></span>  

 <span data-ttu-id="64d2e-111">Aynı türdeki farklı nesneler genellikle aynı boyutta olur.</span><span class="sxs-lookup"><span data-stu-id="64d2e-111">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="64d2e-112">Ancak, diziler veya dizeler gibi bazı türlerin her nesne için farklı boyutta bir boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="64d2e-112">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d2e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64d2e-113">Requirements</span></span>  

 <span data-ttu-id="64d2e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d2e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d2e-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="64d2e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64d2e-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="64d2e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64d2e-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d2e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d2e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64d2e-118">See also</span></span>

- [<span data-ttu-id="64d2e-119">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64d2e-119">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
