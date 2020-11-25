---
title: ICorDebugExceptionDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: c280852d421742cf9e8c2f8dcaa9c0f588f8537b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697395"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="08d2d-102">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08d2d-102">ICorDebugExceptionDebugEvent Interface</span></span>

<span data-ttu-id="08d2d-103">Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="08d2d-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08d2d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="08d2d-104">Methods</span></span>  
  
|<span data-ttu-id="08d2d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="08d2d-105">Method</span></span>|<span data-ttu-id="08d2d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08d2d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08d2d-107">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08d2d-107">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="08d2d-108">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="08d2d-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="08d2d-109">GetNativeIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08d2d-109">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="08d2d-110">Bu özel durum ayıklama olayı için yerel arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="08d2d-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="08d2d-111">GetStackPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08d2d-111">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="08d2d-112">Bu özel durum ayıklama olayının yığın işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="08d2d-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08d2d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08d2d-113">Remarks</span></span>  

 <span data-ttu-id="08d2d-114">`ICorDebugExceptionDebugEvent`Arabirim aşağıdaki olay türleri tarafından uygulanır:</span><span class="sxs-lookup"><span data-stu-id="08d2d-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="08d2d-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="08d2d-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="08d2d-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="08d2d-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="08d2d-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="08d2d-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="08d2d-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="08d2d-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="08d2d-119">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08d2d-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="08d2d-120">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="08d2d-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d2d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08d2d-121">Requirements</span></span>  

 <span data-ttu-id="08d2d-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08d2d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08d2d-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08d2d-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08d2d-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="08d2d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08d2d-125">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d2d-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d2d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08d2d-126">See also</span></span>

- [<span data-ttu-id="08d2d-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08d2d-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="08d2d-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="08d2d-128">Debugging</span></span>](index.md)
