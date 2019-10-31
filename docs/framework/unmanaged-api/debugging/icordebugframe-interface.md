---
title: ICorDebugFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: 5aeea11b7e61869968aafe3425e27d6004f495ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124070"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame Arabirimi

Geçerli yığındaki bir çerçeveyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateStepper Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Bu `ICorDebugFrame`göre atlama işlemleri gerçekleştirmek için bir ICorDebugStepper alır.|  
|[GetCallee Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Geçerli zincirde bu karenin çağırdığı `ICorDebugFrame` bir işaretçi alır veya bu, zincirdeki en içteki çerçevese null değerini döndürür.|  
|[GetCaller Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Bu çerçeveyi çağıran geçerli zincirde `ICorDebugFrame` bir işaretçi alır ya da zincirde en dıştaki çerçevese null değerini döndürür.|  
|[GetChain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Bu `ICorDebugFrame` bir parçası olan ıcordebugzincirine yönelik bir işaretçi alır.|  
|[GetCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Bu yığın çerçevesiyle ilişkili ICorDebugCode için bir işaretçi alır.|  
|[GetFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Bu yığın çerçevesiyle ilişkili kodu içeren ICorDebugFunction için bir işaretçi alır.|  
|[GetFunctionToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.|  
|[GetStackRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Bu `ICorDebugFrame`temsil eden yığın çerçevesinin mutlak adres aralığını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
