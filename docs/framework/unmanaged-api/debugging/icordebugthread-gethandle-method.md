---
title: ICorDebugThread::GetHandle Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 33219d9a67379244e23da49c13617a4c4a2fa66d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133461"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="46b35-102">ICorDebugThread::GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46b35-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="46b35-103">Bu ICorDebugThread 'in etkin bölümü için geçerli tanıtıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="46b35-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46b35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46b35-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46b35-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46b35-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="46b35-106">dışı Bu iş parçacığının etkin bölümünün tanıtıcısı olan bir HTHREAD için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="46b35-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46b35-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46b35-107">Remarks</span></span>  
 <span data-ttu-id="46b35-108">Tanıtıcı, işlem yürütüldüğü gibi değişebilir ve iş parçacığının farklı parçaları için farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="46b35-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="46b35-109">Bu tanıtıcının sahibi hata ayıklama API 'sidir.</span><span class="sxs-lookup"><span data-stu-id="46b35-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="46b35-110">Hata ayıklayıcı, kullanmadan önce onu çoğaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46b35-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46b35-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46b35-111">Requirements</span></span>  
 <span data-ttu-id="46b35-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46b35-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46b35-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="46b35-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46b35-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="46b35-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46b35-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46b35-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
