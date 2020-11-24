---
title: ICorDebugThread2::InterceptCurrentException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: 96e3a90bcb7700915bfd3618d7bae40c0ff64a75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678603"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="0568d-102">ICorDebugThread2::InterceptCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0568d-102">ICorDebugThread2::InterceptCurrentException Method</span></span>

<span data-ttu-id="0568d-103">Bir hata ayıklayıcının bu iş parçacığında geçerli özel durumu kesmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0568d-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0568d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0568d-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0568d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0568d-105">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="0568d-106">'ndaki Etkin yığın çerçevesini temsil eden bir ICorDebugFrame işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0568d-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0568d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0568d-107">Remarks</span></span>  

 <span data-ttu-id="0568d-108">`InterceptCurrentException`Yöntem bir özel durum geri çağırması ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) veya [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) Ile ilişkili [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)öğesine yapılan çağrı arasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0568d-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0568d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0568d-109">Requirements</span></span>  

 <span data-ttu-id="0568d-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0568d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0568d-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0568d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0568d-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0568d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0568d-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0568d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
