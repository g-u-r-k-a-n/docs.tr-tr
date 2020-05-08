---
title: ICorDebugEval::GetResult Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 2d065d956319076d3b92eddafd4a2c25ffbfbac1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976271"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="003e4-102">ICorDebugEval::GetResult Yöntemi</span><span class="sxs-lookup"><span data-stu-id="003e4-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="003e4-103">Bu değerlendirmenin sonuçlarını alır.</span><span class="sxs-lookup"><span data-stu-id="003e4-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="003e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="003e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="003e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="003e4-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="003e4-106">dışı Değerlendirme normal şekilde tamamlanırsa, bu değerlendirmenin sonuçlarını temsil eden bir ICorDebugValue nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="003e4-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="003e4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="003e4-107">Remarks</span></span>  
 <span data-ttu-id="003e4-108">`GetResult` Yöntem yalnızca değerlendirme tamamlandıktan sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="003e4-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="003e4-109">Değerlendirme normal şekilde tamamlanırsa, `ppResult` sonuçları belirtir.</span><span class="sxs-lookup"><span data-stu-id="003e4-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="003e4-110">Bir özel durumla sonlandığında sonuç, oluşturulan özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="003e4-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="003e4-111">Değerlendirme yeni bir nesne için ise, sonuç yeni nesneye başvurudur.</span><span class="sxs-lookup"><span data-stu-id="003e4-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="003e4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="003e4-112">Requirements</span></span>  
 <span data-ttu-id="003e4-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="003e4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="003e4-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="003e4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="003e4-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="003e4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="003e4-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="003e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
