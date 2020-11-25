---
title: ICorDebugChain::GetCallee Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: a28da34cd3080826f346b8957aa6ba38258b924f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730129"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="849b0-102">ICorDebugChain::GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="849b0-102">ICorDebugChain::GetCallee Method</span></span>

<span data-ttu-id="849b0-103">Bu zincir tarafından çağrılan zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="849b0-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="849b0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="849b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="849b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="849b0-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="849b0-106">dışı Çağrılan zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="849b0-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="849b0-107">Bu zincir Şu anda yürütüliyorsa (yani, bu zincir, çağrılan bir zincirin dönmesi beklenmez), `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="849b0-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="849b0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="849b0-108">Remarks</span></span>  

 <span data-ttu-id="849b0-109">Bu zincir, yürütmeyi devam etmeden önce çağrılan zincirin döndürülmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="849b0-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="849b0-110">Çağrılan zincir, çapraz iş parçacığı sıralanmış çağrılar söz konusu olduğunda başka bir iş parçacığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="849b0-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="849b0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="849b0-111">Requirements</span></span>  

 <span data-ttu-id="849b0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="849b0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="849b0-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="849b0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="849b0-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="849b0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="849b0-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="849b0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
