---
title: IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 4149db74adfa26df221eed5c590766a023bb105e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448231"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi
Gets the set of properties for the assembly reference with the specified metadata signature.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mdar`  
 [in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.  
  
 `ppbPublicKeyOrToken`  
 [out] A pointer to the public key or the metadata token.  
  
 `pcbPublicKeyOrToken`  
 [out] The number of bytes in the returned public key or token.  
  
 `szName`  
 [out] The simple name of the assembly.  
  
 `cchName`  
 [in] The size, in wide chars, of `szName`.  
  
 `pchName`  
 [out] A pointer to the number of wide chars actually returned in `szName`.  
  
 `pMetaData`  
 [out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.  
  
 `ppbHashValue`  
 [out] A pointer to the hash value. This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.  
  
 `pcbHashValue`  
 [out] The number of wide chars in the returned hash value.  
  
 `pdwAssemblyRefFlags`  
 [out] A pointer to flags that describe the metadata applied to an assembly. The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.  
  
## <a name="return-value"></a>Dönüş Değeri  
 This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
