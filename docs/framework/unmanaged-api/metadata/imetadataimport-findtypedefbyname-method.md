---
title: IMetaDataImport::FindTypeDefByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
ms.openlocfilehash: b1b1c557eea62cae6d2ad09303441e4635abc899
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437842"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="96ff1-102">IMetaDataImport::FindTypeDefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96ff1-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="96ff1-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span><span class="sxs-lookup"><span data-stu-id="96ff1-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ff1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96ff1-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96ff1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96ff1-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="96ff1-106">[in] The name of the type for which to get the TypeDef token.</span><span class="sxs-lookup"><span data-stu-id="96ff1-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="96ff1-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span><span class="sxs-lookup"><span data-stu-id="96ff1-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="96ff1-108">If the type to find is not a nested class, set this value to NULL.</span><span class="sxs-lookup"><span data-stu-id="96ff1-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="96ff1-109">[out] A pointer to the matching TypeDef token.</span><span class="sxs-lookup"><span data-stu-id="96ff1-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ff1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96ff1-110">Requirements</span></span>  
 <span data-ttu-id="96ff1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96ff1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ff1-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96ff1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96ff1-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96ff1-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96ff1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ff1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ff1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96ff1-115">See also</span></span>

- [<span data-ttu-id="96ff1-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96ff1-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="96ff1-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96ff1-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
