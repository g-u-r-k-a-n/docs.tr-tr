---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineMemberRef yöntemi'
title: IMetaDataEmit::DefineMemberRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: 1d88294cea14369c8a8f16b6048f96472fbb9502
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753425"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="3920b-103">IMetaDataEmit::DefineMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3920b-103">IMetaDataEmit::DefineMemberRef Method</span></span>

<span data-ttu-id="3920b-104">Geçerli kapsam dışındaki bir modülün üyesine yönelik bir başvuru tanımlar ve bu başvuru tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="3920b-104">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3920b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3920b-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3920b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3920b-106">Parameters</span></span>  

 `tkImport`  
 <span data-ttu-id="3920b-107">'ndaki Üye genel değilse hedef üyenin sınıfı veya arabirimi için belirteç; üye geneldir ise, `mdModuleRef` diğer dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="3920b-107">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="3920b-108">'ndaki Hedef üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="3920b-108">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3920b-109">'ndaki Hedef üyenin imzası.</span><span class="sxs-lookup"><span data-stu-id="3920b-109">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3920b-110">'ndaki İçindeki bayt sayısı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="3920b-110">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="3920b-111">dışı `mdMemberRef` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="3920b-111">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3920b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3920b-112">Requirements</span></span>  

 <span data-ttu-id="3920b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3920b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3920b-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3920b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3920b-115">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3920b-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3920b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3920b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3920b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3920b-117">See also</span></span>

- [<span data-ttu-id="3920b-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3920b-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3920b-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3920b-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
