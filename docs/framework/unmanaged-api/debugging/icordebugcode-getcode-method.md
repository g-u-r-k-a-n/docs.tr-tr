---
description: ': ICorDebugCode:: GetCode yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugCode::GetCode Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: 329770fac4f2b375c01dd68e4ea7114e59c609b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711290"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode Metodu

Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır. Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır. Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](icordebugcode2-getcodechunks-method.md) kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `startOffset`  
 'ndaki İşlevin başlangıcının boşluğu.  
  
 `endOffset`  
 'ndaki İşlevin sonundaki fark.  
  
 `cBufferAlloc`  
 'ndaki `buffer` Kodun döndürüleceği dizinin boyutu.  
  
 `buffer`  
 dışı Kodun döndürüleceği dizi.  
  
 `pcBufferSize`  
 dışı Döndürülen bayt sayısı.  
  
## <a name="remarks"></a>Açıklamalar  

 İşlevin kodu birden çok Öbekle ayrılmışsa, bu değerler artan yerel uzaklığa göre birleştirilir. Yönerge sınırları denetlenmez.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetCodeChunks Yöntemi](icordebugcode2-getcodechunks-method.md)
