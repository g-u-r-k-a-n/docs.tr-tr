---
title: IHostTaskManager::ReverseEnterRuntime Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
ms.openlocfilehash: 163bf3327219f1198c5ed078308096ac3d0325be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672974"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a>IHostTaskManager::ReverseEnterRuntime Yöntemi

Ana bilgisayara, yönetilmeyen koddan ortak dil çalışma zamanı (CLR) için bir çağrının yapıldığını bildirir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ReverseEnterRuntime` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen kaynak ayırmayı tamamlamaya yetecek miktarda bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  

 CLR 'ye yapılan çağrı yönetilen kodda oluşturulan bir sıra tarafından yapılırsa, her `ReverseEnterRuntime` bir çağrı bir [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)çağrısına karşılık gelir.  
  
> [!NOTE]
> Çağrılar, iç içe kalmadan yönetilmeyen koddan kaynaklanamaz. Bu durumda, bir [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md)veya ve çağrısı sayısı ile yapılan çağrı `ReverseLeaveRuntime` `ReverseEnterRuntime` sayısına eşit değildir `ReverseLeaveRuntime` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
