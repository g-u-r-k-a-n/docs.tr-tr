---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugILFrame4:: GetLocalVariableEx yöntemi'
title: ICorDebugILFrame4::GetLocalVariableEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: 4eb6b3abbaf05c0373a487d9bd9d575b58a9af49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791224"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx Yöntemi

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Bu ara dil (IL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır ve isteğe bağlı olarak profil oluşturucu yeniden JIT araçlarına eklenen bir değişkene erişir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `flags`  
 'ndaki Profil Oluşturucu ReJIT araçlarına eklenen bir değişkenin çerçeveye dahil edilip edilmeyeceğini belirten bir [ılcodekind](ilcodekind-enumeration.md) numaralandırma üyesi.  
  
 `dwIndex`  
 'ndaki Il yığın çerçevesindeki yerel değişkenin dizini.  
  
 `ppValue`  
 dışı Alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, isteğe bağlı olarak profil oluşturucu yeniden JIT araçları 'nda eklenen bir değişkene eriştiği için [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) yöntemine benzerdir. Bu yöntemin bir değeriyle çağrılması `flags` `ILCODE_ORIGINAL_IL` [GetLocalVariable](icordebugilframe-getlocalvariable-method.md)çağrısı ile eşdeğerdir; Eğer Yöntem ek yerel değişkenlerle birlikte işaretlenmiş ise, bu değişkenlere erişilemez. `ILCODE_REJIT_IL` hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere erişmesine izin verir. Il görünmüyorsa, yöntemi döndürür `E_INVALIDARG` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILFrame4 Arabirimi](icordebugilframe4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ReJIT: A How-To Kılavuzu](/archive/blogs/davbr/rejit-a-how-to-guide)
