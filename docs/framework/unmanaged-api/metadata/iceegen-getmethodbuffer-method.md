---
title: ICeeGen::GetMethodBuffer Metodu
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: e9c2dab9f30be6e5eea8f6570b297f8df11b6fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715339"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="0b406-102">ICeeGen::GetMethodBuffer Metodu</span><span class="sxs-lookup"><span data-stu-id="0b406-102">ICeeGen::GetMethodBuffer Method</span></span>

<span data-ttu-id="0b406-103">Belirtilen göreli sanal adreste Yöntem için uygun boyutun bir arabelleğini alır.</span><span class="sxs-lookup"><span data-stu-id="0b406-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="0b406-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b406-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b406-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0b406-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b406-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b406-106">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="0b406-107">'ndaki Arabellek döndürülecek yöntemin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="0b406-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="0b406-108">dışı Döndürülen arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0b406-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b406-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b406-109">Requirements</span></span>  

 <span data-ttu-id="0b406-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b406-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b406-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0b406-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b406-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0b406-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b406-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b406-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b406-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b406-114">See also</span></span>

- [<span data-ttu-id="0b406-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b406-115">ICeeGen Interface</span></span>](iceegen-interface.md)
