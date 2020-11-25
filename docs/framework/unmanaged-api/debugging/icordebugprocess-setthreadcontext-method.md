---
title: ICorDebugProcess::SetThreadContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 5b4052485a6d420eb83578d135ce51f8a918aab0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724526"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="5871b-102">ICorDebugProcess::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5871b-102">ICorDebugProcess::SetThreadContext Method</span></span>

<span data-ttu-id="5871b-103">Bu işlemdeki verilen iş parçacığının bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5871b-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5871b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5871b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5871b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5871b-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="5871b-106">'ndaki Bağlamını ayarlanacak iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5871b-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5871b-107">'ndaki `context` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="5871b-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="5871b-108">'ndaki İş parçacığının bağlamını tanımlayan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="5871b-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="5871b-109">Bağlam, iş parçacığının yürütüldüğü işlemcinin mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5871b-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5871b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5871b-110">Remarks</span></span>  

 <span data-ttu-id="5871b-111">`SetThreadContext`İş parçacığı gerçekten, bağlamı geçici olarak değiştirilen bir "ele geçirilmiş" durumda olabileceğinden, hata ayıklayıcı Win32 işlevi yerine bu yöntemi çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5871b-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="5871b-112">Bu yöntem, yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5871b-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="5871b-113">Yönetilen koddaki iş parçacıkları için [ICorDebugRegisterSet](icordebugregisterset-interface.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5871b-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="5871b-114">Bant dışı (OOB) hata ayıklama olayı sırasında bir iş parçacığının bağlamını hiçbir şekilde değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5871b-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="5871b-115">Geçirilen veriler, geçerli platform için bir bağlam yapısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5871b-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="5871b-116">Yanlış kullanılırsa, bu yöntem çalışma zamanını bozabilir.</span><span class="sxs-lookup"><span data-stu-id="5871b-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5871b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5871b-117">Requirements</span></span>  

 <span data-ttu-id="5871b-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5871b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5871b-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5871b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5871b-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5871b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5871b-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5871b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
