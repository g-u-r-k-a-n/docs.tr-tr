---
title: ref anahtar sözcüğü C# başvurusu
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 25c74317ce9033ef10735ee0087f275632b6bd17
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715180"
---
# <a name="ref-c-reference"></a><span data-ttu-id="7d133-102">ref (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7d133-102">ref (C# Reference)</span></span>

<span data-ttu-id="7d133-103">`ref` anahtar sözcüğü, başvuruya göre geçirilen bir değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d133-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="7d133-104">Dört farklı bağlamda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="7d133-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="7d133-105">Bir yöntem imzasında ve bir yöntem çağrısında, bir bağımsız değişkeni başvuruya göre bir yönteme geçirmek için.</span><span class="sxs-lookup"><span data-stu-id="7d133-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="7d133-106">Daha fazla bilgi için bkz. [bir bağımsız değişkeni başvuruya göre geçirme](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="7d133-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="7d133-107">Bir yöntem imzasında, çağıran öğesine başvuruya göre bir değer döndürün.</span><span class="sxs-lookup"><span data-stu-id="7d133-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="7d133-108">Daha fazla bilgi için bkz. [Başvuru dönüş değerleri](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="7d133-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="7d133-109">Bir üye gövdesinde, bir başvuru dönüş değerinin, çağıranın değiştirme amaçladığı bir başvuru olarak yerel olarak depolandığını belirtmek için, yerel bir değişken başvuruya göre başka bir değere erişir.</span><span class="sxs-lookup"><span data-stu-id="7d133-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="7d133-110">Daha fazla bilgi için bkz. [ref Yereller](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="7d133-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="7d133-111">Bir `struct` bildiriminde `ref struct` veya `readonly ref struct`bildirme.</span><span class="sxs-lookup"><span data-stu-id="7d133-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="7d133-112">Daha fazla bilgi için bkz. [ref struct Types](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="7d133-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="7d133-113">Bir bağımsız değişkeni başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="7d133-113">Passing an argument by reference</span></span>

<span data-ttu-id="7d133-114">Yöntemin parametre listesinde kullanıldığında, `ref` anahtar sözcüğü bir bağımsız değişkenin değere göre değil başvuruya göre geçtiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d133-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="7d133-115">`ref` anahtar sözcüğü, bir değişken olması gereken bağımsız değişken için biçimsel parametreye bir diğer ad sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d133-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="7d133-116">Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır.</span><span class="sxs-lookup"><span data-stu-id="7d133-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="7d133-117">Örneğin, çağıran bir yerel değişken ifadesi veya bir dizi öğesi erişim ifadesi geçirirse ve çağrılan yöntem Ref parametresinin başvurduğu nesnenin yerini alırsa, bu durumda çağıranın yerel değişkeni veya Array öğesi artık yeni nesnesine başvurur Yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d133-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="7d133-118">Başvuru türü kavramıyla başvuruya göre geçirme kavramını karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="7d133-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="7d133-119">İki kavram aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="7d133-119">The two concepts are not the same.</span></span> <span data-ttu-id="7d133-120">Bir yöntem parametresi, bir değer türü veya bir başvuru türü olmasına bakılmaksızın `ref` değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7d133-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="7d133-121">Başvuru ile geçirildiğinde bir değer türünün kutulenmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7d133-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="7d133-122">Bir `ref` parametresi kullanmak için, aşağıdaki örnekte gösterildiği gibi yöntem tanımı ve çağırma yöntemi açık olarak `ref` anahtar sözcüğünü kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d133-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="7d133-123">Bir `ref` veya `in` parametresine geçirilen bir bağımsız değişken geçirilmeden önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d133-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="7d133-124">Bu, bağımsız değişkenlerin geçirilmeden önce açıkça başlatılmış olması gereken [Out](out-parameter-modifier.md) parametrelerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="7d133-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="7d133-125">Bir sınıfın üyelerinin yalnızca `ref`, `in`veya `out`farklı imzaları olamaz.</span><span class="sxs-lookup"><span data-stu-id="7d133-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="7d133-126">Bir türün iki üyesi arasındaki tek fark, bir `ref` parametresi ve diğeri ise `out`veya `in` parametresine sahipse bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="7d133-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="7d133-127">Aşağıdaki kod, örneğin derlenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7d133-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="7d133-128">Ancak, bir yöntemin `ref`, `in`veya `out` parametresine sahip olduğu ve diğeri bir değer parametresi varsa, aşağıdaki örnekte gösterildiği gibi yöntemler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7d133-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="7d133-129">`in`, `ref`ve `out` gibi imza eşleştirmesi gerektiren diğer durumlarda, imzanın bir parçasıdır ve birbirleriyle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="7d133-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="7d133-130">Özellikler değişken değildir.</span><span class="sxs-lookup"><span data-stu-id="7d133-130">Properties are not variables.</span></span> <span data-ttu-id="7d133-131">Bunlar yöntemlerdir ve `ref` parametrelere geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="7d133-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="7d133-132">Aşağıdaki tür yöntemler için `ref`, `in`ve `out` anahtar sözcüklerini kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="7d133-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="7d133-133">Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.</span><span class="sxs-lookup"><span data-stu-id="7d133-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="7d133-134">Bir [yield return](yield.md) veya `yield break` ifadesini içeren Yineleyici yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="7d133-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="7d133-135">Bir bağımsız değişkeni başvuruya göre geçirme: bir örnek</span><span class="sxs-lookup"><span data-stu-id="7d133-135">Passing an argument by reference: An example</span></span>

<span data-ttu-id="7d133-136">Önceki örneklerde değer türleri başvuruya göre geçer.</span><span class="sxs-lookup"><span data-stu-id="7d133-136">The previous examples pass value types by reference.</span></span> <span data-ttu-id="7d133-137">Başvuru türlerini başvuruya göre geçirmek için `ref` anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d133-137">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="7d133-138">Başvuru türü başvuruya göre geçirilme yöntemi, çağrılan yöntemin, başvuru parametresinin çağırıcının başvurduğu nesneyi değiştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d133-138">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="7d133-139">Nesnenin depolama konumu, başvuru parametresi değeri olarak yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7d133-139">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="7d133-140">Parametresinin depolama konumundaki değeri değiştirirseniz (yeni bir nesneyi işaret etmek için), çağıranın başvurduğu depolama konumunu da değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d133-140">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="7d133-141">Aşağıdaki örnek, bir başvuru türünün örneğini `ref` parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="7d133-141">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="7d133-142">Başvuru türlerini değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz. [başvuru türü parametrelerini geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7d133-142">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="7d133-143">Başvuru dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="7d133-143">Reference return values</span></span>

<span data-ttu-id="7d133-144">Başvuru dönüş değerleri (veya ref dönüşler), bir yöntemin çağırana başvuruya göre döndürdüğü değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="7d133-144">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="7d133-145">Diğer bir deyişle, çağıran bir yöntem tarafından döndürülen değeri değiştirebilir ve bu değişiklik yöntemi içeren nesnenin durumunda yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="7d133-145">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="7d133-146">Başvuru dönüş değeri `ref` anahtar sözcüğü kullanılarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="7d133-146">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="7d133-147">Metot imzasında.</span><span class="sxs-lookup"><span data-stu-id="7d133-147">In the method signature.</span></span> <span data-ttu-id="7d133-148">Örneğin, aşağıdaki yöntem imzası `GetCurrentPrice` yönteminin başvuruya göre <xref:System.Decimal> değer döndürdüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d133-148">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="7d133-149">`return` belirteci ve yöntemi içindeki bir `return` ifadesinde döndürülen değişken arasında.</span><span class="sxs-lookup"><span data-stu-id="7d133-149">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="7d133-150">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7d133-150">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="7d133-151">Çağıranın nesnenin durumunu değiştirmesi için, başvuru dönüş değeri açıkça bir [ref yerel](#ref-locals)olarak tanımlanmış bir değişkene depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d133-151">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="7d133-152">Çağrılan yöntem aynı zamanda değeri başvuruya göre döndürmek için `ref readonly` olarak döndürülen değeri bildirebilir ve çağıran kodun döndürülen değeri değiştiremeyeceğini zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d133-152">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="7d133-153">Çağırma yöntemi, değeri yerel bir [ref salt okunur](#ref-readonly-locals) değişkeninde depolayarak döndürülen değerli değeri kopyalamayı önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7d133-153">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="7d133-154">Bir örnek için, bkz. [bir başvuru dönüşleri ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="7d133-154">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="7d133-155">Başvuru yerelleri</span><span class="sxs-lookup"><span data-stu-id="7d133-155">Ref locals</span></span>

<span data-ttu-id="7d133-156">`return ref`kullanılarak döndürülen değerlere başvurmak için bir ref yerel değişkeni kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d133-156">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="7d133-157">Bir ref yerel değişkeni, ref olmayan bir dönüş değeri olarak başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="7d133-157">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="7d133-158">Diğer bir deyişle, başlatmanın sağ tarafı bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d133-158">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="7d133-159">Ref Local değerindeki tüm değişiklikler, metodu, yöntemi başvuruya göre döndürülen nesnenin durumuna yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="7d133-159">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="7d133-160">Değişken bildiriminden önce `ref` anahtar sözcüğünü kullanarak, ve değeri başvuruya göre döndüren yönteme çağrıdan hemen önce, bir ref yerel tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7d133-160">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="7d133-161">Örneğin, aşağıdaki ifade `GetEstimatedValue`adlı bir yöntem tarafından döndürülen bir ref yerel değeri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="7d133-161">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="7d133-162">Başvuruya göre bir değere aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d133-162">You can access a value by reference in the same way.</span></span> <span data-ttu-id="7d133-163">Bazı durumlarda, başvuruya göre değere erişmek, potansiyel olarak pahalı bir kopyalama işlemini önleyerek performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="7d133-163">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="7d133-164">Örneğin, aşağıdaki ifade bir değere başvurmak için kullanılan bir başvuru yerel değerini nasıl tanımlayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d133-164">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="7d133-165">Her iki örnekte de `ref` anahtar sözcüğünün her iki yerde de kullanılması gerektiğini veya derleyicinin hata CS8172, "bir değere sahip bir başvuruya göre değişkeni başlatamıyor" şeklinde olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7d133-165">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="7d133-166">7,3 ile C# başlayarak, `foreach` deyimin yineleme değişkeni ref yerel veya ref ReadOnly yerel değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d133-166">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="7d133-167">Daha fazla bilgi için [foreach ifadesi](foreach-in.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="7d133-167">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="7d133-168">Ref ReadOnly Yereller</span><span class="sxs-lookup"><span data-stu-id="7d133-168">Ref readonly locals</span></span>

<span data-ttu-id="7d133-169">Ref salt okunur yerel, yöntemi veya özelliği tarafından döndürülen değerlere, imzasında `ref readonly` olan ve `return ref`kullanan değerleri ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d133-169">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="7d133-170">`ref readonly` değişkeni, bir `ref` yerel değişkeninin özelliklerini `readonly` değişkeniyle birleştirir: Bu, atandığı depolamanın diğer adıdır ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="7d133-170">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span> 

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="7d133-171">Bir ref, ve ref Yereller örneği döndürür</span><span class="sxs-lookup"><span data-stu-id="7d133-171">A ref returns and ref locals example</span></span>

<span data-ttu-id="7d133-172">Aşağıdaki örnek, `Title` ve `Author`iki <xref:System.String> alanı olan bir `Book` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d133-172">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="7d133-173">Ayrıca, özel bir `Book` nesneleri dizisi içeren bir `BookCollection` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d133-173">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="7d133-174">Tek kitap nesneleri, `GetBookByTitle` metodu çağırarak başvuruya göre döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7d133-174">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="7d133-175">Çağıran `GetBookByTitle` yöntemi tarafından döndürülen değeri bir ref yerel olarak depoladığında, çağıranın dönüş değeri için yaptığı değişiklikler, aşağıdaki örnekte gösterildiği gibi `BookCollection` nesnesine yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="7d133-175">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="7d133-176">Ref struct türleri</span><span class="sxs-lookup"><span data-stu-id="7d133-176">Ref struct types</span></span>

<span data-ttu-id="7d133-177">`struct` bildirimine `ref` değiştiricisini eklemek, bu türdeki örneklerin yığın olarak ayrılmış olması gerektiğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d133-177">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="7d133-178">Diğer bir deyişle, bu türlerin örnekleri başka bir sınıfın üyesi olarak yığın üzerinde hiçbir şekilde oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="7d133-178">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="7d133-179">Bu özellik için birincil mosyon <xref:System.Span%601> ve ilgili yapılarıdır.</span><span class="sxs-lookup"><span data-stu-id="7d133-179">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="7d133-180">Bir `ref struct` türünü yığın olarak ayrılmış bir değişken olarak tutmanın amacı, derleyicinin tüm `ref struct` türleri için uyguladığı çeşitli kuralları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="7d133-180">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="7d133-181">`ref struct`.</span><span class="sxs-lookup"><span data-stu-id="7d133-181">You can't box a `ref struct`.</span></span> <span data-ttu-id="7d133-182">`ref struct` türü `object`, `dynamic`veya herhangi bir arabirim türü değişkenine atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7d133-182">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="7d133-183">`ref struct` türleri arabirimler uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="7d133-183">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="7d133-184">Bir `ref struct` bir sınıfın alan üyesi veya normal bir yapı olarak bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d133-184">You can't declare a `ref struct` as a field member of a class or a normal struct.</span></span> <span data-ttu-id="7d133-185">Bu, bir derleyici tarafından oluşturulan bir yedekleme alanı oluşturan otomatik uygulanan bir özellik bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="7d133-185">This includes declaring an auto-implemented property, which creates a compiler generated backing field.</span></span> 
- <span data-ttu-id="7d133-186">Zaman uyumsuz yöntemlerde `ref struct` türler olan yerel değişkenler bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d133-186">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="7d133-187"><xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> veya `Task`benzeri türler döndüren zaman uyumlu yöntemlerde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d133-187">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="7d133-188">Yineleyiciler içinde `ref struct` yerel değişken bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d133-188">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="7d133-189">Lambda ifadelerinde veya yerel işlevlerde `ref struct` değişkenlerini yakalayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7d133-189">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="7d133-190">Bu kısıtlamalar, yanlışlıkla `ref struct` yönetilen yığına yükseltebilen bir şekilde kullanmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d133-190">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="7d133-191">Bir yapıyı `readonly ref`olarak bildirmek için değiştiriciler birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d133-191">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="7d133-192">`readonly ref struct`, `ref struct` ve `readonly struct` bildirimlerinin avantajlarını ve kısıtlamalarını birleştirir.</span><span class="sxs-lookup"><span data-stu-id="7d133-192">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7d133-193">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7d133-193">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7d133-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d133-194">See also</span></span>

- [<span data-ttu-id="7d133-195">Güvenli verimli kod yazma</span><span class="sxs-lookup"><span data-stu-id="7d133-195">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="7d133-196">Ref dönüşler ve ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="7d133-196">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="7d133-197">Koşullu başvuru ifadesi</span><span class="sxs-lookup"><span data-stu-id="7d133-197">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="7d133-198">ref atama işleci</span><span class="sxs-lookup"><span data-stu-id="7d133-198">ref assignment operator</span></span>](../operators/assignment-operator.md#ref-assignment-operator)
- [<span data-ttu-id="7d133-199">Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="7d133-199">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="7d133-200">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="7d133-200">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="7d133-201">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="7d133-201">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7d133-202">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7d133-202">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7d133-203">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7d133-203">C# Keywords</span></span>](index.md)
