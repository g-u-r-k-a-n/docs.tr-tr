---
title: ICorDebugModuleBreakpoint Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
ms.openlocfilehash: 14f2b6822744070e649cf9a6722272992c0bf1c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709524"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="563a2-102">ICorDebugModuleBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="563a2-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="563a2-103">Belirli modüllere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="563a2-103">Provides access to specific modules.</span></span> <span data-ttu-id="563a2-104">Bu arabirim, ICorDebugBreakpoint arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="563a2-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="563a2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="563a2-105">Methods</span></span>  
  
|<span data-ttu-id="563a2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="563a2-106">Method</span></span>|<span data-ttu-id="563a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="563a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="563a2-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="563a2-108">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="563a2-109">Bu kesme noktasının ayarlandığı modüle başvuran bir ICorDebugModule için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="563a2-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="563a2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="563a2-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="563a2-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="563a2-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="563a2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="563a2-112">Requirements</span></span>  

 <span data-ttu-id="563a2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="563a2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="563a2-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="563a2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="563a2-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="563a2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="563a2-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="563a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563a2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="563a2-117">See also</span></span>

- [<span data-ttu-id="563a2-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="563a2-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
