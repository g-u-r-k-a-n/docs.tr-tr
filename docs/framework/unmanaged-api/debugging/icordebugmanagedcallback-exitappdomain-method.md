---
title: ICorDebugManagedCallback::ExitAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
ms.openlocfilehash: 5ba6ce4e59057442a9f17338ec7bfff787bd5d05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130801"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="72c56-102">ICorDebugManagedCallback::ExitAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72c56-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="72c56-103">Hata ayıklayıcıya bir uygulama etki alanının çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="72c56-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72c56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72c56-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72c56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72c56-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="72c56-106">'ndaki Verilen uygulama etki alanını içeren işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72c56-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="72c56-107">'ndaki Çıkış yapan uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72c56-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72c56-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72c56-108">Requirements</span></span>  
 <span data-ttu-id="72c56-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72c56-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72c56-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72c56-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72c56-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="72c56-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72c56-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72c56-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c56-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72c56-113">See also</span></span>

- [<span data-ttu-id="72c56-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72c56-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
