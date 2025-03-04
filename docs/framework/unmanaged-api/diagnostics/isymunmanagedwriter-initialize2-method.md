---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: Initialize2 yöntemi'
title: ISymUnmanagedWriter::Initialize2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 0d4c769c9f1b571296cbfe159057df083a6d5ca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762285"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 Yöntemi

Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar ve hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar. Bu yöntem, program veritabanı (PDB) dosyasının son konumunu ayarlamanıza de olanak tanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a>Parametreler  

 `emitter`  
 'ndaki Meta veri verici arabirimine yönelik bir işaretçi.  
  
 `tempfilename`  
 'ndaki `WCHAR` Hata ayıklama simgelerinin yazıldığı dosya adını içeren bir işaretçisi. Dosya adları kullanmayan bir yazıcı için dosya adı belirtilmişse, bu parametre yoksayılır.  
  
 `pIStream`  
 'ndaki Belirtilmişse, sembol yazıcı sembolleri <xref:System.Runtime.InteropServices.ComTypes.IStream> parametresinde belirtilen dosya yerine, belirtilen içine yayar `filename` . `pIStream`Parametresi isteğe bağlıdır.  
  
 `fFullBuild`  
 [in] `true` Bu bir tam yeniden oluşturma ise `false` Bu bir artımlı derleme ise.  
  
 `finalfilename`  
 'ndaki , `WCHAR` Pdb dosyasının son konumunun yol dizesi olan bir işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
- [Initialize Yöntemi](isymunmanagedwriter-initialize-method.md)
