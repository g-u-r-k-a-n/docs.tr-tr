---
title: ICorDebugAppDomain4::GetObjectForCCW Metodu
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 10d32314e46aba4f030b294cadc3cbb36e8742f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179043"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="70367-102">ICorDebugAppDomain4::GetObjectForCCW Metodu</span><span class="sxs-lookup"><span data-stu-id="70367-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="70367-103">Yönetilen bir nesneyi COM çağrılabilir sarıcı (CCW) işaretçisinden alır.</span><span class="sxs-lookup"><span data-stu-id="70367-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70367-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70367-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70367-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70367-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="70367-106">[içinde] Com çağrılabilir sarıcı (CCW) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="70367-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="70367-107">[çıkış] Verilen CCW işaretçisine karşılık gelen yönetilen nesneyi temsil eden bir "ICorDebugValue" nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="70367-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70367-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70367-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70367-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70367-109">Requirements</span></span>  
 <span data-ttu-id="70367-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70367-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70367-111">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70367-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70367-112">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70367-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70367-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70367-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70367-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70367-114">See also</span></span>

- [<span data-ttu-id="70367-115">ICorDebugAppDomain4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70367-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="70367-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="70367-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
