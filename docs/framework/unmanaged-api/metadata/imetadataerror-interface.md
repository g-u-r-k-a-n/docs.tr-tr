---
title: IMetaDataError Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
ms.openlocfilehash: 5f5e04787ce0ab0e1c8ecf3c19ba37e76ba38bfe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701932"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="0916d-102">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0916d-102">IMetaDataError Interface</span></span>

<span data-ttu-id="0916d-103">Meta veri birleştirme sırasında hataları raporlamak için bir geri çağırma mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="0916d-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0916d-104">`IMetaDataError`Arabirimin istemci tarafından uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0916d-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0916d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0916d-105">Methods</span></span>  
  
|<span data-ttu-id="0916d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0916d-106">Method</span></span>|<span data-ttu-id="0916d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0916d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0916d-108">OnError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0916d-108">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="0916d-109">Meta veri birleştirme sırasında oluşan hataların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0916d-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0916d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0916d-110">Requirements</span></span>  

 <span data-ttu-id="0916d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0916d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0916d-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0916d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0916d-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0916d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0916d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0916d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0916d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0916d-115">See also</span></span>

- [<span data-ttu-id="0916d-116">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0916d-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
