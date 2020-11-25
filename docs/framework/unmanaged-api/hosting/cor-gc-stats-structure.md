---
title: COR_GC_STATS Yapısı
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 53a70c53a06ac55a2dab7c646018d63189ee0b36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726229"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="ac107-102">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="ac107-102">COR_GC_STATS Structure</span></span>

<span data-ttu-id="ac107-103">Ortak dil çalışma zamanının (CLR) çöp toplama mekanizması hakkında istatistikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac107-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac107-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac107-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="ac107-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ac107-105">Members</span></span>  
  
|<span data-ttu-id="ac107-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ac107-106">Member</span></span>|<span data-ttu-id="ac107-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac107-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="ac107-108">Hangi alan değerlerinin hesaplanacağını ve döndürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac107-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="ac107-109">Dış istek tarafından zorlanan çöp koleksiyonlarının sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac107-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="ac107-110">Her nesil için gerçekleştirilen çöp koleksiyonlarının sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac107-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="ac107-111">Tüm yığınlara kaydedilen kilobayt toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="ac107-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="ac107-112">Tüm yığınlara ayrılan toplam kilobayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ac107-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="ac107-113">Kuşak sıfır yığınının kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac107-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="ac107-114">Kuşak-tek yığının kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac107-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="ac107-115">Oluşturma-iki yığının kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac107-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="ac107-116">Büyük nesne yığınının kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac107-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="ac107-117">Sıfırdan yükseltilen nesnelerin kilobayt cinsinden boyutu. kuşak.</span><span class="sxs-lookup"><span data-stu-id="ac107-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="ac107-118">Tek nesil bir oluşturma işleminden yükseltilen nesnelerin kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac107-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac107-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac107-119">Remarks</span></span>  

 <span data-ttu-id="ac107-120">[ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md) yöntemi, `Flags` `COR_GC_STATS` hangi istatistiklerin ayarlanacağını belirlemek için yapının alanının [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) numaralandırmasının bir veya daha fazla değerine ayarlanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ac107-120">The [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="ac107-121">Aşağıdaki tabloda, bu yapı tarafından sunulan istatistikler iki [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) numaralandırma değeri `COR_GC_COUNTS` ve ile eşlenir `COR_GC_MEMORYUSAGE` .</span><span class="sxs-lookup"><span data-stu-id="ac107-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="ac107-122">COR_GC_COUNTS tarafından belirtilen</span><span class="sxs-lookup"><span data-stu-id="ac107-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="ac107-123">COR_GC_MEMORYUSAGE tarafından belirtilen</span><span class="sxs-lookup"><span data-stu-id="ac107-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="ac107-124">Kullanım örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ac107-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ac107-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac107-125">Requirements</span></span>  

 <span data-ttu-id="ac107-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac107-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac107-127">**Üst bilgi:** GCHost. IDL</span><span class="sxs-lookup"><span data-stu-id="ac107-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="ac107-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ac107-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac107-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac107-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac107-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac107-130">See also</span></span>

- [<span data-ttu-id="ac107-131">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="ac107-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="ac107-132">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="ac107-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="ac107-133">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="ac107-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
