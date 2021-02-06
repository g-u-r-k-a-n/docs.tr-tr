---
description: 'Daha fazla bilgi edinin: ICorDebugModule2 Interface'
title: ICorDebugModule2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: 28de1f0d3411218ac92991d4fceda0612c8199bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659939"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 Arabirimi

ICorDebugModule arabirimine bir mantıksal uzantı görevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyChanges Yöntemi](icordebugmodule2-applychanges-method.md)|Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.|  
|[GetJITCompilerFlags Yöntemi](icordebugmodule2-getjitcompilerflags-method.md)|Bunun için tam zamanında (JıT) derlemeyi denetleyen bayrakları alır `ICorDebugModule2` .|  
|[ResolveAssembly Yöntemi](icordebugmodule2-resolveassembly-method.md)|Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.|  
|[SetJITCompilerFlags Yöntemi](icordebugmodule2-setjitcompilerflags-method.md)|Bu için JıT derlemesini denetleyen bayrakları ayarlar `ICorDebugModule2` .|  
|[SetJMCStatus Yöntemi](icordebugmodule2-setjmcstatus-method.md)|Bu, dizideki tüm yöntemlerin tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, `ICorDebugModule2` dizideki değerler hariç, bu değerin `pTokens` ters değere göre ayarlanır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
