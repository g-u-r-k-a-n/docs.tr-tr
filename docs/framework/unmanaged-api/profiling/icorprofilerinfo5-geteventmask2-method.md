---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo5:: GetEventMask2 yöntemi'
title: ICorProfilerInfo5::GetEventMask2 Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: c6652ffe1b8fd0d99ce5493c8ba27a971363c423
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646666"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>ICorProfilerInfo5::GetEventMask2 Metodu

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Profil oluşturucunun ortak dil çalışma zamanından (CLR) bildirim almak istediği geçerli olay kategorilerini alır.  [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) yöntemi tarafından sağlanmayan işlevselliği sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pdwEventsLow`  
 dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi. Her bit, farklı bir yetenek, davranış veya olay türünü denetler. Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.  
  
 `pdwEventsHigh`  
 dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi.  Her bit, farklı bir yetenek, davranış veya olay türünü denetler. Bitleri [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetEventMask2`Yöntemi, profil oluşturucunun abone olduğu geri çağırmaları tespit etmek için kullanılır. Genellikle, bir mantıksal veya değerlerini ve ayarlamak istediğiniz `pdwEventsLow` `pdwEventsHigh` Yeni bitleri gerçekleştirirsiniz ve ardından [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemini çağırın.  
  
 Bu yöntem, [GetEventMask](icorprofilerinfo-geteventmask-method.md) yönteminin önerilen alternatifidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo5 Arabirimi](icorprofilerinfo5-interface.md)
- [SetEventMask2 Yöntemi](icorprofilerinfo5-seteventmask2-method.md)
