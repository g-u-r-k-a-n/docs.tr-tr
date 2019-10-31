---
title: GetHistoryFileDirectory İşlevi
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
ms.openlocfilehash: 1aabfad14ee2eb35916bbf115631602276cd1fc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109887"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="e50aa-102">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="e50aa-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="e50aa-103">Uygulama geçmişi dizininin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="e50aa-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e50aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e50aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e50aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e50aa-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="e50aa-106">dışı Uygulama geçmişi dizininin yolunu tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="e50aa-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="e50aa-107">[in, out] Arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e50aa-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e50aa-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e50aa-108">Return Value</span></span>  
 <span data-ttu-id="e50aa-109">Bu yöntem, aşağıdaki değerlere ek olarak WinError. h dosyasında tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e50aa-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="e50aa-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="e50aa-110">Return code</span></span>|<span data-ttu-id="e50aa-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e50aa-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e50aa-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e50aa-112">S_OK</span></span>|<span data-ttu-id="e50aa-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e50aa-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="e50aa-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e50aa-114">E_INVALIDARG</span></span>|<span data-ttu-id="e50aa-115">`wzDir` veya `pdwSize` null ya da sürüm dizesi yanlış.</span><span class="sxs-lookup"><span data-stu-id="e50aa-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e50aa-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e50aa-116">Remarks</span></span>  
 <span data-ttu-id="e50aa-117">Başarıyla tamamlandığında `pdwSize` bağımsız değişkeni yol dizesinin uzunluğuna ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e50aa-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e50aa-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e50aa-118">Requirements</span></span>  
 <span data-ttu-id="e50aa-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e50aa-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e50aa-120">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e50aa-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e50aa-121">**Kitaplık:** Fusion. dll ve mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="e50aa-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="e50aa-122">.NET Framework doğru sürümünü hedefliyorsanız emin olmak için mscorwks. dll yerine Fusion. dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="e50aa-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="e50aa-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e50aa-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e50aa-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e50aa-124">See also</span></span>

- [<span data-ttu-id="e50aa-125">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="e50aa-125">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="e50aa-126">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="e50aa-126">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="e50aa-127">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e50aa-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
