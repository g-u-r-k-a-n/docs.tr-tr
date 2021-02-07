---
description: ': ICorDebugExceptionObjectCallStackEnum arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugExceptionObjectCallStackEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: c72f4299bf3ebc5de2d2ed196801d93ff5fe4356
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693362"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="ae195-103">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae195-103">ICorDebugExceptionObjectCallStackEnum Interface</span></span>

<span data-ttu-id="ae195-104">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae195-104">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="ae195-105">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="ae195-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae195-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ae195-106">Methods</span></span>  
  
|<span data-ttu-id="ae195-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ae195-107">Method</span></span>|<span data-ttu-id="ae195-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae195-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae195-109">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="ae195-109">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="ae195-110">Bir özel durum nesnesinin çağrı yığını hakkında bilgi içeren, belirtilen sayıda [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="ae195-110">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae195-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae195-111">Remarks</span></span>  

 <span data-ttu-id="ae195-112">`ICorDebugExceptionObjectCallStackEnum`Arabirim ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="ae195-112">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="ae195-113">`ICorDebugExceptionObjectCallStackEnum` [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) yöntemi çağırarak bir örnek [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesneleriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ae195-113">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="ae195-114">Koleksiyondaki çağrı yığını öğeleri [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md) yöntemi çağırarak Numaralandırılabilir</span><span class="sxs-lookup"><span data-stu-id="ae195-114">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae195-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae195-115">Requirements</span></span>  

 <span data-ttu-id="ae195-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae195-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae195-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae195-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae195-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae195-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae195-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae195-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae195-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae195-120">See also</span></span>

- [<span data-ttu-id="ae195-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ae195-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ae195-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ae195-122">Debugging</span></span>](index.md)
