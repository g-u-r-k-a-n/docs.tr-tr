---
title: 'ICorDebugVariableSymbol:: Getslotındex yöntemi'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: fc42517cb95dfc14c472b5bb9111ebd70639cee7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725995"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>ICorDebugVariableSymbol:: Getslotındex yöntemi

Yerel bir değişkenin yönetilen yuva dizinini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pSlotIndex`  
 dışı Yerel değişkenin yuva dizinine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` başarılı olursa. `E_FAIL` değişken bir işlev bağımsız değişkenidir.  
  
## <a name="remarks"></a>Açıklamalar  

 Bir yerel değişkenin yönetilen yuva dizini, değişkenin meta veri bilgilerini almak için kullanılabilir  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableSymbol Arabirimi](icordebugvariablesymbol-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
