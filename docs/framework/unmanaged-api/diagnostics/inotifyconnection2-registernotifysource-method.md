---
description: 'Daha fazla bilgi edinin: INotifyConnection2:: RegisterNotifySource Yöntemi'
title: INotifyConnection2::RegisterNotifySource Yöntemi
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: 97aacf7f2005a1e9f21acebd6c5f5ed65867b245
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800324"
---
# <a name="inotifyconnection2registernotifysource-method"></a>INotifyConnection2::RegisterNotifySource Yöntemi

Belirtilen bir bildirim kaynağını yükleme.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `in_pNotifySource`  
 'ndaki Bildirim kaynağı olarak kullanılacak nesneyi belirtir.  
  
 `out_ppNotifySink`  
 dışı Bildirim havuzu olarak kullanılacak nesneyi alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [INotifyConnection2 Arabirimi](inotifyconnection2-interface.md)
- [INotifySource2 Arabirimi](inotifysource2-interface.md)
- [INotifySink2 Arabirimi](inotifysink2-interface.md)
- [UnregisterNotifySource Yöntemi](inotifyconnection2-unregisternotifysource-method.md)
