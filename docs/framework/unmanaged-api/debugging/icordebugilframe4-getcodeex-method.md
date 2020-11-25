---
title: ICorDebugILFrame4::GetCodeEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: a88bb02626dc125c494e4bbe68bfe6ed8bfd3b7b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719651"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx Yöntemi

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Bu yığın çerçevesinin yürütüldüğü koda yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `flags`  
 'ndaki Profiler 'ın ReJIT isteği tarafından tanımlanan ara dilin (IL) çerçeveye dahil edilip edilmeyeceğini belirten bir [ılcodekind](ilcodekind-enumeration.md) numaralandırma üyesi.  
  
 `ppCode`  
 dışı Bu yığın çerçevesinin yürütüldüğü kodu temsil eden bir "ICorDebugCode" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem [ICorDebugFrame:: GetCode](icordebugframe-getcode-method.md) yöntemine benzer, isteğe bağlı olarak Profiler 'ın ReJIT isteği tarafından tanımlanan koda erişir. Bu yöntemin bir değeriyle çağrılması `flags` `ILCODE_ORIGINAL_IL` [GetCode](icordebugframe-getcode-method.md)çağırma ile eşdeğerdir; Eğer Eğer Eğer Eğer Eğer Eğer bu yöntem BELGELENMIŞ ise, onun Il 'ye erişilemeyecektir. `ILCODE_REJIT_IL` hata ayıklayıcının profil oluşturucunun ReJIT isteği tarafından tanımlanan Il 'ye erişmesine izin verir. Il görünmüyorsa, `ppCode` **null** olur ve yöntemi döndürür `S_OK` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILFrame4 Arabirimi](icordebugilframe4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ReJIT: A How-To Kılavuzu](/archive/blogs/davbr/rejit-a-how-to-guide)
