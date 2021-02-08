---
description: 'Daha fazla bilgi edinin: ECustomDumpFlavor numaralandırması'
title: ECustomDumpFlavor Numaralandırması
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 3ef118368fc827472bdaacb0b03d8c2011275056
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785539"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor Numaralandırması

Hataları bildirirken yığın dökümünün özel bir alt kümesine hangi öğelerin ekleneceğini belirten değerler içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|Özel yığın dökümünün bir mini döküm olarak başlaması gerektiğini ve aynı yönteme geçirilen tüm [Customdumpitem](customdumpitem-structure.md) örnekleri tarafından belirtilen ek verileri dahil edileceğini belirtir.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Özel yığın dökümünden dinamik olarak ayrılmamış tüm çalışma zamanı durum verilerini toplaması gerektiğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ECustomDumpFlavor` [Ilrerrorreportingmanager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) metoduna türünde bir parametre geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ECustomDumpItemKind Numaralandırması](ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager Arabirimi](iclrerrorreportingmanager-interface.md)
- [Barındırma Numaralandırmaları](hosting-enumerations.md)
