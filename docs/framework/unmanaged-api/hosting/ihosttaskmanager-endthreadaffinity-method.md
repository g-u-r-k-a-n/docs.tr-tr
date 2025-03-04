---
description: 'Şu konuda daha fazla bilgi edinin: IHostTaskManager:: Endthreadadffinity yöntemi'
title: IHostTaskManager::EndThreadAffinity Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: 0bbe42d8e14d20fb5be18fe7ebb266100ae72fd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789430"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a>IHostTaskManager::EndThreadAffinity Yöntemi

Şu anda [IHostTaskManager:: Beginthreaerffinity](ihosttaskmanager-beginthreadaffinity-method.md)çağrısından sonra, yönetilen kodun, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken dönemden çıkış olduğunu bildirir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`EndThreadAffinity` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_UNEXPECTED|`EndThreadAffinity` daha önceden karşılık gelen bir çağrısı olmadan çağrıldı `BeginThreadAffinity` .|  
  
## <a name="remarks"></a>Açıklamalar  

 CLR `BeginThreadAffinity` çağrılmadan önce geçerli görevde karşılık gelen bir çağrı yapar `EndThreadAffinity` . Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](ihosttaskmanager-interface.md) uygulaması E_UNEXPECTED döndürmelidir ve hiçbir işlem almaz.  
  
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
