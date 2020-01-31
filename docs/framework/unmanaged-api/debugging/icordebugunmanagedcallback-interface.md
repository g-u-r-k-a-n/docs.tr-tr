---
title: ICorDebugUnmanagedCallback Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
ms.openlocfilehash: fdd2fee11e9353c3aa3faee2b137597e4ba47801
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791176"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="38a3b-102">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38a3b-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="38a3b-103">Ortak dil çalışma zamanı (CLR) ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="38a3b-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38a3b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38a3b-104">Methods</span></span>  
  
|<span data-ttu-id="38a3b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="38a3b-105">Method</span></span>|<span data-ttu-id="38a3b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38a3b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38a3b-107">DebugEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38a3b-107">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="38a3b-108">Hata ayıklayıcıyı yerel bir olayın harekete geçirildiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="38a3b-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38a3b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38a3b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38a3b-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="38a3b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38a3b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38a3b-111">Requirements</span></span>  
 <span data-ttu-id="38a3b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38a3b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38a3b-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38a3b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38a3b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="38a3b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38a3b-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38a3b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a3b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38a3b-116">See also</span></span>

- [<span data-ttu-id="38a3b-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="38a3b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
