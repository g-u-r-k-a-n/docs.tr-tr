---
description: ref anahtar sözcüğü-C# başvurusu
title: ref anahtar sözcüğü-C# başvurusu
ms.date: 03/29/2021
f1_keywords:
- ref_CSharpKeyword
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 3392e560eaf0bac39cf4e9707574fd2bb3d96057
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079446"
---
# <a name="ref-c-reference"></a><span data-ttu-id="ccc2b-103">ref (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ccc2b-103">ref (C# Reference)</span></span>

<span data-ttu-id="ccc2b-104">`ref`Anahtar sözcüğü, bir değerin başvuruya göre geçtiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-104">The `ref` keyword indicates that a value is passed by reference.</span></span> <span data-ttu-id="ccc2b-105">Dört farklı bağlamda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="ccc2b-105">It is used in four different contexts:</span></span>

- <span data-ttu-id="ccc2b-106">Bir yöntem imzasında ve bir yöntem çağrısında, bir bağımsız değişkeni başvuruya göre bir yönteme geçirmek için.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-106">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="ccc2b-107">Daha fazla bilgi için bkz. [bir bağımsız değişkeni başvuruya göre geçirme](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="ccc2b-107">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="ccc2b-108">Bir yöntem imzasında, çağıran öğesine başvuruya göre bir değer döndürün.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-108">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="ccc2b-109">Daha fazla bilgi için bkz. [Başvuru dönüş değerleri](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="ccc2b-109">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="ccc2b-110">Bir üye gövdesinde, bir başvuru dönüş değerinin, çağıranın değiştirme amaçladığı bir başvuru olarak yerel olarak depolandığını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-110">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="ccc2b-111">Ya da yerel bir değişkenin başvuruya göre başka bir değere eriştiği anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-111">Or to indicate that a local variable accesses another value by reference.</span></span> <span data-ttu-id="ccc2b-112">Daha fazla bilgi için bkz. [ref Yereller](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="ccc2b-112">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="ccc2b-113">Bir `struct` bildiriminde bir veya bir bildirmek için `ref struct` `readonly ref struct` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-113">In a `struct` declaration, to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="ccc2b-114">Daha fazla bilgi için [yapı türleri](../builtin-types/struct.md) makalesinin [ `ref` struct](../builtin-types/struct.md#ref-struct) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-114">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="ccc2b-115">Bir bağımsız değişkeni başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="ccc2b-115">Passing an argument by reference</span></span>

<span data-ttu-id="ccc2b-116">Bir yöntemin parametre listesinde kullanıldığında, `ref` anahtar sözcüğü bir bağımsız değişkenin değere göre değil başvuruya göre geçtiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-116">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="ccc2b-117">`ref`Anahtar sözcüğü, bir değişken olması gereken bağımsız değişken için biçimsel parametreye bir diğer ad getirir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-117">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="ccc2b-118">Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-118">In other words, any operation on the parameter is made on the argument.</span></span>

<span data-ttu-id="ccc2b-119">Örneğin, çağıranın yerel bir değişken ifadesi veya dizi öğesi erişim ifadesi geçirdiğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-119">For example, suppose the caller passes a local variable expression or an array element access expression.</span></span> <span data-ttu-id="ccc2b-120">Çağrılan yöntem daha sonra ref parametresinin başvurduğu nesnenin yerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-120">The called method can then replace the object to which the ref parameter refers.</span></span> <span data-ttu-id="ccc2b-121">Bu durumda, çağıran yerel değişkeni veya dizi öğesi, yöntemi döndürüldüğünde yeni nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-121">In that case, the caller's local variable or the array element refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="ccc2b-122">Başvuru türü kavramıyla başvuruya göre geçirme kavramını karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-122">Don't confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="ccc2b-123">İki kavram aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-123">The two concepts are not the same.</span></span> <span data-ttu-id="ccc2b-124">Bir yöntem parametresi `ref` , bir değer türü veya bir başvuru türü olmasına bakılmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-124">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="ccc2b-125">Başvuru ile geçirildiğinde bir değer türünün kutulenmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-125">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="ccc2b-126">Bir parametre kullanmak için `ref` , `ref` Aşağıdaki örnekte gösterildiği gibi yöntem tanımı ve çağırma yöntemi anahtar sözcüğünü açıkça kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-126">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span> <span data-ttu-id="ccc2b-127">(Çağırma yöntemi `ref` BIR COM çağrısı yapılırken atlayabilir.)</span><span class="sxs-lookup"><span data-stu-id="ccc2b-127">(Except that the calling method can omit `ref` when making a COM call.)</span></span>

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="ccc2b-128">Bir veya parametresine geçirilen bir bağımsız değişken `ref` `in` geçirilmeden önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-128">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="ccc2b-129">Bu gereksinim, bağımsız değişkenlerin geçirilmeden önce açıkça başlatılması gereken [Out](out-parameter-modifier.md) parametrelerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-129">This requirement differs from [out](out-parameter-modifier.md) parameters, whose arguments don't have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="ccc2b-130">Bir sınıfın üyelerinin yalnızca `ref` ,, veya ile farklı imzaları olamaz `in` `out` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-130">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="ccc2b-131">Bir türün iki üyesi arasındaki tek fark, bir `ref` parametre içeriyorsa ve diğeri `out` veya parametresi varsa bir derleyici hatası oluşur `in` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-131">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="ccc2b-132">Aşağıdaki kod, örneğin derlenmiyor.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-132">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="ccc2b-133">Ancak, bir yöntem bir `ref` , `in` veya `out` parametresi olduğunda ve diğeri, aşağıdaki örnekte gösterildiği gibi değere göre geçirilen bir parametreye sahip olduğunda Yöntemler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-133">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a parameter that is passed by value, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="ccc2b-134">İmza eşleştirmesi gerektiren diğer durumlarda,,, ve,, ve ' ı gizleme veya geçersiz kılma,,, `in` `ref` ve birbirini `out` eşleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-134">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="ccc2b-135">Özellikler değişken değildir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-135">Properties are not variables.</span></span> <span data-ttu-id="ccc2b-136">Bunlar yöntemlerdir ve `ref` parametrelere geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-136">They're methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="ccc2b-137">`ref` `in` `out` Aşağıdaki tür yöntemler için, ve anahtar sözcüklerini kullanamazsınız:</span><span class="sxs-lookup"><span data-stu-id="ccc2b-137">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="ccc2b-138">Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-138">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="ccc2b-139">Bir [yield return](yield.md) veya bildiri içeren Yineleyici yöntemleri `yield break` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-139">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="ccc2b-140">[uzantı yöntemlerinin](../../programming-guide/classes-and-structs/extension-methods.md) bu anahtar sözcüklerin kullanımıyla ilgili kısıtlamaları da vardır:</span><span class="sxs-lookup"><span data-stu-id="ccc2b-140">[extension methods](../../programming-guide/classes-and-structs/extension-methods.md) also have restrictions on the use of these keywords:</span></span>

- <span data-ttu-id="ccc2b-141">`out`Anahtar sözcüğü, bir genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-141">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="ccc2b-142">`ref`Anahtar sözcüğü, bağımsız değişken bir struct olmadığında ya da genel bir tür struct olarak kısıtlanmamışsa Genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-142">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="ccc2b-143">`in`İlk bağımsız değişken bir struct olmadığı müddetçe anahtar sözcüğü kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-143">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="ccc2b-144">`in`Anahtar sözcüğü, bir struct gibi sınırlandırsalar bile herhangi bir genel tür üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-144">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="ccc2b-145">Bir bağımsız değişkeni başvuruya göre geçirme: bir örnek</span><span class="sxs-lookup"><span data-stu-id="ccc2b-145">Passing an argument by reference: An example</span></span>

<span data-ttu-id="ccc2b-146">Önceki örneklerde değer türleri başvuruya göre geçer.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-146">The previous examples pass value types by reference.</span></span> <span data-ttu-id="ccc2b-147">Başvuru `ref` türlerini başvuruya göre geçirmek için anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-147">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="ccc2b-148">Başvuru türü başvuruya göre geçirilme yöntemi, çağrılan yöntemin, başvuru parametresinin çağırıcının başvurduğu nesneyi değiştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-148">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="ccc2b-149">Nesnenin depolama konumu, başvuru parametresi değeri olarak yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-149">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="ccc2b-150">Parametresinin depolama konumundaki değeri değiştirirseniz (yeni bir nesneyi işaret etmek için), çağıranın başvurduğu depolama konumunu da değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-150">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="ccc2b-151">Aşağıdaki örnek, bir başvuru türünün örneğini bir parametre olarak geçirir `ref` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-151">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="ccc2b-152">Başvuru türlerini değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz. [Reference-Type parametrelerini geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ccc2b-152">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="ccc2b-153">Başvuru dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="ccc2b-153">Reference return values</span></span>

<span data-ttu-id="ccc2b-154">Başvuru dönüş değerleri (veya ref dönüşler), bir yöntemin çağırana başvuruya göre döndürdüğü değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-154">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="ccc2b-155">Diğer bir deyişle, çağıran bir yöntem tarafından döndürülen değeri değiştirebilir ve bu değişiklik çağırma yöntemindeki nesnenin durumunda yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-155">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="ccc2b-156">Bir başvuru dönüş değeri `ref` anahtar sözcüğü kullanılarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="ccc2b-156">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="ccc2b-157">Metot imzasında.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-157">In the method signature.</span></span> <span data-ttu-id="ccc2b-158">Örneğin, aşağıdaki yöntem imzası, `GetCurrentPrice` yöntemin başvuruya göre bir değer döndürdüğünü gösterir <xref:System.Decimal> .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-158">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="ccc2b-159">`return`Belirteç ve `return` yöntemin içindeki bir ifadede döndürülen değişken.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-159">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="ccc2b-160">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ccc2b-160">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="ccc2b-161">Çağıranın nesnenin durumunu değiştirmesi için, başvuru dönüş değeri açıkça bir [ref yerel](#ref-locals)olarak tanımlanmış bir değişkene depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-161">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="ccc2b-162">Burada hem yöntem imzasını hem de Yöntem gövdesini gösteren daha tamamlanmış bir ref Return örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-162">Here's a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="ccc2b-163">Çağrılan yöntem, `ref readonly` değeri başvuruya göre döndürmek için dönüş değerini de bildirebilir ve çağıran kodun döndürülen değeri değiştiremeyeceğini zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-163">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code can't modify the returned value.</span></span> <span data-ttu-id="ccc2b-164">Çağırma yöntemi, değeri yerel bir [ref salt okunur](#ref-readonly-locals) değişkeninde depolayarak döndürülen değeri kopyalamayı önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-164">The calling method can avoid copying the returned value by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="ccc2b-165">Bir örnek için, bkz. [bir başvuru dönüşleri ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="ccc2b-165">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="ccc2b-166">Başvuru yerelleri</span><span class="sxs-lookup"><span data-stu-id="ccc2b-166">Ref locals</span></span>

<span data-ttu-id="ccc2b-167">Kullanılarak döndürülen değerlere başvurmak için bir başvuru yerel değişkeni kullanılır `return ref` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-167">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="ccc2b-168">Bir ref yerel değişkeni, ref olmayan bir dönüş değeri olarak başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-168">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="ccc2b-169">Diğer bir deyişle, başlatmanın sağ tarafı bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-169">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="ccc2b-170">Ref Local değerindeki tüm değişiklikler, metodu, yöntemi başvuruya göre döndürülen nesnenin durumuna yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-170">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="ccc2b-171">Anahtar sözcüğünü iki yerde kullanarak bir ref yerel tanımlayın `ref` :</span><span class="sxs-lookup"><span data-stu-id="ccc2b-171">You define a ref local by using the `ref` keyword in two places:</span></span>

- <span data-ttu-id="ccc2b-172">Değişken bildiriminden önce.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-172">Before the variable declaration.</span></span>
- <span data-ttu-id="ccc2b-173">Başvuruya göre değeri döndüren yöntemine yapılan çağrıdan hemen önce.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-173">Immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="ccc2b-174">Örneğin, aşağıdaki ifade adlı bir yöntem tarafından döndürülen bir başvuru yerel değeri tanımlar `GetEstimatedValue` :</span><span class="sxs-lookup"><span data-stu-id="ccc2b-174">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="ccc2b-175">Başvuruya göre bir değere aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-175">You can access a value by reference in the same way.</span></span> <span data-ttu-id="ccc2b-176">Bazı durumlarda, başvuruya göre değere erişmek, potansiyel olarak pahalı bir kopyalama işlemini önleyerek performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-176">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="ccc2b-177">Örneğin, aşağıdaki ifade bir değere başvurmak için kullanılan bir ref yerel değişkeninin nasıl tanımlanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-177">For example, the following statement shows how to define a ref local variable that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="ccc2b-178">Her iki örnekte, `ref` anahtar sözcüğü her iki yerde de kullanılmalıdır veya derleyici hata CS8172 oluşturuyor, "bir değere sahip bir başvuru değişkeni başlatılamaz."</span><span class="sxs-lookup"><span data-stu-id="ccc2b-178">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="ccc2b-179">C# 7,3 ' den başlayarak, deyimin yineleme değişkeni `foreach` bir ref yerel veya ref ReadOnly yerel değişkeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-179">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be a ref local or ref readonly local variable.</span></span> <span data-ttu-id="ccc2b-180">Daha fazla bilgi için [foreach ifadesi](foreach-in.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-180">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="ccc2b-181">Ayrıca C# 7,3 ' den itibaren, ref [atama işleciyle](../operators/assignment-operator.md#ref-assignment-operator)bir ref yerel veya ref ReadOnly yerel değişkenini yeniden atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-181">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="ccc2b-182">Ref ReadOnly Yereller</span><span class="sxs-lookup"><span data-stu-id="ccc2b-182">Ref readonly locals</span></span>

<span data-ttu-id="ccc2b-183">Ref salt okunur yerel, imzası ve kullanımları olan bir yöntem veya özellik tarafından döndürülen değerlere başvurmak için kullanılır `ref readonly` `return ref` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-183">A ref readonly local is used to refer to values returned by a method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="ccc2b-184">`ref readonly`Değişken, yerel bir `ref` değişkenin özelliklerini bir değişkenle birleştirir `readonly` : Bu, atandığı depolamanın diğer adıdır ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-184">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it's an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="ccc2b-185">Bir ref, ve ref Yereller örneği döndürür</span><span class="sxs-lookup"><span data-stu-id="ccc2b-185">A ref returns and ref locals example</span></span>

<span data-ttu-id="ccc2b-186">Aşağıdaki örnek `Book` , ve iki alanı olan bir sınıfı tanımlar <xref:System.String> `Title` `Author` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-186">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="ccc2b-187">Ayrıca `BookCollection` , özel nesne dizisi içeren bir sınıfı tanımlar `Book` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-187">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="ccc2b-188">Bağımsız kitap nesneleri, yöntemi çağırarak başvuruya göre döndürülür `GetBookByTitle` .</span><span class="sxs-lookup"><span data-stu-id="ccc2b-188">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="ccc2b-189">Çağıran, yöntem tarafından döndürülen değeri `GetBookByTitle` bir ref yerel olarak depoladığında, çağıranın dönüş değeri için yaptığı değişiklikler, `BookCollection` Aşağıdaki örnekte gösterildiği gibi nesnesine yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-189">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="ccc2b-190">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ccc2b-190">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ccc2b-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccc2b-191">See also</span></span>

- [<span data-ttu-id="ccc2b-192">Güvenli verimli kod yazma</span><span class="sxs-lookup"><span data-stu-id="ccc2b-192">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="ccc2b-193">Ref dönüşler ve ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="ccc2b-193">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="ccc2b-194">Koşullu başvuru ifadesi</span><span class="sxs-lookup"><span data-stu-id="ccc2b-194">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="ccc2b-195">Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="ccc2b-195">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="ccc2b-196">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="ccc2b-196">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="ccc2b-197">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ccc2b-197">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ccc2b-198">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ccc2b-198">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ccc2b-199">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ccc2b-199">C# Keywords</span></span>](index.md)
