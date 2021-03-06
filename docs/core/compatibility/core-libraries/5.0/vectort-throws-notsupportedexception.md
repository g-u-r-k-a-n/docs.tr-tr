---
title: 'Son değişiklik: vektör, <T> NotSupportedException oluşturur'
description: Çekirdek .NET kitaplıklarında, vektör 'in <T> her zaman desteklenmeyen tür parametreleri için bir özel durum oluşturan .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: dccd39c01f4debd7d1432195e7f3cb14aeda5f65
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257017"
---
# <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a>Vektör, \<T> Desteklenmeyen türler için her zaman NotSupportedException oluşturur

<xref:System.Numerics.Vector%601?displayProperty=nameWithType> Artık, <xref:System.NotSupportedException> desteklenmeyen tür parametreleri için her zaman bir oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, üyeleri <xref:System.Numerics.Vector%601> <xref:System.NotSupportedException> Desteklenmeyen bir tür olduğunda her zaman bir oluşturmaz `T` . [](#unsupported-types) Donanım hızlandırmasının desteklediği kod yolları nedeniyle özel durum her zaman oluşturulmaz. Örneğin, `Vector<bool> + Vector<bool>` ARM32 gibi `default` donanım hızlandırmayan platformlarda bir özel durum oluşturmak yerine döndürüldü. Desteklenmeyen türler için, <xref:System.Numerics.Vector%601> Üyeler farklı platformlarda ve donanım yapılandırmalarında tutarsız davranışlar sergilen.

.NET 5 ' den başlayarak, <xref:System.Numerics.Vector%601> Üyeler <xref:System.NotSupportedException> `T` desteklenen bir tür olmadığında her zaman tüm donanım yapılandırmalarında bir oluşturur.

### <a name="unsupported-types"></a>Desteklenmeyen türler

Tür parametresi için desteklenen türler <xref:System.Numerics.Vector%601> şunlardır:

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

Desteklenen türler değişmemiştir, ancak gelecekte değişebilir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Tür parametresi için desteklenmeyen bir tür kullanmayın <xref:System.Numerics.Vector%601> .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Numerics.Vector%601?displayProperty=fullName> ve tüm üyelerini

<!--

#### Category

Core .NET libraries

### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
