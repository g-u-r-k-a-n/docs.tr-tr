---
title: ICorDebugThread2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: fd4ad536d7d3df2b8f91f206459122cf083c8b9c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691142"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="39086-102">ICorDebugThread2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39086-102">ICorDebugThread2 Interface</span></span>

<span data-ttu-id="39086-103">ICorDebugThread arabirimine bir mantıksal uzantı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="39086-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39086-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="39086-104">Methods</span></span>  
  
|<span data-ttu-id="39086-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="39086-105">Method</span></span>|<span data-ttu-id="39086-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39086-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39086-107">GetActiveFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39086-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="39086-108">Bir iş parçacığının çerçevelerinden etkin işlevlerle ilgili verileri içeren COR_ACTIVE_FUNCTION örneklerinin bir dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="39086-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="39086-109">GetConnectionID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39086-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="39086-110">Bunun için bir bağlantı tanımlayıcısı alır `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="39086-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="39086-111">GetTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39086-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="39086-112">Bunun için bir görev tanımlayıcısı alır `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="39086-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="39086-113">GetVolatileOSThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39086-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="39086-114">Bunun için işletim sistemi iş parçacığı tanımlayıcısını alır `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="39086-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="39086-115">InterceptCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39086-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="39086-116">Bir hata ayıklayıcının bir iş parçacığında geçerli özel durumu ele almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="39086-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39086-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39086-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39086-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="39086-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39086-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39086-119">Requirements</span></span>  

 <span data-ttu-id="39086-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39086-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39086-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="39086-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39086-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="39086-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39086-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39086-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39086-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39086-124">See also</span></span>

- [<span data-ttu-id="39086-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="39086-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
