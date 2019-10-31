---
title: ICorDebugModule Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 971d6a6a2157c48dcb9105e9f523b1f077098479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129482"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="f4cff-102">ICorDebugModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4cff-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="f4cff-103">Yürütülebilir bir dosya veya dinamik bağlantı kitaplığı (DLL) olan bir ortak dil çalışma zamanı (CLR) modülünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f4cff-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4cff-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f4cff-104">Methods</span></span>  
  
|<span data-ttu-id="f4cff-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f4cff-105">Method</span></span>|<span data-ttu-id="f4cff-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4cff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4cff-107">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="f4cff-108">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="f4cff-108">Not implemented.</span></span>|  
|[<span data-ttu-id="f4cff-109">EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="f4cff-110">Bu modül için [ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="f4cff-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="f4cff-111">EnableJITDebugging Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="f4cff-112">Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="f4cff-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="f4cff-113">GetAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="f4cff-114">Bu modülün kapsayan derlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="f4cff-115">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="f4cff-116">Modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="f4cff-117">GetClassFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="f4cff-118">Meta verilerden ICorDebugClass alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="f4cff-119">GetEditAndContinueSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="f4cff-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="f4cff-120">Deprecated.</span></span>|  
|[<span data-ttu-id="f4cff-121">GetFunctionFromRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="f4cff-122">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="f4cff-122">Not implemented.</span></span>|  
|[<span data-ttu-id="f4cff-123">GetFunctionFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="f4cff-124">Meta veri belirteci tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="f4cff-125">GetGlobalVariableValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="f4cff-126">Belirtilen genel değişken için bir değer nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="f4cff-127">GetMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="f4cff-128">Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="f4cff-129">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="f4cff-130">Modülün dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="f4cff-131">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="f4cff-132">Bu modül için kapsayan işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="f4cff-133">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="f4cff-134">Modülün boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="f4cff-135">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="f4cff-136">Bu modül için tablo girişi belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="f4cff-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="f4cff-137">IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="f4cff-138">Modülün Dinamik olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4cff-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="f4cff-139">IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4cff-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="f4cff-140">Bu modülün yalnızca bellekte bulunup bulunmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4cff-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4cff-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4cff-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4cff-142">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f4cff-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4cff-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4cff-143">Requirements</span></span>  
 <span data-ttu-id="f4cff-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4cff-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4cff-145">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f4cff-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4cff-146">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f4cff-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4cff-147">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4cff-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4cff-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4cff-148">See also</span></span>

- [<span data-ttu-id="f4cff-149">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4cff-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="f4cff-150">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f4cff-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
