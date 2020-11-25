---
title: AssemblyFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: 561b4d68a574a2859286fb5f2e2d950518a9d29d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732788"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="e2ca6-102">AssemblyFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e2ca6-102">AssemblyFlags Enumeration</span></span>

<span data-ttu-id="e2ca6-103">Bir derlemenin çalışma zamanı özelliklerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ca6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2ca6-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e2ca6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e2ca6-105">Members</span></span>  
  
|<span data-ttu-id="e2ca6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e2ca6-106">Member</span></span>|<span data-ttu-id="e2ca6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2ca6-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="e2ca6-108">İçe aktarılmış tür tanımlarının derlemeyi oluşturan dosyalar içinde örtük olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="e2ca6-109">.NET Framework sürüm 1,0 ve 1,1 ' de, bu değer her zaman ayarlandığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="e2ca6-110">Kaynak tanımlarının derlemeyi oluşturan dosyalar içinde örtük olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="e2ca6-111">.NET Framework 1,0 ve 1,1 ' de, bu değer her zaman ayarlandığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="e2ca6-112">Derlemenin aynı uygulama etki alanında çalışıyorsa diğer sürümlerle yürütümeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="e2ca6-113">Derlemenin aynı işlemde çalışıyorsa diğer sürümlerle yürütümeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="e2ca6-114">Derlemenin aynı bilgisayarda çalışıyorsa diğer sürümlerle yürütümeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2ca6-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2ca6-115">Remarks</span></span>  

 <span data-ttu-id="e2ca6-116">0x0010 ile 0x0070 (dahil) arasındaki değerler, başvurulan derlemenin yan yana uyumluluk özelliklerini anlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="e2ca6-117">Bu değerlerden hiçbiri ayarlanmamışsa, derlemenin yan yana uyumlu olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2ca6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2ca6-118">Requirements</span></span>  

 <span data-ttu-id="e2ca6-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2ca6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2ca6-120">**Üst bilgi:** MsCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e2ca6-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="e2ca6-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e2ca6-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2ca6-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2ca6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ca6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2ca6-123">See also</span></span>

- [<span data-ttu-id="e2ca6-124">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="e2ca6-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="e2ca6-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2ca6-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
