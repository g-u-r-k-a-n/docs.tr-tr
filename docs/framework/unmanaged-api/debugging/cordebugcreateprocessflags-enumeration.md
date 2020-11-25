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
ms.openlocfilehash: f6f589656a3063fc89bd276b32d0ed751fd8d2d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733405"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="8db08-102">CorDebugCreateProcessFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8db08-102">CorDebugCreateProcessFlags Enumeration</span></span>

<span data-ttu-id="8db08-103">[ICorDebug:: CreateProcess](icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8db08-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8db08-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8db08-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8db08-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8db08-105">Members</span></span>  
  
|<span data-ttu-id="8db08-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8db08-106">Member</span></span>|<span data-ttu-id="8db08-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8db08-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="8db08-108">Hiçbir özel seçenek ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="8db08-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8db08-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8db08-109">Requirements</span></span>  

 <span data-ttu-id="8db08-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8db08-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8db08-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8db08-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8db08-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8db08-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8db08-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8db08-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db08-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8db08-114">See also</span></span>

- [<span data-ttu-id="8db08-115">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="8db08-115">Debugging Enumerations</span></span>](debugging-enumerations.md)
