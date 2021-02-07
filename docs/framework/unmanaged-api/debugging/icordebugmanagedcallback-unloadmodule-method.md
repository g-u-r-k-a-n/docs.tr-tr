---
description: ': ICorDebugManagedCallback:: UnloadModule yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugManagedCallback::UnloadModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: d8d37b28d7a7d11000c259f1bcde3138634b2498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754062"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a>ICorDebugManagedCallback::UnloadModule Yöntemi

Hata ayıklayıcıya ortak dil çalışma zamanı modülü (DLL) kaldırılmış olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pAppDomain`  
 'ndaki Modülün bulunduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pModule`  
 'ndaki Modülünü temsil eden ICorDebugModule nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Modül Bu çağrıdan sonra kullanılmamalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LoadModule Yöntemi](icordebugmanagedcallback-loadmodule-method.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
