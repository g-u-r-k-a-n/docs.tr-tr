---
title: ICorDebugChain::GetCaller Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: 0f616b3bae48a972c0fc8935c35add7d844a7364
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730116"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="a83b1-102">ICorDebugChain::GetCaller Metodu</span><span class="sxs-lookup"><span data-stu-id="a83b1-102">ICorDebugChain::GetCaller Method</span></span>

<span data-ttu-id="a83b1-103">Bu zinciri çağıran zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="a83b1-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a83b1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a83b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a83b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a83b1-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="a83b1-106">dışı Çağıran zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a83b1-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="a83b1-107">Bu zincir daha önce çağrılırsa (Bu zincir veya hata ayıklayıcı çağrı yığınını başlatdıysa olduğu gibi), `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="a83b1-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a83b1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a83b1-108">Remarks</span></span>  

 <span data-ttu-id="a83b1-109">Çağrı iş parçacıkları arasında sıralandıysa, çağırma zinciri farklı bir iş parçacığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="a83b1-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a83b1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a83b1-110">Requirements</span></span>  

 <span data-ttu-id="a83b1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a83b1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a83b1-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a83b1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a83b1-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a83b1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a83b1-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a83b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
