---
title: ICorDebugAppDomain3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
ms.openlocfilehash: 644457edbf5035f6d946e1c83ff0053fb118288e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698240"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="3f983-102">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f983-102">ICorDebugAppDomain3 Interface</span></span>

<span data-ttu-id="3f983-103">Bir uygulama etki alanında yüklü olan Windows Çalışma Zamanı türlerinin yönetilen temsilleri hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f983-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="3f983-104">Bu arabirim, ICorDebugAppDomain ve ICorDebugAppDomain2 arabirimlerinin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="3f983-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f983-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3f983-105">Methods</span></span>  
  
|<span data-ttu-id="3f983-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3f983-106">Method</span></span>|<span data-ttu-id="3f983-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f983-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f983-108">ICorDebugAppDomain3:: Getcachedwınrttypes</span><span class="sxs-lookup"><span data-stu-id="3f983-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="3f983-109">Tüm önbelleğe alınmış Windows Çalışma Zamanı türleri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="3f983-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="3f983-110">ICorDebugAppDomain3:: Getcachedwinrttypesforiıds</span><span class="sxs-lookup"><span data-stu-id="3f983-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="3f983-111">Bir uygulama etki alanındaki önbelleğe alınmış Windows Çalışma Zamanı türleri için kendi arabirim tanımlayıcılarına göre bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="3f983-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f983-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f983-112">Remarks</span></span>  

 <span data-ttu-id="3f983-113">Bu arabirim bir hata ayıklayıcı tarafından, bir işlev değerlendirme çağrısıyla birlikte kullanılmak üzere tasarlanmıştır `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)` .</span><span class="sxs-lookup"><span data-stu-id="3f983-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="3f983-114">Yöntemi bir Windows Çalışma Zamanı sunucusu nesnesi tarafından desteklenen arabirim tanımlayıcılarını aldığında, hata ayıklayıcı bu arayüzlere karşılık gelen yönetilen türlerle eşlemek için bu arabirimde tanımlanan yöntemleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3f983-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="3f983-115">Bu arabirimin bir örneğini almak için `QueryInterface` ICorDebugAppDomain veya ICorDebugAppDomain2 arabiriminin bir örneği üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3f983-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f983-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="3f983-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f983-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f983-117">Requirements</span></span>  

 <span data-ttu-id="3f983-118">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="3f983-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="3f983-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f983-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f983-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f983-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f983-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f983-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f983-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f983-122">See also</span></span>

- [<span data-ttu-id="3f983-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3f983-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
