---
title: IMetaDataAssemblyEmit::SetExportedTypeProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: fa4f1f57cb8fe1ca81bbad6438a88bb43c48e7bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008085"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="88c26-102">IMetaDataAssemblyEmit::SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88c26-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="88c26-103">Belirtilen `ExportedType` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="88c26-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88c26-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="88c26-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88c26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88c26-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="88c26-106">'ndaki `ExportedType`Değiştirilecek meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="88c26-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="88c26-107">'ndaki `File` `AssemblyRef` `ExportedType` Bu türün nasıl uygulandığını belirten, veya türündeki belirteç.</span><span class="sxs-lookup"><span data-stu-id="88c26-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="88c26-108">'ndaki `TypeDef`Kod dosyasında başvurulan belirteç.</span><span class="sxs-lookup"><span data-stu-id="88c26-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="88c26-109">'ndaki Türün özniteliklerini belirten bir bit düzeyinde değer birleşimi.</span><span class="sxs-lookup"><span data-stu-id="88c26-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88c26-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88c26-110">Remarks</span></span>  
 <span data-ttu-id="88c26-111">`ExportedType`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineExportedType](imetadataassemblyemit-defineexportedtype-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="88c26-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88c26-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88c26-112">Requirements</span></span>  
 <span data-ttu-id="88c26-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88c26-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88c26-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="88c26-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88c26-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="88c26-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88c26-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88c26-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c26-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88c26-117">See also</span></span>

- [<span data-ttu-id="88c26-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88c26-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
