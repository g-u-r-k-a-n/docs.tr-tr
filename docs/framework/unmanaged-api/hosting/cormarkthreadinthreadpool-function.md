---
title: CorMarkThreadInThreadPool İşlevi
ms.date: 03/30/2017
api_name:
- CorMarkThreadInThreadPool
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorMarkThreadInThreadPool
helpviewer_keywords:
- CorMarkThreadInThreadPool function [.NET Framework hosting]
ms.assetid: 3f958d41-e82e-4ec3-ae6f-16c7b3b31e3e
topic_type:
- apiref
ms.openlocfilehash: 69508e1ccab2e7aa98f33bf048ccfca5e6f70811
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688022"
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="981f0-102">CorMarkThreadInThreadPool İşlevi</span><span class="sxs-lookup"><span data-stu-id="981f0-102">CorMarkThreadInThreadPool Function</span></span>

<span data-ttu-id="981f0-103">Yönetilen kodun yürütülmesi için şu anda yürütülmekte olan iş parçacığı havuzu iş parçacığını işaretler.</span><span class="sxs-lookup"><span data-stu-id="981f0-103">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="981f0-104">.NET Framework sürüm 2,0 ' den başlayarak, bu işlevin etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="981f0-104">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="981f0-105">Gerekli değildir ve kodınızdan kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="981f0-105">It is not required, and can be removed from your code.</span></span> <span data-ttu-id="981f0-106">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="981f0-106">This function is deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="981f0-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="981f0-107">Syntax</span></span>  
  
```cpp  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="981f0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="981f0-108">Requirements</span></span>  

 <span data-ttu-id="981f0-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="981f0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="981f0-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="981f0-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="981f0-111">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="981f0-111">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="981f0-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="981f0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981f0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="981f0-113">See also</span></span>

- [<span data-ttu-id="981f0-114">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="981f0-114">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
