---
title: IMetaDataEmit::DefineSecurityAttributeSet Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
ms.openlocfilehash: c33ede841324820da16e33d35bbf5e8f8e75924f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009378"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="3c156-102">IMetaDataEmit::DefineSecurityAttributeSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c156-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="3c156-103">Belirtilen belirteç tarafından başvurulan nesneye iliştirilecek bir güvenlik izinleri kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c156-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c156-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3c156-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c156-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c156-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="3c156-106">'ndaki Güvenlik bilgilerinin eklendiği belirteç.</span><span class="sxs-lookup"><span data-stu-id="3c156-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="3c156-107">'ndaki `COR_SECATTR`Yapı dizisi.</span><span class="sxs-lookup"><span data-stu-id="3c156-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="3c156-108">'ndaki İçindeki öğe sayısı `rSecAttrs` .</span><span class="sxs-lookup"><span data-stu-id="3c156-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="3c156-109">dışı Yöntem başarısız olursa, `rSecAttrs` soruna neden olan öğenin içindeki dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c156-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c156-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c156-110">Requirements</span></span>  
 <span data-ttu-id="3c156-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c156-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c156-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3c156-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c156-113">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3c156-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c156-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c156-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c156-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c156-115">See also</span></span>

- [<span data-ttu-id="3c156-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c156-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3c156-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c156-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
