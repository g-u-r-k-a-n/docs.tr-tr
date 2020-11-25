---
title: CorDebugInternalFrameType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: 1c94e03aa088d8f48eb7f7a418cebd0492319513
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696602"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="a937d-102">CorDebugInternalFrameType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a937d-102">CorDebugInternalFrameType Enumeration</span></span>

<span data-ttu-id="a937d-103">Yığın çerçevesinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a937d-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="a937d-104">Bu numaralandırma [ICorDebugInternalFrame:: GetFrameType](icordebuginternalframe-getframetype-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a937d-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a937d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a937d-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="a937d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a937d-106">Members</span></span>  
  
|<span data-ttu-id="a937d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a937d-107">Member</span></span>|<span data-ttu-id="a937d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a937d-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="a937d-109">Null değer.</span><span class="sxs-lookup"><span data-stu-id="a937d-109">A null value.</span></span> <span data-ttu-id="a937d-110">`ICorDebugInternalFrame::GetFrameType`Yöntem hiçbir şekilde bu değeri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="a937d-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="a937d-111">Yönetilen-yönetilmeyen bir saplama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="a937d-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="a937d-112">Yönetilmeyenden yönetilene bir saplama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="a937d-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="a937d-113">Uygulama etki alanları arasında geçiş.</span><span class="sxs-lookup"><span data-stu-id="a937d-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="a937d-114">Hafif bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="a937d-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="a937d-115">İşlev değerlendirmesinin başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="a937d-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="a937d-116">Ortak dil çalışma zamanına bir iç çağrı.</span><span class="sxs-lookup"><span data-stu-id="a937d-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="a937d-117">Bir sınıf başlatma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="a937d-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="a937d-118">Oluşturulan özel durum.</span><span class="sxs-lookup"><span data-stu-id="a937d-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="a937d-119">Kod erişim güvenliği için kullanılan çerçeve.</span><span class="sxs-lookup"><span data-stu-id="a937d-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="a937d-120">Çalışma zamanı JıT olarak bir yöntemi derlemedir.</span><span class="sxs-lookup"><span data-stu-id="a937d-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a937d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a937d-121">Requirements</span></span>  

 <span data-ttu-id="a937d-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a937d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a937d-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a937d-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a937d-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a937d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a937d-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a937d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a937d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a937d-126">See also</span></span>

- [<span data-ttu-id="a937d-127">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a937d-127">Debugging Enumerations</span></span>](debugging-enumerations.md)
