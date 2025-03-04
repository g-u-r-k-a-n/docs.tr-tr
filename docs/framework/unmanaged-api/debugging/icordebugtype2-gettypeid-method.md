---
description: 'Daha fazla bilgi edinin: ICorDebugType2:: GetTypeId yöntemi'
title: 'ICorDebugType2:: GetTypeId metodu'
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 8143ede1a11ee5f73c49fc723920f53430339ed0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738110"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2:: GetTypeId metodu

Bu tür için bir [COR_TYPEID](cor-typeid-structure.md) alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `id`  
 dışı Bu ICorDebugType için [COR_TYPEID](cor-typeid-structure.md) işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu. `HRESULT`Kodlar şunları içerir:  
  
|Dönüş kodu|Description|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu. Yöntem geçerli bir [COR_TYPEID](cor-typeid-structure.md)aldı.|  
|`CORDBG_E_CLASS_NOT_LOADED`|Tür yüklenmedi.|  
|`CORDBG_E_UNSUPPORTED`|Tür desteklenmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, çalışma zamanına yüklenmiş olan [COR_TYPEID](cor-typeid-structure.md)veya bir tür çalışma zamanına yüklenmiş bir türü tanımlayan donuk bir tanıtıcı görevi gören ICorDebugType öğesinden bir eşleme sağlar.  
  
 ICorDebugType 'ın gösterdiği tür henüz yüklenmediyse, bu yöntem döndürür `CORDBG_E_CLASS_NOT_LOADED` .  Tür desteklenmiyorsa, döndürür `CORDBG_E_UNSUPPORTED` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugType2 Arabirimi](icordebugtype2-interface.md)
