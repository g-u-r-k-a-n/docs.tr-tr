---
title: ICorDebugManagedCallback::BreakpointSetError Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
ms.openlocfilehash: dae04e1809c1bb3260461086a4953b8b4e5cce52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122578"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="e2506-102">ICorDebugManagedCallback::BreakpointSetError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2506-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="e2506-103">Hata ayıklayıcısını, ortak dil çalışma zamanının, bir işlev tam zamanında (JıT) derlenmesinden önce ayarlanmış bir kesme noktasını doğru bir şekilde bağlamadığı konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="e2506-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2506-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2506-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2506-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2506-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e2506-106">'ndaki İlişkisiz kesme noktasını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2506-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="e2506-107">'ndaki İlişkisiz kesme noktasını içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2506-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="e2506-108">'ndaki İlişkisiz kesme noktasını temsil eden ICorDebugBreakpoint nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2506-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="e2506-109">'ndaki Hatayı gösteren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e2506-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2506-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2506-110">Remarks</span></span>  
 <span data-ttu-id="e2506-111">Verilen kesme noktası hiçbir şekilde isabet ettirilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="e2506-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="e2506-112">Hata ayıklayıcı devre dışı bırakıp yeniden bağlamasını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e2506-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2506-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2506-113">Requirements</span></span>  
 <span data-ttu-id="e2506-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2506-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2506-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2506-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2506-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2506-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2506-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2506-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2506-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2506-118">See also</span></span>

- [<span data-ttu-id="e2506-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2506-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
