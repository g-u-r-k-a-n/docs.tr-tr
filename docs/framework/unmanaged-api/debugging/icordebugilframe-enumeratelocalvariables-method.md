---
title: ICorDebugILFrame::EnumerateLocalVariables Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: 968ceec53aade3d04c500c8247d397ffb71382c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703214"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="0ccdc-102">ICorDebugILFrame::EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ccdc-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>

<span data-ttu-id="0ccdc-103">Bu çerçevedeki yerel değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="0ccdc-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ccdc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0ccdc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ccdc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ccdc-105">Parameters</span></span>  

 `ppValueEnum`  
 <span data-ttu-id="0ccdc-106">dışı Bu çerçevedeki yerel değişkenlerin numaralandırıcısı olan ICorDebugValueEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0ccdc-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ccdc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ccdc-107">Remarks</span></span>  

 <span data-ttu-id="0ccdc-108">`EnumerateLocalVariables` Bu ICorDebugILFrame nesnesi tarafından temsil edilen çağrı çerçevesinde kullanılabilen yerel değişkenleri listeleyerek bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="0ccdc-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="0ccdc-109">Liste, çalışan işlevdeki tüm yerel değişkenleri içermeyebilir, çünkü bazıları etkin olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0ccdc-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ccdc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ccdc-110">Requirements</span></span>  

 <span data-ttu-id="0ccdc-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ccdc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ccdc-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0ccdc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ccdc-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0ccdc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ccdc-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ccdc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
