---
title: ICeeGen::GetString Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: ada126b41f1c634f7d8daa58480406ac26f92377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177902"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="c6d9f-102">ICeeGen::GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6d9f-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="c6d9f-103">Dize belirtilen göreli sanal adreste depolanan alır.</span><span class="sxs-lookup"><span data-stu-id="c6d9f-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="c6d9f-104">Bu yöntem eskidir ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6d9f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6d9f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6d9f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6d9f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6d9f-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="c6d9f-107">[içinde] Döndürülecek dizenin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="c6d9f-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="c6d9f-108">[çıkış] Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c6d9f-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6d9f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6d9f-109">Requirements</span></span>  
 <span data-ttu-id="c6d9f-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6d9f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6d9f-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c6d9f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6d9f-112">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c6d9f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6d9f-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6d9f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d9f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6d9f-114">See also</span></span>

- [<span data-ttu-id="c6d9f-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6d9f-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
