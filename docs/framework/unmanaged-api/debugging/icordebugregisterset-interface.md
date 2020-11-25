---
title: ICorDebugRegisterSet Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: 940810288b72be0d4dfc5366176663c22c369ebb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712385"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="d5937-102">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5937-102">ICorDebugRegisterSet Interface</span></span>

<span data-ttu-id="d5937-103">Şu anda kod yürüten bilgisayarda kullanılabilir olan yazmaçların kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d5937-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5937-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d5937-104">Methods</span></span>  
  
|<span data-ttu-id="d5937-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d5937-105">Method</span></span>|<span data-ttu-id="d5937-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5937-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5937-107">GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="d5937-107">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="d5937-108">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="d5937-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="d5937-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5937-109">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="d5937-110">Bu, içindeki yazmaçların Şu anda kullanılabilir olduğunu gösteren bir bit maskesi alır `ICorDebugRegisterSet` .</span><span class="sxs-lookup"><span data-stu-id="d5937-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="d5937-111">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5937-111">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="d5937-112">Geçerli iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="d5937-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="d5937-113">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5937-113">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="d5937-114">.NET Framework sürüm 2,0 için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="d5937-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="d5937-115">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5937-115">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="d5937-116">.NET Framework 2,0 için uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="d5937-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5937-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5937-117">Remarks</span></span>  

 <span data-ttu-id="d5937-118">`ICorDebugRegisterSet`Arabirim yalnızca 32 bitlik kayıtları destekler.</span><span class="sxs-lookup"><span data-stu-id="d5937-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="d5937-119">Daha fazla kayıt gerektiren IA-64 gibi platformlarda [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) arabirimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5937-119">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5937-120">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="d5937-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5937-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5937-121">Requirements</span></span>  

 <span data-ttu-id="d5937-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5937-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5937-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5937-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5937-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d5937-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5937-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5937-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5937-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5937-126">See also</span></span>

- [<span data-ttu-id="d5937-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d5937-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d5937-128">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5937-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
