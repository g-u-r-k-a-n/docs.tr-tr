---
title: COR_TYPE_LAYOUT Yapısı
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
ms.openlocfilehash: f33c8f5cf218979404063342d9b1cc5123839f83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726333"
---
# <a name="cor_type_layout-structure"></a><span data-ttu-id="347d1-102">COR_TYPE_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="347d1-102">COR_TYPE_LAYOUT Structure</span></span>

<span data-ttu-id="347d1-103">Bellekteki bir nesnenin düzeni hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="347d1-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="347d1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="347d1-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="347d1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="347d1-105">Members</span></span>  
  
|<span data-ttu-id="347d1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="347d1-106">Member</span></span>|<span data-ttu-id="347d1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="347d1-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="347d1-108">Bu türe üst türün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="347d1-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="347d1-109">Bu, tür kimliği öğesine karşılık geliyorsa, NULL tür kimliği (token1 = 0, token2 = 0) olacaktır <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="347d1-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="347d1-110">Bu türdeki bir nesnenin temel boyutu.</span><span class="sxs-lookup"><span data-stu-id="347d1-110">The base size of an object of this type.</span></span> <span data-ttu-id="347d1-111">Bu, değişken olmayan ölçekli nesnelerin toplam boyutudur.</span><span class="sxs-lookup"><span data-stu-id="347d1-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="347d1-112">Bu türün nesnelerine dahil edilen alan sayısı.</span><span class="sxs-lookup"><span data-stu-id="347d1-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="347d1-113">Bu tür paketlenise, bir nesne alanlarının başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="347d1-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="347d1-114">Bu alan, yalnızca temel öğeler ve yapılar gibi değer türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="347d1-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="347d1-115">Bu türün ait olduğu CorElementType.</span><span class="sxs-lookup"><span data-stu-id="347d1-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="347d1-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="347d1-116">Remarks</span></span>  

 <span data-ttu-id="347d1-117">`numFields`Sıfırdan büyükse, bu türdeki alanlarla ilgili bilgi almak Için [ICorDebugProcess5:: GetTypeFields](icordebugprocess5-gettypefields-method.md) metodunu çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="347d1-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="347d1-118">`type` `ELEMENT_TYPE_STRING` , Veya ise, `ELEMENT_TYPE_ARRAY` `ELEMENT_TYPE_SZARRAY` Bu türün nesnelerinin boyutu değişkendir ve [COR_TYPEID](cor-typeid-structure.md) yapısını [ICorDebugProcess5:: GetArrayLayout](icordebugprocess5-getarraylayout-method.md) metoduna geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="347d1-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="347d1-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="347d1-119">Requirements</span></span>  

 <span data-ttu-id="347d1-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="347d1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="347d1-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="347d1-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="347d1-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="347d1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="347d1-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="347d1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347d1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="347d1-124">See also</span></span>

- [<span data-ttu-id="347d1-125">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="347d1-125">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="347d1-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="347d1-126">Debugging</span></span>](index.md)
