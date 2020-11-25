---
title: CorGCReferenceType Sabit Listesi
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: e2903637faa11a3c0a62080cc6fafcf1fc668a56
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705000"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType Sabit Listesi

Atık olarak toplanmış bir nesnenin kaynağını tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|`CorHandleStrong`|Nesne işleyicisi tablosundan bir güçlü başvuruya işleyici.|  
|`CorHandleStrongPinning`|Nesne tutamacı tablosundan sabitlenmiş güçlü başvuruya yönelik bir tanıtıcı.|  
|`CorHandleWeakShort`|Nesne tutamacı tablosundan zayıf başvuruya yönelik bir tanıtıcı.|  
|`CorHandleWeakRefCount`|Nesne tutamacı tablosundan zayıf başvuru sayılı bir nesne için bir tanıtıcı.|  
|`CorHandleStrongRefCount`|Nesne tutamacı tablosundan başvuru sayılı bir nesne için tanıtıcı.|  
|`CorHandleStrongDependent`|Nesne tutamacı tablosundan bağımlı nesneye yönelik bir tanıtıcı.|  
|`CorHandleStrongAsyncPinned`|Nesne işleyicisi tablosundan bir zaman uyumsuz sabitlenmiş nesne.|  
|`CorHandleStrongSizedByref`|Atık toplama zamanında tüm nesnelerin ve nesne köklerinin toplu kapanışının yaklaşık boyutunu tutan bir güçlü işleyici.|  
|`CorReferenceStack`|Yönetilen yığından bir başvuru.|  
|`CorReferenceFinalizer`|Sonlandırıcı sırasından bir başvuru.|  
|Yalnızca corhandlestrong|Yalnızca tanıtıcı tablosundan güçlü başvurular döndürür. Bu değer yalnızca [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) yöntemi tarafından kullanılır.|  
|`CorHandleWeakOnly`|Tanıtıcı tablosundan yalnızca zayıf başvuruları döndürün. Bu değer yalnızca [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) yöntemi tarafından kullanılır.|  
|`CorHandleAll`|Tanıtıcı tablosundan tüm başvuruları döndürün. Bu değer yalnızca [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) yöntemi tarafından kullanılır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `CorGCReferenceType`Sabit listesi aşağıdaki gibi kullanılır:  
  
- `type` [Cor_gc_reference](cor-gc-reference-structure.md) yapısı alanının değeri olarak, bir başvurunun veya tanıtıcının kaynağını gösterir.  
  
- `types` [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) metoduna bağımsız değişken olarak, sabit listesine dahil edilecek tanıtıcı türlerini belirtir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
