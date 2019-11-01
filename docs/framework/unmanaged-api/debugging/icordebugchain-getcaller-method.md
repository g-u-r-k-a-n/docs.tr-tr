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
ms.openlocfilehash: 5a07550d44857526e8ab4ded9f1827ef12e3bba4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192133"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="75f94-102">ICorDebugChain::GetCaller Metodu</span><span class="sxs-lookup"><span data-stu-id="75f94-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="75f94-103">Bu zinciri çağıran zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="75f94-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f94-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75f94-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75f94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75f94-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="75f94-106">dışı Çağıran zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75f94-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="75f94-107">Bu zincir daha önce çağrılırsa (Bu zincir veya hata ayıklayıcı çağrı yığınını başlatdıysa olduğu gibi) `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="75f94-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75f94-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75f94-108">Remarks</span></span>  
 <span data-ttu-id="75f94-109">Çağrı iş parçacıkları arasında sıralandıysa, çağırma zinciri farklı bir iş parçacığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="75f94-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75f94-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75f94-110">Requirements</span></span>  
 <span data-ttu-id="75f94-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75f94-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75f94-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="75f94-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75f94-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75f94-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75f94-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75f94-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
