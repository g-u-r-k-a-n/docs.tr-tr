---
title: GetPropertyHandle işlevi (yönetilmeyen API Başvurusu)
description: GetPropertyHandle işlevi bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5af003f0295e0b403727f9af6b03ab81c4b8bccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101867"
---
# <a name="getpropertyhandle-function"></a>GetPropertyHandle işlevi

Bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki Bir [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) örneği işaretçisi.

`wszPropertyName`\
'ndaki Özellik adını içeren UTF16 kodlu karakterlerin null ile sonlandırılmış dizesi.

`pType`\
dışı Özelliğin CıM türünü temsil eden [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) numaralandırma üyesine yönelik bir işaretçi.

`pHandle`\
dışı Özellik tanıtıcısını içeren tamsayıya yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik adı bulunamadı. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100C | İstenen özellik `CIM_OBJECT` veya `CIM_ARRAY`. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) yöntemine bir çağrı kaydırır.

Bu tanıtıcıyı, özellik değerlerini okumak veya yazmak için [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) yöntemlerini kullanırken özellikleri tanımlamak için kullanabilirsiniz.

İşleyiciler, `CIM_OBJECT` ve `CIM_ARRAY`dışındaki tüm veri türlerinin özellikleri için alınabilir. Döndürülen tutamaçlar bir sınıfın tüm örneklerinde çalışır.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
