---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo10:: ısfrozenobject yöntemi'
title: 'ICorProfilerInfo10:: ısfrozenobject'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3b47204630056e2797b5cf126bd7c291830cea05
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103458"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>ICorProfilerInfo10:: ısfrozenobject yöntemi

ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a>Parametreler

- `objectId`

  \[içinde] incelenecek nesne.

- `pbFrozen`

  \[out] bir `BOOL` nesnenin salt okunurdur bir kesimde olup olmadığını belirten bir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo10 Arabirimi](icorprofilerinfo10-interface.md)
