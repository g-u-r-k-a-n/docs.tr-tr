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
# <a name="-operator-c-reference"></a><span data-ttu-id="5f7f8-103">?: işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5f7f8-103">?: operator (C# reference)</span></span>

<span data-ttu-id="5f7f8-104">`?:`Üçlü işleç olarak da bilinen koşullu operatör, Boole ifadesi değerlendirir ve `true` `false` Aşağıdaki örnekte gösterildiği gibi, Boolean ifadesinin veya olarak değerlendirildiğine bağlı olarak iki ifadeden birinin sonucunu döndürür:</span><span class="sxs-lookup"><span data-stu-id="5f7f8-104">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`, as the following example shows:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="snippets/shared/ConditionalOperator.cs" id="BasicExample":::

<span data-ttu-id="5f7f8-105">Yukarıdaki örnekte gösterildiği gibi, koşullu işlecin sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5f7f8-105">As the preceding example shows, the syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="5f7f8-106">`condition`İfade veya olarak değerlendirilmelidir `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="5f7f8-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="5f7f8-107">`condition`, Olarak değerlendirilirse `true` , `consequent` ifade değerlendirilir ve sonucu işlemin sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="5f7f8-108">`condition`, Olarak değerlendirilirse `false` , `alternative` ifade değerlendirilir ve sonucu işlemin sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="5f7f8-109">Yalnızca `consequent` veya `alternative` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="5f7f8-110">C# 9,0 ' den başlayarak Koşullu ifadeler Target türünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-110">Beginning with C# 9.0, conditional expressions are target-typed.</span></span> <span data-ttu-id="5f7f8-111">Diğer bir deyişle, koşullu bir ifadenin hedef türü biliniyorsa, `consequent` `alternative` Aşağıdaki örnekte gösterildiği gibi, ve türlerinin hedef türüne örtülü olarak dönüştürülebilir olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="5f7f8-111">That is, if a target type of a conditional expression is known, the types of `consequent` and `alternative` must be implicitly convertible to the target type, as the following example shows:</span></span>

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

<span data-ttu-id="5f7f8-112">Koşullu ifadenin hedef türü bilinmiyorsa (örneğin, [`var`](../keywords/var.md) anahtar sözcüğünü kullandığınızda) veya C# 8,0 ve önceki sürümlerde, türü `consequent` ve `alternative` aynı olmalıdır veya bir türden diğerine örtük bir dönüştürme olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="5f7f8-112">If a target type of a conditional expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword) or in C# 8.0 and earlier, the type of `consequent` and `alternative` must be the same or there must be an implicit conversion from one type to the other:</span></span>

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

<span data-ttu-id="5f7f8-113">Koşullu operatör doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi</span><span class="sxs-lookup"><span data-stu-id="5f7f8-113">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="5f7f8-114">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="5f7f8-114">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="5f7f8-115">Koşullu işlecin nasıl değerlendirildiğini anımsamak için aşağıdaki anımsatıcı cihazı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5f7f8-115">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

## <a name="conditional-ref-expression"></a><span data-ttu-id="5f7f8-116">Koşullu başvuru ifadesi</span><span class="sxs-lookup"><span data-stu-id="5f7f8-116">Conditional ref expression</span></span>

<span data-ttu-id="5f7f8-117">C# 7,2 ile başlayarak, bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkeni koşullu bir başvuru ifadesiyle koşullu olarak atanabilir.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-117">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with a conditional ref expression.</span></span> <span data-ttu-id="5f7f8-118">Ayrıca, bir [Başvuru dönüş değeri](../keywords/ref.md#reference-return-values) veya [ `ref` Yöntem bağımsız değişkeni](../keywords/ref.md#passing-an-argument-by-reference)olarak bir koşullu başvuru ifadesi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-118">You can also use a conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="5f7f8-119">Koşullu başvuru ifadesi için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5f7f8-119">The syntax for a conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="5f7f8-120">Özgün koşullu operatör gibi, koşullu bir başvuru ifadesi iki ifadeden yalnızca birini değerlendirir: `consequent` ya da `alternative` .</span><span class="sxs-lookup"><span data-stu-id="5f7f8-120">Like the original conditional operator, a conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="5f7f8-121">Koşullu başvuru ifadesi durumunda, `consequent` ve türü `alternative` aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-121">In the case of a conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span> <span data-ttu-id="5f7f8-122">Koşullu başvuru ifadeleri Target türünde değil.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-122">Conditional ref expressions are not target-typed.</span></span>

<span data-ttu-id="5f7f8-123">Aşağıdaki örnek, bir koşullu başvuru ifadesinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5f7f8-123">The following example demonstrates the usage of a conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="5f7f8-124">Koşullu işleç ve bir `if..else` ifade</span><span class="sxs-lookup"><span data-stu-id="5f7f8-124">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="5f7f8-125">[İf-else](../keywords/if-else.md) ifadesinin yerine koşullu işlecin kullanılması, bir değeri hesaplamak için koşullu olarak bir değer hesaplamanız gerektiğinde daha kısa kod oluşmasına neden olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-125">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="5f7f8-126">Aşağıdaki örnek, bir tamsayıyı negatif veya negatif olmayan olarak sınıflandırmanın iki yolunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5f7f8-126">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="5f7f8-127">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="5f7f8-127">Operator overloadability</span></span>

<span data-ttu-id="5f7f8-128">Kullanıcı tanımlı bir tür, koşullu işleci aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-128">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5f7f8-129">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5f7f8-129">C# language specification</span></span>

<span data-ttu-id="5f7f8-130">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [koşullu işleç](~/_csharplang/spec/expressions.md#conditional-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-130">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="5f7f8-131">C# 7,2 ve üzeri sürümlerde eklenen özellikler hakkında daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:</span><span class="sxs-lookup"><span data-stu-id="5f7f8-131">For more information about features added in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="5f7f8-132">Koşullu başvuru ifadeleri (C# 7,2)</span><span class="sxs-lookup"><span data-stu-id="5f7f8-132">Conditional ref expressions (C# 7.2)</span></span>](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [<span data-ttu-id="5f7f8-133">Target türü belirtilmiş koşullu ifade (C# 9,0)</span><span class="sxs-lookup"><span data-stu-id="5f7f8-133">Target-typed conditional expression (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a><span data-ttu-id="5f7f8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-134">See also</span></span>

- [<span data-ttu-id="5f7f8-135">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5f7f8-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5f7f8-136">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5f7f8-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="5f7f8-137">if-else deyimi</span><span class="sxs-lookup"><span data-stu-id="5f7f8-137">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="5f7f8-138">[?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="5f7f8-138">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="5f7f8-139">?? ve?? = işleçleri</span><span class="sxs-lookup"><span data-stu-id="5f7f8-139">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="5f7f8-140">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="5f7f8-140">ref keyword</span></span>](../keywords/ref.md)
