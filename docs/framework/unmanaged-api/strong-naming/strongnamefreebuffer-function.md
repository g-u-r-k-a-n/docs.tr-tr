---
title: StrongNameFreeBuffer İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: d93bda046a79dbdec2195eee48fefc1e5538b2e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732261"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="645bb-102">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="645bb-102">StrongNameFreeBuffer Function</span></span>

<span data-ttu-id="645bb-103">[StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)gibi bir tanımlayıcı ad işlevine daha önceki bir çağrı ile ayrılmış belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="645bb-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="645bb-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="645bb-104">This function has been deprecated.</span></span> <span data-ttu-id="645bb-105">Bunun yerine [ICLRStrongName:: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="645bb-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="645bb-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="645bb-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="645bb-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="645bb-107">Parameters</span></span>  

 `pbMemory`  
 <span data-ttu-id="645bb-108">'ndaki Boşaltılacak belleğin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="645bb-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="645bb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="645bb-109">Requirements</span></span>  

 <span data-ttu-id="645bb-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="645bb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="645bb-111">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="645bb-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="645bb-112">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="645bb-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="645bb-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="645bb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="645bb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="645bb-114">See also</span></span>

- [<span data-ttu-id="645bb-115">StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="645bb-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="645bb-116">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="645bb-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
