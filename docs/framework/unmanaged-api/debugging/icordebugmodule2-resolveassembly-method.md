---
title: ICorDebugModule2::ResolveAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: e64e39d10d20f63430ffe9d2c4df8643e286a677
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210046"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="37b33-102">ICorDebugModule2::ResolveAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37b33-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="37b33-103">Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.</span><span class="sxs-lookup"><span data-stu-id="37b33-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="37b33-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37b33-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="37b33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37b33-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="37b33-106">'ndaki `mdToken`Derlemeye başvuran bir değer.</span><span class="sxs-lookup"><span data-stu-id="37b33-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="37b33-107">dışı Derlemeyi temsil eden ICorDebugAssembly nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="37b33-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="37b33-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37b33-108">Remarks</span></span>

<span data-ttu-id="37b33-109">, Çağrıldığında derleme zaten yüklü değilse `ResolveAssembly` , CORDBG_E_CANNOT_RESOLVE_ASSEMBLY HRESULT değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="37b33-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="37b33-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37b33-110">Requirements</span></span>

<span data-ttu-id="37b33-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37b33-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="37b33-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="37b33-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="37b33-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="37b33-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="37b33-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37b33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
