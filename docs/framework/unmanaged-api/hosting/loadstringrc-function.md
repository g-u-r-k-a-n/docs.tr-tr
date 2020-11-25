---
title: LoadStringRC İşlevi
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 16f95f8fce20f2cf46d4cda214e4494bd288bf60
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727555"
---
# <a name="loadstringrc-function"></a>LoadStringRC İşlevi

Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini bir hata iletisine çevirir.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `iResourceID`  
 'ndaki HRESULT.  
  
 `szBuffer`  
 dışı Başarılı bir şekilde tamamlandıktan sonra hata iletisini içeren bir arabellek.  
  
 `iMax`  
 'ndaki Hata iletisi arabelleğinin boyutu.  
  
 `bQuiet`  
 'ndaki LIP.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`szBuffer` null veya `iMax` sıfır (0).|  
  
## <a name="remarks"></a>Açıklamalar  

 Yöntem başarıyla tamamlanmazsa `szBuffer` boş bir dize içerir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll ve Mscorwks.dll. Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine MSCorEE.dll kullanın.  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LoadStringRCEx İşlevi](loadstringrcex-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
