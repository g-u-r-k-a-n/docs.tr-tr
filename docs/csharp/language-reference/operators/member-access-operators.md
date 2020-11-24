---
title: Üye erişim işleçleri ve ifadeleri-C# başvurusu
description: Tür üyelerine erişmek için kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
ms.date: 11/13/2020
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: 28d3d9c3261f1a852d16f2637309b21412611c10
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691246"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="bce38-103">Üye erişim işleçleri ve ifadeleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bce38-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="bce38-104">Bir tür üyesine eriştiğinizde aşağıdaki işleçleri ve ifadeleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bce38-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="bce38-105">[ `.` (üye erişimi)](#member-access-expression-): bir ad alanının veya türün üyesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="bce38-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="bce38-106">[ `[]` (dizi öğesi veya Dizin Oluşturucu erişimi)](#indexer-operator-): bir dizi öğesine veya bir tür dizin oluşturucusuna erişmek için</span><span class="sxs-lookup"><span data-stu-id="bce38-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="bce38-107">[ `?.` ve `?[]` (null koşullu işleçler)](#null-conditional-operators--and-): yalnızca bir işlenen null değilse üye veya öğe erişim işlemi gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="bce38-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="bce38-108">[ `()` (çağırma)](#invocation-expression-): erişilen bir yöntemi çağırmak veya bir temsilciyi çağırmak için</span><span class="sxs-lookup"><span data-stu-id="bce38-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="bce38-109">[ `^` (uçtan dizin)](#index-from-end-operator-): öğe konumunun bir sıranın sonundan olduğunu göstermek için</span><span class="sxs-lookup"><span data-stu-id="bce38-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="bce38-110">[ `..` (Aralık)](#range-operator-): dizi öğeleri aralığını almak için kullanabileceğiniz bir dizin aralığı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="bce38-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="bce38-111">Üye erişim ifadesi.</span><span class="sxs-lookup"><span data-stu-id="bce38-111">Member access expression .</span></span>

<span data-ttu-id="bce38-112">`.`Aşağıdaki örneklerde gösterildiği gibi, belirteci, bir ad uzayı veya bir tür üyesine erişmek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bce38-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="bce38-113">`.`Aşağıdaki bir [ `using` yönerge](../keywords/using-directive.md) örneğinde gösterildiği gibi, bir ad alanı içinde iç içe geçmiş bir ad alanına erişmek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="bce38-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/shared/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="bce38-114">`.`Aşağıdaki kodun gösterdiği gibi, bir ad alanı içindeki bir türe erişmek üzere *nitelenmiş bir ad* oluşturmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="bce38-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/shared/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="bce38-115">Nitelenmiş adların kullanımını isteğe bağlı yapmak için bir [ `using` yönergesi](../keywords/using-directive.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bce38-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="bce38-116">`.`Aşağıdaki kodda gösterildiği gibi, [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan erişim için kullanın:</span><span class="sxs-lookup"><span data-stu-id="bce38-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/shared/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="bce38-117">Ayrıca, `.` bir [genişletme yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bce38-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="bce38-118">Indexer işleci []</span><span class="sxs-lookup"><span data-stu-id="bce38-118">Indexer operator []</span></span>

<span data-ttu-id="bce38-119">Köşeli parantezler, `[]` genellikle Array, Indexer veya pointer öğesi erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bce38-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="bce38-120">Dizi erişimi</span><span class="sxs-lookup"><span data-stu-id="bce38-120">Array access</span></span>

<span data-ttu-id="bce38-121">Aşağıdaki örnek, dizi öğelerine nasıl erişileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="bce38-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/shared/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="bce38-122">Bir dizi dizini, bir dizi karşılık gelen boyutun sınırları dışındaysa, bir oluşturulur <xref:System.IndexOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="bce38-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="bce38-123">Yukarıdaki örnekte gösterildiği gibi, bir dizi türü bildirdiğinizde veya bir dizi örneği örneklediğinizde köşeli parantezleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bce38-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="bce38-124">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="bce38-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="bce38-125">Dizin Oluşturucu erişimi</span><span class="sxs-lookup"><span data-stu-id="bce38-125">Indexer access</span></span>

<span data-ttu-id="bce38-126">Aşağıdaki örnek, <xref:System.Collections.Generic.Dictionary%602> Dizin Oluşturucu erişimini göstermek için .NET türünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="bce38-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/shared/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="bce38-127">Dizin oluşturucular, Kullanıcı tanımlı bir türün örneklerinin, dizi dizini oluşturma gibi benzer şekilde dizinlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bce38-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="bce38-128">Tamsayı olması gereken dizi dizinlerinin aksine, Dizin Oluşturucu parametreleri herhangi bir türde olacak şekilde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bce38-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="bce38-129">Dizin oluşturucular hakkında daha fazla bilgi için bkz. [Dizin oluşturucular](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="bce38-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="bce38-130">[] Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="bce38-130">Other usages of []</span></span>

<span data-ttu-id="bce38-131">İşaretçi öğesi erişimi hakkında daha fazla bilgi için, [işaretçi ilgili işleçler](pointer-related-operators.md) makalesinin [işaretçi öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bce38-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="bce38-132">Ayrıca, [öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için köşeli parantezleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bce38-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="bce38-133">Null koşullu işleçler?.</span><span class="sxs-lookup"><span data-stu-id="bce38-133">Null-conditional operators ?.</span></span> <span data-ttu-id="bce38-134">'? []</span><span class="sxs-lookup"><span data-stu-id="bce38-134">and ?[]</span></span>

<span data-ttu-id="bce38-135">C# 6 ve üzeri sürümlerde kullanılabilir, null koşullu bir operatör, [member access](#member-access-expression-) `?.` yalnızca o işlenen null olmayan olarak değerlendiriliyorsa işlenene bir üye erişimi, veya [öğe erişimi](#indexer-operator-)uygular `?[]` ; Aksi takdirde, döndürür `null` .</span><span class="sxs-lookup"><span data-stu-id="bce38-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="bce38-136">Yani</span><span class="sxs-lookup"><span data-stu-id="bce38-136">That is,</span></span>

- <span data-ttu-id="bce38-137">`a`Olarak değerlendirilirse `null` , `a?.x` veya `a?[x]` olur `null` .</span><span class="sxs-lookup"><span data-stu-id="bce38-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="bce38-138">`a`Null olmayan olarak değerlendirilirse, veya sonucu, `a?.x` sırasıyla veya sonucu ile `a?[x]` aynıdır `a.x` `a[x]` .</span><span class="sxs-lookup"><span data-stu-id="bce38-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="bce38-139">`a.x`Ya da `a[x]` bir özel durum oluşturursa `a?.x` ya da `a?[x]` null olmayan bir özel durum oluşturur `a` .</span><span class="sxs-lookup"><span data-stu-id="bce38-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="bce38-140">Örneğin, `a` null olmayan bir dizi örneğidir ve `x` sınırları dışındaysa `a` `a?[x]` bir oluşturur <xref:System.IndexOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="bce38-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="bce38-141">Null koşullu işleçler kısa devre dışı.</span><span class="sxs-lookup"><span data-stu-id="bce38-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="bce38-142">Diğer bir deyişle, bir koşullu üye veya öğe erişim işlemleri zincirindeki bir işlem dönerse `null` , zincir geri kalanı yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="bce38-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="bce38-143">Aşağıdaki örnekte, `B` `A` olarak değerlendirilirse `null` ve `C` değerlendirmesi durumunda hesaplanmaz `A` `B` `null` :</span><span class="sxs-lookup"><span data-stu-id="bce38-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="bce38-144">Aşağıdaki örnek, `?.` ve işleçlerinin kullanımını gösterir `?[]` :</span><span class="sxs-lookup"><span data-stu-id="bce38-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/shared/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="bce38-145">Yukarıdaki örnek, null-koşullu bir işlemin sonucu olarak değerlendirmek için alternatif bir ifade belirtmek üzere [null birleşim işlecini `??` ](null-coalescing-operator.md) de kullanır `null` .</span><span class="sxs-lookup"><span data-stu-id="bce38-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="bce38-146">`a.x`Ya da `a[x]` null yapılamayan bir değer türü ise `T` `a?.x` veya `a?[x]` buna karşılık gelen [null atanabilir değer türüdür](../builtin-types/nullable-value-types.md) `T?` .</span><span class="sxs-lookup"><span data-stu-id="bce38-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="bce38-147">Türünde bir ifadeye ihtiyacınız varsa `T` , `??` Aşağıdaki örnekte gösterildiği gibi null birleşim işlecini null koşullu ifadeye uygulayın:</span><span class="sxs-lookup"><span data-stu-id="bce38-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/shared/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="bce38-148">Önceki örnekte, işlecini kullanmıyorsanız, `??` `numbers?.Length < 2` `false` ne zaman `numbers` olduğunu değerlendirir `null` .</span><span class="sxs-lookup"><span data-stu-id="bce38-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="bce38-149">Null koşullu üye erişim işleci `?.` ELVIS işleci olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="bce38-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="bce38-150">İş parçacığı açısından güvenli temsilci çağırma</span><span class="sxs-lookup"><span data-stu-id="bce38-150">Thread-safe delegate invocation</span></span>

<span data-ttu-id="bce38-151">`?.`Bir temsilcinin null olup olmadığını denetlemek ve iş parçacığı güvenli bir şekilde (örneğin, [bir olay](../../../standard/events/how-to-raise-and-consume-events.md)yükselttiğinizde) aşağıdaki kodun gösterdiği gibi, bir temsilciyi çağırmak için işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="bce38-151">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="bce38-152">Bu kod, C# 5 veya daha önceki bir sürümünde kullanacağınız aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="bce38-152">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

<span data-ttu-id="bce38-153">Bu, yalnızca null olmayan bir değer çağrılmasını sağlamak için iş parçacığı açısından güvenli bir yoldur `handler` .</span><span class="sxs-lookup"><span data-stu-id="bce38-153">That is a thread-safe way to ensure that only a non-null `handler` is invoked.</span></span> <span data-ttu-id="bce38-154">Temsilci örnekleri sabit olduğu için, hiçbir iş parçacığı yerel değişken tarafından başvurulan nesneyi değiştiremez `handler` .</span><span class="sxs-lookup"><span data-stu-id="bce38-154">Because delegate instances are immutable, no thread can change the object referenced by the `handler` local variable.</span></span> <span data-ttu-id="bce38-155">Özellikle, başka bir iş parçacığı tarafından yürütülen kod, olaydan aboneliği kaldırır `PropertyChanged` ve `PropertyChanged` `null` önce gelirse `handler` , tarafından başvurulan nesne `handler` etkilenmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="bce38-155">In particular, if the code executed by another thread unsubscribes from the `PropertyChanged` event and `PropertyChanged` becomes `null` before `handler` is invoked, the object referenced by `handler` remains unaffected.</span></span> <span data-ttu-id="bce38-156">`?.`İşleci sol taraftaki işlenenini birden çok kez değerlendirir ve `null` null olmayan olarak doğrulandıktan sonra olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="bce38-156">The `?.` operator evaluates its left-hand operand no more than once, guaranteeing that it cannot be changed to `null` after being verified as non-null.</span></span>

## <a name="invocation-expression-"></a><span data-ttu-id="bce38-157">Çağırma ifadesi ()</span><span class="sxs-lookup"><span data-stu-id="bce38-157">Invocation expression ()</span></span>

<span data-ttu-id="bce38-158">`()`Bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) çağırmak veya bir [temsilciyi](../../programming-guide/delegates/index.md)çağırmak için parantezleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="bce38-158">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="bce38-159">Aşağıdaki örnek, bağımsız değişkenler içeren veya olmayan bir yöntemin nasıl çağrılacağını gösterir ve bir temsilciyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="bce38-159">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/shared/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="bce38-160">İşleci ile bir [Oluşturucu](../../programming-guide/classes-and-structs/constructors.md) çağırdığınızda parantezleri de kullanabilirsiniz [`new`](new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="bce38-160">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="bce38-161">() Diğer kullanımları</span><span class="sxs-lookup"><span data-stu-id="bce38-161">Other usages of ()</span></span>

<span data-ttu-id="bce38-162">Ayrıca, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamak için parantez de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bce38-162">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="bce38-163">Daha fazla bilgi için bkz. [C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="bce38-163">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="bce38-164">Açık tür dönüştürmeleri gerçekleştiren [atama ifadeleri](type-testing-and-cast.md#cast-expression), parantez de kullanır.</span><span class="sxs-lookup"><span data-stu-id="bce38-164">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="bce38-165">Bitiş işlecinden Dizin ^</span><span class="sxs-lookup"><span data-stu-id="bce38-165">Index from end operator ^</span></span>

<span data-ttu-id="bce38-166">C# 8,0 ve üzeri sürümlerde kullanılabilen işleç, `^` öğe konumunun bir dizinin sonundan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bce38-166">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="bce38-167">Bir uzunluk sırası için `length` , `^n` `length - n` bir dizi başlangıcının sonuna kadar olan öğesine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="bce38-167">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="bce38-168">Örneğin, `^1` bir sıranın son öğesine işaret eder ve `^length` dizinin ilk öğesine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="bce38-168">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/shared/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="bce38-169">Yukarıdaki örnekte gösterildiği gibi, ifadesi `^e` <xref:System.Index?displayProperty=nameWithType> türüdür.</span><span class="sxs-lookup"><span data-stu-id="bce38-169">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="bce38-170">İfadesinde `^e` , sonucu `e` örtük olarak dönüştürülebilir olmalıdır `int` .</span><span class="sxs-lookup"><span data-stu-id="bce38-170">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="bce38-171">Ayrıca `^` bir dizin aralığı oluşturmak için işleci [Aralık işleciyle](#range-operator-) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bce38-171">You can also use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="bce38-172">Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="bce38-172">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="bce38-173">Aralık işleci..</span><span class="sxs-lookup"><span data-stu-id="bce38-173">Range operator ..</span></span>

<span data-ttu-id="bce38-174">C# 8,0 ve üzeri sürümlerde kullanılabilen işleç, `..` işlenen bir dizin aralığının başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bce38-174">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="bce38-175">Sol işlenen bir aralığın *kapsamlı* bir başlangıcı olur.</span><span class="sxs-lookup"><span data-stu-id="bce38-175">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="bce38-176">Sağ işlenen bir aralığın *dışlamalı* bir sonu.</span><span class="sxs-lookup"><span data-stu-id="bce38-176">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="bce38-177">Her iki işlenen de, aşağıdaki örnekte gösterildiği gibi, bir sıranın başından veya sonundan bir dizin olabilir:</span><span class="sxs-lookup"><span data-stu-id="bce38-177">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/shared/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="bce38-178">Yukarıdaki örnekte gösterildiği gibi, ifadesi `a..b` <xref:System.Range?displayProperty=nameWithType> türüdür.</span><span class="sxs-lookup"><span data-stu-id="bce38-178">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="bce38-179">İfadesinde `a..b` , `a` ve sonuçları `b` örtülü olarak veya olarak dönüştürülebilir olmalıdır `int` <xref:System.Index> .</span><span class="sxs-lookup"><span data-stu-id="bce38-179">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="bce38-180">`..`Açık uçlu bir Aralık almak için işlecin işlenenlerinden herhangi birini atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bce38-180">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="bce38-181">`a..` eşdeğerdir `a..^0`</span><span class="sxs-lookup"><span data-stu-id="bce38-181">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="bce38-182">`..b` eşdeğerdir `0..b`</span><span class="sxs-lookup"><span data-stu-id="bce38-182">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="bce38-183">`..` eşdeğerdir `0..^0`</span><span class="sxs-lookup"><span data-stu-id="bce38-183">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/shared/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="bce38-184">Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="bce38-184">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="bce38-185">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="bce38-185">Operator overloadability</span></span>

<span data-ttu-id="bce38-186">`.`,, `()` `^` , Ve `..` işleçleri aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="bce38-186">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="bce38-187">`[]`İşleci, aşırı yüklenebilir olmayan bir işleç olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="bce38-187">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="bce38-188">Kullanıcı tanımlı türlerle Dizin oluşturmayı desteklemek için [Dizin oluşturucular](../../programming-guide/indexers/index.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bce38-188">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bce38-189">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="bce38-189">C# language specification</span></span>

<span data-ttu-id="bce38-190">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="bce38-190">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="bce38-191">Üye erişimi</span><span class="sxs-lookup"><span data-stu-id="bce38-191">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="bce38-192">Öğe erişimi</span><span class="sxs-lookup"><span data-stu-id="bce38-192">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="bce38-193">Null-koşullu işleç</span><span class="sxs-lookup"><span data-stu-id="bce38-193">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="bce38-194">Çağırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="bce38-194">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="bce38-195">Dizinler ve aralıklar hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="bce38-195">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bce38-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bce38-196">See also</span></span>

- [<span data-ttu-id="bce38-197">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="bce38-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bce38-198">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="bce38-198">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="bce38-199">?? (null birleşim işleci)</span><span class="sxs-lookup"><span data-stu-id="bce38-199">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="bce38-200">:: işleci</span><span class="sxs-lookup"><span data-stu-id="bce38-200">:: operator</span></span>](namespace-alias-qualifier.md)
