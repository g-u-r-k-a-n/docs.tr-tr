---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugAssemblyEnum:: Next yöntemi'
title: ICorDebugAssemblyEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
ms.openlocfilehash: feb77f22ec59fcc0e1b3f5590b7aee4efba13d01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772230"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="833d6-103">ICorDebugAssemblyEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="833d6-103">ICorDebugAssemblyEnum::Next Method</span></span>

<span data-ttu-id="833d6-104">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen sayıda derlemeyi alır.</span><span class="sxs-lookup"><span data-stu-id="833d6-104">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="833d6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="833d6-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="833d6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="833d6-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="833d6-107">'ndaki Alınacak derleme sayısı.</span><span class="sxs-lookup"><span data-stu-id="833d6-107">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="833d6-108">dışı Her biri bir derlemeyi temsil eden ICorDebugAssembly nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="833d6-108">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="833d6-109">dışı Aslında döndürülen derleme sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="833d6-109">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="833d6-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="833d6-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="833d6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="833d6-111">Requirements</span></span>  

 <span data-ttu-id="833d6-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="833d6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="833d6-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="833d6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="833d6-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="833d6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="833d6-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="833d6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
