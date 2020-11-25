---
title: ICorDebugManagedCallback::CreateAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: 5f831f0f42231f594e170567535af75216e68c45
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721315"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="aafd5-102">ICorDebugManagedCallback::CreateAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aafd5-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>

<span data-ttu-id="aafd5-103">Hata ayıklayıcıya bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="aafd5-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aafd5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aafd5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aafd5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aafd5-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="aafd5-106">'ndaki Uygulama etki alanının oluşturulduğu işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aafd5-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="aafd5-107">'ndaki Oluşturulmuş uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aafd5-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aafd5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aafd5-108">Requirements</span></span>  

 <span data-ttu-id="aafd5-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aafd5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aafd5-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aafd5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aafd5-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aafd5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aafd5-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aafd5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aafd5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aafd5-113">See also</span></span>

- [<span data-ttu-id="aafd5-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aafd5-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
