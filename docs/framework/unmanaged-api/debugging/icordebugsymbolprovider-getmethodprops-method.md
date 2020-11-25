---
title: 'ICorDebugSymbolProvider:: GetMethodProps Yöntemi'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 5412b2f06445627c1240d6c8f4efb3ce6bbbec54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730831"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider:: GetMethodProps Yöntemi

Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `codeRVA`  
 'ndaki Hangi bilgilerin alınacağı konusunda yöntemde göreli bir sanal adres.  
  
 `pMethodToken`  
 dışı Metodun meta veri belirtecine yönelik bir işaretçi.  
  
 `pcGenericParams`  
 dışı Bu metotla ilişkili genel parametre sayısına yönelik bir işaretçi.  
  
 `cbSignature`  
 'ndaki `signature` Dizinin boyutu. Açıklamalar bölümüne bakın.  
  
 `pcbSignature`  
 dışı Döndürülen dizinin boyutuna yönelik bir işaretçi `signature` .  
  
 `signature`  
 dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.  
  
## <a name="remarks"></a>Açıklamalar  

 Yöntemin dizisinin gerekli boyutunu almak için `signature` , `cbSignature` bağımsız değişkenini 0 ve `signature` **null** olarak ayarlayın. Yöntemi döndüğünde, `pcbSignature` dizi için gereken bayt sayısını içerir `signature` .  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetTypeProps Yöntemi](icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider Arabirimi](icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
