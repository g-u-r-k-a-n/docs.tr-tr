---
title: GetFileVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: 57b30824c7849127f48d4da61872945366e7141e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733249"
---
# <a name="getfileversion-function"></a><span data-ttu-id="e4e3f-102">GetFileVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="e4e3f-102">GetFileVersion Function</span></span>

<span data-ttu-id="e4e3f-103">Belirtilen arabelleği kullanarak belirtilen dosyanın ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e4e3f-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="e4e3f-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e4e3f-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4e3f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e4e3f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4e3f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4e3f-106">Parameters</span></span>  

 `szFilename`  
 <span data-ttu-id="e4e3f-107">'ndaki İnceedilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="e4e3f-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="e4e3f-108">[in, out] Döndürülen sürüm bilgileri için ayrılan arabellek.</span><span class="sxs-lookup"><span data-stu-id="e4e3f-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e4e3f-109">'ndaki Öğesinin geniş karakterdeki boyutu `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="e4e3f-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e4e3f-110">dışı Döndürülen bayt cinsinden boyutu `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="e4e3f-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4e3f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4e3f-111">Requirements</span></span>  

 <span data-ttu-id="e4e3f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4e3f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4e3f-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4e3f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4e3f-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4e3f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e3f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4e3f-115">See also</span></span>

- [<span data-ttu-id="e4e3f-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e4e3f-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
