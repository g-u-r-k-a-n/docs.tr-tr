---
description: ': ICorDebugAppDomain2:: GetArrayOrPointerType yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugAppDomain2::GetArrayOrPointerType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: e42d105e807bdb8c81f2d6f8ef6c2f65a4081d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754231"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType Yöntemi

Belirtilen türde bir diziyi veya belirtilen türe bir işaretçi ya da başvuru alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `elementType`  
 'ndaki Oluşturulacak temel yerel türü (bir dizi, işaretçi veya başvuru) belirten CorElementType numaralandırması değeri.  
  
 `nRank`  
 'ndaki Dizinin derece (yani boyut sayısı). `elementType`Bir işaretçi veya başvuru türü belirtiyorsa bu değer 0 olmalıdır.  
  
 `pTypeArg`  
 'ndaki Oluşturulacak dizi, işaretçi veya başvurunun türünü temsil eden ICorDebugType nesnesine yönelik bir işaretçi.  
  
 `ppType`  
 dışı `ICorDebugType` Oluşturulan diziyi, işaretçi türünü veya başvuru türünü temsil eden nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 *ElementType* değeri aşağıdakilerden biri olmalıdır:  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY veya ELEMENT_TYPE_SZARRAY  
  
 *ElementType* değeri ELEMENT_TYPE_PTR veya element_type_byref, *nRank* sıfır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
