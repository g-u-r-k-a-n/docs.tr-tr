---
description: 'Daha fazla bilgi edinin: StrongNameGetBlobFromImage Işlevi'
title: StrongNameGetBlobFromImage İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
ms.openlocfilehash: c68d6914d47fbb711c49c1e8432cae1bf33e771f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636359"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage İşlevi

Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pbBase`  
 'ndaki Eşlenen derleme bildiriminin bellek adresi.  
  
 `dwLength`  
 'ndaki İçindeki görüntünün bayt cinsinden boyutu `pbBase` .  
  
 `pbBlob`  
 'ndaki Görüntünün ikili gösterimini içeren bir arabellek.  
  
 `pcbBlob`  
 [in, out] İstenen en büyük boyut (bayt) `pbBlob` . Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` başarıyla tamamlandığında; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 `StrongNameGetBlobFromImage`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetBlobFromImage Yöntemi](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob Yöntemi](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
