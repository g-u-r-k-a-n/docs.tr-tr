---
description: 'Daha fazla bilgi edinin: ICorDebugNativeFrame2 Interface'
title: ICorDebugNativeFrame2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
ms.openlocfilehash: 9ed0e20bb29bef3b210258956ebecb1ee7a96df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722353"
---
# <a name="icordebugnativeframe2-interface"></a>ICorDebugNativeFrame2 Arabirimi

Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IsChild Yöntemi](icordebugnativeframe2-ischild-method.md)|Geçerli çerçevenin bir alt çerçeve olup olmadığını belirler.|  
|[IsMatchingParentFrame Yöntemi](icordebugnativeframe2-ismatchingparentframe-method.md)|Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.|  
|[GetStackParameterSize Yöntemi](icordebugnativeframe2-getstackparametersize-method.md)|X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu arabirim "ICorDebugNativeFrame" arabirimini mantıksal olarak genişletir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
