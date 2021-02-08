---
description: ': IActionOnCLREvent:: OnEvent yöntemi hakkında daha fazla bilgi edinin'
title: IActionOnCLREvent::OnEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: 163956ab319eb34d58da23d2c4ef2a6b592aab0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785152"
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent Yöntemi

[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) metoduna yapılan bir çağrı kullanılarak kaydedilmiş olaylarda geri çağırmaları gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `event`  
 'ndaki Olay türünü gösteren [EClrEvent](eclrevent-enumeration.md) değerlerinden biri.  
  
 `data`  
 'ndaki Hakkındaki ayrıntıları içeren bir nesne işaretçisi `event` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`OnEvent` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz. Herhangi bir barındırma yöntemine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `data`Parametresi, belirtilmeyen türdeki bir nesnenin işaretçisidir. Parametresi ise, `event` `Event_DomainUnload` `data` bellekten kaldırılan için sayısal tanıtıcıdır <xref:System.AppDomain> . Ana bilgisayar bu tanımlayıcıyı anahtar olarak kullanarak uygun eylemi gerçekleştirebilir.  
  
 `event`İse `Event_MDAFired` , `data` yönetilen hata ayıklama Yardımcısı 'nın (MDA) ileti çıkışını Içeren bir [mdadınfo](mdainfo-structure.md) örneğine yönelik bir işaretçidir. Mdalar, geliştiricilerin hata ayıklamasına yardımcı olan ve tuzak zorluğu eden olaylar hakkında XML iletileri oluşturarak CLR 'nin bir özelliğidir. Bu tür iletiler, yönetilen ve yönetilmeyen kod arasındaki geçişlerde hata ayıklama için özellikle yararlı olabilir. Daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [EClrEvent Numaralandırması](eclrevent-enumeration.md)
- [IActionOnCLREvent Arabirimi](iactiononclrevent-interface.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [ICLROnEventManager Arabirimi](iclroneventmanager-interface.md)
- [MDAInfo Yapısı](mdainfo-structure.md)
