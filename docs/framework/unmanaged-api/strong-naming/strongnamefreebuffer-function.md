---
description: 'Daha fazla bilgi edinin: StrongNameFreeBuffer Işlevi'
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
ms.openlocfilehash: fa1b1d7710a981c5284ee79d551cbf51ede285db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736459"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="551d1-103">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="551d1-103">StrongNameFreeBuffer Function</span></span>

<span data-ttu-id="551d1-104">[StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)gibi bir tanımlayıcı ad işlevine daha önceki bir çağrı ile ayrılmış belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="551d1-104">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="551d1-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="551d1-105">This function has been deprecated.</span></span> <span data-ttu-id="551d1-106">Bunun yerine [ICLRStrongName:: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="551d1-106">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="551d1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="551d1-107">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="551d1-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="551d1-108">Parameters</span></span>  

 `pbMemory`  
 <span data-ttu-id="551d1-109">'ndaki Boşaltılacak belleğin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="551d1-109">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="551d1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="551d1-110">Requirements</span></span>  

 <span data-ttu-id="551d1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="551d1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="551d1-112">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="551d1-112">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="551d1-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="551d1-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="551d1-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="551d1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="551d1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="551d1-115">See also</span></span>

- [<span data-ttu-id="551d1-116">StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="551d1-116">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="551d1-117">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="551d1-117">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
