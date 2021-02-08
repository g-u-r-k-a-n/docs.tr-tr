---
description: 'Daha fazla bilgi edinin: EPolicyAction numaralandırması'
title: EPolicyAction Numaralandırması
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
ms.openlocfilehash: fb66de2211972bd4d25ccfbab4965f315c0144a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785477"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="bc6d4-103">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bc6d4-103">EPolicyAction Enumeration</span></span>

<span data-ttu-id="bc6d4-104">[EClrOperation](eclroperation-enumeration.md) tarafından tanımlanan Işlemler ve [EClrFailure](eclrfailure-enumeration.md)tarafından tanımlanan hatalar için konağın ayarlayaşabilemeyen ilke eylemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-104">Describes the policy actions the host can set for operations described by [EClrOperation](eclroperation-enumeration.md) and failures described by [EClrFailure](eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc6d4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc6d4-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="bc6d4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bc6d4-106">Members</span></span>  
  
|<span data-ttu-id="bc6d4-107">Üye</span><span class="sxs-lookup"><span data-stu-id="bc6d4-107">Member</span></span>|<span data-ttu-id="bc6d4-108">Description</span><span class="sxs-lookup"><span data-stu-id="bc6d4-108">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="bc6d4-109">Ortak dil çalışma zamanının (CLR) iş parçacığını düzgün bir şekilde iptal etmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-109">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="bc6d4-110">Düzgün bir şekilde iptali, tüm blokları çalıştırma girişimlerini `finally` , `catch` iş parçacığı iptalleriyle ilgili tüm blokları ve sonlandırıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-110">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="bc6d4-111">CLR 'nin devre dışı bir durum girmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-111">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="bc6d4-112">Etkilenen işlemde başka yönetilen kod yürütülemez ve iş parçacıklarının CLR 'ye girmaları engellenir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-112">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="bc6d4-113">CLR 'nin, sonlandırıcıları çalıştırma ve temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme dahil olmak üzere işlemden düzgün bir şekilde çıkış denemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-113">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="bc6d4-114">CLR 'nin sonlandırıcıları çalıştırmadan veya temizleme ve günlüğe kaydetme işlemlerini gerçekleştirmeksizin işlemden hemen çıkış gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-114">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="bc6d4-115">Ancak, bildirim hata ayıklayıcıya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-115">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="bc6d4-116">Hiçbir eylemin alıngerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-116">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="bc6d4-117">CLR 'nin bir işlenmemiş iş parçacığı iptali gerçekleştirmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-117">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="bc6d4-118">Yalnızca `catch` `finally` ile işaretli olan ve blokları <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-118">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="bc6d4-119">CLR 'nin sonlandırıcılar veya günlüğe kaydetme işlemlerini çalıştırmadan işlemden çıkması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-119">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="bc6d4-120">CLR 'nin bir işlenmemiş yüklemesini gerçekleştirmesi gerektiğini belirtir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="bc6d4-120">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="bc6d4-121">Yalnızca ile işaretlenen sonlandırıcılar <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-121">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="bc6d4-122">Benzer şekilde, yığınında buna sahip olan tüm iş parçacıkları <xref:System.AppDomain> bir alır `ThreadAbortException` , ancak yalnızca `catch` `finally` ile işaretlenmiş olan ve blokları <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-122">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="bc6d4-123">Koşula uygun bir özel durum (örneğin, bellek dışı, arabellek taşması vb.) oluşturulması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-123">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="bc6d4-124">' Nin <xref:System.AppDomain> yüklemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-124">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="bc6d4-125">CLR sonlandırıcıları çalıştırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-125">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc6d4-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc6d4-126">Remarks</span></span>  

 <span data-ttu-id="bc6d4-127">Konak, [ICLRPolicyManager](iclrpolicymanager-interface.md) arabiriminin yöntemlerini çağırarak ilke eylemlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-127">The host sets policy actions by calling methods of the [ICLRPolicyManager](iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="bc6d4-128">İşlenmemiş ve düzgün kaldırma hakkında bilgi için bkz. [EClrOperation](eclroperation-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-128">For information about rude and graceful aborts, see the [EClrOperation](eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc6d4-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc6d4-129">Requirements</span></span>  

 <span data-ttu-id="bc6d4-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc6d4-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc6d4-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bc6d4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc6d4-132">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc6d4-132">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc6d4-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc6d4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6d4-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc6d4-134">See also</span></span>

- [<span data-ttu-id="bc6d4-135">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bc6d4-135">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="bc6d4-136">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc6d4-136">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="bc6d4-137">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc6d4-137">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="bc6d4-138">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="bc6d4-138">Hosting Enumerations</span></span>](hosting-enumerations.md)
