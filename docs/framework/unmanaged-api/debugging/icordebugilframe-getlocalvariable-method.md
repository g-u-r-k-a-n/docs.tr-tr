---
title: ICorDebugILFrame::GetLocalVariable Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: 85f06b49aab1f1d1745bd7e359ed311c2ba1e44d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130976"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="94aa6-102">ICorDebugILFrame::GetLocalVariable Metodu</span><span class="sxs-lookup"><span data-stu-id="94aa6-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="94aa6-103">Bu Microsoft ara dili (MSIL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="94aa6-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94aa6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94aa6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94aa6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94aa6-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="94aa6-106">'ndaki Bu MSIL yığın çerçevesindeki yerel değişkenin dizini.</span><span class="sxs-lookup"><span data-stu-id="94aa6-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="94aa6-107">dışı Alınan değeri temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94aa6-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94aa6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94aa6-108">Remarks</span></span>  
 <span data-ttu-id="94aa6-109">`GetLocalVariable` yöntemi bir MSIL yığın çerçevesinde veya tam zamanında (JıT) derlenmiş çerçevede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94aa6-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94aa6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94aa6-110">Requirements</span></span>  
 <span data-ttu-id="94aa6-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94aa6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94aa6-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="94aa6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94aa6-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="94aa6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94aa6-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94aa6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
