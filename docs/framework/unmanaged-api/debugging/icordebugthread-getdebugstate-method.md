---
title: ICorDebugThread::GetDebugState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
ms.openlocfilehash: 746fef3629e6573d7dfe47d5a3fcf9ee9a1d4250
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728049"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="dca19-102">ICorDebugThread::GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dca19-102">ICorDebugThread::GetDebugState Method</span></span>

<span data-ttu-id="dca19-103">Bu ICorDebugThread nesnesinin geçerli hata ayıklama durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="dca19-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dca19-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dca19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dca19-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dca19-105">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="dca19-106">dışı Bu iş parçacığının geçerli hata ayıklama durumunu açıklayan, CorDebugThreadState numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dca19-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dca19-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dca19-107">Remarks</span></span>  

 <span data-ttu-id="dca19-108">İşlem şu anda durdurulmuşsa, `pState` işlem devam etseydi, bu iş parçacığının gerçek geçerli durumu değil, bu iş parçacığı için mevcut olacak hata ayıklama durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dca19-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dca19-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dca19-109">Requirements</span></span>  

 <span data-ttu-id="dca19-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dca19-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dca19-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dca19-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dca19-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dca19-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dca19-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dca19-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
