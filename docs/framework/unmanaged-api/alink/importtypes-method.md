---
title: ImportTypes Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 76d2b163f959111923bffb1348890f6fbb29828e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445683"
---
# <a name="importtypes-method"></a>ImportTypes Yöntemi
Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 ID of the assembly to import to.  
  
 `FileToken`  
 ID of the file to import from.  
  
 `dwScope`  
 Zero-based scope to import.  
  
 `phEnum`  
 Receives enumerator handle for the types in this scope.  
  
 `ppImportScope`  
 Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.  
  
 `pdwCountOfTypes`  
 Optionally receives count of types in the indicated scope.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Gereksinimler  
 Requires alink.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
