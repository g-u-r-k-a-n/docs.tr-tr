---
title: 'Icordebugınstancefieldsymbol:: GetOffset Yöntemi'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 3886e29a1c2fd44fbe50d1eef722f99da7abdbe5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139010"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="92bd4-102">Icordebugınstancefieldsymbol:: GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92bd4-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="92bd4-103">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="92bd4-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92bd4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92bd4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92bd4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92bd4-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="92bd4-106">Bu örnek alanın üst sınıfında kaydırılacağı bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="92bd4-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92bd4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92bd4-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92bd4-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="92bd4-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92bd4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92bd4-109">Requirements</span></span>  
 <span data-ttu-id="92bd4-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92bd4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92bd4-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92bd4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92bd4-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92bd4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92bd4-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92bd4-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92bd4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92bd4-114">See also</span></span>

- [<span data-ttu-id="92bd4-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92bd4-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="92bd4-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="92bd4-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
