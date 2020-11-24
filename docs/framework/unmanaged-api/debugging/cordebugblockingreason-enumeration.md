---
title: CorDebugBlockingReason Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
ms.openlocfilehash: ddd03d70656ad52fd9d577beedc60b51c7b305d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672857"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="81c38-102">CorDebugBlockingReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="81c38-102">CorDebugBlockingReason Enumeration</span></span>

<span data-ttu-id="81c38-103">Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="81c38-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81c38-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="81c38-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="81c38-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="81c38-105">Members</span></span>  
  
|<span data-ttu-id="81c38-106">Üye</span><span class="sxs-lookup"><span data-stu-id="81c38-106">Member</span></span>|<span data-ttu-id="81c38-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81c38-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="81c38-108">Yalnızca iç kullanım.</span><span class="sxs-lookup"><span data-stu-id="81c38-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="81c38-109">Bir iş parçacığı, bir nesne üzerindeki izleyici kilidi ile ilişkili kritik bölümü almaya çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="81c38-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="81c38-110">Genellikle, veya yöntemlerinden birini çağırdığınızda bu durum oluşur <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="81c38-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="81c38-111">Bir iş parçacığı bir nesne için izleyici kilidi ile ilişkili olayı bekliyor.</span><span class="sxs-lookup"><span data-stu-id="81c38-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="81c38-112">Genellikle, bu yöntemlerden birini çağırdığınızda oluşur <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` .</span><span class="sxs-lookup"><span data-stu-id="81c38-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81c38-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81c38-113">Remarks</span></span>  

 <span data-ttu-id="81c38-114">`BLOCKING_MONITOR_CRITICAL_SECTION`Veya `BLOCKING_MONITOR_EVENT` üyesi bir [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapısında kullanıldığında, `pBlockingObject` yapının üyesi, girilmekte olan nesneyi temsil eden bir "ICorDebugValue" arabirimine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="81c38-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="81c38-115">Ayrıca, [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) arabirimini uygulamak da garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="81c38-115">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81c38-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81c38-116">Requirements</span></span>  

 <span data-ttu-id="81c38-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81c38-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81c38-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81c38-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81c38-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="81c38-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81c38-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81c38-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c38-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81c38-121">See also</span></span>

- [<span data-ttu-id="81c38-122">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="81c38-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="81c38-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="81c38-123">Debugging</span></span>](index.md)
