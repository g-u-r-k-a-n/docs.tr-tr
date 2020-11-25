---
title: ICorDebugManagedCallback::NameChange Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 0307ad5794d641833c2da1a1674e455ebff24861
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726528"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="6aac7-102">ICorDebugManagedCallback::NameChange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6aac7-102">ICorDebugManagedCallback::NameChange Method</span></span>

<span data-ttu-id="6aac7-103">Hata ayıklayıcıya bir uygulama etki alanı ya da bir iş parçacığının adının değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="6aac7-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aac7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6aac7-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aac7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6aac7-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="6aac7-106">'ndaki Bir ad değişikliğine sahip olan ya da bir ad değişikliğine sahip iş parçacığını içeren bir ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6aac7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6aac7-107">'ndaki Bir ad değişikliği olan iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6aac7-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aac7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6aac7-108">Requirements</span></span>  

 <span data-ttu-id="6aac7-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aac7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aac7-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6aac7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6aac7-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6aac7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aac7-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aac7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aac7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6aac7-113">See also</span></span>

- [<span data-ttu-id="6aac7-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6aac7-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
