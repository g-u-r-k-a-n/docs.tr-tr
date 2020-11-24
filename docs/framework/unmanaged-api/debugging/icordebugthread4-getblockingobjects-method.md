---
title: ICorDebugThread4::GetBlockingObjects Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: eb8692aebe7b702b5778b3f13e496d81dcd45784
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678553"
---
# <a name="icordebugthread4getblockingobjects-method"></a>ICorDebugThread4::GetBlockingObjects Metodu

İş parçacığı engelleme bilgileri sağlayan [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının sıralı bir listesini sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppBlockingObjectEnum`  
 dışı [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının sıralı numaralandırması için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Döndürülen Numaralandırmadaki ilk öğe, iş parçacığını engelleyen ilk yapıya karşılık gelir. İkinci öğe, ilk kez engellendiğinde zaman uyumsuz yordam çağrısı (APC) çalıştırılırken karşılaşılan bir engelleme öğesine karşılık gelir ve bu şekilde devam eder.  
  
 Sabit listesi yalnızca geçerli eşitlenmiş durumun süresi için geçerlidir.  
  
 Hata ayıklanan, eşitlenmiş durumda olduğu sürece bu yöntem çağrılmalıdır.  
  
 `ppBlockingObjectEnum`Geçerli bir işaretçi değilse, sonuç tanımsızdır.  
  
 Bir iş parçacığı engellenirse ve hata belirlenemiyorsa, yöntem hatayı gösteren bir HRESULT döndürür; Aksi takdirde, S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugThread4 Arabirimi](icordebugthread4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
