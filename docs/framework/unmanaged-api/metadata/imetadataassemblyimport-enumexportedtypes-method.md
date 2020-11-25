---
title: IMetaDataAssemblyImport::EnumExportedTypes Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: a8b2377c48331ff9f0e69876c51fb78c7190f694
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708900"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="51342-102">IMetaDataAssemblyImport::EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51342-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>

<span data-ttu-id="51342-103">Geçerli meta veri kapsamındaki derleme bildiriminde başvurulan verilen türleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="51342-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51342-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="51342-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51342-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51342-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="51342-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51342-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="51342-107">Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır `EnumExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="51342-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="51342-108">dışı `mdExportedType` Meta veri belirteçlerinin numaralandırılması.</span><span class="sxs-lookup"><span data-stu-id="51342-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="51342-109">'ndaki `mdExportedType` Diziye yerleştirilebilecek en fazla belirteç sayısı `rExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="51342-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="51342-110">dışı `mdExportedType` Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="51342-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51342-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="51342-111">Return Value</span></span>  
  
|<span data-ttu-id="51342-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51342-112">HRESULT</span></span>|<span data-ttu-id="51342-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51342-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="51342-114">`EnumExportedTypes` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="51342-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="51342-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="51342-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="51342-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="51342-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51342-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51342-117">Requirements</span></span>  

 <span data-ttu-id="51342-118">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51342-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51342-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="51342-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51342-120">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="51342-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51342-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51342-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51342-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51342-122">See also</span></span>

- [<span data-ttu-id="51342-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51342-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
