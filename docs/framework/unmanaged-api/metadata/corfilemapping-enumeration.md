---
title: CorFileMapping Numaralandırması
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 0ed1579886f1682348a136be3391f6bdc2543d26
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007396"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="30546-102">CorFileMapping Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="30546-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="30546-103">[IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md) metoduna yapılan çağrıdan döndürülen dosya eşlemesinin türünü tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="30546-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30546-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30546-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="30546-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="30546-105">Members</span></span>  
  
|<span data-ttu-id="30546-106">Üye</span><span class="sxs-lookup"><span data-stu-id="30546-106">Member</span></span>|<span data-ttu-id="30546-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30546-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="30546-108">Dosya bir veri dosyası olarak eşlendi.</span><span class="sxs-lookup"><span data-stu-id="30546-108">The file is mapped as a data file.</span></span> <span data-ttu-id="30546-109">Yani, `SEC_IMAGE` bayrak Microsoft Win32 işlevine geçirilmedi `CreateFileMapping` .</span><span class="sxs-lookup"><span data-stu-id="30546-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="30546-110">Dosya, bayrağı ile işlevi ya da işlevi kullanılarak yürütme için eşlenir `LoadLibrary` `CreateFileMapping` `SEC_IMAGE` .</span><span class="sxs-lookup"><span data-stu-id="30546-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30546-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30546-111">Requirements</span></span>  
 <span data-ttu-id="30546-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30546-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30546-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="30546-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="30546-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30546-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30546-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30546-115">See also</span></span>

- [<span data-ttu-id="30546-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="30546-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="30546-117">GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30546-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
