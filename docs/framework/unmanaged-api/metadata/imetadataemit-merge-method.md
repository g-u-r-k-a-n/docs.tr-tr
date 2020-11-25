---
title: IMetaDataEmit::Merge Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: e64d644b511f7c3249c48b9642bfd3163142af3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722017"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="1dd3f-102">IMetaDataEmit::Merge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dd3f-102">IMetaDataEmit::Merge Method</span></span>

<span data-ttu-id="1dd3f-103">Belirtilen içeri aktarılan kapsamı birleştirilecek kapsamlar listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="1dd3f-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd3f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1dd3f-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd3f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dd3f-105">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="1dd3f-106">'ndaki Birleştirilecek kapsamı tanımlayan bir [IMetaDataImport](imetadataimport-interface.md) nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dd3f-106">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="1dd3f-107">'ndaki Belirteç yeniden eşlemesini belirten bir [IMapToken](imaptoken-interface.md) nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dd3f-107">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="1dd3f-108">'ndaki Hataları belirten [IUnknown](/cpp/atl/iunknown) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dd3f-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dd3f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dd3f-109">Remarks</span></span>  

 <span data-ttu-id="1dd3f-110">Meta verilerin birleştiğini tek bir kapsamda tetiklemek için [ımetadatayayma:: MergeEnd](imetadataemit-mergeend-method.md) ' i çağırın.</span><span class="sxs-lookup"><span data-stu-id="1dd3f-110">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd3f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dd3f-111">Requirements</span></span>  

 <span data-ttu-id="1dd3f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd3f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd3f-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1dd3f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1dd3f-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1dd3f-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd3f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd3f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dd3f-116">See also</span></span>

- [<span data-ttu-id="1dd3f-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dd3f-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1dd3f-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dd3f-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
