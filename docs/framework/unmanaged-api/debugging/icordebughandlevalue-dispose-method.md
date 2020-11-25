---
title: ICorDebugHandleValue::Dispose Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
ms.openlocfilehash: dc24afd8f78a900ea52539bf9dcb522287223c4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705637"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="74ece-102">ICorDebugHandleValue::Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74ece-102">ICorDebugHandleValue::Dispose Method</span></span>

<span data-ttu-id="74ece-103">Arabirim işaretçisini açıkça serbest bırakmadan, bu ıcorıınfo Ghandlivalue nesnesi tarafından başvurulan tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="74ece-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ece-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="74ece-104">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="74ece-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74ece-105">Requirements</span></span>  

 <span data-ttu-id="74ece-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74ece-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ece-107">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74ece-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74ece-108">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74ece-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74ece-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74ece-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
