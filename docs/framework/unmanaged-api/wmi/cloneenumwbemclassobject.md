---
title: CloneEnumWbemClassObject işlevi (yönetilmeyen API Başvurusu)
description: CloneEnumWbemClassObject işlevi bir Numaralandırıcı 'nın mantıksal bir kopyasını oluşturur.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fa8a7f436c018e3e083be452d300eb21e17f93f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708133"
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject işlevi

Bir Numaralandırıcının mantıksal bir kopyasını oluşturur ve geçerli konumunu bir numaralandırıcıda korur.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a>Parametreler

`ppEnum`\
dışı Yeni bir [ıenumwbemclassobject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)için bir işaretçi alır.

`authLevel`\
'ndaki Yetkilendirme düzeyi.

`impLevel`\
'ndaki Kimliğe bürünme düzeyi.

`pCurrentEnumWbemClassObject`\
dışı Kopyalanacak [ıenumwbemclassobject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) örneğine yönelik bir işaretçi.

`strUser`\
'ndaki Kullanıcı adı. Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.

`strPassword`\
'ndaki Parola. Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.

`strAuthority`\
'ndaki Kullanıcının etki alanı adı. Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçersiz. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeterli bellek yok. işlem tamamlanamadı. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [ıenumwbemclassobject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemine bir çağrı kaydırır.

Bu yöntem yalnızca bir "en iyi çaba" kopyası oluşturur. Birçok CıM nesnesinin dinamik doğası nedeniyle, yeni Numaralandırıcı kaynak numaralandırıcı olarak aynı nesne kümesini Numaralandırmıyor olabilir.

İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.

## <a name="example"></a>Örnek

Bir örnek için, bkz. [ıenumwbemclassobject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemi.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi:** WMINet_Utils. IDL

 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
