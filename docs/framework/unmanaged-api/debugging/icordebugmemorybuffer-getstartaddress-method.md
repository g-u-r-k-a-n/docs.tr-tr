---
title: 'ICorDebugMemoryBuffer:: GetStartAddress yöntemi'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: f76bf1479db987e4956d8b876f67d629d927f956
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710772"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a>ICorDebugMemoryBuffer:: GetStartAddress yöntemi

Bellek arabelleğinin başlangıç adresini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `address`  
 dışı Bellek arabelleğinin başlangıç adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!WARNING]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMemoryBuffer Arabirimi](icordebugmemorybuffer-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
