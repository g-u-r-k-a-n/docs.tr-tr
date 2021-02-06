---
description: ': ICorDebugManagedCallback:: NameChange yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5f337f5e05b80c97e8b8e48f8b7bc76b3232b2c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660420"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="3611b-103">ICorDebugManagedCallback::NameChange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3611b-103">ICorDebugManagedCallback::NameChange Method</span></span>

<span data-ttu-id="3611b-104">Hata ayıklayıcıya bir uygulama etki alanı ya da bir iş parçacığının adının değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="3611b-104">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3611b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3611b-105">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3611b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3611b-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="3611b-107">'ndaki Bir ad değişikliğine sahip olan ya da bir ad değişikliğine sahip iş parçacığını içeren bir ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3611b-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="3611b-108">'ndaki Bir ad değişikliği olan iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3611b-108">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3611b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3611b-109">Requirements</span></span>  

 <span data-ttu-id="3611b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3611b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3611b-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3611b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3611b-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3611b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3611b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3611b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3611b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3611b-114">See also</span></span>

- [<span data-ttu-id="3611b-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3611b-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
