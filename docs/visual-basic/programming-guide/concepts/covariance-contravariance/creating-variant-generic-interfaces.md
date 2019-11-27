---
title: Değişken Genel Arabirimler Oluşturma
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 74362b9d9effab028bebb9e9ecf72ac0111366d3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347063"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="35aca-102">Değişken genel arabirimler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35aca-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="35aca-103">Arabirimlerdeki genel tür parametrelerini birlikte değişken veya değişken karşıtı olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35aca-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="35aca-104">*Kovaryans* , Arabirim yöntemlerinin genel tür parametreleri tarafından tanımlananla daha fazla türetilmiş dönüş türüne sahip olmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="35aca-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="35aca-105">*Değişken varyans* , Arabirim yöntemlerinin genel parametreler tarafından belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="35aca-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="35aca-106">Değişkenle birlikte değişken veya değişken karşıtı genel tür parametrelerine sahip genel bir arabirim *değişken*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="35aca-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="35aca-107">.NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="35aca-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="35aca-108">.NET Framework değişken arabirimlerinin listesi için bkz. [Genel Arabirimlerde Varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="35aca-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="35aca-109">VARIANT genel arabirimlerini bildirme</span><span class="sxs-lookup"><span data-stu-id="35aca-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="35aca-110">Genel tür parametreleri için `in` ve `out` anahtar sözcüklerini kullanarak VARIANT genel arabirimleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35aca-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35aca-111">Visual Basic `ByRef` parametreler Variant olamaz.</span><span class="sxs-lookup"><span data-stu-id="35aca-111">`ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="35aca-112">Değer türleri de varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="35aca-112">Value types also do not support variance.</span></span>

<span data-ttu-id="35aca-113">`out` anahtar sözcüğünü kullanarak genel tür parametresi ortak değişkeni bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35aca-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="35aca-114">Covaryant türü şu koşulları karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="35aca-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="35aca-115">Tür, yalnızca Arabirim yöntemlerinin dönüş türü olarak kullanılır ve Yöntem bağımsız değişkenlerinin türü olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="35aca-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="35aca-116">Bu, `R` türünün covaryant olarak bildirildiği aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="35aca-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    <span data-ttu-id="35aca-117">Bu kural için bir özel durum var.</span><span class="sxs-lookup"><span data-stu-id="35aca-117">There is one exception to this rule.</span></span> <span data-ttu-id="35aca-118">Bir yöntem parametresi olarak bir değişken karşıtı genel temsilciniz varsa, türü temsilci için genel bir tür parametresi olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35aca-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="35aca-119">Bu, aşağıdaki örnekte `R` türü tarafından gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="35aca-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="35aca-120">Daha fazla bilgi için bkz. [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="35aca-120">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- <span data-ttu-id="35aca-121">Tür, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="35aca-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="35aca-122">Bu, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="35aca-122">This is illustrated in the following code.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

<span data-ttu-id="35aca-123">`in` anahtar sözcüğünü kullanarak genel tür parametresi değişken karşıtı bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35aca-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="35aca-124">Değişken karşıtı türü, Arabirim yöntemlerinin dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35aca-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="35aca-125">Değişken karşıtı türü, genel kısıtlamalar için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35aca-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="35aca-126">Aşağıdaki kod, bir değişken karşıtı arabirimin nasıl bildirilemeyeceğini ve yöntemlerinden biri için genel bir kısıtlama nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35aca-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

<span data-ttu-id="35aca-127">Ayrıca, aşağıdaki kod örneğinde gösterildiği gibi farklı tür parametreleri için aynı arabirimdeki kovaryansı ve değişken varyansı desteklemek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="35aca-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

<span data-ttu-id="35aca-128">Visual Basic, temsilci türünü belirtmeden değişken arabirimlerde olayları bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="35aca-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="35aca-129">Ayrıca, bir değişken arabirimde iç içe sınıflar, numaralandırmalar veya yapılar bulunamaz, ancak iç içe arabirimler olabilir.</span><span class="sxs-lookup"><span data-stu-id="35aca-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="35aca-130">Bu, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="35aca-130">This is illustrated in the following code.</span></span>

```vb
Interface ICovariant(Of Out R)
    ' The following statement generates a compiler error.
    ' Event SampleEvent()
    ' The following statement specifies the delegate type and
    ' does not generate an error.
    Event AnotherEvent As EventHandler

    ' The following statements generate compiler errors,
    ' because a variant interface cannot have
    ' nested enums, classes, or structures.

    'Enum SampleEnum : test : End Enum
    'Class SampleClass : End Class
    'Structure SampleStructure : Dim value As Integer : End Structure

    ' Variant interfaces can have nested interfaces.
    Interface INested : End Interface
End Interface
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="35aca-131">VARIANT genel arabirimlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="35aca-131">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="35aca-132">Sabit arabirimler için kullanılan söz dizimini kullanarak sınıflarda VARIANT genel arabirimler uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35aca-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="35aca-133">Aşağıdaki kod örneği, bir genel sınıfta birlikte değişken arabiriminin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35aca-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```vb
Interface ICovariant(Of Out R)
    Function GetSomething() As R
End Interface

Class SampleImplementation(Of R)
    Implements ICovariant(Of R)
    Public Function GetSomething() As R _
    Implements ICovariant(Of R).GetSomething
        ' Some code.
    End Function
End Class
```

<span data-ttu-id="35aca-134">Varyant arabirimlerini uygulayan sınıflar sabit.</span><span class="sxs-lookup"><span data-stu-id="35aca-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="35aca-135">Örneğin, aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="35aca-135">For example, consider the following code.</span></span>

```vb
 The interface is covariant.
Dim ibutton As ICovariant(Of Button) =
    New SampleImplementation(Of Button)
Dim iobj As ICovariant(Of Object) = ibutton

' The class is invariant.
Dim button As SampleImplementation(Of Button) =
    New SampleImplementation(Of Button)
' The following statement generates a compiler error
' because classes are invariant.
' Dim obj As SampleImplementation(Of Object) = button
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="35aca-136">VARIANT genel arabirimlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="35aca-136">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="35aca-137">Bir varyant genel arabirimini genişlettiğinizde, türetilmiş arabirimin varyansı destekleyip desteklemediğini açıkça belirtmek için `in` ve `out` anahtar sözcüklerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="35aca-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="35aca-138">Derleyici, genişletilmekte olan arabirimden varyansı çıkarmıyor.</span><span class="sxs-lookup"><span data-stu-id="35aca-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="35aca-139">Örneğin, aşağıdaki arabirimleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="35aca-139">For example, consider the following interfaces.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T)
End Interface

Interface IExtCovariant(Of Out T)
    Inherits ICovariant(Of T)
End Interface
```

<span data-ttu-id="35aca-140">`Invariant(Of T)` arabiriminde, `T` genel tür parametresi değişmez, ancak her iki arabirim de aynı arabirimi genişletse de, tür parametresi birlikte değişken `IExtCovariant (Of Out T)`.</span><span class="sxs-lookup"><span data-stu-id="35aca-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="35aca-141">Aynı kural, değişken karşıtı genel tür parametrelerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="35aca-141">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="35aca-142">Hem genel tür parametresi `T` birlikte değişken olduğu arabirimi hem de genişletme arabiriminde `T` genel tür parametresi sabiti olan arabirimi genişleten bir arabirim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35aca-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="35aca-143">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="35aca-143">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

<span data-ttu-id="35aca-144">Ancak, bir genel tür parametresi `T` bir arabirimde birlikte değişken olarak bildirilirse, genişletme arabiriminde bu değişken karşıtı olarak bildiremezsiniz veya tam tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="35aca-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="35aca-145">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="35aca-145">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="35aca-146">Belirsizlik önleme</span><span class="sxs-lookup"><span data-stu-id="35aca-146">Avoiding Ambiguity</span></span>

<span data-ttu-id="35aca-147">VARIANT genel arabirimleri uyguladığınızda, fark bazen belirsizliğe neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="35aca-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="35aca-148">Bunun kaçınılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="35aca-148">This should be avoided.</span></span>

<span data-ttu-id="35aca-149">Örneğin, tek bir sınıfta farklı genel tür parametreleriyle aynı Varyant genel arabirimini açıkça uygularsanız, belirsizlik oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="35aca-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="35aca-150">Derleyici bu durumda bir hata oluşturmaz, ancak çalışma zamanında hangi arabirim uygulamasının seçilme belirtilecektir.</span><span class="sxs-lookup"><span data-stu-id="35aca-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="35aca-151">Bu, kodunuzda hafif hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="35aca-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="35aca-152">Aşağıdaki kod örneğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="35aca-152">Consider the following code example.</span></span>

> [!NOTE]
> <span data-ttu-id="35aca-153">`Option Strict Off`, belirsiz bir arabirim uygulaması olduğunda Visual Basic bir derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="35aca-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="35aca-154">`Option Strict On`, Visual Basic bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="35aca-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>

```vb
' Simple class hierarchy.
Class Animal
End Class

Class Cat
    Inherits Animal
End Class

Class Dog
    Inherits Animal
End Class

' This class introduces ambiguity
' because IEnumerable(Of Out T) is covariant.
Class Pets
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)

    Public Function GetEnumerator() As IEnumerator(Of Cat) _
        Implements IEnumerable(Of Cat).GetEnumerator
        Console.WriteLine("Cat")
        ' Some code.
    End Function

    Public Function GetEnumerator1() As IEnumerator(Of Dog) _
        Implements IEnumerable(Of Dog).GetEnumerator
        Console.WriteLine("Dog")
        ' Some code.
    End Function

    Public Function GetEnumerator2() As IEnumerator _
        Implements IEnumerable.GetEnumerator
        ' Some code.
    End Function
End Class

Sub Main()
    Dim pets As IEnumerable(Of Animal) = New Pets()
    pets.GetEnumerator()
End Sub
```

<span data-ttu-id="35aca-155">Bu örnekte, `pets.GetEnumerator` yönteminin `Cat` ve `Dog`arasında nasıl seçtiği belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="35aca-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="35aca-156">Bu, kodunuzda sorun oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="35aca-156">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="35aca-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35aca-157">See also</span></span>

- [<span data-ttu-id="35aca-158">Genel Arabirimlerde Varyans (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35aca-158">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="35aca-159">Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35aca-159">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
