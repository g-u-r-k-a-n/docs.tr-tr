---
description: ': IHostMemoryManager:: RegisterMemoryNotificationCallback Yöntemi hakkında daha fazla bilgi edinin'
title: IHostMemoryManager::RegisterMemoryNotificationCallback Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: 26a7468aba4f473eebff78a8c67eeb5b3e866e9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707773"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a>IHostMemoryManager::RegisterMemoryNotificationCallback Yöntemi

Bilgisayarın, bilgisayardaki geçerli bellek yükünün ortak dil çalışma zamanını (CLR) bilgilendirmek için çağırdığı bir geri çağırma işlevine bir işaretçi kaydeder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pCallback`  
 'ndaki CLR tarafından uygulanan [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) örneğine yönelik bir arabirim işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`RegisterMemoryNotificationCallback` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICLRMemoryNotificationCallback`Arabirim yalnızca bir yöntemi ([ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)) TANıMLADıĞıNDAN ve, `pCallback` clr tarafından sağlanmış bir örneğe yönelik bir işaretçi olduğundan `ICLRMemoryNotificationCallback` , geri çağırma işlevinin kendisi için kayıt etkin olur. Ana bilgisayar `OnMemoryNotification` , standart Win32 işlevini kullanmak yerine bellek baskısı koşullarını raporlamak için çağırır `CreateMemoryResourceNotification` . Daha fazla bilgi için bkz. Windows platformu belgeleri.  
  
> [!NOTE]
> Hiçbir şekilde `OnMemoryNotification` engellenmemek için çağrılar. Her zaman hemen döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMemoryNotificationCallback Arabirimi](iclrmemorynotificationcallback-interface.md)
- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
