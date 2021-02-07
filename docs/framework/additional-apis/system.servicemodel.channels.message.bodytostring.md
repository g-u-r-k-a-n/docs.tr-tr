---
description: 'Daha fazla bilgi edinin: Message. BodyToString yöntemi'
title: Message. BodyToString yöntemi (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: babcd881d191ff46b98e9999c4ff04166479a68d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699382"
---
# <a name="messagebodytostring-method"></a>Message. BodyToString yöntemi

Yöntemi çağırarak ileti gövdesini bir dizeye dönüştürür <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> .

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>Parametreler

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  İleti gövdesini bir dizeye dönüştürmek için kullanılan yazıcı.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `Message.BodyToString`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.ServiceModel.Channels>

**Bütünleştirilmiş kod:** System.ServiceModel.dll

**.NET Framework sürümleri:** 3,0 sürümünden itibaren kullanılabilir.
