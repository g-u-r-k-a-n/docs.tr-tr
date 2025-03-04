---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter::D efineLocalVariable yöntemi'
title: ISymUnmanagedWriter::DefineLocalVariable Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
ms.openlocfilehash: cd817e3002c2a55fd8bbd7e565283752926f746b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762376"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable Yöntemi

Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar. Bu yöntem, bir kapsam genelinde birden çok evye sahip olan aynı ada sahip bir değişken için birden çok kez çağrılabilir. Ancak bu durumda, `startOffset` ve `endOffset` parametrelerinin değerleri çakışmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>Parametreler  

 `name`  
 'ndaki `WCHAR` Yerel değişken adını tanımlayan bir işaretçisi.  
  
 `attributes`  
 'ndaki Yerel değişken öznitelikleri.  
  
 `cSig`  
 'ndaki `ULONG32` Bu, arabelleğin bayt cinsinden boyutunu belirten bir `signature` .  
  
 `signature`  
 'ndaki Yerel değişken imzası.  
  
 `addrKind`  
 'ndaki Adres türü.  
  
 `addr1`  
 'ndaki Parametre belirtiminin ilk adresi.  
  
 `addr2`  
 'ndaki Parametre belirtiminin ikinci adresi.  
  
 `addr3`  
 'ndaki Parametre belirtiminin üçüncü adresi.  
  
 `startOffset`  
 'ndaki Değişkenin başlangıç boşluğu. Bu parametre isteğe bağlıdır. 0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır. Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.  
  
 `endOffset`  
 'ndaki Değişkenin bitiş boşluğu. Bu parametre isteğe bağlıdır. 0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır. Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
- [DefineGlobalVariable Yöntemi](isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2 Yöntemi](isymunmanagedwriter2-definelocalvariable2-method.md)
