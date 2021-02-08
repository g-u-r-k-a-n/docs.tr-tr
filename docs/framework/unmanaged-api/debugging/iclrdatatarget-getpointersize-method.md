---
description: ': ICLRDataTarget:: GetPointerSize yöntemi hakkında daha fazla bilgi edinin'
title: ICLRDataTarget::GetPointerSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
ms.openlocfilehash: 4c6e5ab9b919d1c5d2d6e2267a48d46a11cccc09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801338"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="44112-103">ICLRDataTarget::GetPointerSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44112-103">ICLRDataTarget::GetPointerSize Method</span></span>

<span data-ttu-id="44112-104">Hedef işlemin kullandığı işaretçi türünün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="44112-104">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="44112-105">Bu yöntem, ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="44112-105">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44112-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44112-106">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44112-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44112-107">Parameters</span></span>  

 `pointerSize`  
 <span data-ttu-id="44112-108">dışı Hedef işlemdeki bir işaretçinin boyutunu bayt cinsinden belirten bir tamsayı değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="44112-108">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44112-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44112-109">Remarks</span></span>  

 <span data-ttu-id="44112-110">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="44112-110">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44112-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44112-111">Requirements</span></span>  

 <span data-ttu-id="44112-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44112-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44112-113">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="44112-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="44112-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="44112-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44112-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44112-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44112-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44112-116">See also</span></span>

- [<span data-ttu-id="44112-117">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44112-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
