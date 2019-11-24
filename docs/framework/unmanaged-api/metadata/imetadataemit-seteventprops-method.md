---
title: IMetaDataEmit::SetEventProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: 506e13ad956a01b16e36d8c71737fe0efce4c01b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450323"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="f5534-102">IMetaDataEmit::SetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5534-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="f5534-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="f5534-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5534-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5534-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5534-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5534-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="f5534-106">[in] The event token.</span><span class="sxs-lookup"><span data-stu-id="f5534-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="f5534-107">[in] Event flags.</span><span class="sxs-lookup"><span data-stu-id="f5534-107">[in] Event flags.</span></span> <span data-ttu-id="f5534-108">This is a bitmask of `CorEventAttr` values.</span><span class="sxs-lookup"><span data-stu-id="f5534-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="f5534-109">[in] The token for the event class.</span><span class="sxs-lookup"><span data-stu-id="f5534-109">[in] The token for the event class.</span></span> <span data-ttu-id="f5534-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="f5534-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="f5534-111">[in] The method used to subscribe to the event, or null.</span><span class="sxs-lookup"><span data-stu-id="f5534-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="f5534-112">[in] The method used to unsubscribe to the event, or null.</span><span class="sxs-lookup"><span data-stu-id="f5534-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="f5534-113">[in] The method used (by a derived class) to raise the event.</span><span class="sxs-lookup"><span data-stu-id="f5534-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="f5534-114">[in] An array of tokens for other methods associated with the event.</span><span class="sxs-lookup"><span data-stu-id="f5534-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="f5534-115">The last element of the array must be `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="f5534-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5534-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5534-116">Requirements</span></span>  
 <span data-ttu-id="f5534-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5534-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5534-118">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f5534-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5534-119">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5534-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5534-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5534-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5534-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5534-121">See also</span></span>

- [<span data-ttu-id="f5534-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5534-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f5534-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5534-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
