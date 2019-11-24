---
title: CorRefToDefCheck Numaralandırması
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: e6c3c9b842bd823e8975661964480fd801779b2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450126"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="91823-102">CorRefToDefCheck Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="91823-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="91823-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span><span class="sxs-lookup"><span data-stu-id="91823-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91823-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91823-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="91823-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="91823-105">Members</span></span>  
  
|<span data-ttu-id="91823-106">Üye</span><span class="sxs-lookup"><span data-stu-id="91823-106">Member</span></span>|<span data-ttu-id="91823-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91823-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="91823-108">Specifies that type references and member references should be converted to definitions.</span><span class="sxs-lookup"><span data-stu-id="91823-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="91823-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="91823-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="91823-110">Specifies that all referenced items should be converted to definitions.</span><span class="sxs-lookup"><span data-stu-id="91823-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="91823-111">Specifies that no referenced items should be converted to definitions.</span><span class="sxs-lookup"><span data-stu-id="91823-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="91823-112">Specifies that only type references should be converted to type definitions.</span><span class="sxs-lookup"><span data-stu-id="91823-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="91823-113">Specifies that only member references should be converted to definitions.</span><span class="sxs-lookup"><span data-stu-id="91823-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="91823-114">That is, member references should be converted to either method definitions or field definitions.</span><span class="sxs-lookup"><span data-stu-id="91823-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91823-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91823-115">Requirements</span></span>  
 <span data-ttu-id="91823-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91823-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91823-117">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="91823-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="91823-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91823-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91823-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91823-119">See also</span></span>

- [<span data-ttu-id="91823-120">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="91823-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
