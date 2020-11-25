---
title: ICorDebugModule::GetName Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: c2aecadf8688e763a69bd40ca877e44bc0ce5c29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710052"
---
# <a name="icordebugmodulegetname-method"></a>ICorDebugModule::GetName Metodu

Modülün dosya adını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cchname`  
 'ndaki `szName` Dizinin boyutu.  
  
 `pcchName`  
 'ndaki Döndürülen adın uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı Döndürülen adı depolayan bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetName`Modülün dosya adı diskteki adla eşleşiyorsa Yöntem bir S_OK HRESULT döndürür. `GetName` ad, dinamik veya bellek içi bir modül için gibi, varsa HRESULT S_FALSE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
