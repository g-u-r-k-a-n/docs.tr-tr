---
title: EClrFailure Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: d2794b53ed17640413928b3af0d1ed3656e25f22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675769"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="2a709-102">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2a709-102">EClrFailure Enumeration</span></span>

<span data-ttu-id="2a709-103">Bir konağın ilke eylemlerini ayarlayabileceği başarısızlık kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2a709-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a709-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a709-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="2a709-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2a709-105">Members</span></span>  
  
|<span data-ttu-id="2a709-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2a709-106">Member</span></span>|<span data-ttu-id="2a709-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a709-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="2a709-108">Kritik olmayan bir kod bölgesinde bir kaynak (iş parçacığı, bir bellek bloğu veya kilit gibi) ayırma girişimi sırasında bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2a709-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="2a709-109">Kritik kod bölgesinde bir kaynak (iş parçacığı, bir bellek bloğu veya kilit gibi) ayırma girişimi sırasında bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2a709-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="2a709-110">Ortak dil çalışma zamanı (CLR), işlemde yönetilen kodu artık çalıştıraamayacak.</span><span class="sxs-lookup"><span data-stu-id="2a709-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="2a709-111">Henceileri, herhangi bir barındırma işlevlerine yapılan çağrılar HOST_E_CLRNOTAVAILABLE HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a709-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="2a709-112">Bir iş parçacığı bir nesneden dönmeden bir kilidi serbest bırakmaya başarısız oldu <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="2a709-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="2a709-113">Konak, bir iş parçacığının iptal edilmesini sağlamak için bu hatayı ayarlayamadı.</span><span class="sxs-lookup"><span data-stu-id="2a709-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="2a709-114">Yığın taşması oluştu.</span><span class="sxs-lookup"><span data-stu-id="2a709-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="2a709-115">Korunan bellek okuma veya yazma girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="2a709-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="2a709-116">.NET Framework 4 ' te desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2a709-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="2a709-117">Bir kod sözleşmesi hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="2a709-117">A code contract failure occurred.</span></span> <span data-ttu-id="2a709-118">Bkz. [Kod sözleşmeleri](../../debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="2a709-118">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a709-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a709-119">Remarks</span></span>  

 <span data-ttu-id="2a709-120">Konağın hata koşulları için ilke eylemlerini belirtmek için kullanabileceği [EPolicyAction](epolicyaction-enumeration.md) değerlerinin bir listesi Için [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="2a709-120">See the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="2a709-121">Kritik ve kritik olmayan kod bölgeleri hakkında daha fazla bilgi için bkz. [EClrOperation](eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2a709-121">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a709-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a709-122">Requirements</span></span>  

 <span data-ttu-id="2a709-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a709-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a709-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2a709-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a709-125">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a709-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a709-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a709-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a709-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a709-127">See also</span></span>

- [<span data-ttu-id="2a709-128">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a709-128">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="2a709-129">SetActionOnFailure Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a709-129">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="2a709-130">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a709-130">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="2a709-131">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="2a709-131">Hosting Enumerations</span></span>](hosting-enumerations.md)
