---
title: IMetaDataConverter::GetMetaDataFromTypeLib Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: 6391e819d53c3ed8f0d596b15c4a2bb268f72fd5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436278"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="e2b0d-102">IMetaDataConverter::GetMetaDataFromTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2b0d-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="e2b0d-103">Belirtilen `ITypeLib` örneğiyle temsil edilen tür kitaplığının meta veri imzasını temsil eden bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e2b0d-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2b0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2b0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2b0d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2b0d-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="e2b0d-106">'ndaki Tür kitaplığını temsil eden `ITypeLib` nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2b0d-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="e2b0d-107">dışı Meta veri imzasını temsil eden `IMetaDataImport` örneğinin adresini alan bir konum işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e2b0d-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2b0d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2b0d-108">Requirements</span></span>  
 <span data-ttu-id="e2b0d-109">**Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2b0d-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2b0d-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e2b0d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2b0d-111">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e2b0d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2b0d-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2b0d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b0d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2b0d-113">See also</span></span>

- [<span data-ttu-id="e2b0d-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2b0d-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e2b0d-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2b0d-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
