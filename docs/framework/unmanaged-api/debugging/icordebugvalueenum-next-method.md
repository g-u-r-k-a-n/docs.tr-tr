---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugValueEnum:: Next yöntemi'
title: ICorDebugValueEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: 9a02c769f69651227669eb4b3f8c5ce41b670a73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690112"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="c3881-103">ICorDebugValueEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3881-103">ICorDebugValueEnum::Next Method</span></span>

<span data-ttu-id="c3881-104">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen "ICorDebugValue" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c3881-104">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3881-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3881-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3881-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3881-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="c3881-107">'ndaki `ICorDebugValue` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="c3881-107">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="c3881-108">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="c3881-108">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c3881-109">dışı `ICorDebugValue` Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3881-109">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="c3881-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="c3881-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3881-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3881-111">Requirements</span></span>  

 <span data-ttu-id="c3881-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3881-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3881-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3881-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3881-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c3881-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3881-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3881-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3881-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3881-116">See also</span></span>
