---
title: ICLRIoCompletionManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: e23675351e1fd0de510243c9ee8b3a6dd6f29cec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714126"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager Arabirimi

Ana bilgisayarın, belirtilen g/ç isteklerinin durumunun ortak dil çalışma zamanına (CLR) bildirmesini sağlayan bir geri çağırma yöntemi uygular.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OnComplete Yöntemi](iclriocompletionmanager-oncomplete-method.md)|[Ihostiocompletionmanager:: bind](ihostiocompletionmanager-bind-method.md) yöntemine bir çağrı kullanılarak yapılan bir g/ç isteğinin clr 'ye bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Konak, [ıhostiocompletionmanager](ihostiocompletionmanager-interface.md) arabirimini kullanarak g/ç tamamlama soyutlama uygular. CLR bu arabirim aracılığıyla g/ç istekleri yapar ve ana bilgisayar, bu tür isteklerin çalışma zamanına arabirimini kullanarak bildirir `ICLRIoCompletionManager` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostIoCompletionManager Arabirimi](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager Arabirimi](ihostthreadpoolmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
