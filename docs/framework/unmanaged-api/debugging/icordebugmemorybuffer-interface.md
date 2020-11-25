---
title: ICorDebugMemoryBuffer Arabirimi
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 2765852309401d2aa30f91b506ba55156cd8a3e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710758"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="9d51c-102">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51c-102">ICorDebugMemoryBuffer Interface</span></span>

<span data-ttu-id="9d51c-103">Bellek içi arabelleği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d51c-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d51c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9d51c-104">Methods</span></span>  
  
|<span data-ttu-id="9d51c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9d51c-105">Method</span></span>|<span data-ttu-id="9d51c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d51c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d51c-107">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d51c-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="9d51c-108">Bellek arabelleğinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="9d51c-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="9d51c-109">GetStartAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d51c-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="9d51c-110">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="9d51c-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d51c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d51c-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d51c-112">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d51c-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9d51c-113">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="9d51c-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d51c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d51c-114">Requirements</span></span>  

 <span data-ttu-id="9d51c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d51c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d51c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9d51c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d51c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9d51c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d51c-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d51c-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d51c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d51c-119">See also</span></span>

- [<span data-ttu-id="9d51c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d51c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9d51c-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9d51c-121">Debugging</span></span>](index.md)
