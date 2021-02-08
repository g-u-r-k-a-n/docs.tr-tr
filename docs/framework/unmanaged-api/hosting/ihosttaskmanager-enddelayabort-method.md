---
description: ': IHostTaskManager:: EndDelayAbort Yöntemi hakkında daha fazla bilgi'
title: IHostTaskManager::EndDelayAbort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
ms.openlocfilehash: e0d1c4231d381baf2ff92d187d33714f1c6f3003
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784567"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a>IHostTaskManager::EndDelayAbort Yöntemi

Şu anda [IHostTaskManager:: BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md)' e daha önceki bir çağrıdan sonra, yönetilen kodun, geçerli görevin durdurulmadıkları dönemden çıkış olduğunu bildirir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`EndDelayAbort` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_UNEXPECTED|`EndDelayAbort` öğesine karşılık gelen bir çağrısı olmadan çağrıldı `BeginDelayAbort` .|  
  
## <a name="remarks"></a>Açıklamalar  

 CLR `BeginDelayAbort` çağrılmadan önce geçerli görevde karşılık gelen bir çağrı yapar `EndDelayAbort` . Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](ihosttaskmanager-interface.md) uygulaması E_UNEXPECTED ' den döndürmelidir `EndDelayAbort` ve hiçbir işlem yapması gerekmez.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading>
- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
