---
description: ': Imetadatayayma::D efineNestedType yöntemi hakkında daha fazla bilgi'
title: IMetaDataEmit::DefineNestedType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 1b0c5c8d1bffa425b2019a4434042c84a0069907
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753386"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType Yöntemi

Bir tür tanımının meta veri imzasını oluşturur, `mdTypeDef` Bu tür için bir belirteç döndürür ve tanımlı türün parametre tarafından başvurulan türün bir üyesi olduğunu belirtir `tdEncloser` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `szTypeDef`  
 'ndaki Unicode 'daki türün adı.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` özelliklerine. Bu bir değer bit değeridir `CorTypeAttr` .  
  
 `tkExtends`  
 'ndaki Taban sınıfının belirteci. Bu bir ya da `mdTypeDef` bir `mdTypeRef` belirteç.  
  
 `rtkImplements`[]  
 'ndaki Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir belirteç dizisi.  
  
 `tdEncloser`  
 'ndaki Kapsayan türün belirteci. Dizinin son öğesi olmalıdır `mdTokenNil` .  
  
 `ptd`  
 dışı `mdTypeDef` Atanan belirteç.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
