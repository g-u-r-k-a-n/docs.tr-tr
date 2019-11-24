---
title: ICorProfilerInfo2::GetFunctionInfo2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
ms.openlocfilehash: 11f9a186f5ec5e3b9e718a3ccd43b35b66d28078
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433183"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="7cf09-102">ICorProfilerInfo2::GetFunctionInfo2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7cf09-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="7cf09-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span><span class="sxs-lookup"><span data-stu-id="7cf09-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf09-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cf09-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cf09-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cf09-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="7cf09-106">[in] The ID of the function for which to get the parent class and other information.</span><span class="sxs-lookup"><span data-stu-id="7cf09-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="7cf09-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span><span class="sxs-lookup"><span data-stu-id="7cf09-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="7cf09-108">[out] A pointer to the parent class of the function.</span><span class="sxs-lookup"><span data-stu-id="7cf09-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="7cf09-109">[out] A pointer to the module in which the function's parent class is defined.</span><span class="sxs-lookup"><span data-stu-id="7cf09-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="7cf09-110">[out] A pointer to the metadata token for the function.</span><span class="sxs-lookup"><span data-stu-id="7cf09-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="7cf09-111">[in] The size of the `typeArgs` array.</span><span class="sxs-lookup"><span data-stu-id="7cf09-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="7cf09-112">[out] A pointer to the total number of `ClassID` values.</span><span class="sxs-lookup"><span data-stu-id="7cf09-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="7cf09-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span><span class="sxs-lookup"><span data-stu-id="7cf09-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="7cf09-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span><span class="sxs-lookup"><span data-stu-id="7cf09-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cf09-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cf09-115">Remarks</span></span>  
 <span data-ttu-id="7cf09-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span><span class="sxs-lookup"><span data-stu-id="7cf09-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="7cf09-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span><span class="sxs-lookup"><span data-stu-id="7cf09-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="7cf09-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span><span class="sxs-lookup"><span data-stu-id="7cf09-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="7cf09-119">Value of the `frameInfo` parameter</span><span class="sxs-lookup"><span data-stu-id="7cf09-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="7cf09-120">Sonuç</span><span class="sxs-lookup"><span data-stu-id="7cf09-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="7cf09-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span><span class="sxs-lookup"><span data-stu-id="7cf09-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="7cf09-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span><span class="sxs-lookup"><span data-stu-id="7cf09-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="7cf09-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span><span class="sxs-lookup"><span data-stu-id="7cf09-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="7cf09-124">The exact `ClassID` and type arguments cannot be determined.</span><span class="sxs-lookup"><span data-stu-id="7cf09-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="7cf09-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="7cf09-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="7cf09-126">Zero</span><span class="sxs-lookup"><span data-stu-id="7cf09-126">Zero</span></span>|<span data-ttu-id="7cf09-127">The exact `ClassID` and type arguments cannot be determined.</span><span class="sxs-lookup"><span data-stu-id="7cf09-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="7cf09-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="7cf09-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="7cf09-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span><span class="sxs-lookup"><span data-stu-id="7cf09-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="7cf09-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span><span class="sxs-lookup"><span data-stu-id="7cf09-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="7cf09-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span><span class="sxs-lookup"><span data-stu-id="7cf09-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="7cf09-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span><span class="sxs-lookup"><span data-stu-id="7cf09-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7cf09-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span><span class="sxs-lookup"><span data-stu-id="7cf09-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cf09-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cf09-134">Requirements</span></span>  
 <span data-ttu-id="7cf09-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cf09-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf09-136">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7cf09-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cf09-137">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cf09-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cf09-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cf09-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf09-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cf09-139">See also</span></span>

- [<span data-ttu-id="7cf09-140">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cf09-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7cf09-141">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cf09-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="7cf09-142">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7cf09-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="7cf09-143">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7cf09-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
