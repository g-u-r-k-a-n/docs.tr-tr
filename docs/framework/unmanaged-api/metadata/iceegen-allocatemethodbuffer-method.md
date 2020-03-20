---
title: ICeeGen::AllocateMethodBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: 38b9ea2ffab439f55f0a6d34d7f42c7669629168
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177917"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="c28ed-102">ICeeGen::AllocateMethodBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c28ed-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="c28ed-103">Bir yöntem için belirtilen boyutta bir arabellek oluşturur ve yöntemin göreli sanal adresini alır.</span><span class="sxs-lookup"><span data-stu-id="c28ed-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="c28ed-104">Bu yöntem eskidir ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c28ed-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28ed-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c28ed-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c28ed-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c28ed-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="c28ed-107">[içinde] Oluşturulacak arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c28ed-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="c28ed-108">[çıkış] Döndürülen arabellek.</span><span class="sxs-lookup"><span data-stu-id="c28ed-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="c28ed-109">[çıkış] Yöntemin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="c28ed-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c28ed-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c28ed-110">Requirements</span></span>  
 <span data-ttu-id="c28ed-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c28ed-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28ed-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c28ed-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c28ed-113">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c28ed-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c28ed-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c28ed-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28ed-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c28ed-115">See also</span></span>

- [<span data-ttu-id="c28ed-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c28ed-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
