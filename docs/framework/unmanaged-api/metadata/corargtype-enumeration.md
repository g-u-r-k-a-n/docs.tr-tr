---
title: CorArgType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorArgType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorArgType
helpviewer_keywords:
- CorArgType enumeration [.NET Framework metadata]
ms.assetid: 3c1cb268-57a0-4664-91c7-f6908ff29e32
topic_type:
- apiref
ms.openlocfilehash: 6388d804df43964866073d7c3b32dca84fb2d06f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720431"
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="23f68-102">CorArgType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="23f68-102">CorArgType Enumeration</span></span>

<span data-ttu-id="23f68-103">Çalışma zamanı tanıtıcısının yerel türünü tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="23f68-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f68-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="23f68-104">Syntax</span></span>  
  
```cpp  
typedef enum CorArgType {  
  
    IMAGE_CEE_CS_END        = 0x0,  
    IMAGE_CEE_CS_VOID       = 0x1,  
    IMAGE_CEE_CS_I4         = 0x2,  
    IMAGE_CEE_CS_I8         = 0x3,  
    IMAGE_CEE_CS_R4         = 0x4,  
    IMAGE_CEE_CS_R8         = 0x5,  
    IMAGE_CEE_CS_PTR        = 0x6,  
    IMAGE_CEE_CS_OBJECT     = 0x7,  
    IMAGE_CEE_CS_STRUCT4    = 0x8,  
    IMAGE_CEE_CS_STRUCT32   = 0x9,  
    IMAGE_CEE_CS_BYVALUE    = 0xA  
  
} CorArgType;  
```  
  
## <a name="requirements"></a><span data-ttu-id="23f68-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23f68-105">Requirements</span></span>  

 <span data-ttu-id="23f68-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23f68-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f68-107">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="23f68-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="23f68-108">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f68-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f68-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23f68-109">See also</span></span>

- [<span data-ttu-id="23f68-110">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="23f68-110">Metadata Enumerations</span></span>](metadata-enumerations.md)
