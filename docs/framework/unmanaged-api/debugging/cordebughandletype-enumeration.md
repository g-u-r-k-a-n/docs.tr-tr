---
description: 'Daha fazla bilgi edinin: Cordebugghandlitype numaralandırması'
title: CorDebugHandleType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
ms.openlocfilehash: 294fd7b04018331489e51d12930bcbbb81ec340a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662123"
---
# <a name="cordebughandletype-enumeration"></a>CorDebugHandleType Numaralandırması

Tanıtıcı türünü gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`HANDLE_STRONG`|Tanıtıcı güçlü olduğundan, bir nesnenin çöp toplama tarafından geri kazanımasını önler.|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|Tanıtıcı zayıf, bu da bir nesnenin çöp toplama tarafından geri kazanımasını engellemez.<br /><br /> Nesne toplandığında tanıtıcı geçersiz hale gelir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
