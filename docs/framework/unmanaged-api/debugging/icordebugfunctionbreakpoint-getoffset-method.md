---
title: ICorDebugFunctionBreakpoint::GetOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
ms.openlocfilehash: 8b9e483e24068656ddda0a3ecfee5934a2df962d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695900"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="e8e3b-102">ICorDebugFunctionBreakpoint::GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8e3b-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>

<span data-ttu-id="e8e3b-103">İşlev içindeki kesme noktasının konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="e8e3b-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8e3b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e8e3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8e3b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8e3b-105">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="e8e3b-106">dışı Kesme noktasının uzaklığa yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e8e3b-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8e3b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8e3b-107">Requirements</span></span>  

 <span data-ttu-id="e8e3b-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8e3b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8e3b-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e8e3b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8e3b-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e8e3b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8e3b-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8e3b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
