---
title: Desenler-C# başvurusu
description: C# deseni eşleşen ifadeler ve deyimler ile desteklenen desenler hakkında bilgi edinin-C# başvurusu
ms.date: 04/05/2021
f1_keywords:
- and_CSharpKeyword
- or_CSharpKeyword
- not_CSharpKeyword
helpviewer_keywords:
- pattern matching [C#]
- and keyword [C#]
- or keyword [C#]
- not keyword [C#]
ms.openlocfilehash: cac2208d41bca2c6befecffbe4bb0b8ca43042bc
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106499124"
---
# <a name="patterns-c-reference"></a>Desenler (C# Başvurusu)

C#, c# 7,0 ' de model eşleştirmeyi sunmuştur. Bu tarihten sonra, her önemli C# sürümü, model eşleme yeteneklerini genişletiyor. Aşağıdaki C# ifadeleri ve deyimleri, model eşleştirmeyi destekler:

- [`is` ifadesini](../keywords/is.md)
- `switch`[ifade](../keywords/switch.md)
- `switch`[ifade](switch-expression.md) (C# 8,0 ' de tanıtılan)

Bu yapılar içinde, bir giriş ifadesini aşağıdaki desenlerden biriyle eşleştirebilirsiniz:

- [Bildirim deseninin](#declaration-and-type-patterns): bir ifadenin çalışma zamanı türünü denetlemek için ve bir eşleşme başarılı olursa, belirtilen değişkene bir ifade sonucu atayın. C# 7,0 ' de kullanıma sunulmuştur.
- Bir ifadenin çalışma zamanı türünü denetlemek için [tür stili](#declaration-and-type-patterns):. C# 9,0 ' de kullanıma sunulmuştur.
- [Sabit model](#constant-pattern): bir ifade sonucunun belirtilen bir sabit değere eşit olup olmadığını test etmek için. C# 7,0 ' de kullanıma sunulmuştur.
- [İlişkisel desenler](#relational-patterns): bir ifade sonucunu belirtilen bir sabitle karşılaştırmak için. C# 9,0 ' de kullanıma sunulmuştur.
- [Mantıksal desenler](#logical-patterns): bir ifadenin bir mantıksal desen bileşimiyle eşleşip eşleşmediğini test etmek. C# 9,0 ' de kullanıma sunulmuştur.
- [Özellik deseni](#property-pattern): bir ifadenin özellikleri veya alanları iç içe desenlerle eşleşiyorsa test etmek için. C# 8,0 ' de kullanıma sunulmuştur.
- [Konumsal desen](#positional-pattern): bir ifade sonucunu bırakmak ve elde edilen değerler iç içe desenlerle eşleşiyorsa test etmek için. C# 8,0 ' de kullanıma sunulmuştur.
- [ `var` model](#var-pattern): herhangi bir ifadeyi eşleştirmek ve sonucunu belirtilen bir değişkene atamak için. C# 7,0 ' de kullanıma sunulmuştur.
- Herhangi bir ifadeyle eşleşecek şekilde [Düzenle](#discard-pattern):. C# 8,0 ' de kullanıma sunulmuştur.

[Mantıksal](#logical-patterns), [özellik](#property-pattern)ve [konumsal](#positional-pattern) desenler *özyinelemeli* desenlerdir. Diğer bir deyişle, *iç içe* desenler içerebilirler.

Veri odaklı bir algoritma oluşturmak için bu desenleri nasıl kullanacağınızı gösteren örnek için bkz. [öğretici: tür temelli ve veri odaklı algoritmalar oluşturmak için desen eşleştirmeyi kullanma](../../tutorials/pattern-matching.md).

## <a name="declaration-and-type-patterns"></a>Bildirim ve tür desenleri

Bir ifadenin çalışma zamanı türünün belirli bir türle uyumlu olup olmadığını denetlemek için bildirim ve tür desenleri kullanın. Bir bildirim düzeniyle yeni bir yerel değişken de bildirebilirsiniz. Bir bildirim deseninin bir ifadeyle eşleşmesi durumunda, bu değişkene, aşağıdaki örnekte gösterildiği gibi, dönüştürülmüş bir ifade sonucu atanır:

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="BasicExample":::

C# 7,0 ' den başlayarak,  bir `T` ifade sonucu null olmadığında ve aşağıdaki koşullardan herhangi biri doğru olduğunda tür içeren bir bildirim deseninin ifadesiyle eşleşmesi gerekir:

- Bir ifade sonucunun çalışma zamanı türü `T` .

- Bir ifade sonucunun çalışma zamanı türü tür `T` veya Implements arabiriminden türetilir ya da `T` ondan başka bir [örtük başvuru dönüştürmesi](~/_csharplang/spec/conversions.md#implicit-reference-conversions) vardır `T` . Aşağıdaki örnekte, bu koşul doğru olduğunda iki durum gösterilmektedir:

  :::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="ReferenceConversion":::

  Önceki örnekte, yöntemine yapılan ilk çağrıda, `GetSourceLabel` bağımsız değişkenin çalışma zamanı türü türünden türediğinden ilk model bir bağımsız değişken değeriyle eşleşir `int[]` <xref:System.Array> . Yöntemine yapılan ikinci çağrıda `GetSourceLabel` , bağımsız değişkenin çalışma zamanı türü <xref:System.Collections.Generic.List%601> türünden türetilmez, <xref:System.Array> ancak <xref:System.Collections.Generic.ICollection%601> arabirimini uygular.

- Bir ifade sonucunun çalışma zamanı türü, temel alınan türe sahip [null yapılabilen bir değer türüdür](../builtin-types/nullable-value-types.md) `T` .

- Bir ifade sonucunun çalışma zamanı türünden türüne bir [paketleme](../../programming-guide/types/boxing-and-unboxing.md#boxing) veya [kutudan](../../programming-guide/types/boxing-and-unboxing.md#unboxing) çıkarma dönüştürme var `T` .

Aşağıdaki örnek, son iki koşulu göstermektedir:

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="NullableAndUnboxing":::

Yalnızca bir ifadenin türünü denetlemek isterseniz, `_` Aşağıdaki örnekte gösterildiği gibi, bir değişkenin adının yerine bir atma kullanabilirsiniz:

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="DiscardVariable":::

C# 9,0 ' den başlayarak, bu amaçla, aşağıdaki örnekte gösterildiği gibi bir *tür modelini* kullanabilirsiniz:

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="TypePattern":::

Bir bildirim deseninin gibi, bir ifade sonucu null olmadığında ve çalışma zamanı türü yukarıda listelenen koşulları karşılıyorsa bir tür deseninin ifadesi eşleşir.

Daha fazla bilgi için, özellik teklifi notlarının [bildirim düzenine](~/_csharplang/proposals/csharp-8.0/patterns.md#declaration-pattern) ve [tür deseninin](~/_csharplang/proposals/csharp-9.0/patterns3.md#type-patterns) bölümlerine bakın.

## <a name="constant-pattern"></a>Sabit model

C# 7,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi bir ifade sonucunun belirtilen bir sabit değere eşit olup olmadığını test etmek için *sabit bir model* kullanırsınız:

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="BasicExample":::

Sabit bir düzende, şöyle bir sabit ifade kullanabilirsiniz:

- [tamsayı](../builtin-types/integral-numeric-types.md) veya [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal sabit değeri
- bir [char](../builtin-types/char.md) veya [dize](../builtin-types/reference-types.md#the-string-type) sabit değeri
- Boole değeri `true` veya `false`
- [sabit listesi](../builtin-types/enum.md) değeri
- Belirtilen bir [const](../keywords/const.md) alanının veya yerel öğesinin adı
- `null`

`null`Aşağıdaki örnekte gösterildiği gibi, denetlenecek sabit bir model kullanın:

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NullCheck":::

Derleyici, ifade değerlendirildiğinde hiçbir Kullanıcı aşırı yüklenmiş eşitlik işlecinin `==` çağırılmasını güvence altına alır `x is null` .

C# 9,0 ' den başlayarak, [](#logical-patterns) `null` Aşağıdaki örnekte gösterildiği gibi, null olmayan bir sabit model kullanabilirsiniz:

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NonNullCheck":::

Daha fazla bilgi için, özellik teklifi notunun [sabit örüntüsünün](~/_csharplang/proposals/csharp-8.0/patterns.md#constant-pattern) bölümüne bakın.

## <a name="relational-patterns"></a>İlişkisel desenler

C# 9,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi bir ifade sonucunu bir sabit ile karşılaştırmak için bir *ilişkisel model* kullanın:

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="BasicExample":::

İlişkisel bir düzende,,, veya [ilişkisel işleçlerini](comparison-operators.md) kullanabilirsiniz `<` `>` `<=` `>=` . İlişkisel bir düzenin sağ kısmı sabit bir ifade olmalıdır. Sabit ifade bir [tamsayı](../builtin-types/integral-numeric-types.md), [kayan nokta](../builtin-types/floating-point-numeric-types.md), [char](../builtin-types/char.md)veya [enum](../builtin-types/enum.md) türünde olabilir.

Bir ifade sonucunun belirli bir aralıkta olup olmadığını denetlemek için aşağıdaki örnekte gösterildiği gibi, bir [ayırt edici `and` düzende](#logical-patterns)eşleştirin:

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="WithCombinators":::

Bir ifade sonucu, `null` null yapılabilir veya kutudan çıkarma dönüştürmesi ile bir sabit türüne dönüştürülemezse, ilişkisel bir model ifadesiyle eşleşmez.

Daha fazla bilgi için, özellik teklifi notunun [ilişkisel desenler](~/_csharplang/proposals/csharp-9.0/patterns3.md#relational-patterns) bölümüne bakın.

## <a name="logical-patterns"></a>Mantıksal desenler

C# 9,0 ' den başlayarak, `not` `and` `or` aşağıdaki *mantıksal desenleri* oluşturmak için,, ve desenini kombinatör kullanın:

- *Değilleme* `not` bir ifade ile eşleşen, iç içe bir model ifadesiyle eşleşen kalıp. Aşağıdaki örnek, bir ifadenin null olup olmadığını denetlemek için [sabit](#constant-pattern) bir düzenin nasıl yapılacağını gösterir `null` :

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="NotPattern":::

- *Conjunyatif* `and` Her iki desen de ifadesiyle eşleşen bir ifadeyle eşleşen desen. Aşağıdaki örnek, bir değerin belirli bir aralıkta olup olmadığını denetlemek için [ilişkisel desenleri](#relational-patterns) nasıl birleştirebileceğinizi göstermektedir:

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="AndPattern":::

- *Ayırt edici* `or` Aşağıdaki örnekte gösterildiği gibi desenlerden biri ifadesiyle eşleşen bir ifadeyle eşleşen desen:

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="OrPattern":::

Yukarıdaki örnekte gösterildiği gibi, Kombinatör deseninin bir düzende tekrar tekrar kullanabilirsiniz.

`and`Combinator deseninin önceliği daha yüksektir `or` . Önceliği açıkça belirtmek için aşağıdaki örnekte gösterildiği gibi ayraçları kullanın:

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="WithParentheses":::

> [!NOTE]
> Desenlerin denetlenme sırası tanımsız. Çalışma zamanında, ve desenlerinin sağ iç içe geçmiş desenleri `or` `and` önce denetlenebilir.

Daha fazla bilgi için, özellik teklifi notunun [örüntüsünün kombinatör](~/_csharplang/proposals/csharp-9.0/patterns3.md#pattern-combinators) bölümüne bakın.

## <a name="property-pattern"></a>Özellik kalıbı

C# 8,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi bir ifadenin özelliklerini veya alanlarını iç içe desenlerle eşleştirmek için bir *özellik deseni* kullanın:

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="BasicExample":::

Bir ifade sonucu null olmadığında ve tüm iç içe desenler ifade sonucunun karşılık gelen özelliği veya alanıyla eşleştiğinde bir özellik deseninin ifadesiyle eşleşir.

Aşağıdaki örnekte gösterildiği gibi, bir özellik düzenine bir çalışma zamanı türü denetimi ve değişken bildirimi de ekleyebilirsiniz:

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="WithTypeCheck":::

Özellik deseninin özyinelemeli bir deseninin olması. Diğer bir deyişle, herhangi bir kalıbı iç içe geçmiş bir model olarak kullanabilirsiniz. Aşağıdaki örnekte gösterildiği gibi, veri parçalarını iç içe geçmiş desenlere göre eşleştirmek için bir özellik deseni kullanın:

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="RecursivePropertyPattern":::

Yukarıdaki örnek C# 9,0 ve üzeri sürümlerde kullanılabilen iki özelliği kullanır: `or` [örüncombinator](#logical-patterns) ve [kayıt türleri](../builtin-types/record.md).

Daha fazla bilgi için, özellik teklifi notunun [özellik deseninin](~/_csharplang/proposals/csharp-8.0/patterns.md#property-pattern) bölümüne bakın.

## <a name="positional-pattern"></a>Konumsal model

C# 8,0 ' den başlayarak, bir ifade sonucunu bırakmak ve elde edilen değerleri, aşağıdaki örnekte gösterildiği gibi, iç içe geçmiş desenlerle eşleştirmek için bir *konumsal düzen* kullanın:

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="BasicExample":::

Önceki örnekte, bir ifadenin türü bir ifade sonucunu bırakmak için kullanılan [deyapýsý](../../deconstruct.md) metodunu içerir. Ayrıca, konumsal desenlerde [demet türleri](../builtin-types/value-tuples.md) ifadelerini de eşleştirebilirsiniz. Bu şekilde, aşağıdaki örnekte gösterildiği gibi çeşitli modellerdeki birden çok girişi eşleştirebilirsiniz:

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="MatchTuple":::

Önceki örnekte, C# 9,0 ve üzeri sürümlerde kullanılabilen [ilişkisel](#relational-patterns) ve [mantıksal](#logical-patterns) desenler kullanılmaktadır.

`Deconstruct`Aşağıdaki örnekte gösterildiği gibi, konumsal bir düzende demet öğelerinin ve parametrelerinin adlarını kullanabilirsiniz:

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="UseIdentifiers":::

Ayrıca, konum düzenlerini aşağıdaki yollarla genişletebilirsiniz:

- Aşağıdaki örnekte gösterildiği gibi, bir çalışma zamanı türü denetimi ve bir değişken bildirimi ekleyin:

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithTypeCheck":::

  Yukarıdaki örnek, yöntemi örtük olarak sağlayan [konumsal kayıtları](../builtin-types/record.md#positional-syntax-for-property-definition) kullanır `Deconstruct` .

- Aşağıdaki örnekte gösterildiği gibi, konumsal model içinde bir [özellik kalıbı](#property-pattern) kullanın:

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithPropertyPattern":::

- Aşağıdaki örnekte gösterildiği gibi, önceki iki kullanımı birleştirin:

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="CompletePositionalPattern":::

Konumsal bir model özyinelemeli bir modeldir. Diğer bir deyişle, herhangi bir kalıbı iç içe geçmiş bir model olarak kullanabilirsiniz.

Daha fazla bilgi için, özellik teklifi notunun [konumsal model](~/_csharplang/proposals/csharp-8.0/patterns.md#positional-pattern) bölümüne bakın.

## <a name="var-pattern"></a>`var` kalıp

C# 7,0 ' den başlayarak, aşağıdaki örnekte *`var`* gösterildiği gibi herhangi bir ifadeyi eşleştirmek `null` ve bunun sonucunu yeni bir yerel değişkene atamak için bir kalıp kullanın:

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="KeepInterimResult":::

Bir dizi, `var` Ara hesaplamaların sonucunu tutacak bir Boolean ifadesinde geçici bir değişkene ihtiyacınız olduğunda faydalıdır. `var` `when` `switch` Aşağıdaki örnekte gösterildiği gibi, bir ifadenin veya deyimin büyük/küçük harf korugeçirmeleri üzerinde ek denetimler gerçekleştirmeniz gerektiğinde de bir kalıp kullanabilirsiniz:

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="WithCaseGuards":::

Yukarıdaki örnekte, `var (x, y)` bir [konum düzenine](#positional-pattern) eşdeğerdir `(var x, var y)` .

Bir `var` düzende, belirtilen bir değişkenin türü, düzeniyle eşleşen ifadenin derleme zamanı türüdür.

Daha fazla bilgi için, özellik teklifi notunun [var olan örüntüsünün](~/_csharplang/proposals/csharp-8.0/patterns.md#var-pattern) bölümüne bakın.

## <a name="discard-pattern"></a>Stili at

C# 8,0 ' den başlayarak,  `_` `null` Aşağıdaki örnekte gösterildiği gibi herhangi bir ifadeyle eşleşecek bir atma stili kullanın:

:::code language="csharp" source="snippets/patterns/DiscardPattern.cs" id="BasicExample":::

Önceki örnekte, işlemek için bir atma deseninin kullanıldığı `null` ve Numaralandırmadaki karşılık gelen üyesine sahip olmayan herhangi bir tamsayı değeri <xref:System.DayOfWeek> . Bu `switch` , örnekteki bir ifadenin tüm olası girdi değerlerini işlemesini güvence altına alır. Bir ifadede bir atma deseni kullanmıyorsanız `switch` ve ifadenin desenlerinin bir girişle eşleşmesi gerekmiyorsa, çalışma zamanı [bir özel durum oluşturur](switch-expression.md#non-exhaustive-switch-expressions). Bir `switch` ifade tüm olası giriş değerlerini işlemezse derleyici bir uyarı oluşturur.

Bir atma deseninin ifadesi veya deyimi içindeki bir model olamaz `is` `switch` . Bu durumlarda, herhangi bir ifadeyi eşleştirmek için, at: ile bir [ `var` desenler](#var-pattern) kullanın `var _` .

Daha fazla bilgi için, özellik teklifi notunun [atma düzenine](~/_csharplang/proposals/csharp-8.0/patterns.md#discard-pattern) bakın.

## <a name="parenthesized-pattern"></a>Parantez içine alınmış desenler

C# 9,0 ' den başlayarak, herhangi bir düzenin çevresine parantez koyabilirsiniz. Genellikle, aşağıdaki örnekte gösterildiği gibi [mantıksal desenlerdeki](#logical-patterns)önceliği vurgulamak veya değiştirmek için bunu yapabilirsiniz:

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="ChangedPrecedence":::

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:

- [C# 7,0 için model eşleştirme](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Özyinelemeli model eşleştirme (C# 8,0 ' de tanıtılan)](~/_csharplang/proposals/csharp-8.0/patterns.md)
- [C# 9,0 için kalıp eşleme değişiklikleri](~/_csharplang/proposals/csharp-9.0/patterns3.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Öğretici: tür odaklı ve veri odaklı algoritmalar oluşturmak için model eşleştirmeyi kullanın](../../tutorials/pattern-matching.md)
