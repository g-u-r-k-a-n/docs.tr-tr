---
title: Temsilcilerde Varyans
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 86ea9f3f744381bcff71a88e9d88485cafa4a568
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375622"
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="72867-102">Temsilcilerde varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72867-102">Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="72867-103">.NET Framework 3,5, C# ve Visual Basic tüm Temsilcilerde temsilci türleriyle eşleşen yöntem imzaları için varyans desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="72867-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="72867-104">Bu, yalnızca eşleşen imzalara sahip yöntemlerin değil, aynı zamanda daha fazla türetilmiş tür (Kovaryans) döndüren veya temsilci türü tarafından belirtilenden daha az türetilmiş tür (değişken varyans) içeren parametreleri kabul eden yöntemler için atama yaptığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="72867-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="72867-105">Bu hem genel hem de genel olmayan temsilcileri içerir.</span><span class="sxs-lookup"><span data-stu-id="72867-105">This includes both generic and non-generic delegates.</span></span>

<span data-ttu-id="72867-106">Örneğin, iki sınıfı ve iki temsilciyi olan aşağıdaki kodu düşünün: genel ve genel olmayan.</span><span class="sxs-lookup"><span data-stu-id="72867-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

<span data-ttu-id="72867-107">`SampleDelegate`Veya türlerinin temsilcilerini oluşturduğunuzda `SampleDelegate(Of A, R)` , aşağıdaki yöntemlerden herhangi birini bu temsilcilere atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72867-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>

```vb
' Matching signature.
Public Shared Function ASecondRFirst(
    ByVal second As Second) As First
    Return New First()
End Function

' The return type is more derived.
Public Shared Function ASecondRSecond(
    ByVal second As Second) As Second
    Return New Second()
End Function

' The argument type is less derived.
Public Shared Function AFirstRFirst(
    ByVal first As First) As First
    Return New First()
End Function

' The return type is more derived
' and the argument type is less derived.
Public Shared Function AFirstRSecond(
    ByVal first As First) As Second
    Return New Second()
End Function
```

<span data-ttu-id="72867-108">Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasındaki örtük dönüştürmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="72867-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>

```vb
' Assigning a method with a matching signature
' to a non-generic delegate. No conversion is necessary.
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a non-generic delegate.
' The implicit conversion is used.
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond

' Assigning a method with a matching signature to a generic delegate.
' No conversion is necessary.
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a generic delegate.
' The implicit conversion is used.
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond
```

<span data-ttu-id="72867-109">Daha fazla örnek için bkz. [Temsilcilerde varyans kullanma (Visual Basic)](using-variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="72867-109">For more examples, see [Using Variance in Delegates (Visual Basic)](using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span></span>

## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="72867-110">Genel tür parametrelerindeki varyans</span><span class="sxs-lookup"><span data-stu-id="72867-110">Variance in Generic Type Parameters</span></span>

<span data-ttu-id="72867-111">.NET Framework 4 ' te ve daha sonra temsilciler arasında örtük dönüştürmeyi etkinleştirebilirsiniz. böylece türler, genel tür parametreleri tarafından belirtilen farklı türlere sahip olan genel temsilcilerin birbirini fark eden her bir öğeden devralınabileceği her diğerine atanabilmesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="72867-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>

<span data-ttu-id="72867-112">Örtük dönüştürmeyi etkinleştirmek için, `in` veya anahtar sözcüğünü kullanarak bir temsilcinin genel parametrelerini birlikte değişken veya değişken karşıtı olarak açıkça bildirmeniz gerekir `out` .</span><span class="sxs-lookup"><span data-stu-id="72867-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>

<span data-ttu-id="72867-113">Aşağıdaki kod örneği, birlikte değişken genel tür parametresine sahip olan bir temsilciyi nasıl oluşturabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="72867-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>

```vb
' Type T is declared covariant by using the out keyword.
Public Delegate Function SampleGenericDelegate(Of Out T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "
    ' You can assign delegates to each other,
    ' because the type T is declared covariant.
    Dim dObject As SampleGenericDelegate(Of Object) = dString
End Sub
```

<span data-ttu-id="72867-114">Yöntem imzalarını temsilci türleriyle eşleştirmek için yalnızca varyans desteğini kullanırsanız ve `in` ve `out` anahtar sözcüklerini kullanmıyorsanız, bazen aynı lambda ifadeleri veya yöntemlerine sahip temsilciler örnekleyebilirsiniz, ancak bir temsilciyi başka bir temsilciye atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="72867-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>

<span data-ttu-id="72867-115">Aşağıdaki kod örneğinde, `SampleGenericDelegate(Of String)` açıkça öğesine dönüştürülemez `SampleGenericDelegate(Of Object)` , ancak `String` devralır `Object` .</span><span class="sxs-lookup"><span data-stu-id="72867-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="72867-116">Genel parametreyi anahtar sözcüğüyle işaretleyerek bu sorunu çözebilirsiniz `T` `out` .</span><span class="sxs-lookup"><span data-stu-id="72867-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>

```vb
Public Delegate Function SampleGenericDelegate(Of T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "

    ' You can assign the dObject delegate
    ' to the same lambda expression as dString delegate
    ' because of the variance support for
    ' matching method signatures with delegate types.
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "

    ' The following statement generates a compiler error
    ' because the generic type T is not marked as covariant.
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString

End Sub
```

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="72867-117">.NET Framework değişken tür parametrelerine sahip genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="72867-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>

<span data-ttu-id="72867-118">.NET Framework 4, çeşitli genel temsilcilerde genel tür parametrelerine yönelik varyans desteği getirmiştir:</span><span class="sxs-lookup"><span data-stu-id="72867-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>

- <span data-ttu-id="72867-119">`Action`ad alanından temsilciler, <xref:System> Örneğin <xref:System.Action%601> ve<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="72867-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>

- <span data-ttu-id="72867-120">`Func`ad alanından temsilciler, <xref:System> Örneğin <xref:System.Func%601> ve<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="72867-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>

- <span data-ttu-id="72867-121"><xref:System.Predicate%601>Temsilci</span><span class="sxs-lookup"><span data-stu-id="72867-121">The <xref:System.Predicate%601> delegate</span></span>

- <span data-ttu-id="72867-122"><xref:System.Comparison%601>Temsilci</span><span class="sxs-lookup"><span data-stu-id="72867-122">The <xref:System.Comparison%601> delegate</span></span>

- <span data-ttu-id="72867-123"><xref:System.Converter%602>Temsilci</span><span class="sxs-lookup"><span data-stu-id="72867-123">The <xref:System.Converter%602> delegate</span></span>

<span data-ttu-id="72867-124">Daha fazla bilgi ve örnek için bkz. [Func ve eylem genel temsilcileri Için varyans kullanma (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="72867-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span></span>

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="72867-125">Genel Temsilcilerde değişken tür parametreleri bildirme</span><span class="sxs-lookup"><span data-stu-id="72867-125">Declaring Variant Type Parameters in Generic Delegates</span></span>

<span data-ttu-id="72867-126">Genel bir temsilcinin birlikte değişken veya değişken karşıtı genel tür parametreleri varsa, bu, *VARIANT genel temsilcisi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="72867-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>

<span data-ttu-id="72867-127">Anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi ortak değişkeni bildirebilirsiniz `out` .</span><span class="sxs-lookup"><span data-stu-id="72867-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="72867-128">Covaryant türü, yöntem bağımsız değişkenlerinin türü olarak değil, yalnızca bir yöntem dönüş türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72867-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="72867-129">Aşağıdaki kod örneği, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72867-129">The following code example shows how to declare a covariant generic delegate.</span></span>

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

<span data-ttu-id="72867-130">Anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi değişken değişkeni bildirebilirsiniz `in` .</span><span class="sxs-lookup"><span data-stu-id="72867-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="72867-131">Değişken karşıtı türü, yöntem dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72867-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="72867-132">Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72867-132">The following code example shows how to declare a contravariant generic delegate.</span></span>

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> <span data-ttu-id="72867-133">`ByRef`Visual Basic parametreler değişken olarak işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="72867-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>

<span data-ttu-id="72867-134">Aynı temsilci, ancak farklı tür parametreleri için hem varyansı hem de kovaryansı desteklemek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="72867-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="72867-135">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="72867-135">This is shown in the following example.</span></span>

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="72867-136">VARIANT genel temsilcileri örnekleme ve çağırma</span><span class="sxs-lookup"><span data-stu-id="72867-136">Instantiating and Invoking Variant Generic Delegates</span></span>

<span data-ttu-id="72867-137">Sabit temsilcileri örneklediğinizde ve çağırdığınızda değişken temsilcileri örnek oluşturabilir ve çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72867-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="72867-138">Aşağıdaki örnekte, temsilci bir lambda ifadesi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="72867-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="72867-139">Değişken genel temsilcileri birleştirme</span><span class="sxs-lookup"><span data-stu-id="72867-139">Combining Variant Generic Delegates</span></span>

<span data-ttu-id="72867-140">Değişken temsilcileri birleştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="72867-140">You should not combine variant delegates.</span></span> <span data-ttu-id="72867-141"><xref:System.Delegate.Combine%2A>Yöntem, değişken temsilci dönüştürmeyi desteklemez ve temsilcilerin tamamen aynı türde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="72867-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="72867-142">Bu, <xref:System.Delegate.Combine%2A> `+` Aşağıdaki kod örneğinde gösterildiği gibi, (c# ve Visual Basic) ya da işlecini kullanarak (c# ' de), temsilcileri birleştirdiğinizde bir çalışma zamanı özel durumuna yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="72867-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="72867-143">Değer ve başvuru türleri için genel tür parametrelerinin varyansı</span><span class="sxs-lookup"><span data-stu-id="72867-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>

<span data-ttu-id="72867-144">Genel tür parametrelerinin varyansı yalnızca başvuru türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="72867-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="72867-145">Örneğin, `DVariant(Of Int)` `DVariant(Of Object)` tamsayı bir değer türü olduğundan, örtülü olarak veya `DVariant(Of Long)` türüne dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="72867-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>

<span data-ttu-id="72867-146">Aşağıdaki örnek, genel tür parametrelerinin farkının değer türleri için desteklenmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72867-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>

```vb
' The type T is covariant.
Public Delegate Function DVariant(Of Out T)() As T
' The type T is invariant.
Public Delegate Function DInvariant(Of T)() As T
Sub Test()
    Dim i As Integer = 0
    Dim dInt As DInvariant(Of Integer) = Function() i
    Dim dVariantInt As DVariant(Of Integer) = Function() i

    ' All of the following statements generate a compiler error
    ' because type variance in generic parameters is not supported
    ' for value types, even if generic type parameters are declared variant.
    ' Dim dObject As DInvariant(Of Object) = dInt
    ' Dim dLong As DInvariant(Of Long) = dInt
    ' Dim dVariantObject As DInvariant(Of Object) = dInt
    ' Dim dVariantLong As DInvariant(Of Long) = dInt
End Sub
```

## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="72867-147">Visual Basic için gevşek temsilci dönüştürme</span><span class="sxs-lookup"><span data-stu-id="72867-147">Relaxed Delegate Conversion in Visual Basic</span></span>

<span data-ttu-id="72867-148">Gevşek temsilci dönüştürme, temsilci türleriyle eşleşen Yöntem imzalarında daha fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="72867-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="72867-149">Örneğin, bir temsilciye bir yöntem atarken parametre belirtimlerini ve işlev dönüş değerlerini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="72867-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="72867-150">Daha fazla bilgi için bkz. [gevşek temsilci dönüştürme](../../language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="72867-150">For more information, see [Relaxed Delegate Conversion](../../language-features/delegates/relaxed-delegate-conversion.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="72867-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72867-151">See also</span></span>

- [<span data-ttu-id="72867-152">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="72867-152">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="72867-153">Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72867-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)
