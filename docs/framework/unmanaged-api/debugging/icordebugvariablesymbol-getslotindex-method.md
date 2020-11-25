---
title: 'ICorDebugVariableSymbol:: Getslotındex yöntemi'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: fc42517cb95dfc14c472b5bb9111ebd70639cee7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725995"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="640ee-102">ICorDebugVariableSymbol:: Getslotındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="640ee-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>

<span data-ttu-id="640ee-103">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="640ee-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="640ee-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="640ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="640ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="640ee-105">Parameters</span></span>  

 `pSlotIndex`  
 <span data-ttu-id="640ee-106">dışı Yerel değişkenin yuva dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="640ee-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="640ee-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="640ee-107">Return Value</span></span>  

 <span data-ttu-id="640ee-108">`S_OK` başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="640ee-108">`S_OK` if successful.</span></span> <span data-ttu-id="640ee-109">`E_FAIL` değişken bir işlev bağımsız değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="640ee-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="640ee-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="640ee-110">Remarks</span></span>  

 <span data-ttu-id="640ee-111">Bir yerel değişkenin yönetilen yuva dizini, değişkenin meta veri bilgilerini almak için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="640ee-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="640ee-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="640ee-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="640ee-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="640ee-113">Requirements</span></span>  

 <span data-ttu-id="640ee-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="640ee-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="640ee-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="640ee-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="640ee-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="640ee-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="640ee-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="640ee-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="640ee-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="640ee-118">See also</span></span>

- [<span data-ttu-id="640ee-119">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640ee-119">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="640ee-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="640ee-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
