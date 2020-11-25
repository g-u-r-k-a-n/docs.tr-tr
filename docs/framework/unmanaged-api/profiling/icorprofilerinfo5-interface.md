---
title: ICorProfilerInfo5 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: a6206e35280e073df2abfb7ae46aa84d34b30208
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733808"
---
# <a name="icorprofilerinfo5-interface"></a>ICorProfilerInfo5 Arabirimi

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Kod profil oluşturucular tarafından, olay izlemeyi denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak için kullanılacak yöntemler sağlayan bir [ICorProfilerInfo4](icorprofilerinfo4-interface.md) alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetEventMask2 Yöntemi](icorprofilerinfo5-geteventmask2-method.md)|Profil oluşturucunun CLR 'den bildirim almak istediği geçerli olay kategorilerini alır.|  
|[SetEventMask2 Yöntemi](icorprofilerinfo5-seteventmask2-method.md)|Profil oluşturucunun, CLR 'den olay bildirimleri almak istediği olay türlerini belirten bir değer ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu arabirimdeki kullanılabilir yöntemler [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) ve [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemlerinin yerini alacak şekilde tasarlanmıştır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
