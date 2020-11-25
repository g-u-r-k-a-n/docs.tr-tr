---
title: IMetaDataEmit2::SetGenericParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 8858e692d66f7b34a66334bd4e8b906dd12962ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701997"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="071ca-102">IMetaDataEmit2::SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="071ca-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>

<span data-ttu-id="071ca-103">Belirtilen belirteç tarafından başvurulan genel parametre tanımının özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="071ca-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="071ca-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="071ca-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="071ca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="071ca-105">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="071ca-106">'ndaki Değerleri ayarlanacak genel parametre tanımının belirteci.</span><span class="sxs-lookup"><span data-stu-id="071ca-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="071ca-107">'ndaki Genel parametrenin türünü açıklayan [CorGenericParamAttr](corgenericparamattr-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="071ca-107">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="071ca-108">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="071ca-108">[in] Optional.</span></span> <span data-ttu-id="071ca-109">Değerlerinin ayarlanacağı parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="071ca-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="071ca-110">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="071ca-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="071ca-111">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="071ca-111">[in] Optional.</span></span> <span data-ttu-id="071ca-112">Tür kısıtlamaları sıfır ile sonlandırılmış dizi.</span><span class="sxs-lookup"><span data-stu-id="071ca-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="071ca-113">Dizi üyeleri bir `mdTypeDef` , `mdTypeRef` veya `mdTypeSpec` meta veri belirteci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="071ca-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="071ca-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="071ca-114">Requirements</span></span>  

 <span data-ttu-id="071ca-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="071ca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="071ca-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="071ca-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="071ca-117">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="071ca-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="071ca-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="071ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="071ca-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="071ca-119">See also</span></span>

- [<span data-ttu-id="071ca-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="071ca-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="071ca-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="071ca-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
