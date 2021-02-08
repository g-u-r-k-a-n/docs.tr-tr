---
description: ': ICLRStrongName:: StrongNameTokenFromPublicKey yöntemi hakkında daha fazla bilgi'
title: ICLRStrongName::StrongNameTokenFromPublicKey Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: de245b151e5ca016a00793a8901c0fd990a3f804
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789751"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>ICLRStrongName::StrongNameTokenFromPublicKey Yöntemi

Ortak anahtarı temsil eden bir belirteç alır. Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pbPublicKeyBlob`  
 'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) türünde bir yapı.  
  
 `cbPublicKeyBlob`  
 'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob` .  
  
 `ppbStrongNameToken`  
 dışı Geçilen anahtara karşılık gelen tanımlayıcı ad belirteci `pbPublicKeyBlob` . Ortak dil çalışma zamanı, belirtecin döndürüleceği belleği ayırır. Çağıran, [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak bu belleği boşaltmalıdır.  
  
 `pcbStrongNameToken`  
 dışı Döndürülen tanımlayıcı ad belirtecinin bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="remarks"></a>Açıklamalar  

 Tanımlayıcı ad belirteci, meta verilerde anahtar bilgileri depolarken alan kazanmak için kullanılan bir ortak anahtarın kısaltılmış biçimidir. Özellikle, tanımlayıcı ad belirteçleri, bağımlı derlemeye başvurmak için derleme başvurularında kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** mscoree.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetPublicKey Yöntemi](iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob Yapısı](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
