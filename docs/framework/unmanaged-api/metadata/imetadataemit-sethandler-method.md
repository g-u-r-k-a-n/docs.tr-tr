---
title: IMetaDataEmit::SetHandler Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 6737275fb77e6f177832eb1d96214c37942bcd22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442161"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="2d82b-102">IMetaDataEmit::SetHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d82b-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="2d82b-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span><span class="sxs-lookup"><span data-stu-id="2d82b-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d82b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d82b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d82b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d82b-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="2d82b-106">[in] The handler to register.</span><span class="sxs-lookup"><span data-stu-id="2d82b-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d82b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d82b-107">Remarks</span></span>  
 <span data-ttu-id="2d82b-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span><span class="sxs-lookup"><span data-stu-id="2d82b-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="2d82b-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span><span class="sxs-lookup"><span data-stu-id="2d82b-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d82b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d82b-110">Requirements</span></span>  
 <span data-ttu-id="2d82b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d82b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d82b-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2d82b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d82b-113">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d82b-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d82b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d82b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d82b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d82b-115">See also</span></span>

- [<span data-ttu-id="2d82b-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d82b-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2d82b-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d82b-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
