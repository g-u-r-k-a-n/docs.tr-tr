---
title: IMetaDataDispenserEx::FindAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
ms.openlocfilehash: 50aebb09924b93a622e5b7d84e65e41ee91f6018
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006200"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="182c4-102">IMetaDataDispenserEx::FindAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="182c4-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="182c4-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="182c4-103">This method is not implemented.</span></span> <span data-ttu-id="182c4-104">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="182c4-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182c4-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="182c4-105">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="182c4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="182c4-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="182c4-107">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="182c4-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="182c4-108">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="182c4-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="182c4-109">'ndaki Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="182c4-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="182c4-110">'ndaki Bulunan bütünleştirilmiş kod.</span><span class="sxs-lookup"><span data-stu-id="182c4-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="182c4-111">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="182c4-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="182c4-112">'ndaki Bayt cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="182c4-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="182c4-113">dışı Aslında ' de döndürülen karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="182c4-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="182c4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="182c4-114">Requirements</span></span>  
 <span data-ttu-id="182c4-115">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="182c4-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="182c4-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="182c4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="182c4-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="182c4-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="182c4-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="182c4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182c4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="182c4-119">See also</span></span>

- [<span data-ttu-id="182c4-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="182c4-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="182c4-121">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="182c4-121">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
