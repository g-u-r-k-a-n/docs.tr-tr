---
title: GetMethodOrigin işlevi (yönetilmeyen API Başvurusu)
description: GetMethodOrigin işlevi, bir yöntemin bildirildiği sınıfı belirler.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 434392ffb4d9124e319bcd9c42fdd340d3fec5b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722784"
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin işlevi

Bir yöntemin bildirildiği sınıfı belirler.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`wszMethodName`  
'ndaki Sahip sınıfı istenen nesne için yöntemin adı.

`pstrClassName`  
dışı Yöntemine sahip olan sınıfın adını alır.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen yöntem bulunamadı. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemine bir çağrı kaydırır.

Bir sınıf bir veya daha fazla taban sınıftan Yöntemler devraldığı için, geliştiriciler genellikle belirli bir yöntemin tanımlandığı sınıfı belirleyebilmek ister.

Parametresi `pstrClassName` bir parametre olduğundan, işlev çağrılmadan önce geçerli bir işaret içermemelidir `BSTR` `out` ; Bu işaretçi, işlev çağrıldıktan sonra serbest bırakılmaz.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
