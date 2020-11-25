---
title: CorAttributeTargets Numaralandırması
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: fbe721bad56ec2be434039f00e741ad9a177815f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718976"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="1738a-102">CorAttributeTargets Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1738a-102">CorAttributeTargets Enumeration</span></span>

<span data-ttu-id="1738a-103">Bir öznitelik uygulamak için geçerli olduğu uygulama öğelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1738a-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1738a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1738a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a><span data-ttu-id="1738a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1738a-105">Members</span></span>  
  
|<span data-ttu-id="1738a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1738a-106">Member</span></span>|<span data-ttu-id="1738a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1738a-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="1738a-108">Öznitelik, bir derlemeye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="1738a-109">Öznitelik, taşınabilir bir çalıştırılabilir (. dll veya. exe) modülüne uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="1738a-110">Öznitelik, bir sınıfa uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="1738a-111">Öznitelik bir yapıya uygulanabilir; diğer bir deyişle, bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="1738a-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="1738a-112">Öznitelik, bir numaralandırmaya uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="1738a-113">Öznitelik, bir oluşturucuya uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="1738a-114">Öznitelik, bir yönteme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="1738a-115">Öznitelik, bir özelliğe uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="1738a-116">Öznitelik, bir alana uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="1738a-117">Öznitelik, bir olaya uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="1738a-118">Öznitelik, bir arabirime uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="1738a-119">Öznitelik, bir parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="1738a-120">Öznitelik, bir temsilciye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="1738a-121">Öznitelik, genel parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="1738a-122">Özniteliği herhangi bir uygulama öğesine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="1738a-123">Öznitelik, bir sınıfın üyesine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1738a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1738a-124">Remarks</span></span>  

 <span data-ttu-id="1738a-125">`CorAttributeTargets`Sabit listesi değerleri, tercih edilen birleşimi almak için bit DÜZEYINDE veya işlemle birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1738a-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="1738a-126">`CorAttributeTargets`Yönetilen numaralandırmayı paraleller <xref:System.AttributeTargets?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1738a-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1738a-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1738a-127">Requirements</span></span>  

 <span data-ttu-id="1738a-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1738a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1738a-129">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="1738a-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1738a-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1738a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1738a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1738a-131">See also</span></span>

- [<span data-ttu-id="1738a-132">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="1738a-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
