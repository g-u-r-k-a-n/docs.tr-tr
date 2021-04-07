---
title: İşaretçiden ilgili işleçler-C# başvurusu
description: İşaretçilerle çalışırken kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 22cd87a62c92dbfacd0b8ebbdd5cbafb92da73ca
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497365"
---
# <a name="pointer-related-operators-c-reference"></a>İşaretçi ile ilgili işleçler (C# Başvurusu)

İşaretçilerle çalışmak için aşağıdaki işleçleri kullanabilirsiniz:

- Birli [ `&` (Adres-of)](#address-of-operator-) işleci: bir değişkenin adresini almak için
- Birli [ `*` (işaretçi yöneltme)](#pointer-indirection-operator-) işleci: bir işaretçiye işaret eden değişkeni almak için
- [ `->` (Üye erişimi)](#pointer-member-access-operator--) ve [ `[]` (öğe erişimi)](#pointer-element-access-operator-) işleçleri
- Aritmetik işleçler [ `+` , `-` ,, `++` ve `--` ](#pointer-arithmetic-operators)
- Karşılaştırma işleçleri,,,, [ `==` `!=` `<` `>` `<=` ve `>=` ](#pointer-comparison-operators)

İşaretçi türleri hakkında bilgi için bkz. [işaretçi türleri](../unsafe-code.md#pointer-types).

> [!NOTE]
> İşaretçilerle herhangi bir işlem [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektirir. Güvenli olmayan bloklar içeren kodun [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks) derleyici seçeneğiyle derlenmesi gerekir.

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a> Address-of işleci &amp;

Birli `&` işleç, işleneninin adresini döndürür:

[!code-csharp[address of local](snippets/shared/PointerOperators.cs#AddressOf)]

`&`İşlecin işleneni sabit bir değişken olmalıdır. *Sabit* değişkenler, [Atık toplayıcısının](../../../standard/garbage-collection/index.md)işleminden etkilenmeyen depolama konumlarında bulunan değişkenlerdir. Yukarıdaki örnekte, yerel değişken `number` yığında bulunduğundan sabit bir değişkendir. Çöp toplayıcısından etkilenebilecek (örneğin, yeniden konumlandırılan) depolama konumlarında bulunan değişkenler *Taşınabilir* değişkenler olarak adlandırılır. Nesne alanları ve dizi öğeleri taşınabilir değişkenlerin örnekleridir. Taşınabilir bir değişkenin adresini, bir [ `fixed` ifadesiyle](../keywords/fixed-statement.md)"düzelmiyor" veya "sabitle" yaparsanız alabilirsiniz. Alınan adres yalnızca bir deyimin bloğunun içinde geçerlidir `fixed` . Aşağıdaki örnek, bir `fixed` deyimin ve işlecin nasıl kullanılacağını gösterir `&` :

[!code-csharp[address of fixed](snippets/shared/PointerOperators.cs#AddressOfFixed)]

Bir sabit veya bir değerin adresini alamazsınız.

Sabit ve taşınabilir değişkenler hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sabit ve taşınabilir değişkenler](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) bölümüne bakın.

Binary `&` işleci, Boolean işlenenlerinin [mantıksal ve](boolean-logical-operators.md#logical-and-operator-) işlecini ya da tam sayı işlenenlerinin [bit düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar.

## <a name="pointer-indirection-operator-"></a>İşaretçi yöneltme işleci *

Birli işaretçi yöneltme işleci, `*` işleneninin gösterdiği değişkeni edinir. Başvuru operatörü olarak da bilinir. `*`İşlecin işleneni bir işaretçi türünde olmalıdır.

[!code-csharp[pointer indirection](snippets/shared/PointerOperators.cs#PointerIndirection)]

`*`İşleci türündeki bir ifadeye uygulayamazsınız `void*` .

İkili `*` işleç, sayısal işlenenlerinin [çarpımını](arithmetic-operators.md#multiplication-operator-) hesaplar.

## <a name="pointer-member-access-operator--"></a>İşaretçi üyesi erişim işleci->

`->`İşleci [işaretçi yöneltme](#pointer-indirection-operator-) ve [üye erişimini](member-access-operators.md#member-access-expression-)birleştirir. Diğer bir deyişle, `x` türünde bir işaretçisiyse `T*` ve türünün erişilebilir bir üyesi ise, `y` `T` formun bir ifadesi

```csharp
x->y
```

eşdeğerdir

```csharp
(*x).y
```

Aşağıdaki örnek işlecinin kullanımını gösterir `->` :

[!code-csharp[pointer member access](snippets/shared/PointerOperators.cs#MemberAccess)]

`->`İşleci türündeki bir ifadeye uygulayamazsınız `void*` .

## <a name="pointer-element-access-operator-"></a>İşaretçi öğesi erişim işleci []

İşaretçi türünün bir ifadesi için `p` , formun işaretçi öğesi erişimi `p[n]` olarak değerlendirilir `*(p + n)` , burada,, veya ' a `n` örtülü olarak dönüştürülebilir bir tür olması gerekir `int` `uint` `long` `ulong` . İşaretçilerle işlecin davranışı hakkında daha fazla bilgi için `+` , [bir tam sayı değerinin bir Işaretçi bölümüne eklenmesi veya çıkarılması](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) bölümüne bakın.

Aşağıdaki örnek, bir işaretçi ve işleçle dizi öğelerine nasıl erişileceğini göstermektedir `[]` :

[!code-csharp[pointer element access](snippets/shared/PointerOperators.cs#ElementAccess)]

Yukarıdaki örnekte, bir [ `stackalloc` ifade](stackalloc.md) yığında bir bellek bloğu ayırır.

> [!NOTE]
> İşaretçi öğesi erişim işleci, sınır dışı hataları denetlemez.

`[]`Türünde bir ifadeyle işaretçi öğesi erişimi için kullanamazsınız `void*` .

`[]` [Dizi öğesi veya Dizin Oluşturucu erişimi](member-access-operators.md#indexer-operator-)için işlecini de kullanabilirsiniz.

## <a name="pointer-arithmetic-operators"></a>İşaretçi aritmetik işleçleri

İşaretçilerle aşağıdaki aritmetik işlemleri gerçekleştirebilirsiniz:

- Bir işaretçiye veya işaretçiden tamsayı değer ekleme veya çıkarma
- İki işaretçileri çıkar
- Bir işaretçiyi artırma veya azaltma

Bu işlemleri türündeki işaretçilerle gerçekleştiremezsiniz `void*` .

Sayısal türlerle desteklenen aritmetik işlemler hakkında daha fazla bilgi için bkz. [Aritmetik işleçler](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Bir işaretçiye veya bir işaretçiye tamsayı değer ekleme veya çıkarma

Türünde bir işaretçi `p` ve bir `T*` türün bir ifadesi için `n` örtük olarak dönüştürülebilir,, `int` `uint` `long` , veya `ulong` , toplama ve çıkarma için aşağıdaki gibi tanımlanır:

- Hem hem de `p + n` `n + p` ifadeleri, `T*` tarafından verilen adrese eklenmesinin sonucu olan türünde bir işaretçi üretir `n * sizeof(T)` `p` .
- `p - n`İfade, `T*` `n * sizeof(T)` tarafından verilen adresten çıkarılmasına neden olan türde bir işaretçi oluşturur `p` .

[ `sizeof` İşleci](sizeof.md) bir türün boyutunu bayt cinsinden edinir.

Aşağıdaki örnek, `+` bir işaretçi ile işlecinin kullanımını gösterir:

[!code-csharp[pointer addition](snippets/shared/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>İşaretçi çıkarması

İki işaretçi `p1` ve `p2` türü için `T*` , ifadesi `p1 - p2` tarafından verilen `p1` ve `p2` tarafından bölünen adresler arasındaki farkı üretir `sizeof(T)` . Sonucun türü `long` . Diğer bir deyişle, `p1 - p2` olarak hesaplanır `((long)(p1) - (long)(p2)) / sizeof(T)` .

Aşağıdaki örnekte işaretçi çıkarma gösterilmektedir:

[!code-csharp[pointer subtraction](snippets/shared/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>İşaretçi artışı ve azaltma

`++`Artış işleci, işaretçi işleneni 1 [ekler](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) . `--`Azaltma işleci, 1 işaretçi işlenenden [çıkartır](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .

İki tür işleç desteklenir: sonek ( `p++` ve `p--` ) ve ön ek ( `++p` ve `--p` ). Ve sonucu, `p++` `p--` `p` işlemden *önceki* değeridir. Ve sonucu, `++p` `--p` `p` işlemden *sonraki* değeridir.

Aşağıdaki örnek, hem sonek hem de önek artırma işleçlerinin davranışını gösterir:

[!code-csharp[pointer increment](snippets/shared/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>İşaretçi karşılaştırma işleçleri

,,,, `==` `!=` `<` Ve işleçlerini, `>` gibi `<=` `>=` herhangi bir işaretçi türünün işlenenlerini karşılaştırmak için kullanabilirsiniz `void*` . Bu işleçler, iki işlenen tarafından verilen adresleri işaretsiz tamsayılar gibi karşılaştırır.

Diğer türlerin işlenenleri için bu işleçlerin davranışı hakkında daha fazla bilgi için bkz. [eşitlik işleçleri](equality-operators.md) ve [karşılaştırma işleçleri](comparison-operators.md) makaleleri.

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki liste, işaretçinin ilgili işleçlerini en yüksek öncelikten en düşüğe başlayarak sıralar:

- Sonek artırma `x++` ve azaltma `x--` işleçleri ve `->` ve `[]` işleçleri
- Ön ek artırma `++x` ve azaltma `--x` işleçleri ve `&` ve `*` işleçleri
- Eklenebilir `+` ve `-` işleçler
- Karşılaştırma `<` , `>` , `<=` , ve `>=` işleçler
- Eşitlik `==` ve `!=` işleçler

`()`İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantez ' nu kullanın.

Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için [c# işleçleri](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür, işaretçiyle ilgili işleçleri,, `&` `*` `->` ve ile aşırı yükleyemez `[]` .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Sabit ve taşınabilir değişkenler](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Address-of işleci](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [İşaretçi yöneltme](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [İşaretçi üye erişimi](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [İşaretçi öğesi erişimi](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [İşaretçi aritmetiği](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [İşaretçi artışı ve azaltma](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [İşaretçi karşılaştırması](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [İşaretçi türleri](../unsafe-code.md#pointer-types)
- [güvenli olmayan anahtar sözcük](../keywords/unsafe.md)
- [Fixed anahtar sözcüğü](../keywords/fixed-statement.md)
- [stackalloc](stackalloc.md)
- [sizeof işleci](sizeof.md)
