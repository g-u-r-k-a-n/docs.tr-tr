---
description: ': ICLRSyncManager:: GetRWLockOwnerNext yöntemi hakkında daha fazla bilgi edinin'
title: ICLRSyncManager::GetRWLockOwnerNext Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
ms.openlocfilehash: f49bdd5065ac896147967c0a013347ab39ce1eff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785010"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a>ICLRSyncManager::GetRWLockOwnerNext Yöntemi

Geçerli okuyucu-yazıcı kilidinde engellenen bir sonraki [IHostTask](ihosttask-interface.md) örneğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `Iterator`  
 'ndaki [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)çağrısı kullanılarak oluşturulan Yineleyici.  
  
 `ppOwnerHostTask`  
 dışı Bir sonraki, `IHostTask` kilidi bekleyen bir işaretçi veya bekleyen bir görev yoksa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetRWLockOwnerNext` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ppOwnerHostTask`Null olarak ayarlanırsa, yineleme sonlandırılır ve konak [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemini çağırmalıdır.  
  
> [!NOTE]
> `AddRef` `IHostTask` `ppOwnerHostTask` Konakta, konak işaretçiyi tutarken bu görevin çıkış yapmasını engellemek için gereken clr çağrıları. Ana bilgisayar, `Release` tamamlandığında başvuru sayısını azaltmak için çağırmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
