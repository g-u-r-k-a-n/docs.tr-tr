---
description: ': ICorProfilerThreadEnum:: Skip yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerThreadEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: 1da191980364868ed4237fccaf7495d5417705cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736901"
---
# <a name="icorprofilerthreadenumskip-method"></a>ICorProfilerThreadEnum::Skip Yöntemi

Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `celt`  
 'ndaki Atlanacak öğe sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`celt` öğeler atlandı.|  
|S_FALSE|Daha az öğe olmadığını `celt` belirten öğe atlandı.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + ' dır `celt` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerThreadEnum Arabirimi](icorprofilerthreadenum-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
