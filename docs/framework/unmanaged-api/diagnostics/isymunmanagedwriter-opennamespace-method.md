---
title: ISymUnmanagedWriter::OpenNamespace Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
ms.openlocfilehash: acbd49de7362d9c05a609a2d870af100637e10ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427911"
---
# <a name="isymunmanagedwriteropennamespace-method"></a>ISymUnmanagedWriter::OpenNamespace Yöntemi
Opens a new namespace. Call this method before defining methods or variables that occupy a namespace. Namespaces can be nested.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a>Parametreler  
 `name`  
 [in] A pointer to the name of the new namespace.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Gereksinimler  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [CloseNamespace Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
