---
description: ': IMetaDataImport2:: GetGenericParamProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport2::GetGenericParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 06b522531282b4a30cdc8ebf001c16438e8612ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688734"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps Yöntemi

Belirtilen belirteç tarafından temsil edilen genel parametreyle ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `gp`  
 'ndaki Meta veri döndürülecek genel parametresini temsil eden belirteç.  
  
 `pulParamSeq`  
 dışı `Type` Parametrenin üst Oluşturucu veya yöntemdeki sıra konumu.  
  
 `pdwParamFlags`  
 dışı Genel parametresi için tanımlayan [CorGenericParamAttr](corgenericparamattr-enumeration.md) numaralandırması değeri `Type` .  
  
 `ptOwner`  
 dışı Parametrenin sahibini temsil eden bir TypeDef veya MethodDef belirteci.  
  
 `reserved`  
 dışı Gelecekteki genişletilebilirlik için ayrılmıştır.  
  
 `wzName`  
 dışı Genel parametrenin adı.  
  
 `cchName`  
 'ndaki `wzName` Arabelleğin boyutu.  
  
 `pchName`  
 dışı Adın, geniş karakter olarak döndürülen boyutu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
