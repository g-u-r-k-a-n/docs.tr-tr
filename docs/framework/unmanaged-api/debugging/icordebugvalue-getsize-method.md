---
title: ICorDebugValue::GetSize Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3d6caa02333229bcd49f4c6ccf8b93265181a0b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137091"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="aa424-102">ICorDebugValue::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="aa424-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="aa424-103">Bu "ICorDebugValue" nesnesinin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="aa424-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa424-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa424-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa424-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa424-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="aa424-106">dışı Bu değer nesnesinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="aa424-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa424-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa424-107">Remarks</span></span>  
 <span data-ttu-id="aa424-108">Değerin türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçinin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa424-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="aa424-109">`ICorDebugValue::GetSize` yöntemi 64-bit platformlarda 4 GB 'den büyük nesneler için `COR_E_OVERFLOW` döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa424-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="aa424-110">4 GB 'den büyük nesneler için yerine [ICorDebugValue3:: GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa424-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa424-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa424-111">Requirements</span></span>  
 <span data-ttu-id="aa424-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa424-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa424-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aa424-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa424-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aa424-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa424-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa424-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa424-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa424-116">See also</span></span>

- [<span data-ttu-id="aa424-117">GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aa424-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
