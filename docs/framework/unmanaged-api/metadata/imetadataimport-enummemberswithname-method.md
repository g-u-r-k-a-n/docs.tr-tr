---
title: IMetaDataImport::EnumMembersWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
ms.openlocfilehash: 35b82c33e54619eb9bebd5e5749ae202e905357a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721003"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="2b74a-102">IMetaDataImport::EnumMembersWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b74a-102">IMetaDataImport::EnumMembersWithName Method</span></span>

<span data-ttu-id="2b74a-103">Belirtilen ada sahip belirtilen türdeki üyeleri temsil eden MemberDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="2b74a-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b74a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2b74a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b74a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b74a-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="2b74a-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b74a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="2b74a-107">'ndaki Numaralandırılacak üyeleri olan türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="2b74a-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="2b74a-108">'ndaki Numaralandırıcı kapsamını sınırlayan üye adı.</span><span class="sxs-lookup"><span data-stu-id="2b74a-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="2b74a-109">dışı MemberDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="2b74a-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2b74a-110">'ndaki Dizinin en büyük boyutu `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="2b74a-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2b74a-111">dışı İçinde döndürülen MemberDef belirteçlerinin gerçek sayısı `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="2b74a-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b74a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b74a-112">Remarks</span></span>  

 <span data-ttu-id="2b74a-113">Bu yöntem, alanları ve yöntemleri numaralandırır, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="2b74a-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="2b74a-114">[IMetaDataImport:: EnumMembers](imetadataimport-enummembers-method.md)'ın aksine, `EnumMembersWithName` belirtilen ada sahip olmayan tüm alan ve üye belirteçlerini atar.</span><span class="sxs-lookup"><span data-stu-id="2b74a-114">Unlike [IMetaDataImport::EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b74a-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b74a-115">Return Value</span></span>  
  
|<span data-ttu-id="2b74a-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b74a-116">HRESULT</span></span>|<span data-ttu-id="2b74a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b74a-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2b74a-118">`EnumTypeDefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2b74a-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2b74a-119">Numaralandırılacak MemberDef belirteçleri yok.</span><span class="sxs-lookup"><span data-stu-id="2b74a-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="2b74a-120">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="2b74a-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b74a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b74a-121">Requirements</span></span>  

 <span data-ttu-id="2b74a-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b74a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b74a-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2b74a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b74a-124">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2b74a-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b74a-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b74a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b74a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b74a-126">See also</span></span>

- [<span data-ttu-id="2b74a-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b74a-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2b74a-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b74a-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
