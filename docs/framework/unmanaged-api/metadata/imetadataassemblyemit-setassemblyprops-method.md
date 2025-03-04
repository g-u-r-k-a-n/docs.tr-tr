---
description: ': IMetaDataAssemblyEmit:: SetAssemblyProps Yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: d5dfb5fa472bb83863c8e4909998deeb2b9fc53b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678204"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi

Belirtilen `Assembly` meta veri yapısını değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pma`  
 'ndaki `Assembly` Değiştirilecek meta veri yapısını belirten meta veri belirteci.  
  
 `pbPublicKey`  
 'ndaki Derlemenin yayımcısının ortak anahtarına yönelik bir işaretçi.  
  
 `cbPublicKey`  
 'ndaki Bayt cinsinden boyut `pbPublicKey` .  
  
 `ulHashAlgId`  
 'ndaki Derleme dosyalarını karma hale yüklemek için kullanılan karma algoritmanın tanımlayıcısı.  
  
 `szName`  
 'ndaki Derlemenin insanların okunabilir metin adı.  
  
 `pMetaData`  
 'ndaki Derleme için sürüm, platform ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA işaretçisi.  
  
 `dwAssemblyFlags`  
 'ndaki Derlemenin çeşitli özniteliklerini belirten, [AssemblyFlags](assemblyflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  

 `Assembly`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineAssembly](imetadataassemblyemit-defineassembly-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
