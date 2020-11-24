---
title: ICLRGCManager2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: d2873b5e1f8229e8a16dfaacf1c9737ac47405bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672805"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="180d5-102">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="180d5-102">ICLRGCManager2 Interface</span></span>

<span data-ttu-id="180d5-103">Bir konağın ortak dil çalışma zamanının çöp toplama sistemiyle etkileşime geçmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="180d5-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="180d5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="180d5-104">Methods</span></span>  
  
|<span data-ttu-id="180d5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="180d5-105">Method</span></span>|<span data-ttu-id="180d5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="180d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="180d5-107">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="180d5-107">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="180d5-108">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="180d5-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="180d5-109">1. nesil ve kesim boyutlarını daha büyük olarak sunar `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="180d5-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="180d5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="180d5-110">Remarks</span></span>  

 <span data-ttu-id="180d5-111">Bu arabirim [ICLRGCManager arabiriminden](iclrgcmanager-interface.md)devralır.</span><span class="sxs-lookup"><span data-stu-id="180d5-111">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="180d5-112">Ortak dil çalışma zamanı (CLR), kendi çöp toplama mekanizmasını yönetilen türle uygular <xref:System.GC> .</span><span class="sxs-lookup"><span data-stu-id="180d5-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="180d5-113">Çöp toplama sistemi hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="180d5-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="180d5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="180d5-114">Requirements</span></span>  

 <span data-ttu-id="180d5-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="180d5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="180d5-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="180d5-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="180d5-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="180d5-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="180d5-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="180d5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="180d5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="180d5-119">See also</span></span>

- [<span data-ttu-id="180d5-120">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="180d5-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="180d5-121">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="180d5-121">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="180d5-122">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="180d5-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="180d5-123">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="180d5-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="180d5-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="180d5-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="180d5-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="180d5-125">Hosting</span></span>](index.md)
