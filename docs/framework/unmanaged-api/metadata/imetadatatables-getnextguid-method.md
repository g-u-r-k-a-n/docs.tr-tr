---
description: ': IMetaDataTables:: GetNextGuid metodu hakkında daha fazla bilgi edinin'
title: IMetaDataTables::GetNextGuid Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: 86c248bf503410a07fc0b4cf622694c4da213c34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688110"
---
# <a name="imetadatatablesgetnextguid-method"></a>IMetaDataTables::GetNextGuid Metodu

Geçerli tablo sütunundaki sonraki GUID değerinin dizinini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ixGuid`  
 'ndaki Bir GUID tablo sütunundaki dizin değeri.  
  
 `pNext`  
 dışı Sonraki GUID değerinin dizinine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

  Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz. GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği". Belgeler çevrimiçi olarak kullanılabilir; bkz. [ecma C# ve ortak dil altyapısı standartları](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak DIL altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
