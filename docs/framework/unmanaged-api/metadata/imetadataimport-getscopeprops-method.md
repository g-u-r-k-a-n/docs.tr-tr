---
title: IMetaDataImport::GetScopeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 5a89d1406daa9a2416a708b63d88fd9005234015
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729206"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="b2c20-102">IMetaDataImport::GetScopeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="b2c20-102">IMetaDataImport::GetScopeProps Method</span></span>

<span data-ttu-id="b2c20-103">Geçerli meta veri kapsamındaki derleme ya da modülün adını ve isteğe bağlı olarak sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="b2c20-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c20-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b2c20-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2c20-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2c20-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="b2c20-106">dışı Derleme veya modül adı için bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="b2c20-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b2c20-107">'ndaki Öğesinin geniş karakterdeki boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="b2c20-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b2c20-108">dışı İçinde döndürülen geniş karakter sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="b2c20-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="b2c20-109">[Out, isteğe bağlı] Derlemenin veya modülün sürümünü benzersiz bir şekilde tanımlayan GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b2c20-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2c20-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2c20-110">Remarks</span></span>  

 <span data-ttu-id="b2c20-111">Bu özellikleri ayarlamak için [ımetadatayayma:: SetModuleProps](imetadataemit-setmoduleprops-method.md) yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2c20-111">The [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c20-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2c20-112">Requirements</span></span>  

 <span data-ttu-id="b2c20-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c20-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c20-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b2c20-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2c20-115">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b2c20-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2c20-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c20-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c20-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2c20-117">See also</span></span>

- [<span data-ttu-id="b2c20-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2c20-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b2c20-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2c20-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
