---
title: ICorDebugModule2::SetJITCompilerFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: 11ff430c426c93f1c2a5c0582495e089a33995fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709810"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="f7814-102">ICorDebugModule2::SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7814-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>

<span data-ttu-id="f7814-103">Bu ICorDebugModule2 'ın tam zamanında (JıT) derlemesini denetleyen bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7814-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7814-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f7814-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7814-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7814-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="f7814-106">'ndaki [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="f7814-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7814-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7814-107">Remarks</span></span>  

 <span data-ttu-id="f7814-108">`dwFlags`Değer geçersizse, `SetJITCompilerFlags` Yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f7814-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="f7814-109">`SetJITCompilerFlags`Yöntemi yalnızca bu modül Için [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) geri çağırması içinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7814-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="f7814-110">Geri çağırma işlemi geri alındıktan sonra çağrı denemeleri `ICorDebugManagedCallback::LoadModule` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f7814-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="f7814-111">Düzenle ve devam et, 64-bit veya Win9x platformlarında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f7814-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="f7814-112">Bu nedenle, `SetJITCompilerFlags` yöntemi ' de ayarlanmış CORDEBUG_JIT_ENABLE_ENC bayrağı ile bu iki platformundan birine çağırırsanız `dwFlags` , `SetJITCompilerFlags` [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md)gibi, düzenleme ve devam etme yöntemine özgü Yöntem ve tüm yöntemler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f7814-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7814-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7814-113">Requirements</span></span>  

 <span data-ttu-id="f7814-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7814-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7814-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7814-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7814-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f7814-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7814-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7814-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
