---
description: 'Daha fazla bilgi edinin: CorDebugDecodeEventFlagsWindows sabit listesi'
title: CorDebugDecodeEventFlagsWindows Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
ms.openlocfilehash: 765ce4b967d00bd70becca666e2ed418614d6fe3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801702"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="edaff-103">CorDebugDecodeEventFlagsWindows Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="edaff-103">CorDebugDecodeEventFlagsWindows Enumeration</span></span>

<span data-ttu-id="edaff-104">Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="edaff-104">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edaff-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="edaff-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="edaff-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="edaff-106">Members</span></span>  
  
|<span data-ttu-id="edaff-107">Üye</span><span class="sxs-lookup"><span data-stu-id="edaff-107">Member</span></span>|<span data-ttu-id="edaff-108">Description</span><span class="sxs-lookup"><span data-stu-id="edaff-108">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="edaff-109">Hata ayıklama olayının ilk şans özel durumu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="edaff-109">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edaff-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="edaff-110">Remarks</span></span>  

 <span data-ttu-id="edaff-111">[ICorDebugProcess6::D ecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemi `dwFlags` bir hata ayıklama olayı ve değeri hedef mimarisine bağlı olan ek bilgiler sağlayan bir parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="edaff-111">The [ICorDebugProcess6::DecodeEvent](icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="edaff-112">`CorDebugDecodeEventFlagsWindows`Sabit listesi Windows platformunda hata ayıklama olayları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="edaff-112">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edaff-113">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="edaff-113">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edaff-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edaff-114">Requirements</span></span>  

 <span data-ttu-id="edaff-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edaff-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edaff-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="edaff-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edaff-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="edaff-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edaff-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edaff-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edaff-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edaff-119">See also</span></span>

- [<span data-ttu-id="edaff-120">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="edaff-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
