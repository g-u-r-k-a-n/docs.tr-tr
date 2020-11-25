---
title: IMetaDataFilter::IsTokenMarked Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
ms.openlocfilehash: ce7292003872805c9390ce3d9c59b39497a83ed1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701841"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="3f608-102">IMetaDataFilter::IsTokenMarked Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f608-102">IMetaDataFilter::IsTokenMarked Method</span></span>

<span data-ttu-id="3f608-103">Belirtilen meta veri belirtecinin işlenmiş olarak işaretlenip işaretlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="3f608-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f608-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3f608-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f608-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f608-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="3f608-106">'ndaki Bir işleme işareti için incelenecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="3f608-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="3f608-107">dışı İşlendiği bir değer `true` `tk` ; Aksi takdirde `false` .</span><span class="sxs-lookup"><span data-stu-id="3f608-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f608-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f608-108">Requirements</span></span>  

 <span data-ttu-id="3f608-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f608-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f608-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3f608-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f608-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3f608-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f608-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f608-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f608-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f608-113">See also</span></span>

- [<span data-ttu-id="3f608-114">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f608-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
