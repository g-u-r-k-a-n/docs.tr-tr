---
title: IMetaDataImport::GetFieldMarshal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: 35f73135dbeea1c79d15e0a9e9367c5d533487ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676872"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="ee4f3-102">IMetaDataImport::GetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee4f3-102">IMetaDataImport::GetFieldMarshal Method</span></span>

<span data-ttu-id="ee4f3-103">Belirtilen alan meta veri belirteciyle temsil edilen alanın yerel, yönetilmeyen türüne yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee4f3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ee4f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee4f3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee4f3-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="ee4f3-106">'ndaki İçin birlikte çalışma sıralama bilgilerini almak için alanı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="ee4f3-107">dışı Alanın yerel türünün meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="ee4f3-108">dışı Bayt cinsinden boyut `ppvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="ee4f3-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee4f3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee4f3-109">Requirements</span></span>  

 <span data-ttu-id="ee4f3-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee4f3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee4f3-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ee4f3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee4f3-112">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ee4f3-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee4f3-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee4f3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4f3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-114">See also</span></span>

- [<span data-ttu-id="ee4f3-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee4f3-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ee4f3-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee4f3-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
