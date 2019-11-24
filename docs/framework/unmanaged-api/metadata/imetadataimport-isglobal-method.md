---
title: IMetaDataImport::IsGlobal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
ms.openlocfilehash: 8a5dda5861343865a139f6b6b9e2794179b0727a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434722"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="37df9-102">IMetaDataImport::IsGlobal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37df9-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="37df9-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span><span class="sxs-lookup"><span data-stu-id="37df9-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37df9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37df9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37df9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37df9-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="37df9-106">[in] A metadata token that represents a type, field, or method.</span><span class="sxs-lookup"><span data-stu-id="37df9-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="37df9-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="37df9-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37df9-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37df9-108">Requirements</span></span>  
 <span data-ttu-id="37df9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37df9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37df9-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="37df9-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37df9-111">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37df9-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37df9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37df9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37df9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37df9-113">See also</span></span>

- [<span data-ttu-id="37df9-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37df9-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="37df9-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37df9-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
