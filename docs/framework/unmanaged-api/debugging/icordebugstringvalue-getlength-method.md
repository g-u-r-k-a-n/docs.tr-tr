---
title: ICorDebugStringValue::GetLength Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
ms.openlocfilehash: 74a4b42be09c577cc80f1a73e077694e5a4a8d5f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697122"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="1f742-102">ICorDebugStringValue::GetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f742-102">ICorDebugStringValue::GetLength Method</span></span>

<span data-ttu-id="1f742-103">Bu ICorDebugStringValue tarafından başvurulan dizedeki karakter sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1f742-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f742-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1f742-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f742-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f742-105">Parameters</span></span>  

 `pcchString`  
 <span data-ttu-id="1f742-106">dışı Bu nesnenin başvurduğu dizenin uzunluğunu belirten bir değer işaretçisi `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="1f742-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f742-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f742-107">Requirements</span></span>  

 <span data-ttu-id="1f742-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f742-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f742-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1f742-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f742-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1f742-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f742-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f742-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
