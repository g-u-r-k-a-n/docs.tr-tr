---
description: 'Daha fazla bilgi edinin: EClrEvent numaralandırması'
title: EClrEvent Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: 7c2365d1a2fb0109bab9159c3af4e2da3a46de6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785607"
---
# <a name="eclrevent-enumeration"></a>EClrEvent Numaralandırması

Konağın geri çağırmaları kaydedebileceği ortak dil çalışma zamanı (CLR) olaylarını açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`Event_ClrDisabled`|Önemli bir CLR hatası belirtir.|  
|`Event_DomainUnload`|Belirli bir sürümü kaldırmayı belirtir <xref:System.AppDomain> .|  
|`Event_MDAFired`|Yönetilen hata ayıklama Yardımcısı (MDA) iletisinin oluşturulduğunu belirtir.|  
|`Event_StackOverflow`|Yığın taşması hatası oluştuğunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Konak, `EClrEvent` [ICLROnEventManager](iclroneventmanager-interface.md) arabiriminin yöntemlerini çağırarak tarafından tanımlanan olay türlerinden herhangi biri için geri çağırmaları kaydedebilir. Ana bilgisayar [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırarak bu arabirime yönelik bir işaretçi alır.  
  
 `Event_CLRDisabled`Ve `Event_DomainUnload` olayları bir defadan fazla ve farklı iş parçacıklarından bir KALDıRMA veya clr 'nin devre dışı bırakılmasını bildirmek için kullanılabilir.  
  
 `Event_MDAFired`Olay, MDA iletisinin ayrıntılarını içeren bir [Mdadınfo](mdainfo-structure.md) örneği oluşturulmasını başlatır. MDAs hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IActionOnCLREvent Arabirimi](iactiononclrevent-interface.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [Barındırma Numaralandırmaları](hosting-enumerations.md)
