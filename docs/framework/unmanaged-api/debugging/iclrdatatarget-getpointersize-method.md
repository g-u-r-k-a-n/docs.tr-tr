---
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
ms.openlocfilehash: 077aa50465d99c9098f26e67b3852feb0d399142
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703531"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="3dc68-102">ICLRDataTarget::GetPointerSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3dc68-102">ICLRDataTarget::GetPointerSize Method</span></span>

<span data-ttu-id="3dc68-103">Hedef işlemin kullandığı işaretçi türünün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="3dc68-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="3dc68-104">Bu yöntem, ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3dc68-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dc68-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3dc68-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dc68-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3dc68-106">Parameters</span></span>  

 `pointerSize`  
 <span data-ttu-id="3dc68-107">dışı Hedef işlemdeki bir işaretçinin boyutunu bayt cinsinden belirten bir tamsayı değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3dc68-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dc68-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dc68-108">Remarks</span></span>  

 <span data-ttu-id="3dc68-109">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3dc68-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dc68-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3dc68-110">Requirements</span></span>  

 <span data-ttu-id="3dc68-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dc68-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dc68-112">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="3dc68-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3dc68-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3dc68-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dc68-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dc68-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc68-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dc68-115">See also</span></span>

- [<span data-ttu-id="3dc68-116">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dc68-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
