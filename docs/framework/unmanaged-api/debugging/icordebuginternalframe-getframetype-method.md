---
title: ICorDebugInternalFrame::GetFrameType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: b7a33fd6e2178e0e9188b81f516b231702fb6460
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122723"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="ed0a3-102">ICorDebugInternalFrame::GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed0a3-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="ed0a3-103">Bu iç çerçevenin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="ed0a3-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed0a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed0a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed0a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed0a3-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="ed0a3-106">dışı Bu `ICorDebugInternalFrame` nesnesi tarafından temsil edilen iç çerçeve türünü gösteren CorDebugInternalFrameType numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ed0a3-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed0a3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed0a3-107">Remarks</span></span>  
 <span data-ttu-id="ed0a3-108">İç çerçeve türü hiçbir şekilde STUBFRAME_NONE olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="ed0a3-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="ed0a3-109">Hata ayıklayıcılar, tanınmayan iç çerçeve türlerini düzgün şekilde yoksaymalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed0a3-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed0a3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed0a3-110">Requirements</span></span>  
 <span data-ttu-id="ed0a3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed0a3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed0a3-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed0a3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed0a3-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ed0a3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed0a3-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed0a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
