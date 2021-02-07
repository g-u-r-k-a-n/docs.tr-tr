---
description: ': ICLRDebugManager:: SetConnectionTasks yöntemi hakkında daha fazla bilgi edinin'
title: ICLRDebugManager::SetConnectionTasks Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
ms.openlocfilehash: 851b3f54cc5599781596314dfb70296a3d86491a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728749"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a>ICLRDebugManager::SetConnectionTasks Yöntemi

[ICLRTask](iclrtask-interface.md) örneklerinin listesini bir tanımlayıcı ve kolay bir ad ile ilişkilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `id`  
 'ndaki Dizinin ilişkilendirileceği bağlantı için konağa özgü tanımlayıcı `ppCLRTask` .  
  
 `dwCount`  
 'ndaki Üyelerinin sayısı `ppCLRTask` . Bu sayı sıfırdan büyük olmalıdır.  
  
 `ppCLRTask`  
 'ndaki `ICLRTask` Tarafından tanımlanan bağlantıyla ilişkilendirilecek işaretçiler dizisi `id` . Bu dizi en az bir üye içermelidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetConnectionTasks` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|[BeginConnection](iclrdebugmanager-beginconnection-method.md) bu değeri `id` veya `dwCount` ya da sıfır veya `id` öğelerinden biri null olan bu değer kullanılarak çağrılmadı `ppCLRTask` .|  
  
## <a name="remarks"></a>Açıklamalar  

 [ICLRDebugManager](iclrdebugmanager-interface.md) , `BeginConnection` `SetConnectionTasks` görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için üç yöntem,, ve [EndConnection](iclrdebugmanager-endconnection-method.md)sağlar.  
  
> [!IMPORTANT]
> Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir. `BeginConnection` İlk olarak yeni bir bağlantı kurmak için çağırılır. `SetConnectionTasks` ileri, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için çağrılır. `EndConnection` , görev listesi ile tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [ICLRDebugManager Arabirimi](iclrdebugmanager-interface.md)
- [BeginConnection Yöntemi](iclrdebugmanager-beginconnection-method.md)
- [EndConnection Yöntemi](iclrdebugmanager-endconnection-method.md)
- [IHostControl Arabirimi](ihostcontrol-interface.md)
