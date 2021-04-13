---
title: Eşitlik işleçleri-C# başvurusu
description: C# eşitlik karşılaştırma işleçleri ve C# tür eşitliği hakkında bilgi edinin.
ms.date: 10/30/2020
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
ms.openlocfilehash: ee45869dff19712d8e4ef30f2fc01c2d4633acf1
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255460"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="e0780-103">Eşitlik işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e0780-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="e0780-104">[ `==` (Eşitlik)](#equality-operator-) ve [ `!=` (eşitsizlik)](#inequality-operator-) işleçleri işlenenlerinin eşit olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="e0780-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="e0780-105">Eşitlik işleci = =</span><span class="sxs-lookup"><span data-stu-id="e0780-105">Equality operator ==</span></span>

<span data-ttu-id="e0780-106">Eşitlik işleci, `==` `true` işlenenleri eşitse, `false` Aksi takdirde döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0780-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="e0780-107">Değer türleri eşitlik</span><span class="sxs-lookup"><span data-stu-id="e0780-107">Value types equality</span></span>

<span data-ttu-id="e0780-108">[Yerleşik değer türlerinin](../builtin-types/value-types.md#built-in-value-types) işlenenleri, değerleri eşitse eşittir:</span><span class="sxs-lookup"><span data-stu-id="e0780-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/shared/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="e0780-109">,, `==` , [ `<` `>` `<=` Ve `>=` ](comparison-operators.md) işleçleri için İşlenenlerden herhangi biri bir sayı ( <xref:System.Double.NaN?displayProperty=nameWithType> veya <xref:System.Single.NaN?displayProperty=nameWithType> ) değilse, işlemin sonucu olur `false` .</span><span class="sxs-lookup"><span data-stu-id="e0780-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="e0780-110">Bu, değeri, `NaN` dahil olmak üzere herhangi bir değerden büyük, küçüktür veya eşit olmayan bir değere eşit değil anlamına gelir `double` `float` `NaN` .</span><span class="sxs-lookup"><span data-stu-id="e0780-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="e0780-111">Daha fazla bilgi ve örnek için bkz <xref:System.Double.NaN?displayProperty=nameWithType> . veya <xref:System.Single.NaN?displayProperty=nameWithType> başvuru makalesi.</span><span class="sxs-lookup"><span data-stu-id="e0780-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="e0780-112">Temeldeki integral türünün karşılık gelen değerleri eşitse aynı [sabit listesi](../builtin-types/enum.md) türünün iki işleneni eşittir.</span><span class="sxs-lookup"><span data-stu-id="e0780-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="e0780-113">Kullanıcı tanımlı [Yapı](../builtin-types/struct.md) türleri `==` Varsayılan olarak işleci desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e0780-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="e0780-114">İşleci desteklemek için `==` Kullanıcı tanımlı bir yapının onu [tekrar yüklemesi](operator-overloading.md) gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0780-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="e0780-115">C# 7,3 ile başlayarak, `==` ve `!=` Işleçleri c# [Tanımlama grupları](../builtin-types/value-tuples.md)tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e0780-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="e0780-116">Daha fazla bilgi için [demet türleri](../builtin-types/value-tuples.md) makalesinin [kayıt düzeni eşitlik](../builtin-types/value-tuples.md#tuple-equality) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0780-116">For more information, see the [Tuple equality](../builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../builtin-types/value-tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="e0780-117">Başvuru türleri eşitliği</span><span class="sxs-lookup"><span data-stu-id="e0780-117">Reference types equality</span></span>

<span data-ttu-id="e0780-118">Varsayılan olarak, kayıt olmayan iki başvuru türü işleneni aynı nesneye başvurduklarında eşittir:</span><span class="sxs-lookup"><span data-stu-id="e0780-118">By default, two non-record reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/shared/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="e0780-119">Örnekte gösterildiği gibi, Kullanıcı tanımlı başvuru türleri `==` Varsayılan olarak işleci destekler.</span><span class="sxs-lookup"><span data-stu-id="e0780-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="e0780-120">Ancak, bir başvuru türü işleci aşırı yükleyebilir `==` .</span><span class="sxs-lookup"><span data-stu-id="e0780-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="e0780-121">Bir başvuru türü işleci aşırı yükle, `==` <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> Bu türden iki başvurunun aynı nesneye başvurmasını denetlemek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0780-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="record-types-equality"></a><span data-ttu-id="e0780-122">Kayıt türleri eşitliği</span><span class="sxs-lookup"><span data-stu-id="e0780-122">Record types equality</span></span>

<span data-ttu-id="e0780-123">C# 9,0 ve üzeri sürümlerde bulunan [kayıt türleri](../builtin-types/record.md) , `==` `!=` Varsayılan olarak değer eşitlik semantiğini sağlayan ve işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="e0780-123">Available in C# 9.0 and later, [record types](../builtin-types/record.md) support the `==` and `!=` operators that by default provide value equality semantics.</span></span> <span data-ttu-id="e0780-124">Diğer bir deyişle, iki kayıt işleneni her ikisi de `null` ya da tüm alanların karşılık gelen değerleri eşitse ve otomatik uygulanan özellikler eşitse eşittir.</span><span class="sxs-lookup"><span data-stu-id="e0780-124">That is, two record operands are equal when both of them are `null` or corresponding values of all fields and auto-implemented properties are equal.</span></span>

:::code language="csharp" source="snippets/shared/EqualityOperators.cs" id="RecordTypesEquality":::

<span data-ttu-id="e0780-125">Yukarıdaki örnekte gösterildiği gibi, kayıt olmayan başvuru türü Üyeler söz konusu olduğunda başvuru değerleri karşılaştırılır, başvurulan örneklerle değil.</span><span class="sxs-lookup"><span data-stu-id="e0780-125">As the preceding example shows, in case of non-record reference-type members their reference values are compared, not the referenced instances.</span></span>

### <a name="string-equality"></a><span data-ttu-id="e0780-126">Dize eşitlik</span><span class="sxs-lookup"><span data-stu-id="e0780-126">String equality</span></span>

<span data-ttu-id="e0780-127">İki [dize](../builtin-types/reference-types.md#the-string-type) işleneni her ikisi de olduğunda eşittir `null` veya her iki dize örneği de aynı uzunluktadır ve her bir karakter konumunda özdeş karakterlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e0780-127">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/shared/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="e0780-128">Bu, büyük/küçük harfe duyarlı bir sıra karşılaştırmasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e0780-128">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="e0780-129">Dize karşılaştırması hakkında daha fazla bilgi için bkz. [C# içindeki dizeleri karşılaştırma](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="e0780-129">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="e0780-130">Temsilci eşitlik</span><span class="sxs-lookup"><span data-stu-id="e0780-130">Delegate equality</span></span>

<span data-ttu-id="e0780-131">Aynı çalışma zamanı türünün iki [temsilci](../../programming-guide/delegates/index.md) işleneni, her ikisi de `null` aynı uzunluktadır ve her konumda eşit girişlere sahip olduğunda eşittir:</span><span class="sxs-lookup"><span data-stu-id="e0780-131">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/shared/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="e0780-132">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md), [eşitlik işleçlerini temsilci](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0780-132">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="e0780-133">Anlamsal olarak özdeş [lambda ifadeleri](lambda-expressions.md) değerlendirmesinden üretilen temsilciler, aşağıdaki örnekte gösterildiği gibi eşit değildir:</span><span class="sxs-lookup"><span data-stu-id="e0780-133">Delegates that are produced from evaluation of semantically identical [lambda expressions](lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/shared/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="e0780-134">Eşitsizlik işleci! =</span><span class="sxs-lookup"><span data-stu-id="e0780-134">Inequality operator !=</span></span>

<span data-ttu-id="e0780-135">Eşitsizlik işleci, `!=` `true` işlenenleri eşit değilse döndürür, `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="e0780-135">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="e0780-136">[Yerleşik türlerin](../builtin-types/built-in-types.md)işlenenleri için ifade, `x != y` ifadesiyle aynı sonucu üretir `!(x == y)` .</span><span class="sxs-lookup"><span data-stu-id="e0780-136">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="e0780-137">Tür eşitliği hakkında daha fazla bilgi için [eşitlik işleci](#equality-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0780-137">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="e0780-138">Aşağıdaki örnek işlecinin kullanımını gösterir `!=` :</span><span class="sxs-lookup"><span data-stu-id="e0780-138">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/shared/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="e0780-139">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="e0780-139">Operator overloadability</span></span>

<span data-ttu-id="e0780-140">Kullanıcı tanımlı bir tür ve işleçlerini [aşırı](operator-overloading.md) yükleyebilir `==` `!=` .</span><span class="sxs-lookup"><span data-stu-id="e0780-140">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="e0780-141">Bir tür iki işleçten birini aşırı yüklediğinden, diğerini de aşırı yüklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0780-141">If a type overloads one of the two operators, it must also overload the other one.</span></span>

<span data-ttu-id="e0780-142">Kayıt türü, ve işleçlerini açıkça aşırı `==` yükleyemez `!=` .</span><span class="sxs-lookup"><span data-stu-id="e0780-142">A record type cannot explicitly overload the `==` and `!=` operators.</span></span> <span data-ttu-id="e0780-143">`==` `!=` Kayıt türü için ve işleçlerinin davranışını değiştirmeniz gerekiyorsa `T` , <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> yöntemi aşağıdaki imzayla uygulayın:</span><span class="sxs-lookup"><span data-stu-id="e0780-143">If you need to change the behavior of the `==` and `!=` operators for record type `T`, implement the <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> method with the following signature:</span></span>

```csharp
public virtual bool Equals(T? other);
```

## <a name="c-language-specification"></a><span data-ttu-id="e0780-144">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e0780-144">C# language specification</span></span>

<span data-ttu-id="e0780-145">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ilişkisel ve tür-test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0780-145">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="e0780-146">Kayıt türlerinin eşitliği hakkında daha fazla bilgi için, [kayıtlar Özellik teklifi notunun](~/_csharplang/proposals/csharp-9.0/records.md) [eşitlik Üyeler](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0780-146">For more information about equality of record types, see the [Equality members](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) section of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0780-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0780-147">See also</span></span>

- [<span data-ttu-id="e0780-148">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e0780-148">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e0780-149">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="e0780-149">C# operators and expressions</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e0780-150">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="e0780-150">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="e0780-151">Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="e0780-151">Comparison operators</span></span>](comparison-operators.md)
