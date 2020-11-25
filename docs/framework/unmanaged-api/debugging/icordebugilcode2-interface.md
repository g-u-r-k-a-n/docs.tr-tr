---
title: ICorDebugILCode2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: b9289b5afc88c926ce585a4e620364cf2dc979d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703336"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="7672d-102">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7672d-102">ICorDebugILCode2 Interface</span></span>

<span data-ttu-id="7672d-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="7672d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7672d-104">Bir işlevin yerel değişken imzasının belirtecini döndüren ve bir profiler 'ın belgelenmiş ara dili (IL) orijinal Yöntem Il uzaklıklarına eşleyen Yöntemler sağlamak için [ICorDebugILCode](icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="7672d-104">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7672d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7672d-105">Methods</span></span>  
  
|<span data-ttu-id="7672d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7672d-106">Method</span></span>|<span data-ttu-id="7672d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7672d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7672d-108">GetInstrumentedILMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7672d-108">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="7672d-109">Bu örnek için, Oluşturucu tarafından işaretlenmiş Il uzaklıkları orijinal Yöntem Il uzaklıklarından bir harita döndürür.</span><span class="sxs-lookup"><span data-stu-id="7672d-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="7672d-110">GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="7672d-110">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="7672d-111">Bu örnek tarafından temsil edilen işlev için yerel değişken imzasının meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="7672d-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7672d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7672d-112">Requirements</span></span>  

 <span data-ttu-id="7672d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7672d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7672d-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7672d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7672d-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7672d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7672d-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7672d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7672d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7672d-117">See also</span></span>

- [<span data-ttu-id="7672d-118">ICorDebugILCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7672d-118">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="7672d-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7672d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7672d-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7672d-120">Debugging</span></span>](index.md)
