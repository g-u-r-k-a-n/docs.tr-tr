---
title: CoreClrDebugProcInfo Yapısı
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
ms.openlocfilehash: 5996393fd1a0504f9c3d3f9f07aa0e3d886a0787
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719703"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="ec6f2-102">CoreClrDebugProcInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="ec6f2-102">CoreClrDebugProcInfo Structure</span></span>

<span data-ttu-id="ec6f2-103">Uzak makinede çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ec6f2-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec6f2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ec6f2-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="ec6f2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ec6f2-105">Members</span></span>  
  
|<span data-ttu-id="ec6f2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ec6f2-106">Member</span></span>|<span data-ttu-id="ec6f2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec6f2-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="ec6f2-108">İşletim sistemi tarafından atanan işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ec6f2-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="ec6f2-109">Hedef makinede çalışan uzaktan hata ayıklama proxy 'si tarafından atanan işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="ec6f2-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="ec6f2-110">Bu tanımlayıcı, işletim sistemi tanımlayıcısından daha az sıklıkta geri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ec6f2-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="ec6f2-111">İşlemin komut satırı.</span><span class="sxs-lookup"><span data-stu-id="ec6f2-111">Command-line of the process.</span></span> <span data-ttu-id="ec6f2-112">Bu üye kesilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec6f2-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec6f2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec6f2-113">Requirements</span></span>  

 <span data-ttu-id="ec6f2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec6f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec6f2-115">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="ec6f2-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ec6f2-116">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="ec6f2-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ec6f2-117">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="ec6f2-117">**.NET Framework Versions:** 3.5 SP1</span></span>
