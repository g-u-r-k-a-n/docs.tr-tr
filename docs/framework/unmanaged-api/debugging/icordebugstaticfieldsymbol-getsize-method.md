---
title: 'ICorDebugStaticFieldSymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: 0fa9c519a40624dd8c5471231263d2430738af87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131776"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="df3a3-102">ICorDebugStaticFieldSymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="df3a3-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="df3a3-103">Statik alanın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="df3a3-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df3a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df3a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df3a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df3a3-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="df3a3-106">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="df3a3-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df3a3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df3a3-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df3a3-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df3a3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df3a3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df3a3-109">Requirements</span></span>  
 <span data-ttu-id="df3a3-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df3a3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df3a3-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df3a3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df3a3-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="df3a3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df3a3-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df3a3-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df3a3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df3a3-114">See also</span></span>

- [<span data-ttu-id="df3a3-115">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df3a3-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="df3a3-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="df3a3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
