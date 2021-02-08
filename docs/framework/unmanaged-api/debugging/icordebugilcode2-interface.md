---
description: 'Daha fazla bilgi edinin: ICorDebugILCode2 Interface'
title: ICorDebugILCode2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 52e47b8cbf8f9926797e193944fd7e97b2e4dbcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791419"
---
# <a name="icordebugilcode2-interface"></a>ICorDebugILCode2 Arabirimi

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Bir işlevin yerel değişken imzasının belirtecini döndüren ve bir profiler 'ın belgelenmiş ara dili (IL) orijinal Yöntem Il uzaklıklarına eşleyen Yöntemler sağlamak için [ICorDebugILCode](icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetInstrumentedILMap Yöntemi](icordebugilcode2-getinstrumentedilmap-method.md)|Bu örnek için, Oluşturucu tarafından işaretlenmiş Il uzaklıkları orijinal Yöntem Il uzaklıklarından bir harita döndürür.|  
|[GetLocalVarSigToken Metodu](icordebugilcode2-getlocalvarsigtoken-method.md)|Bu örnek tarafından temsil edilen işlev için yerel değişken imzasının meta veri belirtecini alır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILCode Arabirimi](icordebugilcode-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
