---
title: BeginEnumeration işlevi (yönetilmeyen API Başvurusu)
description: BeginEnumeration işlevi bir Numaralandırıcı numaralandırmanın başlangıcına sıfırlanır
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6057526ddbe2efed65f8569e829c35524829e43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708224"
---
# <a name="beginenumeration-function"></a>BeginEnumeration işlevi

Bir numaralandırıcıyı numaralandırmanın başına geri döndürür.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`lEnumFlags`\
'ndaki Numaralandırmada içerilen özellikleri denetleyen [açıklamalar](#remarks) bölümünde açıklanan bayrakların veya değerlerin bit düzeyinde birleşimi.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | İçindeki bayrakların birleşimi `lEnumFlags` geçersiz ya da geçersiz bir bağımsız değişken belirtildi. |
|`WBEM_E_UNEXPECTED` | 0x8004101D | İçin bir `BeginEnumeration` araya giren çağrı yapılmadan ikinci bir çağrı yapıldı [`EndEnumeration`](endenumeration.md) . |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemine bir çağrı kaydırır.

Bağımsız değişken olarak geçirilebilecek bayraklar, `lEnumFlags` *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.  Her bir grup için herhangi bir bayrak ile bir bayrak birleştirebilirsiniz. Ancak, aynı gruptaki Bayraklar birbirini dışlıyor.

**Grup 1**

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 4, | Yalnızca anahtarı oluşturan özellikleri ekleyin. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Yalnızca nesne başvuruları olan özellikleri ekleyin. |

**Grup 2**

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Numaralandırmayı yalnızca sistem özellikleriyle sınırlayın. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Yerel ve yayılmış özellikleri ekleyin, ancak Numaralandırmadaki sistem özelliklerini dışlayın. |

Sınıflar için:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Sabit listesini, sınıf tanımında geçersiz kılınan özelliklerle sınırlayın. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Sabit listesini geçerli sınıf tanımında geçersiz kılınan özelliklerle ve sınıfta tanımlanan yeni özelliklerle sınırlayın. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Ya `lEnumFlags` da ayarlanmış olup olmadığını denetlemek için bir değere karşı uygulanacak bir maske (bayrak yerine) `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` . |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Sabit listesini, sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlayın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Sabit listesini temel sınıflardan devralınan özelliklerle sınırlayın. |

Örnekler için:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Sabit listesini, sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlayın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Sabit listesini temel sınıflardan devralınan özelliklerle sınırlayın. |

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
