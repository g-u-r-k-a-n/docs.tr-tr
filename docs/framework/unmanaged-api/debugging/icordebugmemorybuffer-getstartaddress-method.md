---
title: 'ICorDebugMemoryBuffer:: GetStartAddress yöntemi'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: f2b09c847a6bf577b78c8155f85f07b93877fbe9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793163"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="e021f-102">ICorDebugMemoryBuffer:: GetStartAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="e021f-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="e021f-103">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="e021f-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e021f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e021f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e021f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e021f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e021f-106">dışı Bellek arabelleğinin başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e021f-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e021f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e021f-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e021f-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e021f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e021f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e021f-109">Requirements</span></span>  
 <span data-ttu-id="e021f-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e021f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e021f-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e021f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e021f-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e021f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e021f-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e021f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e021f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e021f-114">See also</span></span>

- [<span data-ttu-id="e021f-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e021f-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="e021f-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e021f-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
