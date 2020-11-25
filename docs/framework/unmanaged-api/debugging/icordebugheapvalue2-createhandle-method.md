---
title: ICorDebugHeapValue2::CreateHandle Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: 278120c6e1bc87a061a3f81f71bdb7b89cd421be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726567"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="aeeca-102">ICorDebugHeapValue2::CreateHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeeca-102">ICorDebugHeapValue2::CreateHandle Method</span></span>

<span data-ttu-id="aeeca-103">Bu ICorDebugHeapValue2 nesnesi tarafından temsil edilen yığın değeri için belirtilen türden bir tanıtıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aeeca-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeeca-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aeeca-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aeeca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aeeca-105">Parameters</span></span>  

 `type`  
 <span data-ttu-id="aeeca-106">'ndaki Oluşturulacak tanıtıcının türünü belirten Cordebugghandlitype numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="aeeca-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="aeeca-107">dışı Bu yığın değeri için yeni tanıtıcıyı temsil eden bir ıcorıbu Ghandtavalue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aeeca-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeeca-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeeca-108">Remarks</span></span>  

 <span data-ttu-id="aeeca-109">Tanıtıcı, yığın değeriyle ilişkili uygulama etki alanında oluşturulur ve uygulama etki alanı kaldırıldığında geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="aeeca-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="aeeca-110">Aynı yığın değeri için bu işleve birden çok çağrı birden çok tanıtıcı oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="aeeca-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="aeeca-111">Tutamaçlar çöp toplayıcısının performansını etkilediği için, hata ayıklayıcı kendisini her seferinde etkin olan görece küçük tanıtıcılara (yaklaşık 256) sınıralmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aeeca-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeeca-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeeca-112">Requirements</span></span>  

 <span data-ttu-id="aeeca-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeeca-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeeca-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aeeca-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeeca-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aeeca-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeeca-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeeca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
