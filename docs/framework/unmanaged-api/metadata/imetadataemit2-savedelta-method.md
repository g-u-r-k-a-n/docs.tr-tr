---
title: IMetaDataEmit2::SaveDelta Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: 0ebcab7a759b64bfbb254df1c1aa339cde77d054
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175570"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="8f4ab-102">IMetaDataEmit2::SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f4ab-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="8f4ab-103">Değişiklikleri geçerli düzenlenen ve devam eden oturumdan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8f4ab-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f4ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f4ab-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f4ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f4ab-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="8f4ab-106">[içinde] Değişiklikleri kaydetmek için altında dosya adı.</span><span class="sxs-lookup"><span data-stu-id="8f4ab-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="8f4ab-107">[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="8f4ab-107">[in] Reserved.</span></span> <span data-ttu-id="8f4ab-108">Sıfır olmalı.</span><span class="sxs-lookup"><span data-stu-id="8f4ab-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f4ab-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f4ab-109">Requirements</span></span>  
 <span data-ttu-id="8f4ab-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f4ab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f4ab-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8f4ab-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f4ab-112">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8f4ab-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f4ab-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f4ab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f4ab-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f4ab-114">See also</span></span>

- [<span data-ttu-id="8f4ab-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f4ab-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="8f4ab-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f4ab-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
