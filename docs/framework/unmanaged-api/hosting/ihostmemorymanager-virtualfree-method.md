---
description: 'Şu konuda daha fazla bilgi edinin: IHostMemoryManager:: VirtualFree yöntemi'
title: IHostMemoryManager::VirtualFree Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
ms.openlocfilehash: 987661ce1b7bfd08f757f53082313b8eb60ff282
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707550"
---
# <a name="ihostmemorymanagervirtualfree-method"></a>IHostMemoryManager::VirtualFree Yöntemi

Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür. Uygulamaları `VirtualFree` yayınlar, serbest bırakır veya yayınlar, çağıran işlemin sanal adres alanındaki bir sayfa bölgesini kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `lpAddress`  
 'ndaki Boşaltılacak sanal bellek sayfalarının temel adresine yönelik bir işaretçi.  
  
 `dwSize`  
 'ndaki Boşaltılacak bölgenin bayt cinsinden boyutu.  
  
 `dwFreeType`  
 'ndaki Boşaltma işleminin türü.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`VirtualFree` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_INVALIDOPERATION|Ana bilgisayar aracılığıyla ayrılmamış belleği serbest bırakma girişiminde bulunuldu.|  
  
## <a name="remarks"></a>Açıklamalar  

 `VirtualFree``lpAddress` [IHostMemoryManager:: VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) işlevine daha önceki bir çağrı yoluyla parametresiyle ilişkili sanal bellek sayfalarını boşaltır. Ana bilgisayar üzerinden ayrılmamış belleği serbest bırakma denemeleri HOST_E_INVALIDOPERATION döndürmelidir.  
  
 Semantiği, Win32 uygulamasıyla aynıdır `VirtualFree` . Daha fazla bilgi için bkz. Windows platformu belgeleri.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
- [IHostMalloc Arabirimi](ihostmalloc-interface.md)
