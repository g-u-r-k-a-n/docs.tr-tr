---
title: ESymbolReadingPolicy Numaralandırması
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 786ff6895383fc18dcfedb26fab344f80f04c1df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138202"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="201b8-102">ESymbolReadingPolicy Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="201b8-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="201b8-103">Program veritabanı (PDB) dosyalarını okumaya yönelik ilkeyi belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="201b8-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="201b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="201b8-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="201b8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="201b8-105">Members</span></span>  
  
|<span data-ttu-id="201b8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="201b8-106">Member</span></span>|<span data-ttu-id="201b8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="201b8-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="201b8-108">Hata ayıklayıcının her zaman PDB dosyalarını okuduğunuzu belirtir.</span><span class="sxs-lookup"><span data-stu-id="201b8-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="201b8-109">Hata ayıklayıcının yalnızca tam güven Derlemeleriyle ilişkili PDB dosyalarını okuması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="201b8-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="201b8-110">Hata ayıklayıcının PDB dosyalarını asla okumayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="201b8-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="201b8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="201b8-111">Remarks</span></span>  
 <span data-ttu-id="201b8-112">`ESymbolReadingPolicy` numaralandırması [ICLRDebugManager:: SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemiyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="201b8-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="201b8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="201b8-113">Requirements</span></span>  
 <span data-ttu-id="201b8-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="201b8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="201b8-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="201b8-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="201b8-116">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="201b8-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="201b8-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="201b8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201b8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="201b8-118">See also</span></span>

- [<span data-ttu-id="201b8-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="201b8-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
