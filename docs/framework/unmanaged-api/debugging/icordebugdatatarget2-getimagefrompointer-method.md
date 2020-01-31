---
title: ICorDebugDataTarget2::GetImageFromPointer Yöntemi
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 55c87731399cf1e7a6747720b8bb33de7e01906c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788838"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="411dc-102">ICorDebugDataTarget2::GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="411dc-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="411dc-103">Bu modüldeki bir adresten modül taban adresini ve boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="411dc-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="411dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="411dc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="411dc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="411dc-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="411dc-106">Modül içindeki bir adresi temsil eden [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="411dc-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="411dc-107">dışı Modülün temel adresini temsil eden bir [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="411dc-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="411dc-108">Modül boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="411dc-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="411dc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="411dc-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="411dc-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="411dc-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="411dc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="411dc-111">Requirements</span></span>  
 <span data-ttu-id="411dc-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="411dc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="411dc-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="411dc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="411dc-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="411dc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="411dc-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="411dc-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411dc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="411dc-116">See also</span></span>

- [<span data-ttu-id="411dc-117">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="411dc-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="411dc-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="411dc-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
