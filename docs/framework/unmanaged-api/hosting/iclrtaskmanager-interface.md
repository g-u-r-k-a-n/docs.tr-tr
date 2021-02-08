---
description: ': ICLRTaskManager arabirimi hakkında daha fazla bilgi edinin'
title: ICLRTaskManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: 0ce3641042725bc2f3acb95933ccd7a5bbe3bc4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789755"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager Arabirimi

Ana bilgisayarın ortak dil çalışma zamanının (CLR) yeni bir görev oluşturmasını, şu anda yürütülmekte olan görevi almasını ve görevin coğrafi dilini ve kültürünü ayarlamanızı sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateTask Yöntemi](iclrtaskmanager-createtask-method.md)|CLR 'nin yeni bir [ICLRTask](iclrtask-interface.md) örneği oluşturmasını açıkça ister.|  
|[GetCurrentTask Yöntemi](iclrtaskmanager-getcurrenttask-method.md)|`ICLRTask`Şu anda yürütülmekte olan görevi temsil eden örneği alır.|  
|[GetCurrentTaskType Yöntemi](iclrtaskmanager-getcurrenttasktype-method.md)|Şu anda yürütülmekte olan görevin türünü alır.|  
|[SetLocale Yöntemi](iclrtaskmanager-setlocale-method.md)|, Konağın Şu anda yürütülmekte olan görevde yerel ayar tanıtıcısını değiştirdiğinizi CLR 'ye bildirir.|  
|[SetUILocale Yöntemi](iclrtaskmanager-setuilocale-method.md)|Ana bilgisayarın şu anda yürütülmekte olan görevde Kullanıcı arabirimi yerel ayar tanımlayıcısını değiştirdiği ortak dil çalışma zamanına bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Barındırılan bir ortamda çalışan her görev, hem konak tarafında (bir [IHostTask](ihosttask-interface.md)örneği) hem de clr tarafında ( [ICLRTask](iclrtask-interface.md)örneği) temsil edilir. Konak veya CLR bir görevin oluşturulmasını başlatabilir, ancak konakla ilgili konak ile CLR arasında başarılı bir iletişim sağlamak için konak tarafı gösteriminin karşılık gelen bir CLR tarafı temsili ile ilişkilendirilmesi gerekir. Yönetilen kodun bir işletim sistemi iş parçacığında yürütülebilmesi için önce iki nesnenin oluşturulup oluşturulması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](iclrtask-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
