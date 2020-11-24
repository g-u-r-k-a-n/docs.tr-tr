---
title: ICorDebugThread::SetDebugState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
ms.openlocfilehash: e28d37e4477862ff2ebeeb05ea5f5386e157cd83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678749"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="7f005-102">ICorDebugThread::SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f005-102">ICorDebugThread::SetDebugState Method</span></span>

<span data-ttu-id="7f005-103">Bu ICorDebugThread 'in hata ayıklama durumunu tanımlayan bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7f005-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f005-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7f005-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f005-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f005-105">Parameters</span></span>  

 `state`  
 <span data-ttu-id="7f005-106">'ndaki Bu iş parçacığının hata ayıklama durumunu belirten, CorDebugThreadState numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="7f005-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f005-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f005-107">Remarks</span></span>  

 <span data-ttu-id="7f005-108">`SetDebugState` iş parçacığının geçerli hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7f005-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="7f005-109">("Geçerli hata ayıklama durumu" işlemi devam etseydi, gerçek geçerli durum değil, hata ayıklama durumunu temsil eder.) Bunun için normal değer THREAD_RUN.</span><span class="sxs-lookup"><span data-stu-id="7f005-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="7f005-110">Yalnızca hata ayıklayıcı bir iş parçacığının hata ayıklama durumunu etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="7f005-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="7f005-111">Hata ayıklama durumları son boyunca devam eder, bu nedenle bir iş parçacığı THREAD_SUSPENDed birden çok kez devam etmek istiyorsanız, onu bir kez ayarlayabilir ve bundan sonra endişelenmenize gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="7f005-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="7f005-112">İş parçacıklarını askıya almak ve işlemi sürdürmek kilitlenmeye neden olabilir, ancak bu genellikle düşüktür.</span><span class="sxs-lookup"><span data-stu-id="7f005-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="7f005-113">Bu, iş parçacıklarının ve işlemlerin gerçek bir kalitesidir ve tasarıma göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="7f005-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="7f005-114">Hata ayıklayıcı kilitlenme kesmek için zaman uyumsuz olarak kesintiye uğratır ve iş parçacıklarını sürdürür.</span><span class="sxs-lookup"><span data-stu-id="7f005-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="7f005-115">İş parçacığının kullanıcı durumu USER_UNSAFE_POINT içeriyorsa, iş parçacığı çöp toplamayı (GC) engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7f005-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="7f005-116">Bu, askıya alınan iş parçacığının kilitlenmeye neden olma olasılığını çok daha yüksek olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7f005-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="7f005-117">Bu, zaten kuyruğa alınmış olan hata ayıklama olaylarını etkilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="7f005-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="7f005-118">Bu nedenle, iş parçacıklarını askıya almadan veya devam ettirmeden önce hata ayıklayıcı tüm olay kuyruğunu ( [ICorDebugController:: HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)çağırarak) boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f005-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="7f005-119">Diğer bir deyişle, zaten askıya alınmış olduğunu düşündüğü bir iş parçacığında olayları alabilir.</span><span class="sxs-lookup"><span data-stu-id="7f005-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f005-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f005-120">Requirements</span></span>  

 <span data-ttu-id="7f005-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f005-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f005-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7f005-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f005-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7f005-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f005-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f005-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
