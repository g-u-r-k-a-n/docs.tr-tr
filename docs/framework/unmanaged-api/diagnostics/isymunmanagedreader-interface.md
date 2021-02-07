---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader arabirimi'
title: ISymUnmanagedReader Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
ms.openlocfilehash: bad4fdbac3bf6f03fa0db79ce54a5b0ca897028f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763806"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader Arabirimi

Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDocument Yöntemi](isymunmanagedreader-getdocument-method.md)|Bir belge bulur.|  
|[GetDocuments Yöntemi](isymunmanagedreader-getdocuments-method.md)|Sembol deposunda tanımlanan tüm belgelerin dizisini döndürür.|  
|[GetDocumentVersion Yöntemi](isymunmanagedreader-getdocumentversion-method.md)|Belirtilen belgenin belirtilen sürümünü alır.|  
|[GetGlobalVariables Yöntemi](isymunmanagedreader-getglobalvariables-method.md)|Tüm genel değişkenleri döndürür.|  
|[GetMethod Yöntemi](isymunmanagedreader-getmethod-method.md)|Yöntem belirteci verilen bir sembol okuyucu yöntemini alır.|  
|[GetMethodByVersion Yöntemi](isymunmanagedreader-getmethodbyversion-method.md)|Yöntem belirteci ve bir düzenleme ve kopyalama sürümü numarası verilen bir sembol okuyucu yöntemi alır.|  
|[GetMethodFromDocumentPosition Yöntemi](isymunmanagedreader-getmethodfromdocumentposition-method.md)|Bir belgede verilen konumdaki kesme noktasını içeren yöntemi döndürür.|  
|[GetMethodsFromDocumentPosition Yöntemi](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Her biri bir belgede verilen konumdaki kesme noktasını içeren bir yöntem dizisi döndürür.|  
|[GetMethodVersion Yöntemi](isymunmanagedreader-getmethodversion-method.md)|Yöntem sürümünü alır.|  
|[GetNamespaces Yöntemi](isymunmanagedreader-getnamespaces-method.md)|Bu sembol deposu içindeki genel kapsamda tanımlanan ad alanlarını alır.|  
|[GetSymAttribute Yöntemi](isymunmanagedreader-getsymattribute-method.md)|Özel bir özniteliği adına göre alır.|  
|[GetSymbolStoreFileName Yöntemi](isymunmanagedreader-getsymbolstorefilename-method.md)|Sembol deposunun disk üzerindeki dosya adını sağlar.|  
|[GetUserEntryPoint Yöntemi](isymunmanagedreader-getuserentrypoint-method.md)|Varsa modül için Kullanıcı giriş noktası olarak belirtilen yöntemi döndürür.|  
|[GetVariables Yöntemi](isymunmanagedreader-getvariables-method.md)|Üst ve adı verilen yerel olmayan bir değişken döndürür.|  
|[Initialize Yöntemi](isymunmanagedreader-initialize-method.md)|Sembol okuyucuyu, bu okuyucunun ilişkilendirildiği meta veri alma arabirimiyle birlikte modülün dosya adı ile başlatır.|  
|[ReplaceSymbolStore Yöntemi](isymunmanagedreader-replacesymbolstore-method.md)|Var olan sembol deposunu bir Delta sembol deposu ile değiştirir.|  
|[UpdateSymbolStore Yöntemi](isymunmanagedreader-updatesymbolstore-method.md)|Var olan sembol deposunu bir Delta sembol deposu ile güncelleştirir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 Arabirimi](isymunmanagedreader2-interface.md)
