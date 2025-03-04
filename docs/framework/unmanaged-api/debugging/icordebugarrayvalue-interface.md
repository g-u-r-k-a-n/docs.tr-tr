---
description: 'Bu konuda daha fazla bilgi edinin: ıcorı, Garrayvalue arabirimi'
title: ICorDebugArrayValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: 2b91c910b9444b061b4a6bea715667bca6a4629c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722899"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue Arabirimi

Tek boyutlu veya çok boyutlu bir diziyi temsil eden ICorDebugHeapValue öğesinin alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBaseIndicies Yöntemi](icordebugarrayvalue-getbaseindicies-method.md)|Dizideki her boyutun temel dizinini alır.|  
|[GetCount Yöntemi](icordebugarrayvalue-getcount-method.md)|Dizideki toplam öğe sayısını alır.|  
|[GetDimensions Yöntemi](icordebugarrayvalue-getdimensions-method.md)|Dizinin boyutlarını alır.|  
|[GetElement Yöntemi](icordebugarrayvalue-getelement-method.md)|Dizide verilen öğeyi temsil eden bir değer alır.|  
|[GetElementAtPosition Yöntemi](icordebugarrayvalue-getelementatposition-method.md)|Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.|  
|[GetElementType Yöntemi](icordebugarrayvalue-getelementtype-method.md)|Dizideki öğelerin basit türünü alır.|  
|[GetRank Yöntemi](icordebugarrayvalue-getrank-method.md)|Dizideki boyut sayısını alır.|  
|[HasBaseIndicies Yöntemi](icordebugarrayvalue-hasbaseindicies-method.md)|Dizinin temel dizinlere sahip olup olmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugArrayValue` hem tek boyutlu hem çok boyutlu dizileri destekler.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
