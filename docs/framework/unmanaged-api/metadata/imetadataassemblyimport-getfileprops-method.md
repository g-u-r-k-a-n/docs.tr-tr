---
description: ': IMetaDataAssemblyImport:: GetFileProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataAssemblyImport::GetFileProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: 6814fee7edf5478a1ce2cf2b81d8f16fa62cd3f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784112"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps Metodu

Belirtilen meta veri imzasıyla dosyanın özelliklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `mdf`  
 'ndaki `mdFile` Özelliklerinin alınacağı dosyayı temsil eden meta veri belirteci.  
  
 `szName`  
 dışı Dosyanın basit adı.  
  
 `cchName`  
 'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .  
  
 `pchName`  
 dışı Aslında ' de döndürülen geniş karakter sayısı `szName` .  
  
 `ppbHashValue`  
 dışı Karma değere yönelik bir işaretçi. Bu, dosyanın SHA-1 algoritmasını kullanan karmadır.  
  
 `pcbHashValue`  
 dışı Döndürülen karma değerindeki geniş karakter sayısı.  
  
 `pdwFileFlags`  
 dışı Bir dosyaya uygulanan meta verileri tanımlayan bayrakların işaretçisi. Flags değeri bir veya daha fazla [CorFileFlags](corfileflags-enumeration.md) değerinin birleşimidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
