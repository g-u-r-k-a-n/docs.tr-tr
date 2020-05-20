---
title: CorExitProcess İşlevi
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: a60805e1fd78cb14835957a7afc14fe279cb20fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616573"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="50b78-102">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="50b78-102">CorExitProcess Function</span></span>
<span data-ttu-id="50b78-103">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="50b78-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="50b78-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="50b78-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="50b78-105">Bunun yerine [ICLRMetaHost:: ExitProcess](iclrmetahost-exitprocess-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="50b78-105">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50b78-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="50b78-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50b78-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50b78-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="50b78-108">İşlem çıkış kodunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="50b78-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50b78-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50b78-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50b78-110">.NET Framework 4 ' ten başlayarak, `CorExitProcess` yalnızca eski API 'lerin bağlandığı çalışma zamanına değil, işlemdeki tüm başlatılan çalışma zamanından çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="50b78-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50b78-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50b78-111">Requirements</span></span>  
 <span data-ttu-id="50b78-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50b78-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50b78-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="50b78-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50b78-114">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="50b78-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50b78-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50b78-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b78-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50b78-116">See also</span></span>

- [<span data-ttu-id="50b78-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="50b78-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
