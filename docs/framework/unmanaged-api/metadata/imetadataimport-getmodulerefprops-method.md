---
title: IMetaDataImport::GetModuleRefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: 606a3f2cfba05b014960842c5db77149f449193d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733133"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="27804-102">IMetaDataImport::GetModuleRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27804-102">IMetaDataImport::GetModuleRefProps Method</span></span>

<span data-ttu-id="27804-103">Belirtilen meta veri belirtecinin başvurduğu modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="27804-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27804-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="27804-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27804-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27804-105">Parameters</span></span>  

 `mur`  
 <span data-ttu-id="27804-106">'ndaki Meta veri bilgilerini almak için modüle başvuruda bulunan ModuleRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="27804-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="27804-107">dışı Modül adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="27804-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="27804-108">'ndaki `szName` Geniş karakter olarak istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="27804-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="27804-109">dışı `szName` Geniş karakter olarak döndürülen boyutu.</span><span class="sxs-lookup"><span data-stu-id="27804-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27804-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27804-110">Requirements</span></span>  

 <span data-ttu-id="27804-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27804-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27804-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="27804-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27804-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="27804-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27804-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27804-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27804-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27804-115">See also</span></span>

- [<span data-ttu-id="27804-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27804-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="27804-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27804-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
