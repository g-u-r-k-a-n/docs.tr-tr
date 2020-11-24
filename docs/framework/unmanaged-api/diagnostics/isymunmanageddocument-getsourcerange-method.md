---
title: ISymUnmanagedDocument::GetSourceRange Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: f5d7df60a7b9c728b73fe6592226a8b6734b1e66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692156"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange Yöntemi

Eklenmiş kaynağın belirtilen aralığını verilen arabelleğe döndürür. Arabellek, kaynağı tutabilecek kadar büyük olmalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `startLine`  
 'ndaki Geçerli belgedeki başlangıç satırı.  
  
 `startColumn`  
 'ndaki Geçerli belgedeki başlangıç sütunu.  
  
 `endLine`  
 'ndaki Geçerli belgedeki son satır.  
  
 `endColumn`  
 'ndaki Geçerli belgedeki son sütun.  
  
 `cSourceBytes`  
 'ndaki Kaynağın bayt cinsinden boyutu.  
  
 `pcSourceBytes`  
 dışı Kaynak boyutunu alan değişken için bir işaretçi.  
  
 `source`  
 dışı Kaynak belge için bayt cinsinden belirtilen aralığın boyutu ve uzunluğu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedDocument Arabirimi](isymunmanageddocument-interface.md)
