---
title: IMetaDataImport2::EnumGenericParamConstraints Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
ms.openlocfilehash: d1683965193801dbdee038ab06366178891fd978
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426729"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="e7e0e-102">IMetaDataImport2::EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7e0e-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="e7e0e-103">Belirtilen belirteçle temsil edilen genel parametreyle ilişkili genel parametre kısıtlamaları dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7e0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7e0e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7e0e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7e0e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e7e0e-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="e7e0e-107">'ndaki   Kısıtlamaları Numaralandırılacak genel parametreyi temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="e7e0e-108">dışı Numaralandırılacak genel parametre kısıtlamaları dizisi.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e7e0e-109">'ndaki   `rGenericParamConstraints`yerleştirmek için istenen en fazla belirteç sayısı.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="e7e0e-110">dışı `rGenericParamConstraints`yerleştirilmiş belirteç sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7e0e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e7e0e-111">Return Value</span></span>  
  
|<span data-ttu-id="e7e0e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7e0e-112">HRESULT</span></span>|<span data-ttu-id="e7e0e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7e0e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e7e0e-114">`EnumGenericParameterConstraints` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e7e0e-115">`phEnum` üye öğesi yok.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="e7e0e-116">Bu durumda, `pcGenericParameterConstraints` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7e0e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7e0e-117">Requirements</span></span>  
 <span data-ttu-id="e7e0e-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7e0e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7e0e-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e7e0e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7e0e-120">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e7e0e-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7e0e-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7e0e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e0e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7e0e-122">See also</span></span>

- [<span data-ttu-id="e7e0e-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7e0e-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="e7e0e-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7e0e-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
