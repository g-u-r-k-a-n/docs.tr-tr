---
title: IManagedObject::GetSerializedBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
ms.openlocfilehash: 159ece09ae0b6a67780639da8aae8c0e4b412bb8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730701"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="1a52b-102">IManagedObject::GetSerializedBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a52b-102">IManagedObject::GetSerializedBuffer Method</span></span>

<span data-ttu-id="1a52b-103">Bu yönetilen nesnenin dize temsilini alır.</span><span class="sxs-lookup"><span data-stu-id="1a52b-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a52b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1a52b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a52b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a52b-105">Parameters</span></span>  

 `pBSTR`  
 <span data-ttu-id="1a52b-106">dışı Serileştirilmiş nesne olan dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1a52b-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a52b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a52b-107">Remarks</span></span>  

 <span data-ttu-id="1a52b-108">`GetSerializedBuffer`Yöntemi, istemciye sıralanabilmesi için nesneyi seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="1a52b-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a52b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a52b-109">Requirements</span></span>  

 <span data-ttu-id="1a52b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a52b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a52b-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a52b-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a52b-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1a52b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a52b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a52b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a52b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a52b-114">See also</span></span>

- [<span data-ttu-id="1a52b-115">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a52b-115">IManagedObject Interface</span></span>](imanagedobject-interface.md)
