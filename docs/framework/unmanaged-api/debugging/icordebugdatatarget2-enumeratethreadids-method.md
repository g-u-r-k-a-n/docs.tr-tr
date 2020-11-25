---
title: ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 31a839076b34901ae1a8f3b43021f64f77629fc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713853"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="28ed2-102">ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28ed2-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>

<span data-ttu-id="28ed2-103">Etkin iş parçacığı kimliklerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="28ed2-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ed2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="28ed2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28ed2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28ed2-105">Parameters</span></span>  

 <span data-ttu-id="28ed2-106">Cthreadıds</span><span class="sxs-lookup"><span data-stu-id="28ed2-106">cThreadIDs</span></span>  
 <span data-ttu-id="28ed2-107">'ndaki Kimlikleri döndürülebilecek en fazla iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="28ed2-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="28ed2-108">Pcthreadıds</span><span class="sxs-lookup"><span data-stu-id="28ed2-108">pcThreadIds</span></span>  
 <span data-ttu-id="28ed2-109">dışı `ULONG32` Diziye yazılan iş parçacığı kimliklerinin gerçek sayısını gösteren bir işaretçisi `pThreadIds` .</span><span class="sxs-lookup"><span data-stu-id="28ed2-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="28ed2-110">Pthreadıds</span><span class="sxs-lookup"><span data-stu-id="28ed2-110">pThreadIDs</span></span>  
 <span data-ttu-id="28ed2-111">Bir dizi iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="28ed2-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28ed2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28ed2-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28ed2-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="28ed2-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28ed2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28ed2-114">Requirements</span></span>  

 <span data-ttu-id="28ed2-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md). **Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="28ed2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28ed2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="28ed2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28ed2-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ed2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ed2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28ed2-118">See also</span></span>

- [<span data-ttu-id="28ed2-119">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28ed2-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="28ed2-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="28ed2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
