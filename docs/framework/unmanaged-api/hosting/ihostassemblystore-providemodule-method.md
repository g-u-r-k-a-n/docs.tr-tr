---
title: IHostAssemblyStore::ProvideModule Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
ms.openlocfilehash: 35805d277774e1de03bb7dee1740a2e1305a97c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733002"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="1f083-102">IHostAssemblyStore::ProvideModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f083-102">IHostAssemblyStore::ProvideModule Method</span></span>

<span data-ttu-id="1f083-103">Derleme içindeki bir modülü veya bağlı (gömülü) bir kaynak dosyasını çözer.</span><span class="sxs-lookup"><span data-stu-id="1f083-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f083-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1f083-104">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f083-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f083-105">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="1f083-106">'ndaki İstenen modülün [ModuleBindInfo](modulebindinfo-structure.md) <xref:System.AppDomain> , derlemenin ve modül adının açıklandığı bir ModuleBindInfo örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1f083-106">[in] A pointer to a [ModuleBindInfo](modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="1f083-107">dışı Yüklenen modülün bulunduğu bir benzersiz tanımlayıcı işaretçisi `IStream` .</span><span class="sxs-lookup"><span data-stu-id="1f083-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="1f083-108">dışı `IStream` Yüklenecek Taşınabilir çalıştırılabilir (PE) görüntüsünü içeren bir nesnenin adresine yönelik bir işaretçi veya modül bulunamazsa null.</span><span class="sxs-lookup"><span data-stu-id="1f083-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="1f083-109">dışı `IStream` İstenen modüle yönelik program hata ayıklama (pdb) bilgilerini içeren nesnenin adresine yönelik bir işaretçi veya. pdb dosyası bulunamazsa null.</span><span class="sxs-lookup"><span data-stu-id="1f083-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f083-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f083-110">Return Value</span></span>  
  
|<span data-ttu-id="1f083-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f083-111">HRESULT</span></span>|<span data-ttu-id="1f083-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f083-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f083-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f083-113">S_OK</span></span>|<span data-ttu-id="1f083-114">`ProvideModule` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1f083-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="1f083-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f083-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f083-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1f083-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f083-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f083-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f083-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1f083-118">The call timed out.</span></span>|  
|<span data-ttu-id="1f083-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f083-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f083-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1f083-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f083-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f083-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f083-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1f083-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f083-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f083-123">E_FAIL</span></span>|<span data-ttu-id="1f083-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1f083-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f083-125">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1f083-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f083-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f083-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1f083-127">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="1f083-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="1f083-128">İstenen derleme veya bağlı kaynak bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="1f083-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="1f083-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="1f083-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="1f083-130">`pdwModuleId` , konağın döndürmek istediği tanımlayıcıyı içerecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="1f083-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f083-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f083-131">Remarks</span></span>  

 <span data-ttu-id="1f083-132">İçin döndürülen kimlik değeri `pdwModuleId` ana bilgisayar tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="1f083-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="1f083-133">Tanımlayıcılar bir işlemin ömrü içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f083-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="1f083-134">CLR bu değeri ilişkili akış için benzersiz tanımlayıcı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f083-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="1f083-135">Her bir değeri `pAssemblyId` , [ProvideAssembly](ihostassemblystore-provideassembly-method.md) çağrıları tarafından döndürülen değerlere ve `pdwModuleId` diğer çağrıları tarafından döndürülen değerlere karşı denetler `ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="1f083-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="1f083-136">Konak diğeri için aynı tanımlayıcı değerini döndürürse `IStream` , clr bu akışın içeriğinin zaten eşlenmiş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1f083-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="1f083-137">Bu durumda, CLR yeni bir tane eşlemek yerine görüntünün var olan kopyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="1f083-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="1f083-138">Bu nedenle, tanımlayıcı aynı zamanda öğesinden döndürülen derleme tanımlayıcılarıyla çakışmamalıdır `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="1f083-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f083-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f083-139">Requirements</span></span>  

 <span data-ttu-id="1f083-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f083-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f083-141">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1f083-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f083-142">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1f083-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f083-143">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f083-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f083-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f083-144">See also</span></span>

- [<span data-ttu-id="1f083-145">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f083-145">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1f083-146">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f083-146">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="1f083-147">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f083-147">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
