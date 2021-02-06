---
description: ': ICorDebugManagedCallback:: Steptamamlanmıştır yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugManagedCallback::StepComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
ms.openlocfilehash: 653abee26f09ac8877be9fa4183763739845666a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660368"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a>ICorDebugManagedCallback::StepComplete Yöntemi

Hata ayıklayıcıyı bir adımın tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pAppDomain`  
 'ndaki Adımın tamamlandığı iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pThread`  
 'ndaki Adımın tamamlandığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.  
  
 `pStepper`  
 'ndaki Kod yürütme adımını temsil eden bir ICorDebugStepper nesnesine yönelik bir işaretçi.  
  
 `reason`  
 'ndaki Tek bir adımın sonucunu gösteren CorDebugStepReason numaralandırması değeri.  
  
## <a name="remarks"></a>Açıklamalar  

 Stepper, hata ayıklama sonlandırılana kadar istenirse Adımlama ile devam etmek için kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
