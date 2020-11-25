---
title: CorDebugJITCompilerFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
ms.openlocfilehash: 0c8398b9e423414f32a391edcd5ea1c709af37f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696576"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="f6492-102">CorDebugJITCompilerFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f6492-102">CorDebugJITCompilerFlags Enumeration</span></span>

<span data-ttu-id="f6492-103">Yönetilen Just-In-Time (JıT) derleyicisinin davranışını etkileyen değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="f6492-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6492-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f6492-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f6492-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f6492-105">Members</span></span>  
  
|<span data-ttu-id="f6492-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f6492-106">Member</span></span>|<span data-ttu-id="f6492-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6492-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="f6492-108">Derleyicinin derleme verilerini izlemesi gerektiğini ve iyileştirmelere izin verdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6492-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="f6492-109">Derleyicinin derleme verilerini izlemesi gerektiğini, ancak iyileştirmeleri devre dışı bıraktığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6492-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="f6492-110">Derleyicinin derleme verilerini izlemesi gerektiğini, iyileştirmeleri devre dışı bıraktığını ve düzenleme ve devam teknolojilerini kullanmasını gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6492-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6492-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6492-111">Requirements</span></span>  

 <span data-ttu-id="f6492-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6492-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6492-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f6492-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6492-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f6492-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6492-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6492-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6492-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6492-116">See also</span></span>

- [<span data-ttu-id="f6492-117">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f6492-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
