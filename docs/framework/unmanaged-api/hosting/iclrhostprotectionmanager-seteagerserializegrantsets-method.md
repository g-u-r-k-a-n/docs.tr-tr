---
title: ICLRHostProtectionManager::SetEagerSerializeGrantSets Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
ms.openlocfilehash: 9ce4a5e042e838da8e9eba614f26e35b38af56c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714139"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="1fce1-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fce1-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>

<span data-ttu-id="1fce1-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="1fce1-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fce1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1fce1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1fce1-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1fce1-105">Return Value</span></span>  
  
|<span data-ttu-id="1fce1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1fce1-106">HRESULT</span></span>|<span data-ttu-id="1fce1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fce1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1fce1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1fce1-108">S_OK</span></span>|<span data-ttu-id="1fce1-109">`SetEagerSerializeGrantSets` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1fce1-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="1fce1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1fce1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1fce1-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1fce1-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1fce1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1fce1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1fce1-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1fce1-113">The call timed out.</span></span>|  
|<span data-ttu-id="1fce1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1fce1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1fce1-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1fce1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1fce1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1fce1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1fce1-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1fce1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1fce1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1fce1-118">E_FAIL</span></span>|<span data-ttu-id="1fce1-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1fce1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1fce1-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1fce1-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1fce1-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1fce1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1fce1-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fce1-122">Requirements</span></span>  

 <span data-ttu-id="1fce1-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fce1-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fce1-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1fce1-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1fce1-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1fce1-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fce1-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fce1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fce1-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fce1-127">See also</span></span>

- [<span data-ttu-id="1fce1-128">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1fce1-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="1fce1-129">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1fce1-129">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
