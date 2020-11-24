---
title: CorBindToRuntimeByCfg İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: d319382b577844a804c3e4562676491a15de5f63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673793"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="1387b-102">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="1387b-102">CorBindToRuntimeByCfg Function</span></span>

<span data-ttu-id="1387b-103">Bir XML dosyasından okunan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="1387b-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="1387b-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="1387b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1387b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1387b-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1387b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1387b-106">Parameters</span></span>  

 `pCfgStream`  
 <span data-ttu-id="1387b-107">'ndaki `IStream` XML dosyasını okuyan bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1387b-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="1387b-108">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1387b-108">[in] Reserved for future use.</span></span> <span data-ttu-id="1387b-109">Değer olarak 0 (sıfır) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1387b-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="1387b-110">'ndaki CLR 'nin başlangıç davranışını belirten [startup_flags](startup-flags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="1387b-110">[in] A value of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="1387b-111">'ndaki `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass.</span><span class="sxs-lookup"><span data-stu-id="1387b-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="1387b-112">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1387b-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="1387b-113">'ndaki `IID` `ICorRuntimeHost` Ya da `ICLRRuntimeHost` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1387b-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="1387b-114">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1387b-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="1387b-115">dışı Döndürülen arabirimin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1387b-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1387b-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1387b-116">Remarks</span></span>  

 <span data-ttu-id="1387b-117">XML dosyasının biçimi, standart uygulama yapılandırma dosyasından sonra modellenir.</span><span class="sxs-lookup"><span data-stu-id="1387b-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="1387b-118">XML dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosya şeması](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="1387b-118">For more information about XML files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1387b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1387b-119">Requirements</span></span>  

 <span data-ttu-id="1387b-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1387b-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1387b-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1387b-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1387b-122">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1387b-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1387b-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1387b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1387b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1387b-124">See also</span></span>

- [<span data-ttu-id="1387b-125">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="1387b-125">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="1387b-126">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="1387b-126">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="1387b-127">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="1387b-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="1387b-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="1387b-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="1387b-129">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1387b-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="1387b-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1387b-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
