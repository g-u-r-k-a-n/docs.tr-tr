---
title: CVStruct Yapısı
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
ms.openlocfilehash: db36b94fafe20b58b9bcbb886b8d285326960f67
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715582"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="1a42f-102">CVStruct Yapısı</span><span class="sxs-lookup"><span data-stu-id="1a42f-102">CVStruct Structure</span></span>

<span data-ttu-id="1a42f-103">Bir modül veya bileşik görüntü yüklerken kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="1a42f-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a42f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1a42f-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="1a42f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1a42f-105">Members</span></span>  
  
|<span data-ttu-id="1a42f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1a42f-106">Member</span></span>|<span data-ttu-id="1a42f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a42f-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1a42f-108">Ana</span><span class="sxs-lookup"><span data-stu-id="1a42f-108">Major</span></span>|<span data-ttu-id="1a42f-109">Ana sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="1a42f-109">Major version build number.</span></span>|  
|<span data-ttu-id="1a42f-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="1a42f-110">Minor</span></span>|<span data-ttu-id="1a42f-111">İkincil sürüm yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="1a42f-111">Minor version build number.</span></span>|  
|<span data-ttu-id="1a42f-112">Alt</span><span class="sxs-lookup"><span data-stu-id="1a42f-112">Sub</span></span>|<span data-ttu-id="1a42f-113">Alt yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="1a42f-113">Sub-build number.</span></span>|  
|<span data-ttu-id="1a42f-114">Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a42f-114">Build</span></span>|<span data-ttu-id="1a42f-115">Yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="1a42f-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a42f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a42f-116">Requirements</span></span>  

 <span data-ttu-id="1a42f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a42f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a42f-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1a42f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a42f-119">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1a42f-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a42f-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a42f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a42f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a42f-121">See also</span></span>

- [<span data-ttu-id="1a42f-122">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="1a42f-122">Metadata Structures</span></span>](metadata-structures.md)
