---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 1088374c9df18ded38b44384be44de245f0bd403
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728959"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="7e00f-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e00f-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>

<span data-ttu-id="7e00f-103">İşlenmeyen bir özel durum oluştuğunda ortak dil çalışma zamanının (CLR) davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e00f-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e00f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e00f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e00f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e00f-105">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="7e00f-106">'ndaki Davranışın CLR veya konak tarafından ayarlanmış olup olmadığını gösteren [EClrUnhandledException](eclrunhandledexception-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="7e00f-106">[in] One of the [EClrUnhandledException](eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e00f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7e00f-107">Return Value</span></span>  
  
|<span data-ttu-id="7e00f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e00f-108">HRESULT</span></span>|<span data-ttu-id="7e00f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e00f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e00f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e00f-110">S_OK</span></span>|<span data-ttu-id="7e00f-111">`SetUnhandledExceptionPolicy` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7e00f-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="7e00f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7e00f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7e00f-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7e00f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7e00f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7e00f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7e00f-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7e00f-115">The call timed out.</span></span>|  
|<span data-ttu-id="7e00f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7e00f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7e00f-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7e00f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7e00f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7e00f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7e00f-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7e00f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7e00f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7e00f-120">E_FAIL</span></span>|<span data-ttu-id="7e00f-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7e00f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7e00f-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7e00f-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7e00f-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e00f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e00f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e00f-124">Remarks</span></span>  

 <span data-ttu-id="7e00f-125">Varsayılan olarak, CLR işlenmeyen tüm özel durumlar için son işleyicidir ve varsayılan davranışı işlemi yavaşlatmak olur.</span><span class="sxs-lookup"><span data-stu-id="7e00f-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="7e00f-126">Konak, `policy` değeri eHostDeterminedPolicy olarak ayarlayarak bu davranışı değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="7e00f-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="7e00f-127">Bu değer, konağın, CLR 'nin önceki sürümlerinde olduğu gibi kendi varsayılan davranışını uygulamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7e00f-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e00f-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e00f-128">Requirements</span></span>  

 <span data-ttu-id="7e00f-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e00f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e00f-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7e00f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e00f-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7e00f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e00f-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e00f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e00f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e00f-133">See also</span></span>

- [<span data-ttu-id="7e00f-134">EClrUnhandledException Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7e00f-134">EClrUnhandledException Enumeration</span></span>](eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="7e00f-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e00f-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7e00f-136">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e00f-136">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="7e00f-137">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e00f-137">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
