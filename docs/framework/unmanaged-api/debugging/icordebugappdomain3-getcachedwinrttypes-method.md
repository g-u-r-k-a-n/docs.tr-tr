---
title: ICorDebugAppDomain3::GetCachedWinRTTypes Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
ms.openlocfilehash: e5fd1730bbe5b6f2905691dce41a7f503227534a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179078"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="9eab9-102">ICorDebugAppDomain3::GetCachedWinRTTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="9eab9-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="9eab9-103">Önbelleğe alınmış tüm Windows Runtime türleri için bir sayısallaştırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="9eab9-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eab9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9eab9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eab9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9eab9-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="9eab9-106">[çıkış] Şu anda uygulama etki alanında yüklenen Windows Runtime türlerinin yönetilen gösterimlerini sayısala bilen [bir ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) arabirim nesnesine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9eab9-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eab9-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9eab9-107">Requirements</span></span>  
 <span data-ttu-id="9eab9-108">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="9eab9-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="9eab9-109">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9eab9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eab9-110">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9eab9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eab9-111">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eab9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eab9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9eab9-112">See also</span></span>

- [<span data-ttu-id="9eab9-113">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9eab9-113">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
