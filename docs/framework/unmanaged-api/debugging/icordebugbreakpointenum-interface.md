---
title: ICorDebugBreakpointEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 97e06a2f20dcc2bb3815b98ba29ff230e37ff29d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730168"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="78ac5-102">ICorDebugBreakpointEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78ac5-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="78ac5-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugBreakpoint dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="78ac5-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78ac5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="78ac5-104">Methods</span></span>  
  
|<span data-ttu-id="78ac5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="78ac5-105">Method</span></span>|<span data-ttu-id="78ac5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78ac5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78ac5-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78ac5-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="78ac5-108">`ICorDebugBreakpoint`Geçerli konumdan başlayarak Numaralandırmadaki belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="78ac5-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78ac5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78ac5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78ac5-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="78ac5-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78ac5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78ac5-111">Requirements</span></span>  

 <span data-ttu-id="78ac5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78ac5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78ac5-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="78ac5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78ac5-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="78ac5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78ac5-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78ac5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ac5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78ac5-116">See also</span></span>

- [<span data-ttu-id="78ac5-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="78ac5-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
