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
ms.openlocfilehash: e98748b523b948dc002f2ebc4e2e79fc7d659918
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781589"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="e1490-102">ICorDebugManagedCallback2::CreateConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1490-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="e1490-103">Hata ayıklayıcıya yeni bir bağlantı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e1490-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1490-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1490-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1490-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1490-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e1490-106">'ndaki Bağlantının oluşturulduğu işlemi temsil eden bir "ICorDebugProcess" nesnesi işaretçisi</span><span class="sxs-lookup"><span data-stu-id="e1490-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="e1490-107">'ndaki Yeni bağlantının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e1490-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="e1490-108">'ndaki Yeni bağlantının adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e1490-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1490-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1490-109">Remarks</span></span>  
 <span data-ttu-id="e1490-110">`CreateConnection` geri çağırma aşağıdaki durumlardan biri içinde tetiklenir:</span><span class="sxs-lookup"><span data-stu-id="e1490-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="e1490-111">Bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirayarlandığında.</span><span class="sxs-lookup"><span data-stu-id="e1490-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="e1490-112">Bu durumda, çalışma zamanı, işlemdeki her bağlantı için bir `CreateConnection` olayı ve bir [ICorDebugManagedCallback2:: ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) olayı oluşturur ve gönderir.</span><span class="sxs-lookup"><span data-stu-id="e1490-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="e1490-113">Bir ana bilgisayar [BARıNDıRMA API](../../../../docs/framework/unmanaged-api/hosting/index.md)'Sinde [ICLRDebugManager:: BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) öğesini çağırdığında.</span><span class="sxs-lookup"><span data-stu-id="e1490-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1490-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1490-114">Requirements</span></span>  
 <span data-ttu-id="e1490-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1490-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1490-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e1490-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1490-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1490-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1490-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1490-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1490-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1490-119">See also</span></span>

- [<span data-ttu-id="e1490-120">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1490-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="e1490-121">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1490-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
