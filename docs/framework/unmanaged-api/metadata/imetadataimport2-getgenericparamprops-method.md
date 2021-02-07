---
description: ': IMetaDataImport2:: GetGenericParamProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport2::GetGenericParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 06b522531282b4a30cdc8ebf001c16438e8612ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688734"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="39a77-103">IMetaDataImport2::GetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39a77-103">IMetaDataImport2::GetGenericParamProps Method</span></span>

<span data-ttu-id="39a77-104">Belirtilen belirteç tarafından temsil edilen genel parametreyle ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="39a77-104">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39a77-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39a77-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39a77-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39a77-106">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="39a77-107">'ndaki Meta veri döndürülecek genel parametresini temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="39a77-107">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="39a77-108">dışı `Type` Parametrenin üst Oluşturucu veya yöntemdeki sıra konumu.</span><span class="sxs-lookup"><span data-stu-id="39a77-108">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="39a77-109">dışı Genel parametresi için tanımlayan [CorGenericParamAttr](corgenericparamattr-enumeration.md) numaralandırması değeri `Type` .</span><span class="sxs-lookup"><span data-stu-id="39a77-109">[out] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="39a77-110">dışı Parametrenin sahibini temsil eden bir TypeDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="39a77-110">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="39a77-111">dışı Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="39a77-111">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="39a77-112">dışı Genel parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="39a77-112">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="39a77-113">'ndaki `wzName` Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="39a77-113">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="39a77-114">dışı Adın, geniş karakter olarak döndürülen boyutu.</span><span class="sxs-lookup"><span data-stu-id="39a77-114">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39a77-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39a77-115">Requirements</span></span>  

 <span data-ttu-id="39a77-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39a77-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39a77-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="39a77-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39a77-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="39a77-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39a77-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39a77-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a77-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39a77-120">See also</span></span>

- [<span data-ttu-id="39a77-121">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39a77-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="39a77-122">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39a77-122">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
