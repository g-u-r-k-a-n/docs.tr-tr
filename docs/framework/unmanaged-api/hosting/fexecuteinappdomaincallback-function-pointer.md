---
title: FExecuteInAppDomainCallback İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
ms.openlocfilehash: 8b9c6bb41b7438b9764ac2a8a7fc1677bc08557a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733691"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="c53eb-102">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="c53eb-102">FExecuteInAppDomainCallback Function Pointer</span></span>

<span data-ttu-id="c53eb-103">Yönetilen kodu yürütmek için ortak dil çalışma zamanı (CLR) tarafından çağrılan bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="c53eb-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="c53eb-104">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c53eb-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c53eb-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c53eb-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c53eb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c53eb-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="c53eb-107">'ndaki Yürütülebilecek yönetilen kodu içeren, bir veya daha fazla arayana ayrılan belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c53eb-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="c53eb-108">Bu belleğin ayrılması ve ömrü, çağıran tarafından denetlenir (yani, CLR).</span><span class="sxs-lookup"><span data-stu-id="c53eb-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="c53eb-109">Bu, CLR tarafından yönetilen yığın belleği değildir.</span><span class="sxs-lookup"><span data-stu-id="c53eb-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c53eb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c53eb-110">Requirements</span></span>  

 <span data-ttu-id="c53eb-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c53eb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c53eb-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c53eb-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c53eb-113">**Kitaplık:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="c53eb-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="c53eb-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c53eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c53eb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c53eb-115">See also</span></span>

- [<span data-ttu-id="c53eb-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c53eb-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
