---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataEmit2:: SaveDeltaToStream yöntemi'
title: IMetaDataEmit2::SaveDeltaToStream Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: ce2e7822a5220a8ab1264a6e18337ba0f7828e3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771710"
---
# <a name="imetadataemit2savedeltatostream-method"></a>IMetaDataEmit2::SaveDeltaToStream Yöntemi

Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen akışa kaydeder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pIStream`  
 'ndaki Değişikliklerin kaydedileceği yazılabilir akışa yönelik bir arabirim işaretçisi.  
  
 `dwSaveFlags`  
 'ndaki Ayrılamadı. Bu değer sıfır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
