---
title: IMetaDataImport::EnumTypeRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 778ebf1d4fad0c8703964be88fdc3ff8c033bc28
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449988"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="82ed3-102">IMetaDataImport::EnumTypeRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82ed3-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="82ed3-103">Enumerates TypeRef tokens defined in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="82ed3-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82ed3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82ed3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82ed3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82ed3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="82ed3-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="82ed3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="82ed3-107">This must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="82ed3-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="82ed3-108">[out] The array used to store the TypeRef tokens.</span><span class="sxs-lookup"><span data-stu-id="82ed3-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="82ed3-109">[in] The maximum size of the `rTypeRefs` array.</span><span class="sxs-lookup"><span data-stu-id="82ed3-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="82ed3-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="82ed3-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82ed3-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="82ed3-111">Return Value</span></span>  
  
|<span data-ttu-id="82ed3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82ed3-112">HRESULT</span></span>|<span data-ttu-id="82ed3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82ed3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="82ed3-114">`EnumTypeRefs` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="82ed3-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="82ed3-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="82ed3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="82ed3-116">In that case, `pcTypeRefs` is zero.</span><span class="sxs-lookup"><span data-stu-id="82ed3-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82ed3-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82ed3-117">Remarks</span></span>  
 <span data-ttu-id="82ed3-118">A TypeRef token represents a reference to a type.</span><span class="sxs-lookup"><span data-stu-id="82ed3-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82ed3-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82ed3-119">Requirements</span></span>  
 <span data-ttu-id="82ed3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82ed3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82ed3-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="82ed3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82ed3-122">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82ed3-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82ed3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82ed3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ed3-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82ed3-124">See also</span></span>

- [<span data-ttu-id="82ed3-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82ed3-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="82ed3-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82ed3-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
