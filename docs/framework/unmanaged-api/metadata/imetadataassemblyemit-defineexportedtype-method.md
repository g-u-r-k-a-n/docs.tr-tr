---
title: IMetaDataAssemblyEmit::DefineExportedType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 6b30218cc7373494870ec54a3196857fcc5c08a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689431"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="126b7-102">IMetaDataAssemblyEmit::DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="126b7-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>

<span data-ttu-id="126b7-103">`ExportedType`Belirtilen içe aktarılmış tür için meta veri içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="126b7-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="126b7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="126b7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="126b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="126b7-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="126b7-106">'ndaki Aktarılacak türün adı.</span><span class="sxs-lookup"><span data-stu-id="126b7-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="126b7-107">Ortak dil çalışma zamanının 1,1 sürümü için, verilen türün adı, türü için verilen adla tam olarak eşleşmelidir `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="126b7-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="126b7-108">'ndaki İçe aktarılmış türün nerede uygulandığını belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="126b7-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="126b7-109">Geçerli değerler ve bunlarla ilişkili anlamları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="126b7-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="126b7-110">`mdFile` Bu derleme içindeki farklı bir dosyada tür uygulandı.</span><span class="sxs-lookup"><span data-stu-id="126b7-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="126b7-111">`mdAssemblyRef` Tür, farklı bir derlemede uygulanır.</span><span class="sxs-lookup"><span data-stu-id="126b7-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="126b7-112">`mdExportedTYpe` Tür başka bir tür içinde iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="126b7-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="126b7-113">`mdFileNil` Tür, bildirimle aynı dosyada ve iç içe geçmiş bir tür değil.</span><span class="sxs-lookup"><span data-stu-id="126b7-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="126b7-114">'ndaki Meta veriye aktarılacak türü belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="126b7-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="126b7-115">Bu değer `TypeDef` , türü uygulayan dosyanın tablosuna girilir ve yalnızca söz konusu dosya bu derlemede olduğunda ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="126b7-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="126b7-116">'ndaki İçe aktarılmış tür için özellik ayarlarını tanımlayan [CorTypeAttr](cortypeattr-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="126b7-116">[in] A bitwise combination of [CorTypeAttr](cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="126b7-117">dışı Verilen türü gösteren döndürülen meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="126b7-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="126b7-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="126b7-118">Remarks</span></span>  

 <span data-ttu-id="126b7-119">`ExportedType`Bu derleme tarafından sunulan ve bildirimi içeren bir modülde uygulanan her tür için bir meta veri yapısı tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="126b7-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="126b7-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="126b7-120">Requirements</span></span>  

 <span data-ttu-id="126b7-121">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="126b7-121">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="126b7-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="126b7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="126b7-123">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="126b7-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="126b7-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="126b7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126b7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="126b7-125">See also</span></span>

- [<span data-ttu-id="126b7-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="126b7-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
