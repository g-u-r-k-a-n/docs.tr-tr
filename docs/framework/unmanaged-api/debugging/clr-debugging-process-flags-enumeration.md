---
title: CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
ms.openlocfilehash: dd148d23d6e29f03052d3bbf1fcd5d02fb332a0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729856"
---
# <a name="clr_debugging_process_flags-enumeration"></a><span data-ttu-id="4f8be-102">CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4f8be-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>

<span data-ttu-id="4f8be-103">[ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f8be-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f8be-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4f8be-104">Syntax</span></span>  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4f8be-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4f8be-105">Members</span></span>  
  
|<span data-ttu-id="4f8be-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4f8be-106">Member</span></span>|<span data-ttu-id="4f8be-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f8be-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="4f8be-108">Bu çalışma zamanının gönderileceği, ön olmayan bir yönetilen hata ayıklayıcı olayı vardır.</span><span class="sxs-lookup"><span data-stu-id="4f8be-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="4f8be-109">Yakalama ve ön uç olmayan olaylar arasındaki ayrım için açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4f8be-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="4f8be-110">Bekleyen yönetilen olay bir <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> istek.</span><span class="sxs-lookup"><span data-stu-id="4f8be-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f8be-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f8be-111">Remarks</span></span>  

 <span data-ttu-id="4f8be-112">Yakalama olayları işlem, uygulama etki alanı, derleme, modül ve hata ayıklayıcıyı bir işleme eklendikten sonra geçerli duruma getirecek olan iş parçacığı oluşturma bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4f8be-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="4f8be-113">Bayrak tarafından belirtilen yakalama olmayan olaylar `CLR_DEBUGGING_MANAGED_EVENT_PENDING` , özel durumlar ve yönetilen hata ayıklama Yardımcısı (MDA) bildirimleri gibi diğer tüm hata ayıklayıcı olaylarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4f8be-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="4f8be-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`Bayrak, çalışma zamanının, iptal edilmiş bir yönetilen hata ayıklayıcı eklemek için bir Sonlandırıcı özel durumu ve isteği ayırt etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f8be-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f8be-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f8be-115">Requirements</span></span>  

 <span data-ttu-id="4f8be-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f8be-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f8be-117">**Üst bilgi:** Metahost. IDL, Metahost. h</span><span class="sxs-lookup"><span data-stu-id="4f8be-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="4f8be-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4f8be-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f8be-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f8be-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f8be-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f8be-120">See also</span></span>

- [<span data-ttu-id="4f8be-121">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="4f8be-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="4f8be-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4f8be-122">Debugging</span></span>](index.md)
