---
title: LoadLibraryShim İşlevi
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
ms.openlocfilehash: 11bb220068e978dc130701e3b28ab3f421be7337
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937648"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="764b5-102">LoadLibraryShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="764b5-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="764b5-103">Yeniden dağıtılabilir .NET Framework paketinde bulunan bir DLL 'nin belirtilen sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="764b5-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="764b5-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="764b5-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="764b5-105">Bunun yerine [ICLRRuntimeInfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="764b5-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="764b5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="764b5-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="764b5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="764b5-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="764b5-108">'ndaki .NET Framework kitaplığından yüklenecek DLL 'nin adını temsil eden sıfır ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="764b5-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="764b5-109">'ndaki Yüklenecek DLL sürümünü temsil eden sıfır ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="764b5-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="764b5-110">`szVersion` null ise, yükleme için seçilen sürüm, belirtilen DLL 'nin sürüm 4 ' ten küçük olan en son sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="764b5-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="764b5-111">Diğer bir deyişle, `szVersion` null olduğunda ve sürüm 4 ' ten küçük bir sürüm yüklü değilse DLL yüklenemediğinde, sürüm 4 ' ten büyük veya bundan büyük tüm sürümler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="764b5-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="764b5-112">Bu, .NET Framework 4 yüklemesinin önceden var olan uygulamaları veya bileşenleri etkilememesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="764b5-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="764b5-113">CLR ekibi bloguna [-proc sxs ve geçiş hızlı başlangıç](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) girdisine bakın.</span><span class="sxs-lookup"><span data-stu-id="764b5-113">See the entry [In-Proc SxS and Migration Quick Start](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="764b5-114">Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="764b5-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="764b5-115">dışı Modülün tanıtıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="764b5-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="764b5-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="764b5-116">Return Value</span></span>  
 <span data-ttu-id="764b5-117">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="764b5-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="764b5-118">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="764b5-118">Return code</span></span>|<span data-ttu-id="764b5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="764b5-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="764b5-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="764b5-120">S_OK</span></span>|<span data-ttu-id="764b5-121">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="764b5-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="764b5-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="764b5-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="764b5-123">`szDllName` yüklemek için ortak dil çalışma zamanının (CLR) yüklenmesi gerekir ve CLR 'nin gerekli sürümü yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="764b5-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="764b5-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="764b5-124">Remarks</span></span>  
 <span data-ttu-id="764b5-125">Bu işlev, .NET Framework yeniden dağıtılabilir pakette bulunan dll 'Leri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="764b5-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="764b5-126">Kullanıcı tarafından oluşturulan dll 'Leri yüklemez.</span><span class="sxs-lookup"><span data-stu-id="764b5-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="764b5-127">.NET Framework sürüm 2,0 ' den başlayarak Fusion. dll ' yi yüklemek CLR 'nin yüklenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="764b5-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="764b5-128">Bunun nedeni, Fusion. dll ' deki işlevlerin artık uygulamaları çalışma zamanı tarafından sağlanışları olan sarmalayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="764b5-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="764b5-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="764b5-129">Requirements</span></span>  
 <span data-ttu-id="764b5-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="764b5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="764b5-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="764b5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="764b5-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="764b5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764b5-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="764b5-133">See also</span></span>

- [<span data-ttu-id="764b5-134">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="764b5-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
