---
title: IMetaDataImport::EnumMethodsWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: 5b5345fc4819716dc6c2a00323f94546cfc67f32
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720938"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="43e32-102">IMetaDataImport::EnumMethodsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43e32-102">IMetaDataImport::EnumMethodsWithName Method</span></span>

<span data-ttu-id="43e32-103">Belirtilen ada sahip olan ve belirtilen TypeDef belirtecinin başvurduğu tür tarafından tanımlanan yöntemleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="43e32-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43e32-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="43e32-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43e32-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43e32-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="43e32-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43e32-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="43e32-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43e32-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="43e32-108">'ndaki Yöntemlerini Numaralandırılacak türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="43e32-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="43e32-109">'ndaki Sabit listesinin kapsamını sınırlayan ad.</span><span class="sxs-lookup"><span data-stu-id="43e32-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="43e32-110">dışı MethodDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="43e32-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="43e32-111">'ndaki Dizinin en büyük boyutu `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="43e32-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="43e32-112">dışı İçinde döndürülen MethodDef belirteçleri sayısı `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="43e32-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43e32-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43e32-113">Remarks</span></span>  

 <span data-ttu-id="43e32-114">Bu yöntem, alanları ve yöntemleri numaralandırır, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="43e32-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="43e32-115">[IMetaDataImport:: EnumMethods](imetadataimport-enummethods-method.md)'ın aksine, `EnumMethodsWithName` belirtilen ada sahip olmayan tüm metot belirteçlerini atar.</span><span class="sxs-lookup"><span data-stu-id="43e32-115">Unlike [IMetaDataImport::EnumMethods](imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43e32-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43e32-116">Return Value</span></span>  
  
|<span data-ttu-id="43e32-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43e32-117">HRESULT</span></span>|<span data-ttu-id="43e32-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43e32-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="43e32-119">`EnumMethodsWithName` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="43e32-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="43e32-120">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="43e32-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="43e32-121">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="43e32-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43e32-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43e32-122">Requirements</span></span>  

 <span data-ttu-id="43e32-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43e32-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43e32-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="43e32-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43e32-125">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="43e32-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43e32-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43e32-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e32-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43e32-127">See also</span></span>

- [<span data-ttu-id="43e32-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43e32-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="43e32-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43e32-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
