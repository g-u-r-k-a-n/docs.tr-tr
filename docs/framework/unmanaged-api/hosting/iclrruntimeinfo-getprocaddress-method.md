---
title: ICLRRuntimeInfo::GetProcAddress Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: cedda39aeebc62c6bf43f42ae2daf6f6f515fd27
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120269"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="d6c0a-102">ICLRRuntimeInfo::GetProcAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="d6c0a-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="d6c0a-103">Bu arabirimle ilişkili ortak dil çalışma zamanından (CLR) aktarılmış olan belirli bir işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="d6c0a-104">Bu yöntem [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c0a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6c0a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6c0a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6c0a-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="d6c0a-107">'ndaki İçe aktarılmış işlevin adı.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="d6c0a-108">dışı İçe aktarılmış işlevin adresi.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6c0a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d6c0a-109">Return Value</span></span>  
 <span data-ttu-id="d6c0a-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d6c0a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6c0a-111">HRESULT</span></span>|<span data-ttu-id="d6c0a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6c0a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6c0a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6c0a-113">S_OK</span></span>|<span data-ttu-id="d6c0a-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d6c0a-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d6c0a-115">E_POINTER</span></span>|<span data-ttu-id="d6c0a-116">`pszProcName` veya `ppProc` null.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="d6c0a-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="d6c0a-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="d6c0a-118">Belirtilen işlev, dışarıya aktarılmış bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6c0a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6c0a-119">Remarks</span></span>  
 <span data-ttu-id="d6c0a-120">Bu yöntem CLR 'nin yüklenmesine, ancak başlatılmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c0a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6c0a-121">Requirements</span></span>  
 <span data-ttu-id="d6c0a-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6c0a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c0a-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d6c0a-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d6c0a-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d6c0a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6c0a-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c0a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c0a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-126">See also</span></span>

- [<span data-ttu-id="d6c0a-127">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6c0a-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d6c0a-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d6c0a-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d6c0a-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="d6c0a-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
