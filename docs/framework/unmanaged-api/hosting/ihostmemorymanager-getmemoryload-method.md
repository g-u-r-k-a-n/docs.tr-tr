---
description: 'Şu konuda daha fazla bilgi edinin: IHostMemoryManager:: GetMemoryLoad yöntemi'
title: IHostMemoryManager::GetMemoryLoad Metodu
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 82288e6a705b014c2768c75e15376f7e6a0af428
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707853"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a>IHostMemoryManager::GetMemoryLoad Metodu

Şu anda kullanımda olan fiziksel bellek miktarını ve bu nedenle ana bilgisayar tarafından bildirilen kullanım sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pMemoryLoad`  
 dışı Şu anda kullanımda olan toplam fiziksel belleğin yaklaşık yüzdesine yönelik bir işaretçi.  
  
 `pAvailableBytes`  
 dışı Ortak dil çalışma zamanı (CLR) için kullanılabilen bayt sayısına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetMemoryLoad` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `GetMemoryLoad` Win32 işlevini kaydırır `GlobalMemoryStatus` . Değeri, `pMemoryLoad` `dwMemoryLoad` `MEMORYSTATUS` öğesinden döndürülen yapıdaki alanın eşdeğeridir `GlobalMemoryStatus` .  
  
 Çalışma zamanı, çöp toplayıcı için bir buluşsal yöntem olarak dönüş değerini kullanır. Örneğin, ana bilgisayar belleğin çoğunluğunun kullanımda olduğunu bildirirse çöp toplayıcı, kullanılabilir olabilecek bellek miktarını artırmak için birden çok nesden toplamayı tercih edebilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.GC?displayProperty=nameWithType>
- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
