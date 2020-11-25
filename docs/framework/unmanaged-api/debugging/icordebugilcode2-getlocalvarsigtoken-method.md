---
title: ICorDebugILCode2::GetLocalVarSigToken Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
ms.openlocfilehash: 33533c9e3bfbe78abeddb5ed591f741219826127
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728639"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a>ICorDebugILCode2::GetLocalVarSigToken Metodu

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Bu örnek tarafından temsil edilen işlev için yerel değişken imzasının meta veri belirtecini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pmdSig`  
 dışı `mdSignature` Bu işlev için yerel değişken imzasının belirtecine yönelik bir işaretçi veya `mdSignatureNil` imza yoksa (işlev herhangi bir yerel değişken içermiyorsa).  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILCode2 Arabirimi](icordebugilcode2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
