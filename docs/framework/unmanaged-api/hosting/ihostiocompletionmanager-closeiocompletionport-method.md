---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: CloseIoCompletionPort Yöntemi'
title: IHostIoCompletionManager::CloseIoCompletionPort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: 987b9f4e0fa22fa977fa1b14c77c8c0381e3e399
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728515"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a>IHostIoCompletionManager::CloseIoCompletionPort Yöntemi

Konağın bir [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)daha önceki çağrısıyla açılan bir bağlantı noktasını kapatmasını ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `hPort`  
 'ndaki Kapatılacak bağlantı noktasının tanıtıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CloseIoCompletionPort` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|Geçersiz bir bağlantı noktası tanıtıcısı geçildi.|  
  
## <a name="remarks"></a>Açıklamalar  

 `hPort` daha önceki çağrısıyla oluşturulmuş bir bağlantı noktasının tanıtıcısı olmalıdır `CreateIoCompletionPort` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager Arabirimi](ihostiocompletionmanager-interface.md)
