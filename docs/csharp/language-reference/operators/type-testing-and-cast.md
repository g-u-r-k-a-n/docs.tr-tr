---
title: Tür testi işleçleri ve Cast ifadesi-C# başvurusu
description: Bir ifade sonucunun türünü denetlemek ve gerekirse başka bir türe dönüştürmek için kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
- as
- typeof
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: f47074fda20c1bc2eda75184dd26c9de1c0e3701
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075322"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a>Tür testi işleçleri ve Cast ifadesi (C# Başvurusu)

Tür denetimi veya tür dönüştürme gerçekleştirmek için aşağıdaki işleçleri ve ifadeleri kullanabilirsiniz:

- [işleç](#is-operator): bir ifadenin çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetlemek için
- [as işleci](#as-operator): çalışma zamanı türü bu türle uyumluysa bir ifadeyi açıkça belirli bir türe dönüştürmek için
- [Cast ifadesi](#cast-expression): açık bir dönüştürme gerçekleştirmek için
- [typeof işleci](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> bir türün örneğini almak için

## <a name="is-operator"></a>işleç

`is`İşleci, bir ifade sonucunun çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetler. C# 7,0 ile başlayarak, `is` işleci bir ifade sonucunu bir düzene göre de sınar.

Type-Testing işlecine sahip ifade `is` aşağıdaki biçimdedir

```csharp
E is T
```

`E`, bir değer döndüren ve `T` bir tür ya da tür parametresinin adı olan bir ifadedir. `E` anonim bir yöntem veya lambda ifadesi olamaz.

`E is T`İfadesi, `true` sonucu `E` null olmayan ve `T` bir başvuru dönüştürmesi, paketleme dönüştürmesi ya da bir kutudan çıkarma dönüştürmesi tarafından türe dönüştürülebileceğinden, öğesini döndürür; Aksi takdirde, döndürür `false` . `is`İşleci Kullanıcı tanımlı dönüştürmeleri dikkate almaz.

Aşağıdaki örnek, `is` `true` bir ifade sonucunun çalışma zamanı türü verilen bir türden türetilse, yani türler arasında bir başvuru dönüştürmesi varsa, işlecinin döndürdüğü gösterilmektedir:

[!code-csharp[is with reference conversion](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Sonraki örnekte, `is` işlecin hesap paketleme ve kutudan çıkarma dönüştürmelerinin gösterdiği ancak [sayısal dönüştürmeleri](../builtin-types/numeric-conversions.md)düşünmeyen bir örnek gösterilmektedir:

[!code-csharp-interactive[is with int](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithInt)]

C# dönüştürmeleri hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [dönüşümler](~/_csharplang/spec/conversions.md) bölümüne bakın.

### <a name="type-testing-with-pattern-matching"></a>Model eşleştirme ile test türü

C# 7,0 ile başlayarak, `is` işleci bir ifade sonucunu bir düzene göre de sınar. Aşağıdaki örnek, bir ifadenin çalışma zamanı türünü denetlemek için bir [bildirim deseninin](patterns.md#declaration-and-type-patterns) nasıl kullanılacağını gösterir:

[!code-csharp-interactive[is with declaration pattern](snippets/shared/TypeTestingAndConversionOperators.cs#IsDeclarationPattern)]

Desteklenen desenler hakkında daha fazla bilgi için bkz. [desenler](patterns.md).

## <a name="as-operator"></a>as işleci

`as`İşleci, bir ifadenin sonucunu açıkça belirli bir başvuruya veya null yapılabilir değer türüne dönüştürür. Dönüştürme mümkün değilse, `as` işleç döndürülür `null` . [Atama ifadesinin](#cast-expression)aksine, `as` işleç hiçbir şekilde özel durum oluşturmaz.

Formun ifadesi

```csharp
E as T
```

, `E` bir değer döndüren ve `T` bir tür ya da tür parametresinin adı olan bir ifadedir, aynı sonucu şöyle üretir

```csharp
E is T ? (T)(E) : (T)null
```

hariç `E` yalnızca bir kez değerlendirilir.

`as`İşleci yalnızca başvuru, null yapılabilir, kutulama ve kutudan çıkarma dönüştürmelerini dikkate alır. `as`Kullanıcı tanımlı bir dönüştürme gerçekleştirmek için işlecini kullanamazsınız. Bunu yapmak için bir [atama ifadesi](#cast-expression)kullanın.

Aşağıdaki örnek işlecinin kullanımını gösterir `as` :

[!code-csharp-interactive[as operator](snippets/shared/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Yukarıdaki örnekte gösterildiği gibi, `as` `null` dönüştürmenin başarılı olup olmadığını kontrol etmek için ifadesinin sonucunu karşılaştırmanız gerekir. C# 7,0 ' den başlayarak, dönüştürmenin başarılı olup olmadığını test etmek için, her iki [işleci](#type-testing-with-pattern-matching) de kullanabilirsiniz ve başarılı olursa, sonucunu yeni bir değişkene atayın.

## <a name="cast-expression"></a>Atama ifadesi

Formun bir atama ifadesi `(T)E` , ifadenin sonucunun türüne açık bir şekilde dönüştürülmesini gerçekleştirir `E` `T` . Türünden türüne hiçbir açık dönüştürme yoksa `E` `T` , derleme zamanı hatası oluşur. Çalışma zamanında, açık bir dönüştürme başarılı olmayabilir ve bir atama ifadesi bir özel durum oluşturabilir.

Aşağıdaki örnek, açık sayısal ve başvuru dönüştürmelerini göstermektedir:

[!code-csharp-interactive[cast expression](snippets/shared/TypeTestingAndConversionOperators.cs#Cast)]

Desteklenen açık dönüştürmeler hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümüne bakın. Özel bir açık veya örtük tür dönüştürme tanımlama hakkında daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>() Diğer kullanımları

Ayrıca, [bir yöntemi çağırmak veya bir temsilciyi çağırmak](member-access-operators.md#invocation-expression-)için parantezleri de kullanabilirsiniz.

Diğer parantez kullanımı, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamadır. Daha fazla bilgi için bkz. [C# işleçleri](index.md).

## <a name="typeof-operator"></a>typeof işleci

`typeof`İşleci <xref:System.Type?displayProperty=nameWithType> bir tür için örneği edinir. `typeof`Aşağıdaki örnekte gösterildiği gibi, işlecin bağımsız değişkeni bir tür veya tür parametresinin adı olmalıdır:

[!code-csharp-interactive[typeof operator](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOf)]

`typeof`İşleci ilişkisiz genel türler ile de kullanabilirsiniz. İlişkisiz genel türün adı, tür parametrelerinin sayısından küçük olan uygun sayıda virgül içermelidir. Aşağıdaki örnek, `typeof` sınırsız bir genel türü olan işlecinin kullanımını gösterir:

[!code-csharp-interactive[typeof unbound generic](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

İfade, işlecin bağımsız değişkeni olamaz `typeof` . <xref:System.Type?displayProperty=nameWithType>Bir ifade sonucunun çalışma zamanı türünün örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.

### <a name="type-testing-with-the-typeof-operator"></a>İşleci ile test türü `typeof`

`typeof`İfade sonucunun çalışma zamanı türünün verilen bir türle tam olarak eşleşip eşleşmediğini denetlemek için işlecini kullanın. Aşağıdaki örnek, işleç ve işleç işleci ile gerçekleştirilen tür denetimi arasındaki farkı gösterir `typeof` : [](#is-operator)

[!code-csharp[typeof vs is](snippets/shared/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Operatör overloadability

`is`, `as` Ve `typeof` işleçleri aşırı yüklenemez.

Kullanıcı tanımlı bir tür işleci aşırı yükleyemez `()` , ancak bir atama ifadesi tarafından gerçekleştirilebilecek özel tür dönüştürmeleri tanımlayabilir. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [SIS işleci](~/_csharplang/spec/expressions.md#the-is-operator)
- [As işleci](~/_csharplang/spec/expressions.md#the-as-operator)
- [Atama ifadeleri](~/_csharplang/spec/expressions.md#cast-expressions)
- [Typeof işleci](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Desenler ve as işleçlerini kullanarak güvenli bir şekilde atama](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [.NET içindeki Genel Türler](../../../standard/generics/index.md)
