---
title: ICorDebugAppDomain4::GetObjectForCCW Metodu
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 8b046eb5926bb9aa4738e8fff8e61b0b7c23a3aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088824"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="78ef8-102">ICorDebugAppDomain4::GetObjectForCCW Metodu</span><span class="sxs-lookup"><span data-stu-id="78ef8-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="78ef8-103">COM çağrılabilir sarmalayıcı (CCW) işaretçisinden yönetilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="78ef8-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78ef8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78ef8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78ef8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78ef8-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="78ef8-106">'ndaki COM çağrılabilir sarmalayıcı (CCW) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="78ef8-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="78ef8-107">dışı Verilen CCW işaretçisine karşılık gelen yönetilen nesneyi temsil eden "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="78ef8-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78ef8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78ef8-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78ef8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78ef8-109">Requirements</span></span>  
 <span data-ttu-id="78ef8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78ef8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78ef8-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="78ef8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78ef8-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="78ef8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78ef8-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78ef8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ef8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78ef8-114">See also</span></span>

- [<span data-ttu-id="78ef8-115">ICorDebugAppDomain4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78ef8-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="78ef8-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="78ef8-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
