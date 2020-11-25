---
title: IMetaDataImport::EnumUserStrings Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: c7dcc740dcf9b228713693a57dc8ef96d215ebad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716570"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="3393f-102">IMetaDataImport::EnumUserStrings Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3393f-102">IMetaDataImport::EnumUserStrings Method</span></span>

<span data-ttu-id="3393f-103">Geçerli meta veri kapsamındaki sabit kodlanmış dizeleri temsil eden dize belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="3393f-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3393f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3393f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3393f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3393f-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="3393f-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3393f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3393f-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3393f-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="3393f-108">dışı Dize belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="3393f-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3393f-109">'ndaki Dizinin en büyük boyutu `rStrings` .</span><span class="sxs-lookup"><span data-stu-id="3393f-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="3393f-110">dışı İçinde döndürülen dize belirteçleri sayısı `rStrings` .</span><span class="sxs-lookup"><span data-stu-id="3393f-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3393f-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3393f-111">Return Value</span></span>  
  
|<span data-ttu-id="3393f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3393f-112">HRESULT</span></span>|<span data-ttu-id="3393f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3393f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3393f-114">`EnumUserStrings` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3393f-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3393f-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="3393f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3393f-116">Bu durumda, `pcStrings` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="3393f-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3393f-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3393f-117">Remarks</span></span>  

 <span data-ttu-id="3393f-118">Dize belirteçleri [ımetadatayayma::D efineUserString](imetadataemit-defineuserstring-method.md) yöntemi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3393f-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="3393f-119">Bu yöntem, bir derleyici yerine bir meta veri tarayıcısı tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3393f-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3393f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3393f-120">Requirements</span></span>  

 <span data-ttu-id="3393f-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3393f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3393f-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3393f-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3393f-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3393f-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3393f-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3393f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3393f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3393f-125">See also</span></span>

- [<span data-ttu-id="3393f-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3393f-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3393f-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3393f-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
