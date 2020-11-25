---
title: ICorDebugEval2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
ms.openlocfilehash: 090b587ef509795609250914ce8883ad96d28c18
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729687"
---
# <a name="icordebugeval2-interface"></a>ICorDebugEval2 Arabirimi

Genel türler için destek sağlamak üzere "ıcorınkınogeval" öğesini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CallParameterizedFunction Yöntemi](icordebugeval2-callparameterizedfunction-method.md)|Belirtilen "ICorDebugFunction" öğesine bir çağrı yapar, bu, Oluşturucusu tür parametreleri alan bir türün içinde iç içe eklenebilir veya kendisi tür parametreleri alabilir.|  
|[CreateValueForType Yöntemi](icordebugeval2-createvaluefortype-method.md)|Belirtilen türün yeni bir "ICorDebugValue" değerine, null veya sıfır başlangıç değerine sahip bir işaretçi alır.|  
|[NewParameterizedArray Yöntemi](icordebugeval2-newparameterizedarray-method.md)|Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.|  
|[NewParameterizedObject Yöntemi](icordebugeval2-newparameterizedobject-method.md)|Yeni parametreli bir tür nesnesi oluşturur ve nesnenin Oluşturucu yöntemini çağırır.|  
|[NewParameterizedObjectNoConstructor Yöntemi](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Bir Oluşturucu yöntemi çağırmaya çalışmadan, belirtilen sınıfın yeni parametreli tür nesnesini başlatır|  
|[NewStringWithLength Yöntemi](icordebugeval2-newstringwithlength-method.md)|Belirtilen içerikle belirtilen uzunluğa sahip yeni bir dize oluşturur.|  
|[RudeAbort Yöntemi](icordebugeval2-rudeabort-method.md)|`ICorDebugEval2`Şu anda gerçekleştirdiği hesaplamayı iptal eder.|  
  
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
