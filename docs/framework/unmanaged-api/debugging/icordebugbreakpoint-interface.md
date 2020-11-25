---
title: ICorDebugBreakpoint Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 0c84a91c7da553d0c84a4995b4744576d861dcb9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730207"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="70045-102">ICorDebugBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70045-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="70045-103">Bir işlevde bir kesme noktasını veya bir değer üzerinde bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="70045-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70045-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="70045-104">Methods</span></span>  
  
|<span data-ttu-id="70045-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="70045-105">Method</span></span>|<span data-ttu-id="70045-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70045-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70045-107">Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70045-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="70045-108">Bunun etkin durumunu ayarlar `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="70045-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="70045-109">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70045-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="70045-110">Bu, etkin olup olmadığını gösteren bir değer alır `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="70045-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70045-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70045-111">Remarks</span></span>  

 <span data-ttu-id="70045-112">Kesme noktaları, Koşullu ifadeleri doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="70045-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="70045-113">Bu tür işlevler isteniyorsa, bir hata ayıklayıcının üzerinde uygulaması gerekir `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="70045-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="70045-114">ICorDebugFunctionBreakpoint Arabirimi `ICorDebugBreakpoint` işlevleri içindeki kesme noktalarını destekleyecek şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="70045-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70045-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="70045-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70045-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70045-116">Requirements</span></span>  

 <span data-ttu-id="70045-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70045-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70045-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="70045-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70045-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="70045-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70045-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70045-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70045-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70045-121">See also</span></span>

- [<span data-ttu-id="70045-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="70045-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
