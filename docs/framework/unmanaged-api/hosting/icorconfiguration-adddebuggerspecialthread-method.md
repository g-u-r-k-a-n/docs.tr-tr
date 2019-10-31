---
title: ICorConfiguration::AddDebuggerSpecialThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
ms.openlocfilehash: c5d6cfa3826667514eb70f9bb0df118d9ba0d07c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127816"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="3eb27-102">ICorConfiguration::AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3eb27-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="3eb27-103">Hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryolarında durdurulan bir uygulamaya sahip olsa da, belirli bir iş parçacığının yürütmeye devam etmesine izin verilmesi gerektiğini hata ayıklama hizmetlerine bildirir.</span><span class="sxs-lookup"><span data-stu-id="3eb27-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3eb27-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eb27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3eb27-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="3eb27-106">'ndaki Yürütülmeye devam etmesi için izin verilmesi gereken iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3eb27-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eb27-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3eb27-107">Remarks</span></span>  
 <span data-ttu-id="3eb27-108">Belirtilen iş parçacığının yönetilen kodu çalıştırmasına izin verilmez veya çalışma zamanını herhangi bir şekilde giremeyecektir.</span><span class="sxs-lookup"><span data-stu-id="3eb27-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="3eb27-109">Bu tür bir iş parçacığına bir örnek, eski betik hata ayıklayıcılarını desteklemek için işlem içi bir iş parçacığı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3eb27-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eb27-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3eb27-110">Requirements</span></span>  
 <span data-ttu-id="3eb27-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eb27-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eb27-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3eb27-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3eb27-113">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3eb27-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3eb27-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eb27-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb27-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eb27-115">See also</span></span>

- [<span data-ttu-id="3eb27-116">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3eb27-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
