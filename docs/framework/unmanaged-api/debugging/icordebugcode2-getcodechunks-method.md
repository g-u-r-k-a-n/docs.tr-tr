---
title: ICorDebugCode2::GetCodeChunks Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
ms.openlocfilehash: e419ebb6ffd404368baf32e591e08c4a70645127
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121115"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="43388-102">ICorDebugCode2::GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43388-102">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="43388-103">Bu kod nesnesinin oluştuğu kod öbeklerini alır.</span><span class="sxs-lookup"><span data-stu-id="43388-103">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="43388-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43388-104">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="43388-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43388-105">Parameters</span></span>

`cbufSize`  
<span data-ttu-id="43388-106">'ndaki `chunks` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="43388-106">[in] Size of the `chunks` array.</span></span>

`pcnumChunks`  
<span data-ttu-id="43388-107">dışı `chunks` dizisinde döndürülen öbeklerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="43388-107">[out] The number of chunks returned in the `chunks` array.</span></span>

`chunks`  
<span data-ttu-id="43388-108">dışı Her biri tek bir kod öbeğini temsil eden bir "CodeChunkInfo" yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="43388-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="43388-109">`cbufSize` değeri 0 ise, bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="43388-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="43388-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43388-110">Remarks</span></span>

<span data-ttu-id="43388-111">Kod öbekleri hiçbir şekilde çakışacaktır ve [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md)tarafından bitiştirildiği sırayı takip eder.</span><span class="sxs-lookup"><span data-stu-id="43388-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="43388-112">.NET Framework sürüm 2,0 ' deki bir Microsoft ara dili (MSIL) kod nesnesi, tek bir kod öbeğini kapsar.</span><span class="sxs-lookup"><span data-stu-id="43388-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="43388-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43388-113">Requirements</span></span>

<span data-ttu-id="43388-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43388-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="43388-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="43388-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="43388-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="43388-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="43388-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43388-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
