---
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 3d808fd49eb7767f1f48ad4e07d8ba7e47c8f34b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679487"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="78efa-102">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78efa-102">ICorDebugVariableSymbol Interface</span></span>

<span data-ttu-id="78efa-103">Bir değişken için hata ayıklama sembol bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="78efa-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78efa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="78efa-104">Methods</span></span>  
  
|<span data-ttu-id="78efa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="78efa-105">Method</span></span>|<span data-ttu-id="78efa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78efa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78efa-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78efa-107">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="78efa-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="78efa-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="78efa-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78efa-109">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="78efa-110">Bir değişkenin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="78efa-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="78efa-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78efa-111">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="78efa-112">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="78efa-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="78efa-113">GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="78efa-113">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="78efa-114">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="78efa-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="78efa-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78efa-115">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="78efa-116">Bir bayt dizisinin değerini bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="78efa-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78efa-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78efa-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78efa-118">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78efa-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="78efa-119">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="78efa-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78efa-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78efa-120">Requirements</span></span>  

 <span data-ttu-id="78efa-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78efa-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78efa-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="78efa-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78efa-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="78efa-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78efa-124">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78efa-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78efa-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78efa-125">See also</span></span>

- [<span data-ttu-id="78efa-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="78efa-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="78efa-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="78efa-127">Debugging</span></span>](index.md)
