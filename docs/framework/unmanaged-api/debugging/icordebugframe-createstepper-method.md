---
title: ICorDebugFrame::CreateStepper Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
ms.openlocfilehash: 5dfb64d0c440cbd2c8a8a65b2c18d78f02a7615e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679721"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="7e876-102">ICorDebugFrame::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e876-102">ICorDebugFrame::CreateStepper Method</span></span>

<span data-ttu-id="7e876-103">Hata ayıklayıcının bu ICorDebugFrame 'e göre atlama işlemleri gerçekleştirmesini sağlayan bir Stepper alır.</span><span class="sxs-lookup"><span data-stu-id="7e876-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e876-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e876-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e876-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e876-105">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="7e876-106">dışı Hata ayıklayıcının geçerli çerçeveye göre atlama işlemleri gerçekleştirmesini sağlayan bir ICorDebugStepper nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7e876-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e876-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e876-107">Remarks</span></span>  

 <span data-ttu-id="7e876-108">Çerçeve etkin değilse, Stepper nesnesi genellikle adım tamamlanmadan önce çerçeveye geri dönmesi gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="7e876-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e876-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e876-109">Requirements</span></span>  

 <span data-ttu-id="7e876-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e876-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e876-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7e876-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e876-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7e876-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e876-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e876-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
