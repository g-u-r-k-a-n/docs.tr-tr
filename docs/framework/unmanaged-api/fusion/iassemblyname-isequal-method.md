---
title: IAssemblyName::IsEqual Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
ms.openlocfilehash: 23bc251053dd27a7c5accb48ab4759ecdb79fe09
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134301"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="00ce2-102">IAssemblyName::IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00ce2-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="00ce2-103">Belirtilen bir [IAssemblyName](iassemblyname-interface.md) nesnesinin, belirtilen karşılaştırma bayraklarını temel alarak bu `IAssemblyName`eşit olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="00ce2-103">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ce2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00ce2-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00ce2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00ce2-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="00ce2-106">'ndaki Bu `IAssemblyName`Karşılaştırılacak `IAssemblyName` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="00ce2-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="00ce2-107">'ndaki Karşılaştırmayı etkileyen [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="00ce2-107">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00ce2-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00ce2-108">Requirements</span></span>  
 <span data-ttu-id="00ce2-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00ce2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00ce2-110">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="00ce2-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="00ce2-111">**Net Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00ce2-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ce2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00ce2-112">See also</span></span>

- [<span data-ttu-id="00ce2-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00ce2-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="00ce2-114">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="00ce2-114">Fusion Enumerations</span></span>](fusion-enumerations.md)
