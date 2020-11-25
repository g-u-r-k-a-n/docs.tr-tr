---
title: ICorDebugArrayValue::GetElementType Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
ms.openlocfilehash: 1deadef7517772460adc96cd0dd630d85cb21c9f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698175"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="f8df3-102">ICorDebugArrayValue::GetElementType Metodu</span><span class="sxs-lookup"><span data-stu-id="f8df3-102">ICorDebugArrayValue::GetElementType Method</span></span>

<span data-ttu-id="f8df3-103">Dizideki öğelerin basit türünü gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f8df3-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8df3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f8df3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8df3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f8df3-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="f8df3-106">dışı Türü gösteren CorElementType numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f8df3-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8df3-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8df3-107">Requirements</span></span>  

 <span data-ttu-id="f8df3-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8df3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8df3-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f8df3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8df3-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f8df3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8df3-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8df3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
