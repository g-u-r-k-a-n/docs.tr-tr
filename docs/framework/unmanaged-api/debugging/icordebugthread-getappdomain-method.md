---
description: ': ICorDebugThread:: GetAppDomain Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugThread::GetAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
ms.openlocfilehash: 416ab80fa08786fb5e95776b164723317fa59ca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659211"
---
# <a name="icordebugthreadgetappdomain-method"></a>ICorDebugThread::GetAppDomain Yöntemi

Bu ICorDebugThread 'in Şu anda yürütüldüğü uygulama etki alanına bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppAppDomain`  
 dışı Bu iş parçacığının Şu anda yürütüldüğü uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
