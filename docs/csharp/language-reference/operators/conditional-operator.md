---
description: '?: operator-C# başvurusu'
title: '?: operator-C# başvurusu'
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 84a740f3afeca94a706b4120b8cd8f191f49a048
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369575"
---
# <a name="-operator-c-reference"></a>?: işleci (C# Başvurusu)

`?:`Üçlü işleç olarak da bilinen koşullu operatör, Boole ifadesi değerlendirir ve `true` `false` Aşağıdaki örnekte gösterildiği gibi, Boolean ifadesinin veya olarak değerlendirildiğine bağlı olarak iki ifadeden birinin sonucunu döndürür:

:::code language="csharp" interactive="try-dotnet-method" source="snippets/shared/ConditionalOperator.cs" id="BasicExample":::

Yukarıdaki örnekte gösterildiği gibi, koşullu işlecin sözdizimi aşağıdaki gibidir:

```csharp
condition ? consequent : alternative
```

`condition`İfade veya olarak değerlendirilmelidir `true` `false` . `condition`, Olarak değerlendirilirse `true` , `consequent` ifade değerlendirilir ve sonucu işlemin sonucu olur. `condition`, Olarak değerlendirilirse `false` , `alternative` ifade değerlendirilir ve sonucu işlemin sonucu olur. Yalnızca `consequent` veya `alternative` değerlendirilir.

C# 9,0 ' den başlayarak Koşullu ifadeler Target türünde bulunur. Diğer bir deyişle, koşullu bir ifadenin hedef türü biliniyorsa, `consequent` `alternative` Aşağıdaki örnekte gösterildiği gibi, ve türlerinin hedef türüne örtülü olarak dönüştürülebilir olması gerekir:

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

Koşullu ifadenin hedef türü bilinmiyorsa (örneğin, [`var`](../keywords/var.md) anahtar sözcüğünü kullandığınızda) veya C# 8,0 ve önceki sürümlerde, türü `consequent` ve `alternative` aynı olmalıdır veya bir türden diğerine örtük bir dönüştürme olması gerekir:

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

Koşullu operatör doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi

```csharp
a ? b : c ? d : e
```

şöyle değerlendirilir

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> Koşullu işlecin nasıl değerlendirildiğini anımsamak için aşağıdaki anımsatıcı cihazı kullanabilirsiniz:
>
> ```text
> is this condition true ? yes : no
> ```

## <a name="conditional-ref-expression"></a>Koşullu başvuru ifadesi

C# 7,2 ile başlayarak, bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkeni koşullu bir başvuru ifadesiyle koşullu olarak atanabilir. Ayrıca, bir [Başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya [ `ref` Yöntem bağımsız değişkeni](../keywords/ref.md#passing-an-argument-by-reference)olarak bir koşullu başvuru ifadesi de kullanabilirsiniz.

Koşullu başvuru ifadesi için sözdizimi aşağıdaki gibidir:

```csharp
condition ? ref consequent : ref alternative
```

Özgün koşullu operatör gibi, koşullu bir başvuru ifadesi iki ifadeden yalnızca birini değerlendirir: `consequent` ya da `alternative` .

Koşullu başvuru ifadesi durumunda, `consequent` ve türü `alternative` aynı olmalıdır. Koşullu başvuru ifadeleri Target türünde değil.

Aşağıdaki örnek, bir koşullu başvuru ifadesinin kullanımını gösterir:

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Koşullu işleç ve bir `if..else` ifade

[İf-else](../keywords/if-else.md) ifadesinin yerine koşullu işlecin kullanılması, bir değeri hesaplamak için koşullu olarak bir değer hesaplamanız gerektiğinde daha kısa kod oluşmasına neden olacaktır. Aşağıdaki örnek, bir tamsayıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu göstermektedir:

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür, koşullu işleci aşırı yükleyemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.

C# 7,2 ve üzeri sürümlerde eklenen özellikler hakkında daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:

- [Koşullu başvuru ifadeleri (C# 7,2)](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [Target türü belirtilmiş koşullu ifade (C# 9,0)](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [if-else deyimi](../keywords/if-else.md)
- [?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?? ve?? = işleçleri](null-coalescing-operator.md)
- [ref anahtar sözcüğü](../keywords/ref.md)
