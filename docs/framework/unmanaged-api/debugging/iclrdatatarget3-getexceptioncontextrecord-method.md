---
description: 'Şu konuda daha fazla bilgi edinin: ICLRDataTarget3:: GetExceptionContextRecord yöntemi'
title: ICLRDataTarget3::GetExceptionContextRecord Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: c722eaaf0f9935bc7adaa69a1792f934f631a728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794838"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord Metodu

Hedef işlemle ilişkili bağlam kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır. Örneğin, bir döküm hedefi için, bu, `ExceptionParam` Windows hata ayıklama Yardım Kitaplığı 'ndaki (DbgHelp) [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlevine bağımsız değişken aracılığıyla geçirilen bağlam kaydıyla eşdeğerdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `bufferSize`  
 'ndaki Giriş arabelleğinin bayt cinsinden boyutu. Bu, bağlam kaydına uyum sağlayacak kadar büyük olmalıdır.  
  
 `bufferUsed`  
 dışı `ULONG32` Gerçekte arabelleğe yazılan bayt sayısını alan türe yönelik bir işaretçi.  
  
 `buffer`  
 dışı Bağlam kaydının bir kopyasını alan bir bellek arabelleği işaretçisi. Özel durum kaydı, [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) türü olarak döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu. `HRESULT`Kodlar şunlar olabilir ancak bunlarla sınırlı değildir:  
  
|Dönüş kodu|Description|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu. Bağlam kaydı çıkış arabelleğine kopyalanmış.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Hedefle ilişkili bağlam kaydı yok.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Giriş arabelleği boyutu, bağlam kaydına uyum sağlayacak kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  

 [Bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) , Windows SDK tarafından belirtilen üst bilgilerde tanımlanan platforma özgü bir yapıdır.  
  
 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget3 Arabirimi](iclrdatatarget3-interface.md)
- [GetExceptionRecord Yöntemi](iclrdatatarget3-getexceptionrecord-method.md)
- [GetExceptionThreadID Yöntemi](iclrdatatarget3-getexceptionthreadid-method.md)
