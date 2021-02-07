---
description: ': ICLRDebugManager:: EndConnection yöntemi hakkında daha fazla bilgi edinin'
title: ICLRDebugManager::EndConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: 06dc9e20ec02c3e3040090babcc443a2ae59848b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746060"
---
# <a name="iclrdebugmanagerendconnection-method"></a>ICLRDebugManager::EndConnection Yöntemi

Bir görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwConnectionId`  
 'ndaki Bağlantı için konağa özgü tanımlayıcı ve ortak dil çalışma zamanı (CLR) görevlerinin ilişkili listesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`EndConnection` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|[BeginConnection](iclrdebugmanager-beginconnection-method.md) hiçbir şekilde hiçbir şekilde çağrılmadı `dwConnectionId` veya `dwConnectionId` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  

 [ICLRDebugManager](iclrdebugmanager-interface.md) , `BeginConnection` görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)ve olmak üzere üç yöntem sağlar `EndConnection` .  
  
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
- [SetConnectionTasks Yöntemi](iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl Arabirimi](ihostcontrol-interface.md)
