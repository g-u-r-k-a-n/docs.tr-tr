---
title: ICorProfilerThreadEnum::GetCount Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 230b02b71abea48b1c3ad4094ea90812493149d1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861001"
---
# <a name="icorprofilerthreadenumgetcount-method"></a>ICorProfilerThreadEnum::GetCount Yöntemi
Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 dışı Uygulama tarafından kullanılan iş parçacıklarının sayısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerThreadEnum Arabirimi](icorprofilerthreadenum-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
