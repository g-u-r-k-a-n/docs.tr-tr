---
title: ICLRControl Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: 914a2f6103fb0ffb9a7b9fcb895ecf0cd62f3c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126601"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="120e5-102">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="120e5-102">ICLRControl Interface</span></span>
<span data-ttu-id="120e5-103">, Bir konağın ortak dil çalışma zamanı (CLR) için başvuruları almasını ve yönlerini yapılandırmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="120e5-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="120e5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="120e5-104">Methods</span></span>  
  
|<span data-ttu-id="120e5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="120e5-105">Method</span></span>|<span data-ttu-id="120e5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="120e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="120e5-107">GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="120e5-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="120e5-108">Konağın CLR 'yi yapılandırmak için kullanabileceği bir yönetici türü örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="120e5-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="120e5-109">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="120e5-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="120e5-110">Uygulama etki alanı yöneticileri için tür olarak <xref:System.AppDomainManager> türetilmiş bir tür belirler.</span><span class="sxs-lookup"><span data-stu-id="120e5-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="120e5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="120e5-111">Requirements</span></span>  
 <span data-ttu-id="120e5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="120e5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="120e5-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="120e5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="120e5-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="120e5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="120e5-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="120e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120e5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="120e5-116">See also</span></span>

- [<span data-ttu-id="120e5-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="120e5-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="120e5-118">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="120e5-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="120e5-119">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="120e5-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="120e5-120">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="120e5-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="120e5-121">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="120e5-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="120e5-122">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="120e5-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="120e5-123">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="120e5-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="120e5-124">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="120e5-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="120e5-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="120e5-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
