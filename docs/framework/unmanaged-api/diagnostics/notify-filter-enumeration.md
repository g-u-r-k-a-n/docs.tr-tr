---
description: 'Hakkında daha fazla bilgi edinin: NOTIFY_FILTER numaralandırması'
title: NOTIFY_FILTER Numaralandırması
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
ms.openlocfilehash: 0ed09af0af302b08102b7b08fa72a2d255c5b231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761492"
---
# <a name="notify_filter-enumeration"></a>NOTIFY_FILTER Numaralandırması

Hata ayıklayıcı işlevleri için geri çağırmaları tanımlar. Daha fazla bilgi için bkz. [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) yöntemi.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|[INotifySink2:: Onsyncbelirtme](inotifysink2-onsynccallout-method.md) yönteminin çağrılması gerektiğini gösterir.|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|[INotifySink2:: OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) yönteminin çağrılması gerektiğini gösterir.|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|[INotifySink2:: OnSyncCallExit](inotifysink2-onsynccallexit-method.md) yönteminin çağrılması gerektiğini gösterir.|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|[INotifySink2:: OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) yönteminin çağrılması gerektiğini gösterir.|  
|`NOTIFY_FILTER_ALLSYNC`|Tüm [INotifySink2](inotifysink2-interface.md) yöntemlerinin çağrılması gerektiğini gösterir.|  
|`NOTIFY_FILTER_ALL`|Tüm mevcut ve gelecekteki bildirimleri etkinleştirir.|  
|`NOTIFY_FILTER_NONE`|Hiçbir bildirim yönteminin çağrılması gerektiğini gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Numaralandırmaları](diagnostics-symbol-store-enumerations.md)
