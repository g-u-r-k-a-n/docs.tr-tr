---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedmethod:: Getscopefromsapmasını yöntemi'
title: ISymUnmanagedMethod::GetScopeFromOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: 87dd1f1732ec5d7c8669dbc2bf73b0b6128aafa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721326"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a>ISymUnmanagedMethod::GetScopeFromOffset Metodu

Bu yöntem içinde verilen sapmayı kapsayan en kapsamlı sözcük kapsamını alır. Bu, yerel değişken aramalarını başlatmak için kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  

 `offset`  
 'ndaki `ULONG` Bu, sapmayı içeren bir.  
  
 `pRetVal`  
 dışı Döndürülen [ıdimunmanagedscope](isymunmanagedscope-interface.md) arabirimine ayarlanmış bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedMethod Arabirimi](isymunmanagedmethod-interface.md)
