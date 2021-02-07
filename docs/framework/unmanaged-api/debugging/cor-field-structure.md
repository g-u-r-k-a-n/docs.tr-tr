---
description: 'Daha fazla bilgi edinin: COR_FIELD yapısı'
title: COR_FIELD Yapısı
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
ms.openlocfilehash: a3e9dcc2a5c3bb2abae42dab4292c1d285df5ad7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747120"
---
# <a name="cor_field-structure"></a><span data-ttu-id="0de64-103">COR_FIELD Yapısı</span><span class="sxs-lookup"><span data-stu-id="0de64-103">COR_FIELD Structure</span></span>

<span data-ttu-id="0de64-104">Bir nesne içindeki bir alan hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0de64-104">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de64-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0de64-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="0de64-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0de64-106">Members</span></span>  
  
|<span data-ttu-id="0de64-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0de64-107">Member</span></span>|<span data-ttu-id="0de64-108">Description</span><span class="sxs-lookup"><span data-stu-id="0de64-108">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="0de64-109">`mdFieldDef`Alan bilgilerini almak için kullanılabilen bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="0de64-109">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="0de64-110">Nesnedeki alan verilerine göre bayt cinsinden fark.</span><span class="sxs-lookup"><span data-stu-id="0de64-110">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="0de64-111">Bu alanın türünü tanımlayan [COR_TYPEID](cor-typeid-structure.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="0de64-111">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="0de64-112">Alanın türünü gösteren bir CorElementType numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="0de64-112">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0de64-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0de64-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0de64-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0de64-114">Requirements</span></span>  

 <span data-ttu-id="0de64-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0de64-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0de64-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0de64-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0de64-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0de64-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0de64-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0de64-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de64-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0de64-119">See also</span></span>

- [<span data-ttu-id="0de64-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="0de64-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0de64-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0de64-121">Debugging</span></span>](index.md)
