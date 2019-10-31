---
title: CoUninitializeCor İşlevi
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
ms.openlocfilehash: eddc2f29da0efd9e56df710203b1d7621ffc27a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136865"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="5f919-102">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="5f919-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="5f919-103">`CoUninitializeCor` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="5f919-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f919-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f919-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="5f919-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f919-105">Remarks</span></span>  
 <span data-ttu-id="5f919-106">Ortak dil çalışma zamanı bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="5f919-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="5f919-107">Çalışma zamanını çalışan bir işlemden tamamen kaldırmak için bu işlemi kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f919-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f919-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f919-108">See also</span></span>

- [<span data-ttu-id="5f919-109">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5f919-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
