---
title: COR_PRF_STATIC_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: 2fbcbb6f6115ec48085b533dbf5611054a8235c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696745"
---
# <a name="cor_prf_static_type-enumeration"></a><span data-ttu-id="29d30-102">COR_PRF_STATIC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="29d30-102">COR_PRF_STATIC_TYPE Enumeration</span></span>

<span data-ttu-id="29d30-103">Bir alanın statik olup olmadığını ve bu durumda alan için geçerli olan statik kaliteyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="29d30-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="29d30-104">Bu değerler, alanın birden çok, farklı statik kalitede olduğunu göstermek için bit düzeyinde OR işlemi kullanılarak birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="29d30-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d30-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="29d30-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="29d30-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="29d30-106">Members</span></span>  
  
|<span data-ttu-id="29d30-107">Üye</span><span class="sxs-lookup"><span data-stu-id="29d30-107">Member</span></span>|<span data-ttu-id="29d30-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29d30-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="29d30-109">Alan statik değil.</span><span class="sxs-lookup"><span data-stu-id="29d30-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="29d30-110">Alan, uygulama etki alanı-statik ' dır.</span><span class="sxs-lookup"><span data-stu-id="29d30-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="29d30-111">Alan, Thread-static ' dir.</span><span class="sxs-lookup"><span data-stu-id="29d30-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="29d30-112">Alan, bağlam statiktir.</span><span class="sxs-lookup"><span data-stu-id="29d30-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="29d30-113">Alan göreli sanal adres (RVA)-statik ' dır.</span><span class="sxs-lookup"><span data-stu-id="29d30-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29d30-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29d30-114">Requirements</span></span>  

 <span data-ttu-id="29d30-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29d30-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d30-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="29d30-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29d30-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="29d30-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29d30-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d30-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d30-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29d30-119">See also</span></span>

- [<span data-ttu-id="29d30-120">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="29d30-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
