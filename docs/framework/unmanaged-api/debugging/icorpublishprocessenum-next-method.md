---
description: 'Şu konuda daha fazla bilgi edinin: ICorPublishProcessEnum:: Next yöntemi'
title: ICorPublishProcessEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
ms.openlocfilehash: 14b4f815aff986b23a22ed3d5736c37128d3d7e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790483"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="309f2-103">ICorPublishProcessEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="309f2-103">ICorPublishProcessEnum::Next Method</span></span>

<span data-ttu-id="309f2-104">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen işlem sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="309f2-104">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="309f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="309f2-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="309f2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="309f2-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="309f2-107">'ndaki Alınacak işlem sayısı.</span><span class="sxs-lookup"><span data-stu-id="309f2-107">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="309f2-108">dışı Her biri bir işlemi temsil eden [ICorPublishProcess](icorpublishprocess-interface.md) nesnelerinin dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="309f2-108">[out] A pointer to the array of retrieved [ICorPublishProcess](icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="309f2-109">dışı Gerçekten döndürülen işlem sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="309f2-109">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="309f2-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="309f2-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="309f2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="309f2-111">Requirements</span></span>  

 <span data-ttu-id="309f2-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="309f2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="309f2-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="309f2-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="309f2-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="309f2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="309f2-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="309f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309f2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="309f2-116">See also</span></span>

- [<span data-ttu-id="309f2-117">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="309f2-117">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)
