---
title: INotifySource2::SetNotifyFilter Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 99bce831405d722f1f1ca0ae56e60f95f2d905e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719937"
---
# <a name="inotifysource2setnotifyfilter-method"></a>INotifySource2::SetNotifyFilter Yöntemi

Bu kaynakla kullanılmak üzere bir bildirim filtresi atar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `in_NotifyFilter`  
 'ndaki Hata ayıklayıcı API 'SI için geri çağırmaları tanımlayan [NOTIFY_FILTER](notify-filter-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.  
  
 `in_pUserThreadFilter`  
 'ndaki Hata ayıklayıcı API 'SI için iş parçacıklarını tanımlayan [USER_THREAD](user-thread-structure.md) yapısına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [INotifySource2 Arabirimi](inotifysource2-interface.md)
- [INotifyConnection2 Arabirimi](inotifyconnection2-interface.md)
- [INotifySink2 Arabirimi](inotifysink2-interface.md)
