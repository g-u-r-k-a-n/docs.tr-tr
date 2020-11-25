---
title: ICorDebugManagedCallback2::CreateConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: 5a4ebf65dfaaa487e87f3fd78e54c468c7e24a89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697252"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="fe0fa-102">ICorDebugManagedCallback2::CreateConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe0fa-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>

<span data-ttu-id="fe0fa-103">Hata ayıklayıcıya yeni bir bağlantı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe0fa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fe0fa-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe0fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe0fa-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="fe0fa-106">'ndaki Bağlantının oluşturulduğu işlemi temsil eden bir "ICorDebugProcess" nesnesi işaretçisi</span><span class="sxs-lookup"><span data-stu-id="fe0fa-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="fe0fa-107">'ndaki Yeni bağlantının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="fe0fa-108">'ndaki Yeni bağlantının adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe0fa-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe0fa-109">Remarks</span></span>  

 <span data-ttu-id="fe0fa-110">`CreateConnection`Aşağıdaki durumlardan birinde bir geri çağırma harekete geçirilir:</span><span class="sxs-lookup"><span data-stu-id="fe0fa-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="fe0fa-111">Bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirayarlandığında.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="fe0fa-112">Bu durumda, çalışma zamanı `CreateConnection` işlemdeki her bağlantı için bir olay ve bir [ICorDebugManagedCallback2:: ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) olayı oluşturur ve gönderir.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="fe0fa-113">Bir ana bilgisayar [BARıNDıRMA API](../hosting/index.md)'Sinde [ICLRDebugManager:: BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) öğesini çağırdığında.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-113">When a host calls [ICLRDebugManager::BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe0fa-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe0fa-114">Requirements</span></span>  

 <span data-ttu-id="fe0fa-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe0fa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe0fa-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fe0fa-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe0fa-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe0fa-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe0fa-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe0fa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0fa-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe0fa-119">See also</span></span>

- [<span data-ttu-id="fe0fa-120">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe0fa-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="fe0fa-121">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe0fa-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
