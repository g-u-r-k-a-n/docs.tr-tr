---
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 25ffa55eeeb82d6feaf5696ea96dae81774e3d70
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121908"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="0b70e-102">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b70e-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="0b70e-103">Bir değişken için hata ayıklama sembol bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="0b70e-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b70e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0b70e-104">Methods</span></span>  
  
|<span data-ttu-id="0b70e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0b70e-105">Method</span></span>|<span data-ttu-id="0b70e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b70e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b70e-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b70e-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="0b70e-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="0b70e-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="0b70e-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b70e-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="0b70e-110">Bir değişkenin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="0b70e-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="0b70e-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b70e-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="0b70e-112">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="0b70e-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="0b70e-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b70e-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="0b70e-114">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="0b70e-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="0b70e-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b70e-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="0b70e-116">Bir bayt dizisinin değerini bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="0b70e-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b70e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b70e-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b70e-118">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b70e-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0b70e-119">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="0b70e-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b70e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b70e-120">Requirements</span></span>  
 <span data-ttu-id="0b70e-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b70e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b70e-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b70e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b70e-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b70e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b70e-124">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b70e-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b70e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b70e-125">See also</span></span>

- [<span data-ttu-id="0b70e-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b70e-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0b70e-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0b70e-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
