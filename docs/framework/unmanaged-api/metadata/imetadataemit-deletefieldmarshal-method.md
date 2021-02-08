---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D eleteFieldMarshal yöntemi'
title: IMetaDataEmit::DeleteFieldMarshal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 966f2ae20ad9ff4b9c1c9eec32974bc89aa76d13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783969"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="b6f47-103">IMetaDataEmit::DeleteFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6f47-103">IMetaDataEmit::DeleteFieldMarshal Method</span></span>

<span data-ttu-id="b6f47-104">Belirtilen belirteç tarafından başvurulan nesne için PInvoke sıralama meta veri imzasını yok eder.</span><span class="sxs-lookup"><span data-stu-id="b6f47-104">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f47-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6f47-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6f47-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6f47-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="b6f47-107">'ndaki `mdFieldDef` `mdParamDef` Sıralama meta verileri imzasının silineceği alanı veya parametreyi temsil eden bir veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="b6f47-107">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6f47-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6f47-108">Requirements</span></span>  

 <span data-ttu-id="b6f47-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6f47-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6f47-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b6f47-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6f47-111">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b6f47-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6f47-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6f47-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f47-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6f47-113">See also</span></span>

- [<span data-ttu-id="b6f47-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6f47-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b6f47-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6f47-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
