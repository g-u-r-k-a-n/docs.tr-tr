---
description: 'Daha fazla bilgi edinin: ICorDebugILFrame4 Interface'
title: ICorDebugILFrame4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: f2d29229f039509ed7799399f0d4d701e8cafba7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791211"
---
# <a name="icordebugilframe4-interface"></a>ICorDebugILFrame4 Arabirimi

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Ara dil (IL) kodunun yığın çerçevesindeki yerel değişkenlere ve koda erişmenize imkan tanıyan yöntemler sağlar. Bir parametre, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere ve koda erişip erişemeyeceğini belirtir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx Yöntemi](icordebugilframe4-enumeratelocalvariablesex-method.md)|Geçerli çerçevede kullanılabilir olan yerel değişkenlerin listesini döndürür.|  
|[GetCodeEx Yöntemi](icordebugilframe4-getcodeex-method.md)|Bu yığın çerçevesinin çalıştığı kodu döndürür.|  
|[GetLocalVariableEx Yöntemi](icordebugilframe4-getlocalvariableex-method.md)|Il çerçevesindeki yerel bir değişkenin değerini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntemler, [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)ve [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) yöntemleri tarafından sağlana ek olarak işlevsellik sunar. Her yöntem `flags` , profil oluşturucunun yeniden JIT isteği tarafından tanımlanan ek yerel değişkenlerin veya kodun görünür olup olmadığını belirten bir parametre içerir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
