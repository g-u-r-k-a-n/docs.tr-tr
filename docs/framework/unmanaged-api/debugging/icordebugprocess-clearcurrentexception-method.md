---
title: ICorDebugProcess::ClearCurrentException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: 0d36390a905561b64b3ca6ca95722f82158450be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695224"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException Yöntemi

Belirtilen iş parçacığında geçerli yönetilmeyen özel durumu temizler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a>Parametreler  

 `threadID`  
 'ndaki Geçerli yönetilmeyen özel durumun temizleneceği iş parçacığının KIMLIĞI.  
  
## <a name="remarks"></a>Açıklamalar  

 Bir iş parçacığı hata ayıklanan tarafından yoksayılması gereken yönetilmeyen bir özel durum raporlandığı için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) öğesini çağırmadan önce bu yöntemi çağırın. Bu işlem, verilen iş parçacığında hem bekleyen bant içi (ıB) hem de bant dışı (OOB) olaylarını temizler. Tüm OOB kesme noktaları ve tek adımlı özel durumlar otomatik olarak temizlenir.  
  
 Bir iş parçacığında geçerli yönetilen özel durumu ele almak için [ICorDebugThread2:: Yakatcurrentexception](icordebugthread2-interceptcurrentexception-method.md) kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
