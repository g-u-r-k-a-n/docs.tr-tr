---
title: ICorDebugModuleEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: a4bdac42c584d5d34b072354de65ed20c6a80609
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709498"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="0d30c-102">ICorDebugModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d30c-102">ICorDebugModuleEnum::Next Method</span></span>

<span data-ttu-id="0d30c-103">`celt`Geçerli konumdan başlayarak, numaralandırmadan belirtilen "ICorDebugModule" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0d30c-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d30c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0d30c-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d30c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d30c-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="0d30c-106">'ndaki `ICorDebugModule` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="0d30c-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="0d30c-107">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugModule` .</span><span class="sxs-lookup"><span data-stu-id="0d30c-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0d30c-108">dışı `ICorDebugModule` Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d30c-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="0d30c-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="0d30c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d30c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d30c-110">Requirements</span></span>  

 <span data-ttu-id="0d30c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d30c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d30c-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0d30c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d30c-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0d30c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d30c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d30c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d30c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d30c-115">See also</span></span>
