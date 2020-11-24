---
title: ICLRGCManager2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: d2873b5e1f8229e8a16dfaacf1c9737ac47405bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672805"
---
# <a name="iclrgcmanager2-interface"></a>ICLRGCManager2 Arabirimi

Bir konağın ortak dil çalışma zamanının çöp toplama sistemiyle etkileşime geçmesini sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetGCStartupLimitsEx Yöntemi](iclrgcmanager2-setgcstartuplimitsex-method.md)|Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar. 1. nesil ve kesim boyutlarını daha büyük olarak sunar `DWORD` .|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu arabirim [ICLRGCManager arabiriminden](iclrgcmanager-interface.md)devralır.  
  
 Ortak dil çalışma zamanı (CLR), kendi çöp toplama mekanizmasını yönetilen türle uygular <xref:System.GC> . Çöp toplama sistemi hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik bellek yönetimi](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS Yapısı](cor-gc-stats-structure.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
- [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)
