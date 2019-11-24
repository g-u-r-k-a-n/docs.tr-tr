---
title: ICorProfilerInfo::GetObjectSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: de6d46897f3d3266bf708528efd712ca7db8ea4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438832"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="dccff-102">ICorProfilerInfo::GetObjectSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dccff-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="dccff-103">Gets the size of a specified object.</span><span class="sxs-lookup"><span data-stu-id="dccff-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dccff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dccff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dccff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dccff-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="dccff-106">[in] The ID of the object.</span><span class="sxs-lookup"><span data-stu-id="dccff-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="dccff-107">[out] A pointer to the object's size, in bytes.</span><span class="sxs-lookup"><span data-stu-id="dccff-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dccff-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dccff-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dccff-109">This method is obsolete.</span><span class="sxs-lookup"><span data-stu-id="dccff-109">This method is obsolete.</span></span> <span data-ttu-id="dccff-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span><span class="sxs-lookup"><span data-stu-id="dccff-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="dccff-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span><span class="sxs-lookup"><span data-stu-id="dccff-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="dccff-112">Different objects of the same types often have the same size.</span><span class="sxs-lookup"><span data-stu-id="dccff-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="dccff-113">However, some types, such as arrays or strings, may have a different size for each object.</span><span class="sxs-lookup"><span data-stu-id="dccff-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="dccff-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span><span class="sxs-lookup"><span data-stu-id="dccff-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="dccff-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span><span class="sxs-lookup"><span data-stu-id="dccff-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="dccff-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span><span class="sxs-lookup"><span data-stu-id="dccff-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="dccff-117">On 64-bit Windows, the alignment is always 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="dccff-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dccff-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dccff-118">Requirements</span></span>  
 <span data-ttu-id="dccff-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dccff-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dccff-120">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dccff-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dccff-121">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dccff-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dccff-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dccff-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dccff-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dccff-123">See also</span></span>

- [<span data-ttu-id="dccff-124">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dccff-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
