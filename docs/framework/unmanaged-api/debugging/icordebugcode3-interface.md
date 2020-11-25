---
title: ICorDebugCode3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: 609cd557db71fac53aadf613534a23e988b14bde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720768"
---
# <a name="icordebugcode3-interface"></a>ICorDebugCode3 Arabirimi

Yönetilen bir dönüş değeri hakkında bilgi sağlamak için "ICorDebugCode" ve "ICorDebugCode2" değerlerini genişleten bir yöntem sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReturnValueLiveOffset Yöntemi](icordebugcode3-getreturnvalueliveoffset-method.md)|Belirtilen bir Il ofseti için, hata ayıklayıcının bir işlevden dönüş değeri alabileceği şekilde, bir kesme noktasının yerleştirilmesi gereken yerel uzaklıkları alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILFrame3 Arabirimi](icordebugilframe3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
