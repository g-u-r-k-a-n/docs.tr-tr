---
title: ICorDebugRegisterSet::SetRegisters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: 4be5d2d9d891010e68cd6eb96cd4456e04d8c8b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712293"
---
# <a name="icordebugregistersetsetregisters-method"></a>ICorDebugRegisterSet::SetRegisters Yöntemi

`SetRegisters` .NET Framework sürüm 2,0 ' de uygulanmıyor. Bu yöntemi çağırmayın.  
  
> [!NOTE]
> [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) veya [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md)gibi daha üst düzey işlemleri kullanın.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet Arabirimi](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)
