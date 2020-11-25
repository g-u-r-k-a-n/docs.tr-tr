---
title: ICorDebugGuidToTypeEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: 149c5b09639c8809e736ade09566e7b1b530e3eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705728"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="4e43f-102">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e43f-102">ICorDebugGuidToTypeEnum Interface</span></span>

<span data-ttu-id="4e43f-103">ICorDebugType örnekleri tarafından temsil edilen bir GUID kümesi ve bunlara karşılık gelen türleri arasındaki eşlemeyi tanımlayan bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e43f-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="4e43f-104">Bu arabirim, ıcorıcertificate Genum arabiriminden gelen yöntemleri devralır.</span><span class="sxs-lookup"><span data-stu-id="4e43f-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e43f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4e43f-105">Methods</span></span>  
  
|<span data-ttu-id="4e43f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4e43f-106">Method</span></span>|<span data-ttu-id="4e43f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e43f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e43f-108">ICorDebugGuidToTypeEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="4e43f-108">ICorDebugGuidToTypeEnum::Next</span></span>](icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="4e43f-109">GUID 'Leri tür bilgilerine eşleyen, belirtilen [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4e43f-109">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e43f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e43f-110">Remarks</span></span>  

 <span data-ttu-id="4e43f-111">Bir `ICorDebugGuidToTypeEnum` arabirim nesnesi, [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi çağırarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="4e43f-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="4e43f-112">Bir hata ayıklayıcı, [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) yöntemine yapılan çağrı için kullanılan uygulama etki alanında yüklü Windows çalışma zamanı türlerinin yönetilen gösterimlerinden eşlemelerini temsil eden [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) nesnelerini almak için bu arabirimin [sonraki](icordebugguidtotypeenum-next-method.md) metodunu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="4e43f-112">A debugger can call this interface's [Next](icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e43f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e43f-113">Requirements</span></span>  

 <span data-ttu-id="4e43f-114">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="4e43f-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="4e43f-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4e43f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e43f-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4e43f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e43f-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e43f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e43f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e43f-118">See also</span></span>

- [<span data-ttu-id="4e43f-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4e43f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
