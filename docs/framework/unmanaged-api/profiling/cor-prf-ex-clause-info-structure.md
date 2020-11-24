---
title: COR_PRF_EX_CLAUSE_INFO Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
ms.openlocfilehash: e8dd9f21803021975f4651ba3e6e5f4d3da0ea82
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675002"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="11224-102">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="11224-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>

<span data-ttu-id="11224-103">Belirli bir özel durum yan tümcesi ve onunla ilişkili çerçevesini hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="11224-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11224-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="11224-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="11224-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="11224-105">Members</span></span>  
  
|<span data-ttu-id="11224-106">Üye</span><span class="sxs-lookup"><span data-stu-id="11224-106">Member</span></span>|<span data-ttu-id="11224-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11224-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="11224-108">Yeni girilen veya soldaki kodun özel durum yan tümcesinin türünü belirten [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="11224-108">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="11224-109">Yan tümce işleyicisinin yerel giriş noktası — Örneğin, x86 EıP kaydının içeriği.</span><span class="sxs-lookup"><span data-stu-id="11224-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="11224-110">Yan tümce işleyicisi için mantıksal çerçeveye yönelik işaretçi — Örneğin, x86 EBP kaydının içeriği.</span><span class="sxs-lookup"><span data-stu-id="11224-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="11224-111">Gölge yığınının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="11224-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="11224-112">Bu değer BSP yazmacın içerikleri ve yalnızca ıA64 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="11224-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11224-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11224-113">Remarks</span></span>  

 <span data-ttu-id="11224-114">Bir özel durum bildirimi alındığında, çalıştırılmak üzere veya yalnızca çalıştırılmış olan özel durum yan tümcesinin (/Filter) yerel adres ve çerçeve bilgilerini almak için [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) kullanılabilir `catch` / `finally` .</span><span class="sxs-lookup"><span data-stu-id="11224-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="11224-115">Özel durum yan tümcesinin yürütülmesi, ortak dil çalışma zamanından (CLR) bu geri çağırmaları içerir:</span><span class="sxs-lookup"><span data-stu-id="11224-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="11224-116">ICorProfilerCallback:: ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="11224-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="11224-117">ICorProfilerCallback:: Exceptionunwınbir Finallyenter</span><span class="sxs-lookup"><span data-stu-id="11224-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="11224-118">ICorProfilerCallback:: ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="11224-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="11224-119">ICorProfilerCallback:: Exceptioncatch Erleave</span><span class="sxs-lookup"><span data-stu-id="11224-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="11224-120">ICorProfilerCallback:: Exceptionunwınbir Finallyleave</span><span class="sxs-lookup"><span data-stu-id="11224-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="11224-121">ICorProfilerCallback:: ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="11224-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="11224-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11224-122">Requirements</span></span>  

 <span data-ttu-id="11224-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11224-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11224-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="11224-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="11224-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="11224-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11224-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11224-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11224-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11224-127">See also</span></span>

- [<span data-ttu-id="11224-128">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="11224-128">Profiling Structures</span></span>](profiling-structures.md)
