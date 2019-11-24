---
title: IMetaDataEmit::DefineImportType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 5b4b0682b2bddff96cb3d720900ed3aa39f06f9d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431844"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="ebc56-102">IMetaDataEmit::DefineImportType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebc56-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="ebc56-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span><span class="sxs-lookup"><span data-stu-id="ebc56-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebc56-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebc56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebc56-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="ebc56-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span><span class="sxs-lookup"><span data-stu-id="ebc56-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="ebc56-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="ebc56-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="ebc56-108">[in] The number of bytes in the `pbHashValue` array.</span><span class="sxs-lookup"><span data-stu-id="ebc56-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="ebc56-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span><span class="sxs-lookup"><span data-stu-id="ebc56-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="ebc56-110">[in] An `mdTypeDef` token that specifies the target type.</span><span class="sxs-lookup"><span data-stu-id="ebc56-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="ebc56-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span><span class="sxs-lookup"><span data-stu-id="ebc56-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="ebc56-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span><span class="sxs-lookup"><span data-stu-id="ebc56-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebc56-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebc56-113">Remarks</span></span>  
 <span data-ttu-id="ebc56-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span><span class="sxs-lookup"><span data-stu-id="ebc56-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebc56-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebc56-115">Requirements</span></span>  
 <span data-ttu-id="ebc56-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebc56-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebc56-117">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ebc56-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ebc56-118">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebc56-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebc56-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebc56-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc56-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebc56-120">See also</span></span>

- [<span data-ttu-id="ebc56-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebc56-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ebc56-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebc56-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
