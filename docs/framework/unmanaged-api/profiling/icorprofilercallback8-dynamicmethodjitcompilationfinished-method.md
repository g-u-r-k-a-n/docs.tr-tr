---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 6354667e754da42692cc0de2dc5330c56f951aa1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725449"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi

[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]  
  
Dinamik bir yöntemin JıT derlemesi tamamlandığında profil oluşturucuyu bilgilendirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a>Parametreler  

'ndaki `functionId`  
JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.

[in] `hrStatus` JıT derlemesinin başarılı olup olmadığını gösteren bir değer.

[in] `fIsSafeToBlock` 
 `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false`engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.  

## <a name="remarks"></a>Açıklamalar  

Bu geri çağırma, dinamik bir yöntemin JıT derlemesi tamamlandığında tetiklenir. Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir. Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.

> [!NOTE]
> `functionId` Dinamik metotların meta verisi olmadığından, meta veri belirteçlerine çözümlemek için değerler kullanılamaz.

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DynamicMethodJITCompilationStarted Yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 Arabirimi](icorprofilercallback8-interface.md)
