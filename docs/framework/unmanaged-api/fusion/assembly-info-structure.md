---
title: ASSEMBLY_INFO Yapısı
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
ms.openlocfilehash: a43d5e15c02a97ff10a6a5afd439cadebb6b33d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109221"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="71f30-102">ASSEMBLY_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="71f30-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="71f30-103">Genel derleme önbelleğinde kayıtlı olan bir derleme hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="71f30-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71f30-104">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="71f30-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="71f30-105">Members</span></span>  
  
|<span data-ttu-id="71f30-106">Üye</span><span class="sxs-lookup"><span data-stu-id="71f30-106">Member</span></span>|<span data-ttu-id="71f30-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71f30-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="71f30-108">Yapının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="71f30-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="71f30-109">Bu alan gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="71f30-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="71f30-110">Derlemeyle ilgili yükleme ayrıntılarını gösteren Bayraklar.</span><span class="sxs-lookup"><span data-stu-id="71f30-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="71f30-111">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="71f30-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="71f30-112">-Derlemenin yüklendiğini gösteren ASSEMBLYINFO_FLAG_INSTALLED değeri.</span><span class="sxs-lookup"><span data-stu-id="71f30-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="71f30-113">.NET Framework geçerli sürümü her zaman bu değere `dwAssemblyFlags` belirler.</span><span class="sxs-lookup"><span data-stu-id="71f30-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="71f30-114">-Derlemenin bir yükün yerleşik olduğunu gösteren ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri.</span><span class="sxs-lookup"><span data-stu-id="71f30-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="71f30-115">.NET Framework geçerli sürümü bu değere `dwAssemblyFlags` hiçbir şekilde ayarlamamez.</span><span class="sxs-lookup"><span data-stu-id="71f30-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="71f30-116">Derlemenin içerdiği dosyaların kilobayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="71f30-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="71f30-117">Bildirim dosyasının geçerli yolunu tutan bir dize arabelleği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="71f30-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="71f30-118">Yol, null bir karakterle bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="71f30-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="71f30-119">`pszCurrentAssemblyPathBuf` içerdiği null Sonlandırıcı dahil olmak üzere geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="71f30-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71f30-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71f30-120">Requirements</span></span>  
 <span data-ttu-id="71f30-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71f30-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71f30-122">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="71f30-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="71f30-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71f30-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f30-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71f30-124">See also</span></span>

- [<span data-ttu-id="71f30-125">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="71f30-125">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="71f30-126">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="71f30-126">Global Assembly Cache</span></span>](../../app-domains/gac.md)
