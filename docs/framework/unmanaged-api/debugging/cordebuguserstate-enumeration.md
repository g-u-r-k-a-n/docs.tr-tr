---
description: 'Bu konuda daha fazla bilgi edinin: CorDebugUserState numaralandırması'
title: CorDebugUserState Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: c556e7943751fb8e159e3e0d0b9a71baf1f6b5b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661746"
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState Numaralandırması

Bir iş parçacığının kullanıcı durumunu belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>Üyeler  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|İş parçacığının sonlandırılması istendi.|  
|`USER_SUSPEND_REQUESTED`|İş parçacığını askıya alma istendi.|  
|`USER_BACKGROUND`|İş parçacığı arka planda çalışıyor.|  
|`USER_UNSTARTED`|İş parçacığı yürütmeyi başlatmadı.|  
|`USER_STOPPED`|İş parçacığı sonlandırıldı.|  
|`USER_WAIT_SLEEP_JOIN`|İş parçacığı başka bir iş parçacığının bir görevi tamamlamasını bekliyor.|  
|`USER_SUSPENDED`|İş parçacığı askıya alındı.|  
|`USER_UNSAFE_POINT`|İş parçacığı güvenli olmayan bir noktada. Diğer bir deyişle, iş parçacığı, atık toplamayı engelleyebileceği bir yürütme noktasıdır.<br /><br /> Hata ayıklama olayları güvenli olmayan noktalarından gönderilebilir, ancak bir iş parçacığının güvenli olmayan bir noktada askıya alınması, iş parçacığı sürdürülene kadar kilitlenmeye neden olur. Güvenli ve güvenli olmayan noktaları, tam zamanında (JıT) ve çöp toplama uygulamasıyla belirlenir.|  
|`USER_THREADPOOL`|İş parçacığı iş parçacığı havuzundan yapılır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir iş parçacığının kullanıcı durumu, iş parçacığının hata ayıklayıcı tarafından incelediği durumdur. Bir iş parçacığında Kullanıcı durumlarının bir birleşimi olabilir.  
  
 Bir iş parçacığının kullanıcı durumunu almak için [ICorDebugThread:: GetUserState](icordebugthread-getuserstate-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
