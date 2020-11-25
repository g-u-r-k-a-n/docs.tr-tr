---
title: CorRegFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
ms.openlocfilehash: 5ea588194720394ad9f361fbba702f3fcdcbe110
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706105"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="95d2e-102">CorRegFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="95d2e-102">CorRegFlags Enumeration</span></span>

<span data-ttu-id="95d2e-103">Modül veya bileşik görüntü yüklerken kayıt için kullanılan bayrak değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="95d2e-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d2e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="95d2e-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="95d2e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="95d2e-105">Members</span></span>  
  
|<span data-ttu-id="95d2e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="95d2e-106">Member</span></span>|<span data-ttu-id="95d2e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95d2e-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="95d2e-108">Dosyaların hedefe kopyalanmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="95d2e-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="95d2e-109">Modülün veya kompozit 'in bir yapılandırma olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="95d2e-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="95d2e-110">Modülün veya Composite sınıf başvurularına sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="95d2e-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95d2e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95d2e-111">Requirements</span></span>  

 <span data-ttu-id="95d2e-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95d2e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95d2e-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="95d2e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95d2e-114">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="95d2e-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95d2e-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95d2e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d2e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95d2e-116">See also</span></span>

- [<span data-ttu-id="95d2e-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="95d2e-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
