---
title: IHostSecurityContext Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: aafaa1d648396ddaa76193fa15cf7f74394777a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724812"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="767bc-102">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="767bc-102">IHostSecurityContext Interface</span></span>

<span data-ttu-id="767bc-103">Ortak dil çalışma zamanının (CLR) konak tarafından uygulanan güvenlik bağlamı bilgilerini korumasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="767bc-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="767bc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="767bc-104">Methods</span></span>  
  
|<span data-ttu-id="767bc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="767bc-105">Method</span></span>|<span data-ttu-id="767bc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="767bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="767bc-107">Capture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="767bc-107">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="767bc-108">`IHostSecurityContext` [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)çağrısından döndürülen örneğinin bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="767bc-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="767bc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="767bc-109">Remarks</span></span>  

 <span data-ttu-id="767bc-110">Bir konak, iş parçacığı belirteçlerine yönelik tüm kod erişimini CLR ve Kullanıcı koduna göre denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="767bc-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="767bc-111">Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="767bc-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="767bc-112">`IHostSecurityContext` çalışma zamanı için donuk olan bu güvenlik bağlamı bilgilerini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="767bc-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="767bc-113">Çalışma zamanı bu bilgileri kullanarak yakalar `Capture` ve iş parçacığı havuzu çalışan öğesi gönderimi, sonlandırıcısı yürütmesi ve modül ve sınıf oluşturucuları arasında gider.</span><span class="sxs-lookup"><span data-stu-id="767bc-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="767bc-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="767bc-114">Requirements</span></span>  

 <span data-ttu-id="767bc-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="767bc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="767bc-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="767bc-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="767bc-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="767bc-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="767bc-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="767bc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="767bc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="767bc-119">See also</span></span>

- [<span data-ttu-id="767bc-120">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="767bc-120">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="767bc-121">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="767bc-121">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="767bc-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="767bc-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
