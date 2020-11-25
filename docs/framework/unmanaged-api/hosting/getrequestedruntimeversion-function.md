---
title: GetRequestedRuntimeVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 6c16b02a5ae323ba80d44937f322810022dfa9f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711643"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="189f4-102">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="189f4-102">GetRequestedRuntimeVersion Function</span></span>

<span data-ttu-id="189f4-103">Belirtilen uygulama tarafından istenen ortak dil çalışma zamanının (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="189f4-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="189f4-104">Bu sürüm yüklü değilse, istenen sürümden önce yüklenen en son sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="189f4-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="189f4-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="189f4-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="189f4-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="189f4-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="189f4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="189f4-107">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="189f4-108">'ndaki Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="189f4-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="189f4-109">dışı Başarılı bir şekilde tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="189f4-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="189f4-110">'ndaki Sürüm arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="189f4-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="189f4-111">dışı Sürüm numarası dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="189f4-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="189f4-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="189f4-112">Return Value</span></span>  

 <span data-ttu-id="189f4-113">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="189f4-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="189f4-114">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="189f4-114">Return code</span></span>|<span data-ttu-id="189f4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="189f4-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="189f4-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="189f4-116">S_OK</span></span>|<span data-ttu-id="189f4-117">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="189f4-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="189f4-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="189f4-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="189f4-119">Sürüm arabelleği, sürüm dizesini depolamak için yeterince büyük değil.</span><span class="sxs-lookup"><span data-stu-id="189f4-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="189f4-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="189f4-120">E_POINTER</span></span>|<span data-ttu-id="189f4-121">`pdwLength` null.</span><span class="sxs-lookup"><span data-stu-id="189f4-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="189f4-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="189f4-122">Requirements</span></span>  

 <span data-ttu-id="189f4-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="189f4-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="189f4-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="189f4-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="189f4-125">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="189f4-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="189f4-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="189f4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="189f4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="189f4-127">See also</span></span>

- [<span data-ttu-id="189f4-128">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="189f4-128">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="189f4-129">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="189f4-129">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="189f4-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="189f4-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
