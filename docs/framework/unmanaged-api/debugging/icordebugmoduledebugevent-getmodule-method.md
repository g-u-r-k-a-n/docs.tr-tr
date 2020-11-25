---
title: 'Icordebugmoduledebuggevent:: GetModule yöntemi'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: ec23cda02ff689a3365fe96fb5280054a9795caa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709511"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="c3b5c-102">Icordebugmoduledebuggevent:: GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3b5c-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>

<span data-ttu-id="c3b5c-103">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="c3b5c-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b5c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c3b5c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3b5c-105">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="c3b5c-106">dışı Yeni yüklenen veya kaldırılan birleştirilmiş modülü temsil eden ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3b5c-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3b5c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3b5c-107">Remarks</span></span>  

 <span data-ttu-id="c3b5c-108">Modülün yüklenip yüklenmediğini veya bellekten kaldırılmadığını anlamak için [GetEventKind](icordebugdebugevent-geteventkind-method.md) metodunu çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3b5c-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3b5c-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3b5c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b5c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3b5c-110">Requirements</span></span>  

 <span data-ttu-id="c3b5c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3b5c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3b5c-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3b5c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3b5c-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c3b5c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3b5c-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b5c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b5c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3b5c-115">See also</span></span>

- [<span data-ttu-id="c3b5c-116">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3b5c-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="c3b5c-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c3b5c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
