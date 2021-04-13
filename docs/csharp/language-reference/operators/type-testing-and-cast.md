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
# <a name="type-testing-operators-and-cast-expression-c-reference"></a><span data-ttu-id="32983-103">Tür testi işleçleri ve Cast ifadesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="32983-103">Type-testing operators and cast expression (C# reference)</span></span>

<span data-ttu-id="32983-104">Tür denetimi veya tür dönüştürme gerçekleştirmek için aşağıdaki işleçleri ve ifadeleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="32983-104">You can use the following operators and expressions to perform type checking or type conversion:</span></span>

- <span data-ttu-id="32983-105">[işleç](#is-operator): bir ifadenin çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="32983-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="32983-106">[as işleci](#as-operator): çalışma zamanı türü bu türle uyumluysa bir ifadeyi açıkça belirli bir türe dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="32983-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="32983-107">[Cast ifadesi](#cast-expression): açık bir dönüştürme gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="32983-107">[cast expression](#cast-expression): to perform an explicit conversion</span></span>
- <span data-ttu-id="32983-108">[typeof işleci](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> bir türün örneğini almak için</span><span class="sxs-lookup"><span data-stu-id="32983-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="32983-109">işleç</span><span class="sxs-lookup"><span data-stu-id="32983-109">is operator</span></span>

<span data-ttu-id="32983-110">`is`İşleci, bir ifade sonucunun çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="32983-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="32983-111">C# 7,0 ile başlayarak, `is` işleci bir ifade sonucunu bir düzene göre de sınar.</span><span class="sxs-lookup"><span data-stu-id="32983-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="32983-112">Type-Testing işlecine sahip ifade `is` aşağıdaki biçimdedir</span><span class="sxs-lookup"><span data-stu-id="32983-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="32983-113">`E`, bir değer döndüren ve `T` bir tür ya da tür parametresinin adı olan bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="32983-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="32983-114">`E` anonim bir yöntem veya lambda ifadesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="32983-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="32983-115">`E is T`İfadesi, `true` sonucu `E` null olmayan ve `T` bir başvuru dönüştürmesi, paketleme dönüştürmesi ya da bir kutudan çıkarma dönüştürmesi tarafından türe dönüştürülebileceğinden, öğesini döndürür; Aksi takdirde, döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="32983-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="32983-116">`is`İşleci Kullanıcı tanımlı dönüştürmeleri dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="32983-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="32983-117">Aşağıdaki örnek, `is` `true` bir ifade sonucunun çalışma zamanı türü verilen bir türden türetilse, yani türler arasında bir başvuru dönüştürmesi varsa, işlecinin döndürdüğü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="32983-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="32983-118">Sonraki örnekte, `is` işlecin hesap paketleme ve kutudan çıkarma dönüştürmelerinin gösterdiği ancak [sayısal dönüştürmeleri](../builtin-types/numeric-conversions.md)düşünmeyen bir örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="32983-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="32983-119">C# dönüştürmeleri hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [dönüşümler](~/_csharplang/spec/conversions.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32983-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="32983-120">Model eşleştirme ile test türü</span><span class="sxs-lookup"><span data-stu-id="32983-120">Type testing with pattern matching</span></span>

<span data-ttu-id="32983-121">C# 7,0 ile başlayarak, `is` işleci bir ifade sonucunu bir düzene göre de sınar.</span><span class="sxs-lookup"><span data-stu-id="32983-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="32983-122">Aşağıdaki örnek, bir ifadenin çalışma zamanı türünü denetlemek için bir [bildirim deseninin](patterns.md#declaration-and-type-patterns) nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="32983-122">The following example shows how to use a [declaration pattern](patterns.md#declaration-and-type-patterns) to check the runtime type of an expression:</span></span>

[!code-csharp-interactive[is with declaration pattern](snippets/shared/TypeTestingAndConversionOperators.cs#IsDeclarationPattern)]

<span data-ttu-id="32983-123">Desteklenen desenler hakkında daha fazla bilgi için bkz. [desenler](patterns.md).</span><span class="sxs-lookup"><span data-stu-id="32983-123">For information about the supported patterns, see [Patterns](patterns.md).</span></span>

## <a name="as-operator"></a><span data-ttu-id="32983-124">as işleci</span><span class="sxs-lookup"><span data-stu-id="32983-124">as operator</span></span>

<span data-ttu-id="32983-125">`as`İşleci, bir ifadenin sonucunu açıkça belirli bir başvuruya veya null yapılabilir değer türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="32983-125">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="32983-126">Dönüştürme mümkün değilse, `as` işleç döndürülür `null` .</span><span class="sxs-lookup"><span data-stu-id="32983-126">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="32983-127">[Atama ifadesinin](#cast-expression)aksine, `as` işleç hiçbir şekilde özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="32983-127">Unlike a [cast expression](#cast-expression), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="32983-128">Formun ifadesi</span><span class="sxs-lookup"><span data-stu-id="32983-128">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="32983-129">, `E` bir değer döndüren ve `T` bir tür ya da tür parametresinin adı olan bir ifadedir, aynı sonucu şöyle üretir</span><span class="sxs-lookup"><span data-stu-id="32983-129">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="32983-130">hariç `E` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="32983-130">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="32983-131">`as`İşleci yalnızca başvuru, null yapılabilir, kutulama ve kutudan çıkarma dönüştürmelerini dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="32983-131">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="32983-132">`as`Kullanıcı tanımlı bir dönüştürme gerçekleştirmek için işlecini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="32983-132">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="32983-133">Bunu yapmak için bir [atama ifadesi](#cast-expression)kullanın.</span><span class="sxs-lookup"><span data-stu-id="32983-133">To do that, use a [cast expression](#cast-expression).</span></span>

<span data-ttu-id="32983-134">Aşağıdaki örnek işlecinin kullanımını gösterir `as` :</span><span class="sxs-lookup"><span data-stu-id="32983-134">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/shared/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="32983-135">Yukarıdaki örnekte gösterildiği gibi, `as` `null` dönüştürmenin başarılı olup olmadığını kontrol etmek için ifadesinin sonucunu karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32983-135">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="32983-136">C# 7,0 ' den başlayarak, dönüştürmenin başarılı olup olmadığını test etmek için, her iki [işleci](#type-testing-with-pattern-matching) de kullanabilirsiniz ve başarılı olursa, sonucunu yeni bir değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="32983-136">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-expression"></a><span data-ttu-id="32983-137">Atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="32983-137">Cast expression</span></span>

<span data-ttu-id="32983-138">Formun bir atama ifadesi `(T)E` , ifadenin sonucunun türüne açık bir şekilde dönüştürülmesini gerçekleştirir `E` `T` .</span><span class="sxs-lookup"><span data-stu-id="32983-138">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="32983-139">Türünden türüne hiçbir açık dönüştürme yoksa `E` `T` , derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="32983-139">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="32983-140">Çalışma zamanında, açık bir dönüştürme başarılı olmayabilir ve bir atama ifadesi bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="32983-140">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="32983-141">Aşağıdaki örnek, açık sayısal ve başvuru dönüştürmelerini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="32983-141">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/shared/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="32983-142">Desteklenen açık dönüştürmeler hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32983-142">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="32983-143">Özel bir açık veya örtük tür dönüştürme tanımlama hakkında daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="32983-143">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="32983-144">() Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="32983-144">Other usages of ()</span></span>

<span data-ttu-id="32983-145">Ayrıca, [bir yöntemi çağırmak veya bir temsilciyi çağırmak](member-access-operators.md#invocation-expression-)için parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32983-145">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-expression-).</span></span>

<span data-ttu-id="32983-146">Diğer parantez kullanımı, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamadır.</span><span class="sxs-lookup"><span data-stu-id="32983-146">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="32983-147">Daha fazla bilgi için bkz. [C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="32983-147">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="32983-148">typeof işleci</span><span class="sxs-lookup"><span data-stu-id="32983-148">typeof operator</span></span>

<span data-ttu-id="32983-149">`typeof`İşleci <xref:System.Type?displayProperty=nameWithType> bir tür için örneği edinir.</span><span class="sxs-lookup"><span data-stu-id="32983-149">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="32983-150">`typeof`Aşağıdaki örnekte gösterildiği gibi, işlecin bağımsız değişkeni bir tür veya tür parametresinin adı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="32983-150">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="32983-151">`typeof`İşleci ilişkisiz genel türler ile de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32983-151">You can also use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="32983-152">İlişkisiz genel türün adı, tür parametrelerinin sayısından küçük olan uygun sayıda virgül içermelidir.</span><span class="sxs-lookup"><span data-stu-id="32983-152">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="32983-153">Aşağıdaki örnek, `typeof` sınırsız bir genel türü olan işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="32983-153">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="32983-154">İfade, işlecin bağımsız değişkeni olamaz `typeof` .</span><span class="sxs-lookup"><span data-stu-id="32983-154">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="32983-155"><xref:System.Type?displayProperty=nameWithType>Bir ifade sonucunun çalışma zamanı türünün örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="32983-155">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="32983-156">İşleci ile test türü `typeof`</span><span class="sxs-lookup"><span data-stu-id="32983-156">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="32983-157">`typeof`İfade sonucunun çalışma zamanı türünün verilen bir türle tam olarak eşleşip eşleşmediğini denetlemek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="32983-157">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="32983-158">Aşağıdaki örnek, işleç ve işleç işleci ile gerçekleştirilen tür denetimi arasındaki farkı gösterir `typeof` : [](#is-operator)</span><span class="sxs-lookup"><span data-stu-id="32983-158">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/shared/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="32983-159">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="32983-159">Operator overloadability</span></span>

<span data-ttu-id="32983-160">`is`, `as` Ve `typeof` işleçleri aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="32983-160">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="32983-161">Kullanıcı tanımlı bir tür işleci aşırı yükleyemez `()` , ancak bir atama ifadesi tarafından gerçekleştirilebilecek özel tür dönüştürmeleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="32983-161">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="32983-162">Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="32983-162">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="32983-163">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="32983-163">C# language specification</span></span>

<span data-ttu-id="32983-164">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="32983-164">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="32983-165">SIS işleci</span><span class="sxs-lookup"><span data-stu-id="32983-165">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="32983-166">As işleci</span><span class="sxs-lookup"><span data-stu-id="32983-166">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="32983-167">Atama ifadeleri</span><span class="sxs-lookup"><span data-stu-id="32983-167">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="32983-168">Typeof işleci</span><span class="sxs-lookup"><span data-stu-id="32983-168">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="32983-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32983-169">See also</span></span>

- [<span data-ttu-id="32983-170">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="32983-170">C# reference</span></span>](../index.md)
- [<span data-ttu-id="32983-171">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="32983-171">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="32983-172">Desenler ve as işleçlerini kullanarak güvenli bir şekilde atama</span><span class="sxs-lookup"><span data-stu-id="32983-172">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="32983-173">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="32983-173">Generics in .NET</span></span>](../../../standard/generics/index.md)
