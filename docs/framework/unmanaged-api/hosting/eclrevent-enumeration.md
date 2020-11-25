---
title: EClrEvent Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: 5d6ec42da60a7b294177063b9f8bd5afbf352c62
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726827"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="ced50-102">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ced50-102">EClrEvent Enumeration</span></span>

<span data-ttu-id="ced50-103">Konağın geri çağırmaları kaydedebileceği ortak dil çalışma zamanı (CLR) olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ced50-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ced50-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ced50-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="ced50-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ced50-105">Members</span></span>  
  
|<span data-ttu-id="ced50-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ced50-106">Member</span></span>|<span data-ttu-id="ced50-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ced50-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="ced50-108">Önemli bir CLR hatası belirtir.</span><span class="sxs-lookup"><span data-stu-id="ced50-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="ced50-109">Belirli bir sürümü kaldırmayı belirtir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ced50-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="ced50-110">Yönetilen hata ayıklama Yardımcısı (MDA) iletisinin oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ced50-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="ced50-111">Yığın taşması hatası oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ced50-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ced50-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ced50-112">Remarks</span></span>  

 <span data-ttu-id="ced50-113">Konak, `EClrEvent` [ICLROnEventManager](iclroneventmanager-interface.md) arabiriminin yöntemlerini çağırarak tarafından tanımlanan olay türlerinden herhangi biri için geri çağırmaları kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="ced50-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="ced50-114">Ana bilgisayar [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırarak bu arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ced50-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="ced50-115">`Event_CLRDisabled`Ve `Event_DomainUnload` olayları bir defadan fazla ve farklı iş parçacıklarından bir KALDıRMA veya clr 'nin devre dışı bırakılmasını bildirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ced50-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="ced50-116">`Event_MDAFired`Olay, MDA iletisinin ayrıntılarını içeren bir [Mdadınfo](mdainfo-structure.md) örneği oluşturulmasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="ced50-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="ced50-117">MDAs hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="ced50-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ced50-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ced50-118">Requirements</span></span>  

 <span data-ttu-id="ced50-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ced50-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ced50-120">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ced50-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ced50-121">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ced50-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ced50-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ced50-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ced50-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ced50-123">See also</span></span>

- [<span data-ttu-id="ced50-124">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ced50-124">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="ced50-125">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ced50-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ced50-126">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ced50-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
