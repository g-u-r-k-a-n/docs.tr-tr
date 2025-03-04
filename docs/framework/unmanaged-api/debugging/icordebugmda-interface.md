---
description: ': ICorDebugMDA arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugMDA Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: 8e6e779c58d71b07edc9b63dff72aef728ebe050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801132"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA Arabirimi

Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDescription Yöntemi](icordebugmda-getdescription-method.md)|Bu MDA 'ın açıklamasını içeren bir dize alır.|  
|[GetFlags Yöntemi](icordebugmda-getflags-method.md)|Bu MDA ile ilişkili bayrakları alır.|  
|[GetName Yöntemi](icordebugmda-getname-method.md)|Bu MDA 'ın adını içeren bir dize alır.|  
|[GetOSThreadId Yöntemi](icordebugmda-getosthreadid-method.md)|Bu MDA 'ın üzerinde yürütüldüğü işletim sistemi iş parçacığı tanımlayıcısını alır.|  
|[GetXML Yöntemi](icordebugmda-getxml-method.md)|Bu MDA ile ilişkili tam XML akışını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
