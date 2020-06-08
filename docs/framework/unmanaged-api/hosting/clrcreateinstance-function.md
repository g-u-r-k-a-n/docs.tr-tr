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
ms.openlocfilehash: 4aeacc718632c133550ed8de6649716c5d8b7423
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504465"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="55f91-102">CLRCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="55f91-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="55f91-103">Üç arabirimden birini sunar: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="55f91-103">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f91-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="55f91-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55f91-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55f91-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="55f91-106">'ndaki Üç sınıf tanımlayıcılarından biri: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy veya CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="55f91-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="55f91-107">'ndaki Üç arabirim tanımlayıcılarından biri (IIDS): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy veya IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="55f91-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="55f91-108">dışı Üç arabirimden biri: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="55f91-108">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55f91-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="55f91-109">Return Value</span></span>  
 <span data-ttu-id="55f91-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="55f91-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="55f91-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55f91-111">HRESULT</span></span>|<span data-ttu-id="55f91-112">Description</span><span class="sxs-lookup"><span data-stu-id="55f91-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55f91-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="55f91-113">S_OK</span></span>|<span data-ttu-id="55f91-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="55f91-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="55f91-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="55f91-115">E_POINTER</span></span>|<span data-ttu-id="55f91-116">`ppInterface`null.</span><span class="sxs-lookup"><span data-stu-id="55f91-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55f91-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55f91-117">Remarks</span></span>  
 <span data-ttu-id="55f91-118">Aşağıdaki tabloda ve için desteklenen birleşimler gösterilmektedir `clsid` `riid` .</span><span class="sxs-lookup"><span data-stu-id="55f91-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="55f91-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="55f91-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="55f91-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="55f91-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="55f91-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="55f91-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="55f91-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="55f91-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="55f91-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="55f91-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="55f91-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="55f91-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="55f91-125">Aşağıdaki kod, `CLRCreateInstance` üç arabirimi de almak için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="55f91-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="55f91-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55f91-126">Requirements</span></span>  
 <span data-ttu-id="55f91-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55f91-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55f91-128">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="55f91-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="55f91-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="55f91-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55f91-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f91-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f91-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55f91-131">See also</span></span>

- [<span data-ttu-id="55f91-132">Hosting</span><span class="sxs-lookup"><span data-stu-id="55f91-132">Hosting</span></span>](index.md)
