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
# <a name="patterns-c-reference"></a><span data-ttu-id="5a3e1-103">Desenler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5a3e1-103">Patterns (C# reference)</span></span>

<span data-ttu-id="5a3e1-104">C#, c# 7,0 ' de model eşleştirmeyi sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-104">C# introduced pattern matching in C# 7.0.</span></span> <span data-ttu-id="5a3e1-105">Bu tarihten sonra, her önemli C# sürümü, model eşleme yeteneklerini genişletiyor.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-105">Since then, each major C# version extends pattern matching capabilities.</span></span> <span data-ttu-id="5a3e1-106">Aşağıdaki C# ifadeleri ve deyimleri, model eşleştirmeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-106">The following C# expressions and statements support pattern matching:</span></span>

- [<span data-ttu-id="5a3e1-107">`is` ifadesini</span><span class="sxs-lookup"><span data-stu-id="5a3e1-107">`is` expression</span></span>](../keywords/is.md)
- <span data-ttu-id="5a3e1-108">`switch`[ifade](../keywords/switch.md)</span><span class="sxs-lookup"><span data-stu-id="5a3e1-108">`switch` [statement](../keywords/switch.md)</span></span>
- <span data-ttu-id="5a3e1-109">`switch`[ifade](switch-expression.md) (C# 8,0 ' de tanıtılan)</span><span class="sxs-lookup"><span data-stu-id="5a3e1-109">`switch` [expression](switch-expression.md) (introduced in C# 8.0)</span></span>

<span data-ttu-id="5a3e1-110">Bu yapılar içinde, bir giriş ifadesini aşağıdaki desenlerden biriyle eşleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-110">In those constructs, you can match an input expression against any of the following patterns:</span></span>

- <span data-ttu-id="5a3e1-111">[Bildirim deseninin](#declaration-and-type-patterns): bir ifadenin çalışma zamanı türünü denetlemek için ve bir eşleşme başarılı olursa, belirtilen değişkene bir ifade sonucu atayın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-111">[Declaration pattern](#declaration-and-type-patterns): to check the runtime type of an expression and, if a match succeeds, assign an expression result to a declared variable.</span></span> <span data-ttu-id="5a3e1-112">C# 7,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-112">Introduced in C# 7.0.</span></span>
- <span data-ttu-id="5a3e1-113">Bir ifadenin çalışma zamanı türünü denetlemek için [tür stili](#declaration-and-type-patterns):.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-113">[Type pattern](#declaration-and-type-patterns): to check the runtime type of an expression.</span></span> <span data-ttu-id="5a3e1-114">C# 9,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-114">Introduced in C# 9.0.</span></span>
- <span data-ttu-id="5a3e1-115">[Sabit model](#constant-pattern): bir ifade sonucunun belirtilen bir sabit değere eşit olup olmadığını test etmek için.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-115">[Constant pattern](#constant-pattern): to test if an expression result equals a specified constant.</span></span> <span data-ttu-id="5a3e1-116">C# 7,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-116">Introduced in C# 7.0.</span></span>
- <span data-ttu-id="5a3e1-117">[İlişkisel desenler](#relational-patterns): bir ifade sonucunu belirtilen bir sabitle karşılaştırmak için.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-117">[Relational patterns](#relational-patterns): to compare an expression result with a specified constant.</span></span> <span data-ttu-id="5a3e1-118">C# 9,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-118">Introduced in C# 9.0.</span></span>
- <span data-ttu-id="5a3e1-119">[Mantıksal desenler](#logical-patterns): bir ifadenin bir mantıksal desen bileşimiyle eşleşip eşleşmediğini test etmek.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-119">[Logical patterns](#logical-patterns): to test if an expression matches a logical combination of patterns.</span></span> <span data-ttu-id="5a3e1-120">C# 9,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-120">Introduced in C# 9.0.</span></span>
- <span data-ttu-id="5a3e1-121">[Özellik deseni](#property-pattern): bir ifadenin özellikleri veya alanları iç içe desenlerle eşleşiyorsa test etmek için.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-121">[Property pattern](#property-pattern): to test if an expression's properties or fields match nested patterns.</span></span> <span data-ttu-id="5a3e1-122">C# 8,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-122">Introduced in C# 8.0.</span></span>
- <span data-ttu-id="5a3e1-123">[Konumsal desen](#positional-pattern): bir ifade sonucunu bırakmak ve elde edilen değerler iç içe desenlerle eşleşiyorsa test etmek için.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-123">[Positional pattern](#positional-pattern): to deconstruct an expression result and test if the resulting values match nested patterns.</span></span> <span data-ttu-id="5a3e1-124">C# 8,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-124">Introduced in C# 8.0.</span></span>
- <span data-ttu-id="5a3e1-125">[ `var` model](#var-pattern): herhangi bir ifadeyi eşleştirmek ve sonucunu belirtilen bir değişkene atamak için.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-125">[`var` pattern](#var-pattern): to match any expression and assign its result to a declared variable.</span></span> <span data-ttu-id="5a3e1-126">C# 7,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-126">Introduced in C# 7.0.</span></span>
- <span data-ttu-id="5a3e1-127">Herhangi bir ifadeyle eşleşecek şekilde [Düzenle](#discard-pattern):.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-127">[Discard pattern](#discard-pattern): to match any expression.</span></span> <span data-ttu-id="5a3e1-128">C# 8,0 ' de kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-128">Introduced in C# 8.0.</span></span>

<span data-ttu-id="5a3e1-129">[Mantıksal](#logical-patterns), [özellik](#property-pattern)ve [konumsal](#positional-pattern) desenler *özyinelemeli* desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-129">[Logical](#logical-patterns), [property](#property-pattern), and [positional](#positional-pattern) patterns are *recursive* patterns.</span></span> <span data-ttu-id="5a3e1-130">Diğer bir deyişle, *iç içe* desenler içerebilirler.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-130">That is, they can contain *nested* patterns.</span></span>

<span data-ttu-id="5a3e1-131">Veri odaklı bir algoritma oluşturmak için bu desenleri nasıl kullanacağınızı gösteren örnek için bkz. [öğretici: tür temelli ve veri odaklı algoritmalar oluşturmak için desen eşleştirmeyi kullanma](../../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="5a3e1-131">For the example of how to use those patterns to build a data-driven algorithm, see [Tutorial: Use pattern matching to build type-driven and data-driven algorithms](../../tutorials/pattern-matching.md).</span></span>

## <a name="declaration-and-type-patterns"></a><span data-ttu-id="5a3e1-132">Bildirim ve tür desenleri</span><span class="sxs-lookup"><span data-stu-id="5a3e1-132">Declaration and type patterns</span></span>

<span data-ttu-id="5a3e1-133">Bir ifadenin çalışma zamanı türünün belirli bir türle uyumlu olup olmadığını denetlemek için bildirim ve tür desenleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-133">You use declaration and type patterns to check if the runtime type of an expression is compatible with a given type.</span></span> <span data-ttu-id="5a3e1-134">Bir bildirim düzeniyle yeni bir yerel değişken de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-134">With a declaration pattern, you can also declare a new local variable.</span></span> <span data-ttu-id="5a3e1-135">Bir bildirim deseninin bir ifadeyle eşleşmesi durumunda, bu değişkene, aşağıdaki örnekte gösterildiği gibi, dönüştürülmüş bir ifade sonucu atanır:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-135">When a declaration pattern matches an expression, that variable is assigned a converted expression result, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="BasicExample":::

<span data-ttu-id="5a3e1-136">C# 7,0 ' den başlayarak,  bir `T` ifade sonucu null olmadığında ve aşağıdaki koşullardan herhangi biri doğru olduğunda tür içeren bir bildirim deseninin ifadesiyle eşleşmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-136">Beginning with C# 7.0, a *declaration pattern* with type `T` matches an expression when an expression result is non-null and any of the following conditions are true:</span></span>

- <span data-ttu-id="5a3e1-137">Bir ifade sonucunun çalışma zamanı türü `T` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-137">The runtime type of an expression result is `T`.</span></span>

- <span data-ttu-id="5a3e1-138">Bir ifade sonucunun çalışma zamanı türü tür `T` veya Implements arabiriminden türetilir ya da `T` ondan başka bir [örtük başvuru dönüştürmesi](~/_csharplang/spec/conversions.md#implicit-reference-conversions) vardır `T` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-138">The runtime type of an expression result derives from type `T` or implements interface `T` or another [implicit reference conversion](~/_csharplang/spec/conversions.md#implicit-reference-conversions) exists from it to `T`.</span></span> <span data-ttu-id="5a3e1-139">Aşağıdaki örnekte, bu koşul doğru olduğunda iki durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-139">The following example demonstrates two cases when this condition is true:</span></span>

  :::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="ReferenceConversion":::

  <span data-ttu-id="5a3e1-140">Önceki örnekte, yöntemine yapılan ilk çağrıda, `GetSourceLabel` bağımsız değişkenin çalışma zamanı türü türünden türediğinden ilk model bir bağımsız değişken değeriyle eşleşir `int[]` <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-140">In the preceding example, at the first call to the `GetSourceLabel` method, the first pattern matches an argument value because the argument's runtime type `int[]` derives from the <xref:System.Array> type.</span></span> <span data-ttu-id="5a3e1-141">Yöntemine yapılan ikinci çağrıda `GetSourceLabel` , bağımsız değişkenin çalışma zamanı türü <xref:System.Collections.Generic.List%601> türünden türetilmez, <xref:System.Array> ancak <xref:System.Collections.Generic.ICollection%601> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-141">At the second call to the `GetSourceLabel` method, the argument's runtime type <xref:System.Collections.Generic.List%601> doesn't derive from the <xref:System.Array> type but implements the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

- <span data-ttu-id="5a3e1-142">Bir ifade sonucunun çalışma zamanı türü, temel alınan türe sahip [null yapılabilen bir değer türüdür](../builtin-types/nullable-value-types.md) `T` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-142">The runtime type of an expression result is a [nullable value type](../builtin-types/nullable-value-types.md) with the underlying type `T`.</span></span>

- <span data-ttu-id="5a3e1-143">Bir ifade sonucunun çalışma zamanı türünden türüne bir [paketleme](../../programming-guide/types/boxing-and-unboxing.md#boxing) veya [kutudan](../../programming-guide/types/boxing-and-unboxing.md#unboxing) çıkarma dönüştürme var `T` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-143">A [boxing](../../programming-guide/types/boxing-and-unboxing.md#boxing) or [unboxing](../../programming-guide/types/boxing-and-unboxing.md#unboxing) conversion exists from the runtime type of an expression result to type `T`.</span></span>

<span data-ttu-id="5a3e1-144">Aşağıdaki örnek, son iki koşulu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-144">The following example demonstrates the last two conditions:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="NullableAndUnboxing":::

<span data-ttu-id="5a3e1-145">Yalnızca bir ifadenin türünü denetlemek isterseniz, `_` Aşağıdaki örnekte gösterildiği gibi, bir değişkenin adının yerine bir atma kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-145">If you want to check only the type of an expression, you can use a discard `_` in place of a variable's name, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="DiscardVariable":::

<span data-ttu-id="5a3e1-146">C# 9,0 ' den başlayarak, bu amaçla, aşağıdaki örnekte gösterildiği gibi bir *tür modelini* kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-146">Beginning with C# 9.0, for that purpose you can use a *type pattern*, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="TypePattern":::

<span data-ttu-id="5a3e1-147">Bir bildirim deseninin gibi, bir ifade sonucu null olmadığında ve çalışma zamanı türü yukarıda listelenen koşulları karşılıyorsa bir tür deseninin ifadesi eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-147">Like a declaration pattern, a type pattern matches an expression when an expression result is non-null and its runtime type satisfies any of the conditions listed above.</span></span>

<span data-ttu-id="5a3e1-148">Daha fazla bilgi için, özellik teklifi notlarının [bildirim düzenine](~/_csharplang/proposals/csharp-8.0/patterns.md#declaration-pattern) ve [tür deseninin](~/_csharplang/proposals/csharp-9.0/patterns3.md#type-patterns) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-148">For more information, see the [Declaration pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#declaration-pattern) and [Type pattern](~/_csharplang/proposals/csharp-9.0/patterns3.md#type-patterns) sections of the feature proposal notes.</span></span>

## <a name="constant-pattern"></a><span data-ttu-id="5a3e1-149">Sabit model</span><span class="sxs-lookup"><span data-stu-id="5a3e1-149">Constant pattern</span></span>

<span data-ttu-id="5a3e1-150">C# 7,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi bir ifade sonucunun belirtilen bir sabit değere eşit olup olmadığını test etmek için *sabit bir model* kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-150">Beginning with C# 7.0, you use a *constant pattern* to test if an expression result equals a specified constant, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="BasicExample":::

<span data-ttu-id="5a3e1-151">Sabit bir düzende, şöyle bir sabit ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-151">In a constant pattern, you can use any constant expression, such as:</span></span>

- <span data-ttu-id="5a3e1-152">[tamsayı](../builtin-types/integral-numeric-types.md) veya [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal sabit değeri</span><span class="sxs-lookup"><span data-stu-id="5a3e1-152">an [integer](../builtin-types/integral-numeric-types.md) or [floating-point](../builtin-types/floating-point-numeric-types.md) numerical literal</span></span>
- <span data-ttu-id="5a3e1-153">bir [char](../builtin-types/char.md) veya [dize](../builtin-types/reference-types.md#the-string-type) sabit değeri</span><span class="sxs-lookup"><span data-stu-id="5a3e1-153">a [char](../builtin-types/char.md) or a [string](../builtin-types/reference-types.md#the-string-type) literal</span></span>
- <span data-ttu-id="5a3e1-154">Boole değeri `true` veya `false`</span><span class="sxs-lookup"><span data-stu-id="5a3e1-154">a Boolean value `true` or `false`</span></span>
- <span data-ttu-id="5a3e1-155">[sabit listesi](../builtin-types/enum.md) değeri</span><span class="sxs-lookup"><span data-stu-id="5a3e1-155">an [enum](../builtin-types/enum.md) value</span></span>
- <span data-ttu-id="5a3e1-156">Belirtilen bir [const](../keywords/const.md) alanının veya yerel öğesinin adı</span><span class="sxs-lookup"><span data-stu-id="5a3e1-156">the name of a declared [const](../keywords/const.md) field or local</span></span>
- `null`

<span data-ttu-id="5a3e1-157">`null`Aşağıdaki örnekte gösterildiği gibi, denetlenecek sabit bir model kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-157">Use a constant pattern to check for `null`, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NullCheck":::

<span data-ttu-id="5a3e1-158">Derleyici, ifade değerlendirildiğinde hiçbir Kullanıcı aşırı yüklenmiş eşitlik işlecinin `==` çağırılmasını güvence altına alır `x is null` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-158">The compiler guarantees that no user-overloaded equality operator `==` is invoked when expression `x is null` is evaluated.</span></span>

<span data-ttu-id="5a3e1-159">C# 9,0 ' den başlayarak, [](#logical-patterns) `null` Aşağıdaki örnekte gösterildiği gibi, null olmayan bir sabit model kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-159">Beginning with C# 9.0, you can use a [negated](#logical-patterns) `null` constant pattern to check for non-null, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NonNullCheck":::

<span data-ttu-id="5a3e1-160">Daha fazla bilgi için, özellik teklifi notunun [sabit örüntüsünün](~/_csharplang/proposals/csharp-8.0/patterns.md#constant-pattern) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-160">For more information, see the [Constant pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#constant-pattern) section of the feature proposal note.</span></span>

## <a name="relational-patterns"></a><span data-ttu-id="5a3e1-161">İlişkisel desenler</span><span class="sxs-lookup"><span data-stu-id="5a3e1-161">Relational patterns</span></span>

<span data-ttu-id="5a3e1-162">C# 9,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi bir ifade sonucunu bir sabit ile karşılaştırmak için bir *ilişkisel model* kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-162">Beginning with C# 9.0, you use a *relational pattern* to compare an expression result with a constant, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="BasicExample":::

<span data-ttu-id="5a3e1-163">İlişkisel bir düzende,,, veya [ilişkisel işleçlerini](comparison-operators.md) kullanabilirsiniz `<` `>` `<=` `>=` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-163">In a relational pattern, you can use any of the [relational operators](comparison-operators.md) `<`, `>`, `<=`, or `>=`.</span></span> <span data-ttu-id="5a3e1-164">İlişkisel bir düzenin sağ kısmı sabit bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-164">The right-hand part of a relational pattern must be a constant expression.</span></span> <span data-ttu-id="5a3e1-165">Sabit ifade bir [tamsayı](../builtin-types/integral-numeric-types.md), [kayan nokta](../builtin-types/floating-point-numeric-types.md), [char](../builtin-types/char.md)veya [enum](../builtin-types/enum.md) türünde olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-165">The constant expression can be of an [integer](../builtin-types/integral-numeric-types.md), [floating-point](../builtin-types/floating-point-numeric-types.md), [char](../builtin-types/char.md), or [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="5a3e1-166">Bir ifade sonucunun belirli bir aralıkta olup olmadığını denetlemek için aşağıdaki örnekte gösterildiği gibi, bir [ayırt edici `and` düzende](#logical-patterns)eşleştirin:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-166">To check if an expression result is in a certain range, match it against a [conjunctive `and` pattern](#logical-patterns), as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="WithCombinators":::

<span data-ttu-id="5a3e1-167">Bir ifade sonucu, `null` null yapılabilir veya kutudan çıkarma dönüştürmesi ile bir sabit türüne dönüştürülemezse, ilişkisel bir model ifadesiyle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-167">If an expression result is `null` or fails to convert to the type of a constant by a nullable or unboxing conversion, a relational pattern doesn't match an expression.</span></span>

<span data-ttu-id="5a3e1-168">Daha fazla bilgi için, özellik teklifi notunun [ilişkisel desenler](~/_csharplang/proposals/csharp-9.0/patterns3.md#relational-patterns) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-168">For more information, see the [Relational patterns](~/_csharplang/proposals/csharp-9.0/patterns3.md#relational-patterns) section of the feature proposal note.</span></span>

## <a name="logical-patterns"></a><span data-ttu-id="5a3e1-169">Mantıksal desenler</span><span class="sxs-lookup"><span data-stu-id="5a3e1-169">Logical patterns</span></span>

<span data-ttu-id="5a3e1-170">C# 9,0 ' den başlayarak, `not` `and` `or` aşağıdaki *mantıksal desenleri* oluşturmak için,, ve desenini kombinatör kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-170">Beginning with C# 9.0, you use the `not`, `and`, and `or` pattern combinators to create the following *logical patterns*:</span></span>

- <span data-ttu-id="5a3e1-171">*Değilleme* `not` bir ifade ile eşleşen, iç içe bir model ifadesiyle eşleşen kalıp.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-171">*Negation* `not` pattern that matches an expression when the negated pattern doesn't match the expression.</span></span> <span data-ttu-id="5a3e1-172">Aşağıdaki örnek, bir ifadenin null olup olmadığını denetlemek için [sabit](#constant-pattern) bir düzenin nasıl yapılacağını gösterir `null` :</span><span class="sxs-lookup"><span data-stu-id="5a3e1-172">The following example shows how you can negate a [constant](#constant-pattern) `null` pattern to check if an expression is non-null:</span></span>

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="NotPattern":::

- <span data-ttu-id="5a3e1-173">*Conjunyatif* `and` Her iki desen de ifadesiyle eşleşen bir ifadeyle eşleşen desen.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-173">*Conjunctive* `and` pattern that matches an expression when both patterns match the expression.</span></span> <span data-ttu-id="5a3e1-174">Aşağıdaki örnek, bir değerin belirli bir aralıkta olup olmadığını denetlemek için [ilişkisel desenleri](#relational-patterns) nasıl birleştirebileceğinizi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-174">The following example shows how you can combine [relational patterns](#relational-patterns) to check if a value is in a certain range:</span></span>

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="AndPattern":::

- <span data-ttu-id="5a3e1-175">*Ayırt edici* `or` Aşağıdaki örnekte gösterildiği gibi desenlerden biri ifadesiyle eşleşen bir ifadeyle eşleşen desen:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-175">*Disjunctive* `or` pattern that matches an expression when either of patterns matches the expression, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="OrPattern":::

<span data-ttu-id="5a3e1-176">Yukarıdaki örnekte gösterildiği gibi, Kombinatör deseninin bir düzende tekrar tekrar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-176">As the preceding example shows, you can repeatedly use the pattern combinators in a pattern.</span></span>

<span data-ttu-id="5a3e1-177">`and`Combinator deseninin önceliği daha yüksektir `or` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-177">The `and` pattern combinator has higher precedence than `or`.</span></span> <span data-ttu-id="5a3e1-178">Önceliği açıkça belirtmek için aşağıdaki örnekte gösterildiği gibi ayraçları kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-178">To explicitly specify the precedence, use parentheses, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="WithParentheses":::

> [!NOTE]
> <span data-ttu-id="5a3e1-179">Desenlerin denetlenme sırası tanımsız.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-179">The order in which patterns are checked is undefined.</span></span> <span data-ttu-id="5a3e1-180">Çalışma zamanında, ve desenlerinin sağ iç içe geçmiş desenleri `or` `and` önce denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-180">At run time, the right-hand nested patterns of `or` and `and` patterns can be checked first.</span></span>

<span data-ttu-id="5a3e1-181">Daha fazla bilgi için, özellik teklifi notunun [örüntüsünün kombinatör](~/_csharplang/proposals/csharp-9.0/patterns3.md#pattern-combinators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-181">For more information, see the [Pattern combinators](~/_csharplang/proposals/csharp-9.0/patterns3.md#pattern-combinators) section of the feature proposal note.</span></span>

## <a name="property-pattern"></a><span data-ttu-id="5a3e1-182">Özellik kalıbı</span><span class="sxs-lookup"><span data-stu-id="5a3e1-182">Property pattern</span></span>

<span data-ttu-id="5a3e1-183">C# 8,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi bir ifadenin özelliklerini veya alanlarını iç içe desenlerle eşleştirmek için bir *özellik deseni* kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-183">Beginning with C# 8.0, you use a *property pattern* to match an expression's properties or fields against nested patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="BasicExample":::

<span data-ttu-id="5a3e1-184">Bir ifade sonucu null olmadığında ve tüm iç içe desenler ifade sonucunun karşılık gelen özelliği veya alanıyla eşleştiğinde bir özellik deseninin ifadesiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-184">A property pattern matches an expression when an expression result is non-null and every nested pattern matches the corresponding property or field of the expression result.</span></span>

<span data-ttu-id="5a3e1-185">Aşağıdaki örnekte gösterildiği gibi, bir özellik düzenine bir çalışma zamanı türü denetimi ve değişken bildirimi de ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-185">You can also add a runtime type check and a variable declaration to a property pattern, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="WithTypeCheck":::

<span data-ttu-id="5a3e1-186">Özellik deseninin özyinelemeli bir deseninin olması.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-186">A property pattern is a recursive pattern.</span></span> <span data-ttu-id="5a3e1-187">Diğer bir deyişle, herhangi bir kalıbı iç içe geçmiş bir model olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-187">That is, you can use any pattern as a nested pattern.</span></span> <span data-ttu-id="5a3e1-188">Aşağıdaki örnekte gösterildiği gibi, veri parçalarını iç içe geçmiş desenlere göre eşleştirmek için bir özellik deseni kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-188">Use a property pattern to match parts of data against nested patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="RecursivePropertyPattern":::

<span data-ttu-id="5a3e1-189">Yukarıdaki örnek C# 9,0 ve üzeri sürümlerde kullanılabilen iki özelliği kullanır: `or` [örüncombinator](#logical-patterns) ve [kayıt türleri](../builtin-types/record.md).</span><span class="sxs-lookup"><span data-stu-id="5a3e1-189">The preceding example uses two features available in C# 9.0 and later: `or` [pattern combinator](#logical-patterns) and [record types](../builtin-types/record.md).</span></span>

<span data-ttu-id="5a3e1-190">Daha fazla bilgi için, özellik teklifi notunun [özellik deseninin](~/_csharplang/proposals/csharp-8.0/patterns.md#property-pattern) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-190">For more information, see the [Property pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#property-pattern) section of the feature proposal note.</span></span>

## <a name="positional-pattern"></a><span data-ttu-id="5a3e1-191">Konumsal model</span><span class="sxs-lookup"><span data-stu-id="5a3e1-191">Positional pattern</span></span>

<span data-ttu-id="5a3e1-192">C# 8,0 ' den başlayarak, bir ifade sonucunu bırakmak ve elde edilen değerleri, aşağıdaki örnekte gösterildiği gibi, iç içe geçmiş desenlerle eşleştirmek için bir *konumsal düzen* kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-192">Beginning with C# 8.0, you use a *positional pattern* to deconstruct an expression result and match the resulting values against the corresponding nested patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="BasicExample":::

<span data-ttu-id="5a3e1-193">Önceki örnekte, bir ifadenin türü bir ifade sonucunu bırakmak için kullanılan [deyapýsý](../../deconstruct.md) metodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-193">At the preceding example, the type of an expression contains the [Deconstruct](../../deconstruct.md) method, which is used to deconstruct an expression result.</span></span> <span data-ttu-id="5a3e1-194">Ayrıca, konumsal desenlerde [demet türleri](../builtin-types/value-tuples.md) ifadelerini de eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-194">You can also match expressions of [tuple types](../builtin-types/value-tuples.md) against positional patterns.</span></span> <span data-ttu-id="5a3e1-195">Bu şekilde, aşağıdaki örnekte gösterildiği gibi çeşitli modellerdeki birden çok girişi eşleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-195">In that way, you can match multiple inputs against various patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="MatchTuple":::

<span data-ttu-id="5a3e1-196">Önceki örnekte, C# 9,0 ve üzeri sürümlerde kullanılabilen [ilişkisel](#relational-patterns) ve [mantıksal](#logical-patterns) desenler kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-196">The preceding example uses [relational](#relational-patterns) and [logical](#logical-patterns) patterns, which are available in C# 9.0 and later.</span></span>

<span data-ttu-id="5a3e1-197">`Deconstruct`Aşağıdaki örnekte gösterildiği gibi, konumsal bir düzende demet öğelerinin ve parametrelerinin adlarını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-197">You can use the names of tuple elements and `Deconstruct` parameters in a positional pattern, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="UseIdentifiers":::

<span data-ttu-id="5a3e1-198">Ayrıca, konum düzenlerini aşağıdaki yollarla genişletebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-198">You can also extend a positional pattern in any of the following ways:</span></span>

- <span data-ttu-id="5a3e1-199">Aşağıdaki örnekte gösterildiği gibi, bir çalışma zamanı türü denetimi ve bir değişken bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-199">Add a runtime type check and a variable declaration, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithTypeCheck":::

  <span data-ttu-id="5a3e1-200">Yukarıdaki örnek, yöntemi örtük olarak sağlayan [konumsal kayıtları](../builtin-types/record.md#positional-syntax-for-property-definition) kullanır `Deconstruct` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-200">The preceding example uses [positional records](../builtin-types/record.md#positional-syntax-for-property-definition) that implicitly provide the `Deconstruct` method.</span></span>

- <span data-ttu-id="5a3e1-201">Aşağıdaki örnekte gösterildiği gibi, konumsal model içinde bir [özellik kalıbı](#property-pattern) kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-201">Use a [property pattern](#property-pattern) within a positional pattern, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithPropertyPattern":::

- <span data-ttu-id="5a3e1-202">Aşağıdaki örnekte gösterildiği gibi, önceki iki kullanımı birleştirin:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-202">Combine two preceding usages, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="CompletePositionalPattern":::

<span data-ttu-id="5a3e1-203">Konumsal bir model özyinelemeli bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-203">A positional pattern is a recursive pattern.</span></span> <span data-ttu-id="5a3e1-204">Diğer bir deyişle, herhangi bir kalıbı iç içe geçmiş bir model olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-204">That is, you can use any pattern as a nested pattern.</span></span>

<span data-ttu-id="5a3e1-205">Daha fazla bilgi için, özellik teklifi notunun [konumsal model](~/_csharplang/proposals/csharp-8.0/patterns.md#positional-pattern) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-205">For more information, see the [Positional pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#positional-pattern) section of the feature proposal note.</span></span>

## <a name="var-pattern"></a><span data-ttu-id="5a3e1-206">`var` kalıp</span><span class="sxs-lookup"><span data-stu-id="5a3e1-206">`var` pattern</span></span>

<span data-ttu-id="5a3e1-207">C# 7,0 ' den başlayarak, aşağıdaki örnekte *`var`* gösterildiği gibi herhangi bir ifadeyi eşleştirmek `null` ve bunun sonucunu yeni bir yerel değişkene atamak için bir kalıp kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-207">Beginning with C# 7.0, you use a *`var` pattern* to match any expression, including `null`, and assign its result to a new local variable, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="KeepInterimResult":::

<span data-ttu-id="5a3e1-208">Bir dizi, `var` Ara hesaplamaların sonucunu tutacak bir Boolean ifadesinde geçici bir değişkene ihtiyacınız olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-208">A `var` pattern is useful when you need a temporary variable within a Boolean expression to hold the result of intermediate calculations.</span></span> <span data-ttu-id="5a3e1-209">`var` `when` `switch` Aşağıdaki örnekte gösterildiği gibi, bir ifadenin veya deyimin büyük/küçük harf korugeçirmeleri üzerinde ek denetimler gerçekleştirmeniz gerektiğinde de bir kalıp kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-209">You can also use a `var` pattern when you need to perform additional checks in `when` case guards of a `switch` expression or statement, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="WithCaseGuards":::

<span data-ttu-id="5a3e1-210">Yukarıdaki örnekte, `var (x, y)` bir [konum düzenine](#positional-pattern) eşdeğerdir `(var x, var y)` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-210">In the preceding example, pattern `var (x, y)` is equivalent to a [positional pattern](#positional-pattern) `(var x, var y)`.</span></span>

<span data-ttu-id="5a3e1-211">Bir `var` düzende, belirtilen bir değişkenin türü, düzeniyle eşleşen ifadenin derleme zamanı türüdür.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-211">In a `var` pattern, the type of a declared variable is the compile-time type of the expression that is matched against the pattern.</span></span>

<span data-ttu-id="5a3e1-212">Daha fazla bilgi için, özellik teklifi notunun [var olan örüntüsünün](~/_csharplang/proposals/csharp-8.0/patterns.md#var-pattern) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-212">For more information, see the [Var pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#var-pattern) section of the feature proposal note.</span></span>

## <a name="discard-pattern"></a><span data-ttu-id="5a3e1-213">Stili at</span><span class="sxs-lookup"><span data-stu-id="5a3e1-213">Discard pattern</span></span>

<span data-ttu-id="5a3e1-214">C# 8,0 ' den başlayarak,  `_` `null` Aşağıdaki örnekte gösterildiği gibi herhangi bir ifadeyle eşleşecek bir atma stili kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-214">Beginning with C# 8.0, you use a *discard pattern* `_` to match any expression, including `null`, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DiscardPattern.cs" id="BasicExample":::

<span data-ttu-id="5a3e1-215">Önceki örnekte, işlemek için bir atma deseninin kullanıldığı `null` ve Numaralandırmadaki karşılık gelen üyesine sahip olmayan herhangi bir tamsayı değeri <xref:System.DayOfWeek> .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-215">In the preceding example, a discard pattern is used to handle `null` and any integer value that doesn't have the corresponding member of the <xref:System.DayOfWeek> enumeration.</span></span> <span data-ttu-id="5a3e1-216">Bu `switch` , örnekteki bir ifadenin tüm olası girdi değerlerini işlemesini güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-216">That guarantees that a `switch` expression in the example handles all possible input values.</span></span> <span data-ttu-id="5a3e1-217">Bir ifadede bir atma deseni kullanmıyorsanız `switch` ve ifadenin desenlerinin bir girişle eşleşmesi gerekmiyorsa, çalışma zamanı [bir özel durum oluşturur](switch-expression.md#non-exhaustive-switch-expressions).</span><span class="sxs-lookup"><span data-stu-id="5a3e1-217">If you don't use a discard pattern in a `switch` expression and none of the expression's patterns matches an input, the runtime [throws an exception](switch-expression.md#non-exhaustive-switch-expressions).</span></span> <span data-ttu-id="5a3e1-218">Bir `switch` ifade tüm olası giriş değerlerini işlemezse derleyici bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-218">The compiler generates a warning if a `switch` expression doesn't handle all possible input values.</span></span>

<span data-ttu-id="5a3e1-219">Bir atma deseninin ifadesi veya deyimi içindeki bir model olamaz `is` `switch` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-219">A discard pattern cannot be a pattern in an `is` expression or a `switch` statement.</span></span> <span data-ttu-id="5a3e1-220">Bu durumlarda, herhangi bir ifadeyi eşleştirmek için, at: ile bir [ `var` desenler](#var-pattern) kullanın `var _` .</span><span class="sxs-lookup"><span data-stu-id="5a3e1-220">In those cases, to match any expression, use a [`var` pattern](#var-pattern) with a discard: `var _`.</span></span>

<span data-ttu-id="5a3e1-221">Daha fazla bilgi için, özellik teklifi notunun [atma düzenine](~/_csharplang/proposals/csharp-8.0/patterns.md#discard-pattern) bakın.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-221">For more information, see the [Discard pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#discard-pattern) section of the feature proposal note.</span></span>

## <a name="parenthesized-pattern"></a><span data-ttu-id="5a3e1-222">Parantez içine alınmış desenler</span><span class="sxs-lookup"><span data-stu-id="5a3e1-222">Parenthesized pattern</span></span>

<span data-ttu-id="5a3e1-223">C# 9,0 ' den başlayarak, herhangi bir düzenin çevresine parantez koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-223">Beginning with C# 9.0, you can put parentheses around any pattern.</span></span> <span data-ttu-id="5a3e1-224">Genellikle, aşağıdaki örnekte gösterildiği gibi [mantıksal desenlerdeki](#logical-patterns)önceliği vurgulamak veya değiştirmek için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-224">Typically, you do that to emphasize or change the precedence in [logical patterns](#logical-patterns), as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="ChangedPrecedence":::

## <a name="c-language-specification"></a><span data-ttu-id="5a3e1-225">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5a3e1-225">C# language specification</span></span>

<span data-ttu-id="5a3e1-226">Daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:</span><span class="sxs-lookup"><span data-stu-id="5a3e1-226">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="5a3e1-227">C# 7,0 için model eşleştirme</span><span class="sxs-lookup"><span data-stu-id="5a3e1-227">Pattern matching for C# 7.0</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="5a3e1-228">Özyinelemeli model eşleştirme (C# 8,0 ' de tanıtılan)</span><span class="sxs-lookup"><span data-stu-id="5a3e1-228">Recursive pattern matching (introduced in C# 8.0)</span></span>](~/_csharplang/proposals/csharp-8.0/patterns.md)
- [<span data-ttu-id="5a3e1-229">C# 9,0 için kalıp eşleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="5a3e1-229">Pattern-matching changes for C# 9.0</span></span>](~/_csharplang/proposals/csharp-9.0/patterns3.md)

## <a name="see-also"></a><span data-ttu-id="5a3e1-230">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a3e1-230">See also</span></span>

- [<span data-ttu-id="5a3e1-231">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5a3e1-231">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5a3e1-232">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5a3e1-232">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="5a3e1-233">Öğretici: tür odaklı ve veri odaklı algoritmalar oluşturmak için model eşleştirmeyi kullanın</span><span class="sxs-lookup"><span data-stu-id="5a3e1-233">Tutorial: Use pattern matching to build type-driven and data-driven algorithms</span></span>](../../tutorials/pattern-matching.md)
