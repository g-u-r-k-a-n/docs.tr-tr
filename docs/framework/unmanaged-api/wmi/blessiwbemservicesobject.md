---
title: Blessıwbemservicesobject işlevi (yönetilmeyen API Başvurusu)
description: Blessıwbemservicesobject işlevi, Kullanıcı kimlik bilgilerinin bir IWbemServices nesnesine erişime izin verip vermediğini belirtir
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1aab2076f57f938715a3e65481a3540dc52279c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719755"
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject işlevi

Kullanıcı kimlik bilgilerinin belirtilen bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine erişime izin verip vermediğini belirtir.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a>Parametreler

`pIWbemServices`\
'ndaki WMI hizmeti nesnesine yönelik bir işaretçi.

`strUser`\
'ndaki Kullanıcı adı.

`strPassword`\
'ndaki İle ilişkili parola `strUser` .

`strAuthority`\
'ndaki Kullanıcının etki alanı adı. Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.

`impLevel`\
'ndaki Kimliğe bürünme düzeyi.

`authnLevel`\
'ndaki Yetkilendirme düzeyi.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *Winerror. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Bir veya daha fazla bağımsız değişken geçersiz. |
| `E_POINTER` | 0x80004003 | `pIWbemServices`, `null` değeridir. |
| `E_FAIL` | 0x80000008 | Belirtilmeyen bir hata oluştu. |
| `E_OUTOFMEMORY` | 0x80000002 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `S_OK` | 0 | İşlev çağrısı başarılı oldu. |

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi:** WMINet_Utils. IDL

 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
