---
title: CorDebugCreateProcessFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: d28f6eab5390194a4089cbbaf1f586c3f53a7db5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132251"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="86955-102">CorDebugCreateProcessFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="86955-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="86955-103">[ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="86955-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86955-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86955-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="86955-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="86955-105">Members</span></span>  
  
|<span data-ttu-id="86955-106">Üye</span><span class="sxs-lookup"><span data-stu-id="86955-106">Member</span></span>|<span data-ttu-id="86955-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86955-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="86955-108">Hiçbir özel seçenek ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="86955-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86955-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86955-109">Requirements</span></span>  
 <span data-ttu-id="86955-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86955-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86955-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86955-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86955-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86955-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86955-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86955-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86955-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86955-114">See also</span></span>

- [<span data-ttu-id="86955-115">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="86955-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
