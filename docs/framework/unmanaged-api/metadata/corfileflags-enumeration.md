---
description: 'Hakkında daha fazla bilgi edinin: CorFileFlags numaralandırması'
title: CorFileFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
ms.openlocfilehash: 8ffad9bad9c656a10c2c556f5e06f9d510ccb45a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784489"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="a7195-103">CorFileFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a7195-103">CorFileFlags Enumeration</span></span>

<span data-ttu-id="a7195-104">IMetaDataAssemblyEmit çağrısında tanımlanan dosya türünü tanımlayan değerleri içerir [::D efineFile](imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a7195-104">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7195-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a7195-105">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a7195-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a7195-106">Members</span></span>  
  
|<span data-ttu-id="a7195-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a7195-107">Member</span></span>|<span data-ttu-id="a7195-108">Description</span><span class="sxs-lookup"><span data-stu-id="a7195-108">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="a7195-109">Dosyanın bir kaynak dosyası olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7195-109">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="a7195-110">Dosyanın, muhtemelen bir kaynak dosyasında meta veri içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7195-110">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7195-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7195-111">Requirements</span></span>  

 <span data-ttu-id="a7195-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7195-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7195-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a7195-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a7195-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7195-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7195-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7195-115">See also</span></span>

- [<span data-ttu-id="a7195-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="a7195-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
