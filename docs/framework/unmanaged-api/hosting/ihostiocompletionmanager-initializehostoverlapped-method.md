---
description: ': Ihostiocompletionmanager:: ınitializehostoverlapoladmethod hakkında daha fazla bilgi edinin'
title: IHostIoCompletionManager::InitializeHostOverlapped Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
ms.openlocfilehash: 10be7edb67143937dec6efc6e35466466374d32d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708469"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped Yöntemi

Ana bilgisayara, `OVERLAPPED` zaman uyumsuz g/ç istekleri için kullanılan bir Win32 yapısına eklenecek özel verileri başlatma fırsatı sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pvOverlapped`  
 'ndaki `OVERLAPPED` G/ç isteğine dahil edilecek Win32 yapısına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen kaynağı ayırmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  

 Windows platformu işlevleri, `OVERLAPPED` zaman uyumsuz g/ç isteklerinin durumunu depolamak için yapıyı kullanır. CLR, `InitializeHostOverlapped` konağa özel verileri ekleme fırsatına bir örneğe çağrı yapmak için yöntemini çağırır `OVERLAPPED` .  
  
> [!IMPORTANT]
> Özel veri bloğunun başlangıcına ulaşmak için, konaklar yapının () boyutuna kadar olan sapmayı ayarlamış olmalıdır `OVERLAPPED` `sizeof(OVERLAPPED)` .  
  
 E_OUTOFMEMORY dönüş değeri konağın özel verilerini başlatamadığını gösterir. Bu durumda, CLR bir hata bildirir ve çağrı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](iclriocompletionmanager-interface.md)
- [GetHostOverlappedSize Yöntemi](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [IHostIoCompletionManager Arabirimi](ihostiocompletionmanager-interface.md)
