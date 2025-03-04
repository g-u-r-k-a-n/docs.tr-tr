---
title: Ara değerli dizeler
description: 'Doğrudan içerdikleri F # ifadelerini gömmeyi sağlayan özel bir dize biçimi olan, enterpolasyonlu dizeler hakkında bilgi edinin.'
ms.date: 11/12/2020
ms.openlocfilehash: 8c552b44cea7d6c51ec333b6bdd4d407c6f10da7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829693"
---
# <a name="interpolated-strings"></a>Ara değerli dizeler

Enterpolasyonlu dizeler, bunlara F # ifadeleri eklemenize olanak sağlayan [dizelerdir](strings.md) . Bir dizenin değerinin bir değer veya ifadenin sonucuna göre değiştirebildiği çok çeşitli senaryolarda faydalıdır.

## <a name="syntax"></a>Syntax

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a>Açıklamalar

Enterpolasyonlu dizeler, bir dize sabit değerinin içindeki "delikler" içinde kod yazmanızı sağlar. Basit bir örnek verelim:

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

Her `{}` küme ayracı çifti arasındaki içerikler herhangi bir F # ifadesi olabilir.

Bir `{}` küme ayracı çiftini atlamak için, bunların ikisini de şöyle yazın:

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a>Türü belirlenmiş dizeler

Enterpolasyonlu dizeler tür güvenliğini zorlamak için F # biçim belirticilerine de sahip olabilir.

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

Önceki örnekte, kod yanlışlıkla `age` olması gereken değeri yanlışlıkla geçirir `name` ve tam tersi de geçerlidir. Enterpolasyonlu dizeler biçim belirticileri kullandığından, bu, hafif bir çalışma zamanı hatası yerine bir derleme hatasıdır.

[Düz metin biçimlendirmesi](plaintext-formatting.md) kapsamındaki tüm biçim belirticileri, enterpolasyonlu bir dizenin içinde geçerlidir.

## <a name="verbatim-interpolated-strings"></a>Harfine enterpolasyonlu dizeler

F #, dize sabit değerlerini katıştırabilmeniz için üçlü tırnaklarla birlikte bulunan dizeleri destekler.

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a>Enterpolasyonlu dizelerde ifadeleri hizalama

Enterpolasyonlu dizelerin içindeki ifadeleri `|` ve kaç boşluk olduğunu bir belirtim ile sola hizalayabilirsiniz veya sağa hizalayabilirsiniz. Aşağıdaki enterpolasyonlu dize sol ve sağ ifadeleri sırasıyla yedi boşlukla sola ve sağa hizalar.

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a>Enterpolasyonlu dizeler ve `FormattableString` biçimlendirmeler

Ayrıca, için kurallara uygun biçimlendirme uygulayabilirsiniz <xref:System.FormattableString> :

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

Ayrıca, enterpolasyonlu bir dize bir tür <xref:System.FormattableString> ek açıklaması aracılığıyla olarak denetlenebilir.

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

Tür ek açıklamanın, enterpolasyonlu dize ifadesinin kendisinde olması gerektiğini unutmayın. F #, bir enterpolasyonlu dizeyi örtük olarak bir öğesine dönüştürmez <xref:System.FormattableString> .

## <a name="see-also"></a>Ayrıca bkz.

* [Dizeler](strings.md)
