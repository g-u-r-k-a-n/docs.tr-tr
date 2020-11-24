---
title: GetCORVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: e7ef3f300c8cfa0c275d15913e171abe09385eea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681216"
---
# <a name="getcorversion-function"></a><span data-ttu-id="55e04-102">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="55e04-102">GetCORVersion Function</span></span>

<span data-ttu-id="55e04-103">Geçerli işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="55e04-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="55e04-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="55e04-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e04-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="55e04-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="55e04-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55e04-106">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="55e04-107">CLR 'nin şu anda işleme yüklenmiş çalışma zamanının sürümünü belirten bir dize döndürdüğü bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="55e04-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="55e04-108">Döndürülen dize [CorBindToRuntimeEx](corbindtoruntimeex-function.md)öğesine geçirilen dizelerle aynı formu alır, örneğin, "v 1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="55e04-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="55e04-109">Çalışma zamanı işleme henüz yüklenmemişse, işlev, bilgisayarda yüklü olan çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="55e04-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="55e04-110">`WCHAR`İçinde tutulabilecek karakter sayısı `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="55e04-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="55e04-111">Aslında ' de döndürülen karakter sayısına yönelik bir işaretçi `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="55e04-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="55e04-112">`pbuffer`Null işaretçisiyse, çalışma zamanı E_POINTER döndürür.</span><span class="sxs-lookup"><span data-stu-id="55e04-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="55e04-113">Karakter sayısının uzunluğu daha büyükse `pbuffer` , çalışma zamanı ERROR_INSUFFICIENT_BUFFER döndürür.</span><span class="sxs-lookup"><span data-stu-id="55e04-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55e04-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55e04-114">Requirements</span></span>  

 <span data-ttu-id="55e04-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55e04-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55e04-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="55e04-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55e04-117">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="55e04-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55e04-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55e04-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e04-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55e04-119">See also</span></span>

- [<span data-ttu-id="55e04-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="55e04-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
