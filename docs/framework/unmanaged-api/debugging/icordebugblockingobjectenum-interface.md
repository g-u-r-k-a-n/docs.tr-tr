---
title: ICorDebugBlockingObjectEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
ms.openlocfilehash: 8be4332da77c3fbf4229a3fbeb9ba835a7a13eee
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894801"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="5a57f-102">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a57f-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="5a57f-103">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesi için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a57f-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="5a57f-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="5a57f-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a57f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5a57f-105">Methods</span></span>  
  
|<span data-ttu-id="5a57f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5a57f-106">Method</span></span>|<span data-ttu-id="5a57f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a57f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a57f-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a57f-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="5a57f-109">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesini sıralar.</span><span class="sxs-lookup"><span data-stu-id="5a57f-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a57f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a57f-110">Remarks</span></span>  
 <span data-ttu-id="5a57f-111">Her `CorDebugBlockingObject` yapı, bir iş parçacığını engelleyen bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a57f-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a57f-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="5a57f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a57f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a57f-113">Requirements</span></span>  
 <span data-ttu-id="5a57f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a57f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a57f-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5a57f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a57f-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5a57f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a57f-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a57f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a57f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a57f-118">See also</span></span>

- [<span data-ttu-id="5a57f-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5a57f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5a57f-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5a57f-120">Debugging</span></span>](index.md)
