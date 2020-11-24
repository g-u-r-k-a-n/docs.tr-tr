---
title: ICLRGCManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
ms.openlocfilehash: dbe3df6bb20e5ad8f9eb534a366405eb9c33984f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678252"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="359ad-102">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="359ad-102">ICLRGCManager Interface</span></span>

<span data-ttu-id="359ad-103">Bir konağın ortak dil çalışma zamanının çöp toplama sistemiyle etkileşime geçmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="359ad-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="359ad-104">4,5 .NET Framework başlayarak, [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini kullanarak bir çöp toplama kesiminin boyutunu ve çöp toplama sisteminin en büyük boyutunu `DWORD` [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) yöntemi tarafından uygulanan sınırdan daha büyük değerlere ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="359ad-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="359ad-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="359ad-105">Methods</span></span>  
  
|<span data-ttu-id="359ad-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="359ad-106">Method</span></span>|<span data-ttu-id="359ad-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="359ad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="359ad-108">Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="359ad-108">Collect Method</span></span>](iclrgcmanager-collect-method.md)|<span data-ttu-id="359ad-109">Belirtilen oluşturma için bir çöp toplamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="359ad-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="359ad-110">GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="359ad-110">GetStats Method</span></span>](iclrgcmanager-getstats-method.md)|<span data-ttu-id="359ad-111">Çöp toplama sistemiyle ilgili geçerli istatistik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="359ad-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="359ad-112">SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="359ad-112">SetGCStartupLimits Method</span></span>](iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="359ad-113">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="359ad-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="359ad-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="359ad-114">Remarks</span></span>  

 <span data-ttu-id="359ad-115">Ortak dil çalışma zamanı (CLR), kendi çöp toplama mekanizmasını yönetilen türle uygular <xref:System.GC> .</span><span class="sxs-lookup"><span data-stu-id="359ad-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="359ad-116">Çöp toplama sistemi hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="359ad-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="359ad-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="359ad-117">Requirements</span></span>  

 <span data-ttu-id="359ad-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="359ad-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="359ad-119">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="359ad-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="359ad-120">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="359ad-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="359ad-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="359ad-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359ad-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="359ad-122">See also</span></span>

- [<span data-ttu-id="359ad-123">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="359ad-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="359ad-124">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="359ad-124">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="359ad-125">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="359ad-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="359ad-126">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="359ad-126">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="359ad-127">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="359ad-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="359ad-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="359ad-128">Hosting</span></span>](index.md)
