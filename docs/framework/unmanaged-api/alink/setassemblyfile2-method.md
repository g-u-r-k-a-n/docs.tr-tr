---
description: 'Daha fazla bilgi edinin: SetAssemblyFile2 yöntemi'
title: SetAssemblyFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 890646b718c211b476d013daf021f8889198c1ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662409"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 Yöntemi

Yeni bir derleme için adını ve seçeneklerini ayarlar. İlişkisiz modüller üretmeniz durumunda bu yöntemi çağırmayın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `pszFilename`  
 Bildirim dosyasının adı.  
  
 `pEmitter`  
 Bu dosya için [IMetaDataEmit2 arabirimi](../metadata/imetadataemit2-interface.md) arabirimi.  
  
 `afFlags`  
 [AssemblyFlags numaralandırması](../metadata/assemblyflags-enumeration.md)tarafından temsil edilen seçenekler.  
  
 `pAssemblyID`  
 Oluşturulan derlemenin benzersiz KIMLIĞINI alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
