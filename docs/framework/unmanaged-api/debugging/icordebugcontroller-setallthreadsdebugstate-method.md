---
description: ': ICorDebugController:: SetAllThreadsDebugState yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugController::SetAllThreadsDebugState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: 3bce5360833ae18c68bc8d7ea24f0dec7615f7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710744"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState Yöntemi

İşlemdeki tüm yönetilen iş parçacıklarının hata ayıklama durumunu ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `state`  
 'ndaki Hata ayıklama için iş parçacığının durumunu belirten "CorDebugThreadState" numaralandırmasının değeri.  
  
 `pExceptThisThread`  
 'ndaki Hata ayıklama durumu ayarından muaf tutulan bir iş parçacığını temsil eden "ICorDebugThread" nesnesine yönelik bir işaretçi. Bu değer null ise, hiçbir iş parçacığı muaf tutulur.  
  
## <a name="remarks"></a>Açıklamalar  

 `SetAllThreadsDebugState`Yöntemi, [EnumerateThreads yöntemi](icordebugcontroller-enumeratethreads-method.md)aracılığıyla görünmeyen iş parçacıklarını etkileyebilir, bu nedenle yöntemiyle askıya alınan iş parçacıklarının `SetAllThreadsDebugState` yöntemiyle sürdürülmeleri gerekir `SetAllThreadsDebugState` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
