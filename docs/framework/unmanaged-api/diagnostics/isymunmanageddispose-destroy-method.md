---
title: ISymUnmanagedDispose::Destroy Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
ms.openlocfilehash: 5bd94cb851d4bb044d4ce03b97d6342a2c9652e4
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441324"
---
# <a name="isymunmanageddisposedestroy-method"></a>ISymUnmanagedDispose::Destroy Yöntemi
Alttaki nesnenin tüm iç başvuruları serbest bırakmaya ve sonraki yöntem çağrılarında hata döndürmesine neden olur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedDispose Arabirimi](isymunmanageddispose-interface.md)
