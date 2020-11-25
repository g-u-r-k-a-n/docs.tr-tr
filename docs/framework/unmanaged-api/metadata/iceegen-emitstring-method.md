---
title: ICeeGen::EmitString Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
ms.openlocfilehash: b9c907868df31da8d995c6a6b86db258d395335d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715452"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="99fe5-102">ICeeGen::EmitString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99fe5-102">ICeeGen::EmitString Method</span></span>

<span data-ttu-id="99fe5-103">Belirtilen dizeyi kod tabanına yayar.</span><span class="sxs-lookup"><span data-stu-id="99fe5-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="99fe5-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="99fe5-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99fe5-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="99fe5-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99fe5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99fe5-106">Parameters</span></span>  

 `lpString`  
 <span data-ttu-id="99fe5-107">'ndaki Yayyapılacak dize.</span><span class="sxs-lookup"><span data-stu-id="99fe5-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="99fe5-108">dışı Yayılan dizenin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="99fe5-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99fe5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99fe5-109">Requirements</span></span>  

 <span data-ttu-id="99fe5-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99fe5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99fe5-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="99fe5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99fe5-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="99fe5-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99fe5-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99fe5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fe5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99fe5-114">See also</span></span>

- [<span data-ttu-id="99fe5-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99fe5-115">ICeeGen Interface</span></span>](iceegen-interface.md)
