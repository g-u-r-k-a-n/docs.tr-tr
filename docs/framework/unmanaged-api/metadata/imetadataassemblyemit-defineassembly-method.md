---
title: IMetaDataAssemblyEmit::DefineAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 20628e708261076c6e172ff30c366a0d69c2e0f2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432123"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="08300-102">IMetaDataAssemblyEmit::DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08300-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="08300-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span><span class="sxs-lookup"><span data-stu-id="08300-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08300-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08300-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08300-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08300-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="08300-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span><span class="sxs-lookup"><span data-stu-id="08300-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="08300-107">[in] The size in bytes of `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="08300-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="08300-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span><span class="sxs-lookup"><span data-stu-id="08300-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="08300-109">[in] The human-readable text name of the assembly.</span><span class="sxs-lookup"><span data-stu-id="08300-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="08300-110">This value must not exceed 1024 characters.</span><span class="sxs-lookup"><span data-stu-id="08300-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="08300-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span><span class="sxs-lookup"><span data-stu-id="08300-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="08300-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span><span class="sxs-lookup"><span data-stu-id="08300-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="08300-113">[out] A pointer to the metadata token.</span><span class="sxs-lookup"><span data-stu-id="08300-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08300-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08300-114">Remarks</span></span>  
 <span data-ttu-id="08300-115">Only one `Assembly` metadata structure can be defined within a manifest.</span><span class="sxs-lookup"><span data-stu-id="08300-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08300-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08300-116">Requirements</span></span>  
 <span data-ttu-id="08300-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08300-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08300-118">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08300-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08300-119">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08300-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08300-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08300-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08300-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08300-121">See also</span></span>

- [<span data-ttu-id="08300-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08300-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
