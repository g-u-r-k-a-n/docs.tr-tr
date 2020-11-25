---
title: CorSetENC Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: df945803f2d56d04ccc68f314eb55665579ed7fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706000"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="433a6-102">CorSetENC Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="433a6-102">CorSetENC Enumeration</span></span>

<span data-ttu-id="433a6-103">Meta veri oluşturma sırasında davranışı etkilemek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="433a6-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="433a6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="433a6-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="433a6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="433a6-105">Members</span></span>  
  
|<span data-ttu-id="433a6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="433a6-106">Member</span></span>|<span data-ttu-id="433a6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="433a6-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="433a6-108">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="433a6-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="433a6-109">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="433a6-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="433a6-110">Meta verilerin güncelleştirilebileceğini, belirteçlerin taşınamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="433a6-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="433a6-111">Simgelerin güncelleştirmeler sırasında taşınabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="433a6-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="433a6-112">Güncelleştirmelerin yalnızca eklemelerden oluşabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="433a6-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="433a6-113">Belirteçler taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="433a6-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="433a6-114">Derlemenin artımlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="433a6-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="433a6-115">Yalnızca değiştirilen meta verilerin kaydedilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="433a6-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="433a6-116">`MDUpdateENC`, `MDUpdateFull` Ve içerir `MDUpdateIncremental` .</span><span class="sxs-lookup"><span data-stu-id="433a6-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="433a6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="433a6-117">Requirements</span></span>  

 <span data-ttu-id="433a6-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="433a6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="433a6-119">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="433a6-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="433a6-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="433a6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="433a6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="433a6-121">See also</span></span>

- [<span data-ttu-id="433a6-122">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="433a6-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
