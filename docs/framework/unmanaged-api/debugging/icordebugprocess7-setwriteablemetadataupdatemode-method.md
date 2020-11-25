---
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 5671f8cb51210c27dffdedba28b4b145b3fedc55
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732560"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Hata ayıklayıcının, hedef işlem içindeki meta veriler için bellek içi güncelleştirmeleri nasıl işlediğini yapılandırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `flags`  
 Hedef işlemdeki meta verilere yönelik bellek güncelleştirmelerinin görünür olup olmadığını belirten bir [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) numaralandırma değeri ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) ve `WriteableMetadataUpdateMode::LegacyCompatPolicy` hata ayıklayıcıya görünür değil.  
  
## <a name="remarks"></a>Açıklamalar  

 Hedef işlemin meta verilerinde yapılan güncelleştirmeler, düzenleme ve devam etme, profil oluşturucu veya ile gelebilir <xref:System.Reflection.Emit?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess7 Arabirimi](icordebugprocess7-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
