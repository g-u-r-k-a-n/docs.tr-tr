---
title: IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 06b81615565a04db7d6cfef4da9b5372a85afd68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450350"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="366d7-102">IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="366d7-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="366d7-103">Derleme bildiriminde tanımlanan `mdAssemblyRef` örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="366d7-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="366d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="366d7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="366d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="366d7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="366d7-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="366d7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="366d7-107">`EnumAssemblyRefs` yöntemi ilk kez çağrıldığında bu null bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="366d7-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="366d7-108">dışı `mdAssemblyRef` meta veri belirteçleri numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="366d7-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="366d7-109">'ndaki `rAssemblyRefs` dizisine yerleştirilebilecek en fazla belirteç sayısı.</span><span class="sxs-lookup"><span data-stu-id="366d7-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="366d7-110">dışı Gerçekten `rAssemblyRefs`yer aldığı belirteçlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="366d7-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="366d7-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="366d7-111">Return Value</span></span>  
  
|<span data-ttu-id="366d7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="366d7-112">HRESULT</span></span>|<span data-ttu-id="366d7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="366d7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="366d7-114">`EnumAssemblyRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="366d7-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="366d7-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="366d7-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="366d7-116">Bu durumda `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="366d7-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="366d7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="366d7-117">Requirements</span></span>  
 <span data-ttu-id="366d7-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="366d7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="366d7-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="366d7-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="366d7-120">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="366d7-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="366d7-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="366d7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366d7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="366d7-122">See also</span></span>

- [<span data-ttu-id="366d7-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="366d7-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
