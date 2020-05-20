---
title: CLRCreateInstance İşlevi
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: c3011149b9b23e776ad3baac9e41f3c42213654d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616833"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="5a04d-102">CLRCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="5a04d-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="5a04d-103">Üç arabirimden birini sunar: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5a04d-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a04d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5a04d-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a04d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a04d-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="5a04d-106">'ndaki Üç sınıf tanımlayıcılarından biri: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy veya CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="5a04d-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="5a04d-107">'ndaki Üç arabirim tanımlayıcılarından biri (IIDS): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy veya IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="5a04d-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="5a04d-108">dışı Üç arabirimden biri: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5a04d-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a04d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a04d-109">Return Value</span></span>  
 <span data-ttu-id="5a04d-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a04d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5a04d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a04d-111">HRESULT</span></span>|<span data-ttu-id="5a04d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a04d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a04d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a04d-113">S_OK</span></span>|<span data-ttu-id="5a04d-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5a04d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5a04d-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5a04d-115">E_POINTER</span></span>|<span data-ttu-id="5a04d-116">`ppInterface`null.</span><span class="sxs-lookup"><span data-stu-id="5a04d-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a04d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a04d-117">Remarks</span></span>  
 <span data-ttu-id="5a04d-118">Aşağıdaki tabloda ve için desteklenen birleşimler gösterilmektedir `clsid` `riid` .</span><span class="sxs-lookup"><span data-stu-id="5a04d-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="5a04d-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="5a04d-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="5a04d-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="5a04d-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="5a04d-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="5a04d-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="5a04d-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="5a04d-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="5a04d-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="5a04d-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="5a04d-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="5a04d-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="5a04d-125">Aşağıdaki kod, `CLRCreateInstance` üç arabirimi de almak için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5a04d-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5a04d-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a04d-126">Requirements</span></span>  
 <span data-ttu-id="5a04d-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a04d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a04d-128">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="5a04d-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5a04d-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5a04d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a04d-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a04d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a04d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a04d-131">See also</span></span>

- [<span data-ttu-id="5a04d-132">Barındırma</span><span class="sxs-lookup"><span data-stu-id="5a04d-132">Hosting</span></span>](index.md)
