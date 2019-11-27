---
title: LinkResource Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
ms.openlocfilehash: 9e91d990a8f23335248043c59eb210e8c4155e3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445624"
---
# <a name="linkresource-method"></a>LinkResource Yöntemi
Bir kaynaktaki bağlantılar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Derlemenin KIMLIĞI.  
  
 `pszFileName`  
 Dosyanın adı.  
  
 `pszNewLocation`  
 İsteğe bağlı yeni dosya adı. NULL olmayan `pszFileName`, pszNewLocation ' a kopyalanacaktır.  
  
 `pszResourceName`  
 Kaynağın adı.  
  
 `dwFlags`  
 `mrPublic` ve `mrPrivate`gibi erişilebilirlik bayrakları. Bu parametre [DefineManifestResource metoduna](../metadata/imetadataassemblyemit-definemanifestresource-method.md)geçirilebilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
