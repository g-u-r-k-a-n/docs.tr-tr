---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugThread2:: Yakatcurrentexception yöntemi'
title: ICorDebugThread2::InterceptCurrentException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: 5bf8d3adf6f5e4a24d8fc5abddb72c0c8963c142
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790721"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>ICorDebugThread2::InterceptCurrentException Yöntemi

Bir hata ayıklayıcının bu iş parçacığında geçerli özel durumu kesmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pFrame`  
 'ndaki Etkin yığın çerçevesini temsil eden bir ICorDebugFrame işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 `InterceptCurrentException`Yöntem bir özel durum geri çağırması ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) veya [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) Ile ilişkili [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)öğesine yapılan çağrı arasında çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
