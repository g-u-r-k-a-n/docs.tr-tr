---
title: Eşitlik işleçleri-C# başvurusu
description: C# eşitlik karşılaştırma işleçleri ve C# tür eşitliği hakkında bilgi edinin.
ms.date: 06/26/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 33215e2440b14fb888a6f0df5c220c891ebed0e2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063100"
---
# <a name="equality-operators-c-reference"></a>Eşitlik işleçleri (C# Başvurusu)

[ `==` (Eşitlik)](#equality-operator-) ve [ `!=` (eşitsizlik)](#inequality-operator-) işleçleri işlenenlerinin eşit olup olmadığını denetler.

## <a name="equality-operator-"></a>Eşitlik işleci = =

Eşitlik işleci, `==` `true` işlenenleri eşitse, `false` Aksi takdirde döndürür.

### <a name="value-types-equality"></a>Değer türleri eşitlik

[Yerleşik değer türlerinin](../builtin-types/value-types.md#built-in-value-types) işlenenleri, değerleri eşitse eşittir:

[!code-csharp-interactive[value types equality](snippets/shared/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> ,, `==` , [ `<` `>` `<=` Ve `>=` ](comparison-operators.md) işleçleri için İşlenenlerden herhangi biri bir sayı ( <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> ) değilse, işlemin sonucu olur `false` . Bu, değeri, `NaN` dahil olmak üzere herhangi bir değerden büyük, küçüktür veya eşit olmayan bir değere eşit değil anlamına gelir `double` `float` `NaN` . Daha fazla bilgi ve örnek için bkz <xref:System.Double.NaN?displayProperty=nameWithType> . veya <xref:System.Single.NaN?displayProperty=nameWithType> başvuru makalesi.

Temeldeki integral türünün karşılık gelen değerleri eşitse aynı [sabit listesi](../builtin-types/enum.md) türünün iki işleneni eşittir.

Kullanıcı tanımlı [Yapı](../builtin-types/struct.md) türleri `==` Varsayılan olarak işleci desteklemez. İşleci desteklemek için `==` Kullanıcı tanımlı bir yapının onu [tekrar yüklemesi](operator-overloading.md) gerekir.

C# 7,3 ile başlayarak, `==` ve `!=` Işleçleri c# [Tanımlama grupları](../builtin-types/value-tuples.md)tarafından desteklenir. Daha fazla bilgi için [demet türleri](../builtin-types/value-tuples.md) makalesinin [kayıt düzeni eşitlik](../builtin-types/value-tuples.md#tuple-equality) bölümüne bakın.

### <a name="reference-types-equality"></a>Başvuru türleri eşitliği

Varsayılan olarak, iki başvuru türü işlenen aynı nesneye başvurduklarında eşittir:

[!code-csharp[reference type equality](snippets/shared/EqualityOperators.cs#ReferenceTypesEquality)]

Örnekte gösterildiği gibi, Kullanıcı tanımlı başvuru türleri `==` Varsayılan olarak işleci destekler. Ancak, bir başvuru türü işleci aşırı yükleyebilir `==` . Bir başvuru türü işleci aşırı yükle, `==` <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> Bu türden iki başvurunun aynı nesneye başvurmasını denetlemek için yöntemini kullanın.

### <a name="string-equality"></a>Dize eşitlik

İki [dize](../builtin-types/reference-types.md#the-string-type) işleneni her ikisi de olduğunda eşittir `null` veya her iki dize örneği de aynı uzunluktadır ve her bir karakter konumunda özdeş karakterlere sahiptir:

[!code-csharp-interactive[string equality](snippets/shared/EqualityOperators.cs#StringEquality)]

Bu, büyük/küçük harfe duyarlı bir sıra karşılaştırmasına sahiptir. Dize karşılaştırması hakkında daha fazla bilgi için bkz. [C# içindeki dizeleri karşılaştırma](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Temsilci eşitlik

Aynı çalışma zamanı türünün iki [temsilci](../../programming-guide/delegates/index.md) işleneni, her ikisi de `null` aynı uzunluktadır ve her konumda eşit girişlere sahip olduğunda eşittir:

[!code-csharp-interactive[delegate equality](snippets/shared/EqualityOperators.cs#DelegateEquality)]

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md), [eşitlik işleçlerini temsilci](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.

Anlamsal olarak özdeş [lambda ifadeleri](lambda-expressions.md) değerlendirmesinden üretilen temsilciler, aşağıdaki örnekte gösterildiği gibi eşit değildir:

[!code-csharp-interactive[from identical lambdas](snippets/shared/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Eşitsizlik işleci! =

Eşitsizlik işleci, `!=` `true` işlenenleri eşit değilse döndürür, `false` Aksi takdirde. [Yerleşik türlerin](../builtin-types/built-in-types.md)işlenenleri için ifade, `x != y` ifadesiyle aynı sonucu üretir `!(x == y)` . Tür eşitliği hakkında daha fazla bilgi için [eşitlik işleci](#equality-operator-) bölümüne bakın.

Aşağıdaki örnek işlecinin kullanımını gösterir `!=` :

[!code-csharp-interactive[non-equality examples](snippets/shared/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür ve işleçlerini [aşırı](operator-overloading.md) yükleyebilir `==` `!=` . Bir tür iki işleçten birini aşırı yüklediğinden, diğerini de aşırı yüklemesi gerekir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ilişkisel ve tür-test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Eşitlik karşılaştırmaları](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Karşılaştırma işleçleri](comparison-operators.md)
