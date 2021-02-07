---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugProcess6::D ecodeEvent yöntemi'
title: ICorDebugProcess6::DecodeEvent Yöntemi
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: 241b24335f96a250156effde34683c8f32a47e3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746223"
---
# <a name="icordebugprocess6decodeevent-method"></a>ICorDebugProcess6::DecodeEvent Yöntemi

Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarının yükünde kapsüllenmiş yönetilen hata ayıklama olaylarının kodunu çözer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,
        [in] DWORD dwThreadId,
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pRecord`  
 'ndaki Bir yönetilen hata ayıklama olayı hakkında bilgi içeren bir yerel özel durum ayıklama olayından bayt dizisine yönelik bir işaretçi.  
  
 `countBytes`  
 'ndaki `pRecord` Bayt dizisindeki öğelerin sayısı.  
  
 `format`  
 'ndaki Yönetilmeyen hata ayıklama olayının biçimini belirten [Cordebugrecordformat](cordebugrecordformat-enumeration.md) numaralandırma üyesi.  
  
 `dwFlags`  
 'ndaki Hedef mimarisine bağlı ve hata ayıklama olayı hakkında ek bilgiler belirten bir bit alanı. Windows sistemleri için, [Cordebugdecodeeventflagswindows](cordebugdecodeeventflagswindows-enumeration.md) sabit listesinin bir üyesi olabilir.  
  
 `dwThreadId`  
 'ndaki Özel durumun oluşturulduğu iş parçacığının işletim sistemi tanımlayıcısı.  
  
 `ppEvent`  
 dışı Kodu çözülmüş bir yönetilen hata ayıklama olayını temsil eden [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
