---
title: _CorExeMain İşlevi
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
ms.openlocfilehash: af1d0e2039024a51341e30bec497c581a0bcacb3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673676"
---
# <a name="_corexemain-function"></a><span data-ttu-id="4df1d-102">_CorExeMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="4df1d-102">_CorExeMain Function</span></span>

<span data-ttu-id="4df1d-103">Ortak dil çalışma zamanını (CLR) başlatır, çalıştırılabilir derlemenin CLR üstbilgisindeki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="4df1d-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df1d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4df1d-104">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4df1d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4df1d-105">Remarks</span></span>  

 <span data-ttu-id="4df1d-106">Bu işlev, yönetilen yürütülebilir derlemelerden oluşturulan süreçlerdeki yükleyici tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="4df1d-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="4df1d-107">DLL derlemeleri için yükleyici bunun yerine [_CorDllMain](cordllmain-function.md) işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="4df1d-107">For DLL assemblies, the loader calls the [_CorDllMain](cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="4df1d-108">İşletim sistemi yükleyicisi, görüntü dosyasında belirtilen giriş noktası ne olursa olsun bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="4df1d-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="4df1d-109">Windows 98, Windows ME, Windows NT ve Windows 2000 ' de, `_CorExeMain` işlev, işletim sistemi yükleyicisinde bir düzeltme aracılığıyla dolaylı olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4df1d-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="4df1d-110">Tüm Windows sürümlerinde, işletim sistemi yükleyicisi tarafından doğrudan çağırılır.</span><span class="sxs-lookup"><span data-stu-id="4df1d-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="4df1d-111">Daha fazla bilgi için, [_CorValidateImage](corvalidateimage-function.md) konusunun açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4df1d-111">For additional information, see the Remarks section in the [_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df1d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4df1d-112">Requirements</span></span>  

 <span data-ttu-id="4df1d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4df1d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df1d-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4df1d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4df1d-115">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4df1d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4df1d-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4df1d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df1d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4df1d-117">See also</span></span>

- [<span data-ttu-id="4df1d-118">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4df1d-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
