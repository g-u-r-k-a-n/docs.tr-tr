---
title: OSINFO Yapısı
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 89111bf7eb03d20c2010c7a20c4cd055c2a021e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430725"
---
# <a name="osinfo-structure"></a><span data-ttu-id="f6617-102">OSINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="f6617-102">OSINFO Structure</span></span>
<span data-ttu-id="f6617-103">Bir derleme veya modül için işletim sistemiyle ilgili ayrıntıları içerir.</span><span class="sxs-lookup"><span data-stu-id="f6617-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6617-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6617-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="f6617-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="f6617-105">Members</span></span>  
  
|<span data-ttu-id="f6617-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="f6617-106">Member</span></span>|<span data-ttu-id="f6617-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6617-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="f6617-108">Microsoft Windows platformu işlevi tarafından tanımlanan tanımlayıcı değerlerinden biri `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="f6617-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="f6617-109">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f6617-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="f6617-110">-VER_PLATFORM_WIN32s veya 0x0000, Microsoft Windows 3,1 belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f6617-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="f6617-111">-VER_PLATFORM_WIN32_WINDOWS veya 0x0001, Windows 95, Windows 98 veya bunların alt öğelerinden birine ait işletim sistemlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f6617-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="f6617-112">-VER_PLATFORM_WIN32_NT veya 0x0010, Windows NT veya bundan sonra gelen işletim sistemlerini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f6617-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="f6617-113">İşletim sistemi ana sürümü veya herhangi bir sürümü göstermek için NULL değer.</span><span class="sxs-lookup"><span data-stu-id="f6617-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="f6617-114">İşletim sistemi alt sürümü veya herhangi bir sürümü göstermek için NULL değer.</span><span class="sxs-lookup"><span data-stu-id="f6617-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6617-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6617-115">Remarks</span></span>  
 <span data-ttu-id="f6617-116">`OSINFO`, Microsoft Windows platformu işlevi `GetVersionEx`çağrılarında kullanılan `OSVERSIONINFOEX` yapısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f6617-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="f6617-117">Bu yapı, ASSEMBLYMETADATA yapısı tarafından, işletim sistemi desteğini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6617-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6617-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6617-118">Requirements</span></span>  
 <span data-ttu-id="f6617-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6617-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6617-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f6617-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6617-121">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f6617-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6617-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6617-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6617-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6617-123">See also</span></span>

- [<span data-ttu-id="f6617-124">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="f6617-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="f6617-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6617-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
