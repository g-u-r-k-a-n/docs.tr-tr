---
title: IMetaDataImport::EnumCustomAttributes Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 3b12200dae23a7b6a2f6e1654e46fdf74dc90968
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700541"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="d17aa-102">IMetaDataImport::EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d17aa-102">IMetaDataImport::EnumCustomAttributes Method</span></span>

<span data-ttu-id="d17aa-103">Belirtilen tür veya üyeyle ilişkili özel öznitelik tanımı belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d17aa-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d17aa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d17aa-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d17aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d17aa-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="d17aa-106">[in, out] Döndürülen Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d17aa-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="d17aa-107">'ndaki Numaralandırma kapsamı için bir belirteç veya tüm özel öznitelikler için sıfır.</span><span class="sxs-lookup"><span data-stu-id="d17aa-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="d17aa-108">'ndaki Numaralandırılacak özniteliklerin türünün veya `null` tüm türlerin oluşturucusunun belirteci.</span><span class="sxs-lookup"><span data-stu-id="d17aa-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="d17aa-109">dışı Özel öznitelik belirteçlerinin dizisi.</span><span class="sxs-lookup"><span data-stu-id="d17aa-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d17aa-110">'ndaki Dizinin en büyük boyutu `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="d17aa-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="d17aa-111">[Out, isteğe bağlı] İçinde döndürülen belirteç değerlerinin gerçek sayısı `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="d17aa-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d17aa-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d17aa-112">Return Value</span></span>  
  
|<span data-ttu-id="d17aa-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d17aa-113">HRESULT</span></span>|<span data-ttu-id="d17aa-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d17aa-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d17aa-115">`EnumCustomAttributes` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d17aa-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d17aa-116">Numaralandırılacak özel öznitelik yok.</span><span class="sxs-lookup"><span data-stu-id="d17aa-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="d17aa-117">Bu durumda, `pcCustomAttributes` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="d17aa-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d17aa-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d17aa-118">Requirements</span></span>  

 <span data-ttu-id="d17aa-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d17aa-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d17aa-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d17aa-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d17aa-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d17aa-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d17aa-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d17aa-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d17aa-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d17aa-123">See also</span></span>

- [<span data-ttu-id="d17aa-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d17aa-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d17aa-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d17aa-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
