---
title: RUNTIME_INFO_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
ms.openlocfilehash: 80643187045e7e96b9c18169c5e71287713d711f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106244"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="6cf5b-102">RUNTIME_INFO_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6cf5b-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="6cf5b-103">Ortak dil çalışma zamanı (CLR) hakkında hangi bilgilerin döndürüleceğini belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cf5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cf5b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6cf5b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6cf5b-105">Members</span></span>  
  
|<span data-ttu-id="6cf5b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6cf5b-106">Member</span></span>|<span data-ttu-id="6cf5b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cf5b-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="6cf5b-108">Dizin bilgilerinin içerilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="6cf5b-109">Sürüm bilgisinin dahil edilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="6cf5b-110">Hata sonrasında bir hata iletişim kutusu gösterilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="6cf5b-111">[SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) işlevini SEM_FAILCRITICALERRORS bayrağıyla çağırmanın etkilerinin geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-111">Indicates that the effects of calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="6cf5b-112">Diğer bir deyişle, bir yükleme iletişim kutusu gizlenmeden önce hata sonrasında gösterilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="6cf5b-113">Çalışma zamanının AMD-64 ile uyumlu bir sürümü hakkında bilgi isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="6cf5b-114">Çalışma zamanının IA-64 ile uyumlu bir sürümü hakkında bilgi isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="6cf5b-115">Çalışma zamanının x86 uyumlu sürümü hakkında bilgi isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="6cf5b-116">Sürüm yükseltme bilgilerinin dahil edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cf5b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6cf5b-117">Remarks</span></span>  
 <span data-ttu-id="6cf5b-118">Aşağıdaki platform mimarisi bayrakları tek seferde belirtilebilir ve birleştirilemez:</span><span class="sxs-lookup"><span data-stu-id="6cf5b-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="6cf5b-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="6cf5b-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="6cf5b-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="6cf5b-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="6cf5b-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="6cf5b-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cf5b-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cf5b-122">Requirements</span></span>  
 <span data-ttu-id="6cf5b-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cf5b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cf5b-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6cf5b-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cf5b-125">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6cf5b-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cf5b-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cf5b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf5b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cf5b-127">See also</span></span>

- [<span data-ttu-id="6cf5b-128">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6cf5b-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
