---
title: IMetaDataImport2::EnumMethodSpecs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 8f6fbc570e7ea85aca5b365611d58a1700fb27cd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490734"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="d9b4d-102">IMetaDataImport2::EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9b4d-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="d9b4d-103">Belirtilen MethodDef veya MemberRef belirteciyle ilişkili bir MethodSpec belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d9b4d-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b4d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d9b4d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d9b4d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9b4d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d9b4d-106">[in, out] İçin numaralandırıcı işaretçisi `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="d9b4d-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="d9b4d-107">'ndaki MethodSpec belirteçleri numaralandırılmış olan yöntemi temsil eden MemberRef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="d9b4d-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="d9b4d-108">Değeri `tk` 0 (sıfır) ise, kapsamdaki tüm MethodSpec belirteçleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="d9b4d-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="d9b4d-109">dışı Numaralandırılacak MethodSpec belirteçlerinin dizisi.</span><span class="sxs-lookup"><span data-stu-id="d9b4d-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d9b4d-110">'ndaki İstenen en fazla belirteç sayısı, içine yerleştirilecek `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="d9b4d-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="d9b4d-111">dışı Döndürülen belirteç sayısı döndürüldü `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="d9b4d-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9b4d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9b4d-112">Return Value</span></span>  
  
|<span data-ttu-id="d9b4d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9b4d-113">HRESULT</span></span>|<span data-ttu-id="d9b4d-114">Description</span><span class="sxs-lookup"><span data-stu-id="d9b4d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d9b4d-115">`EnumMethodSpecs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d9b4d-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d9b4d-116">`phEnum`Üye öğesi yok.</span><span class="sxs-lookup"><span data-stu-id="d9b4d-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="d9b4d-117">Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d9b4d-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9b4d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9b4d-118">Requirements</span></span>  
 <span data-ttu-id="d9b4d-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9b4d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9b4d-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d9b4d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9b4d-121">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d9b4d-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9b4d-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9b4d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b4d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9b4d-123">See also</span></span>

- [<span data-ttu-id="d9b4d-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9b4d-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="d9b4d-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9b4d-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
