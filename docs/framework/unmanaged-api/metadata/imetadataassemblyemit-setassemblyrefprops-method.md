---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: e28659f3c6912489775dd09951610f19e4400942
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672757"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="90fc3-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90fc3-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>

<span data-ttu-id="90fc3-103">Belirtilen `AssemblyRef` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="90fc3-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90fc3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="90fc3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90fc3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="90fc3-105">Parameters</span></span>  

 `ar`  
 <span data-ttu-id="90fc3-106">'ndaki `AssemblyRef` Değiştirilecek meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="90fc3-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="90fc3-107">'ndaki Başvurulan derlemenin yayımcısının ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="90fc3-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="90fc3-108">'ndaki Bayt cinsinden boyut `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="90fc3-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="90fc3-109">'ndaki Derlemenin insanların okunabilir metin adı.</span><span class="sxs-lookup"><span data-stu-id="90fc3-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="90fc3-110">'ndaki Derleme için sürüm, platform ve yerel ayar bilgilerini içeren bir ASSEMBLYMETADATA örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="90fc3-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="90fc3-111">'ndaki Derlemeyle ilişkili karma verileri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="90fc3-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="90fc3-112">'ndaki Bayt cinsinden boyut `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="90fc3-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="90fc3-113">'ndaki Başvurulan derlemenin özniteliklerini belirten, [AssemblyRefFlags](assemblyrefflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="90fc3-113">[in] A bitwise combination of [AssemblyRefFlags](assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90fc3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90fc3-114">Remarks</span></span>  

 <span data-ttu-id="90fc3-115">`AssemblyRef`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="90fc3-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90fc3-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90fc3-116">Requirements</span></span>  

 <span data-ttu-id="90fc3-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90fc3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90fc3-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="90fc3-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90fc3-119">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="90fc3-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90fc3-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90fc3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90fc3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90fc3-121">See also</span></span>

- [<span data-ttu-id="90fc3-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90fc3-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
