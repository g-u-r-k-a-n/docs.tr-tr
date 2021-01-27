---
title: Yöntemler-C# Programlama Kılavuzu
description: C# içindeki bir yöntem, bir dizi deyim içeren bir kod bloğudur. Program, yöntemini çağırarak ve bağımsız değişkenleri belirterek deyimleri çalıştırır.
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 879e57cfbce82f1aa77f8810e23d6a61a6ea5bc8
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899457"
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="942a2-104">Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="942a2-104">Methods (C# Programming Guide)</span></span>

<span data-ttu-id="942a2-105">Yöntemi, bir dizi deyim içeren bir kod bloğudur.</span><span class="sxs-lookup"><span data-stu-id="942a2-105">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="942a2-106">Program, metodu çağırarak ve gerekli Yöntem bağımsız değişkenlerini belirterek deyimlerin yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="942a2-106">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="942a2-107">C# ' de, yürütülen her yönerge bir yöntem bağlamında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-107">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="942a2-108">`Main`Yöntemi her C# uygulamasının giriş noktasıdır ve program başlatıldığında ortak dil çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="942a2-108">The `Main` method is the entry point for every C# application and it's called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="942a2-109">Bu makalede adlandırılmış yöntemler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="942a2-109">This article discusses named methods.</span></span> <span data-ttu-id="942a2-110">Anonim işlevler hakkında daha fazla bilgi için bkz. [Anonim işlevler](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="942a2-110">For information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>

## <a name="method-signatures"></a><span data-ttu-id="942a2-111">Yöntem imzaları</span><span class="sxs-lookup"><span data-stu-id="942a2-111">Method signatures</span></span>

<span data-ttu-id="942a2-112">Yöntemler veya, [](../../language-reference/keywords/class.md) [](../../language-reference/builtin-types/struct.md) [](../interfaces/index.md) `public` `private` `abstract` `sealed` dönüş değeri, yöntemin adı ve herhangi bir yöntem parametresi gibi erişim düzeyi belirtilerek, veya gibi isteğe bağlı değiştiriciler belirtilerek bir sınıf, yapı veya arabirim içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="942a2-112">Methods are declared in a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../interfaces/index.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="942a2-113">Bu parçalar, yönteminin imzasıdır.</span><span class="sxs-lookup"><span data-stu-id="942a2-113">These parts together are the signature of the method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="942a2-114">Bir yöntemin dönüş türü, yöntem aşırı yüklemesi amaçları için yöntemin imzasının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="942a2-114">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="942a2-115">Ancak, bir temsilci ve işaret ettiği yöntem arasındaki uyumluluğun belirlenmesi sırasında yönteminin imzasının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="942a2-115">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="942a2-116">Yöntem parametreleri parantez içine alınır ve virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="942a2-116">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="942a2-117">Boş parantezler, yöntemin hiçbir parametre gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="942a2-117">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="942a2-118">Bu sınıf dört yöntem içerir:</span><span class="sxs-lookup"><span data-stu-id="942a2-118">This class contains four methods:</span></span>

[!code-csharp[DifferentModifiersOnMethods#1](snippets/methods/Program.cs#1)]

## <a name="method-access"></a><span data-ttu-id="942a2-119">Yöntem erişimi</span><span class="sxs-lookup"><span data-stu-id="942a2-119">Method access</span></span>

<span data-ttu-id="942a2-120">Bir nesne üzerinde bir yöntemi çağırmak, bir alana erişme gibidir.</span><span class="sxs-lookup"><span data-stu-id="942a2-120">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="942a2-121">Nesne adından sonra bir nokta, yöntemin adı ve parantez ekleyin.</span><span class="sxs-lookup"><span data-stu-id="942a2-121">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="942a2-122">Bağımsız değişkenler parantez içinde listelenir ve virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="942a2-122">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="942a2-123">`Motorcycle`Bu nedenle, sınıfının yöntemleri aşağıdaki örnekte olduğu gibi çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="942a2-123">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>

[!code-csharp[CallingMethods#2](snippets/methods/Program.cs#2)]

## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="942a2-124">Yöntem parametreleri ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="942a2-124">Method parameters vs. arguments</span></span>

<span data-ttu-id="942a2-125">Yöntem tanımı, gerekli parametrelerin adlarını ve türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="942a2-125">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="942a2-126">Kodu çağırırken yöntemi çağırdığında, her parametre için bağımsız değişkenler olarak adlandırılan somut değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="942a2-126">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="942a2-127">Bağımsız değişkenlerin parametre türüyle uyumlu olması gerekir, ancak çağıran kodda kullanılan bağımsız değişken adı (varsa) yöntemde tanımlanan parametre ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="942a2-127">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code doesn't have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="942a2-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="942a2-128">For example:</span></span>

[!code-csharp[MethodExamples#3](snippets/methods/Program.cs#3)]

## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="942a2-129">Başvuruya göre geçirme-değere göre geçirme</span><span class="sxs-lookup"><span data-stu-id="942a2-129">Passing by reference vs. passing by value</span></span>

<span data-ttu-id="942a2-130">Varsayılan olarak, bir [değer türü](../../language-reference/builtin-types/value-types.md) örneği bir yönteme geçirildiğinde, kopyasının kendisi yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-130">By default, when an instance of a [value type](../../language-reference/builtin-types/value-types.md) is passed to a method, its copy is passed instead of the instance itself.</span></span> <span data-ttu-id="942a2-131">Bu nedenle, bağımsız değişkende yapılan değişikliklerin, çağırma yönteminde orijinal örnek üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="942a2-131">Therefore, changes to the argument have no effect on the original instance in the calling method.</span></span> <span data-ttu-id="942a2-132">Değer türü örneği başvuruya göre geçirmek için `ref` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="942a2-132">To pass a value-type instance by reference, use the `ref` keyword.</span></span> <span data-ttu-id="942a2-133">Daha fazla bilgi için bkz. [Value-Type parametrelerini geçirme](./passing-value-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="942a2-133">For more information, see [Passing Value-Type Parameters](./passing-value-type-parameters.md).</span></span>

<span data-ttu-id="942a2-134">Başvuru türündeki bir nesne yöntemine geçirildiğinde, nesnesine bir başvuru geçirilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-134">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="942a2-135">Diğer bir deyişle, yöntem nesnenin kendisini değil, nesnenin konumunu gösteren bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="942a2-135">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="942a2-136">Bu başvuruyu kullanarak nesnesinin bir üyesini değiştirirseniz, nesneyi değere göre iletseniz bile, değişiklik çağırma yöntemindeki bağımsız değişkende yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="942a2-136">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>

<span data-ttu-id="942a2-137">`class`Aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü kullanarak bir başvuru türü oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="942a2-137">You create a reference type by using the `class` keyword, as the following example shows:</span></span>

[!code-csharp[SampleRefTypeClass#4](snippets/methods/Program.cs#4)]

<span data-ttu-id="942a2-138">Artık, bu türü temel alan bir nesneyi bir yönteme geçirirseniz, nesnesine bir başvuru geçirilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-138">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="942a2-139">Aşağıdaki örnek, türünde bir nesnesini yöntemine geçirir `SampleRefType` `ModifyObject` :</span><span class="sxs-lookup"><span data-stu-id="942a2-139">The following example passes an object of type `SampleRefType` to method `ModifyObject`:</span></span>

[!code-csharp[PassingAReferenceType#5](snippets/methods/Program.cs#5)]

<span data-ttu-id="942a2-140">Örnek temelde bir yönteme değere göre bir bağımsız değişken geçirdiğinden önceki örnekle aynı şeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="942a2-140">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="942a2-141">Ancak, bir başvuru türü kullanıldığından, sonuç farklıdır.</span><span class="sxs-lookup"><span data-stu-id="942a2-141">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="942a2-142">Parametresinin alanı üzerinde yapılan değişiklik, `ModifyObject` `value` `obj` `value` yöntemi içindeki bağımsız değişkenin alanını da değiştirir `rt` `TestRefType` .</span><span class="sxs-lookup"><span data-stu-id="942a2-142">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="942a2-143">`TestRefType`Yöntemi çıkış olarak 33 görüntüler.</span><span class="sxs-lookup"><span data-stu-id="942a2-143">The `TestRefType` method displays 33 as the output.</span></span>

<span data-ttu-id="942a2-144">Başvuru türlerini başvuruya ve değere göre geçirme hakkında daha fazla bilgi için bkz. [Reference-Type parametrelerini](./passing-reference-type-parameters.md) ve [başvuru türlerini](../../language-reference/keywords/reference-types.md)geçirme.</span><span class="sxs-lookup"><span data-stu-id="942a2-144">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](./passing-reference-type-parameters.md) and [Reference Types](../../language-reference/keywords/reference-types.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="942a2-145">Dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="942a2-145">Return values</span></span>

<span data-ttu-id="942a2-146">Yöntemler çağırana bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-146">Methods can return a value to the caller.</span></span> <span data-ttu-id="942a2-147">Dönüş türü, yöntem adından önce listelenen tür değilse, `void` yöntemi anahtar sözcüğünü kullanarak değeri döndürebilir `return` .</span><span class="sxs-lookup"><span data-stu-id="942a2-147">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="942a2-148">`return`Dönüş türüyle eşleşen bir değer gelen anahtar sözcüğünü içeren bir ifade, bu değeri çağıran metoda döndürür.</span><span class="sxs-lookup"><span data-stu-id="942a2-148">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span>

<span data-ttu-id="942a2-149">Değer, çağıran değere veya C# 7,0 ile başlayarak [başvuruya göre](ref-returns.md)döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-149">The value can be returned to the caller by value or, starting with C# 7.0, [by reference](ref-returns.md).</span></span> <span data-ttu-id="942a2-150">`ref`Anahtar sözcüğü Yöntem imzasında kullanılıyorsa ve her bir anahtar sözcüğü izliyorsa, değerler, çağıran başvuruya göre döndürülür `return` .</span><span class="sxs-lookup"><span data-stu-id="942a2-150">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="942a2-151">Örneğin, aşağıdaki yöntem imzası ve Return deyimleri, yöntemin çağırana başvuruya göre değişken adlarını döndürdüğünü gösterir `estDistance` .</span><span class="sxs-lookup"><span data-stu-id="942a2-151">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

<span data-ttu-id="942a2-152">`return`Anahtar sözcüğü, yönteminin yürütülmesini de sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="942a2-152">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="942a2-153">Dönüş türü ise, `void` `return` değeri olmayan bir ifade, metodun yürütülmesini durdurmak için hala yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="942a2-153">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="942a2-154">`return`Anahtar sözcüğü olmadan Yöntem, kod bloğunun sonuna ulaştığında yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="942a2-154">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="942a2-155">`return`Bir değer döndürmek için anahtar sözcüğünü kullanmak için void olmayan bir dönüş türüne sahip metotlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="942a2-155">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="942a2-156">Örneğin, bu iki yöntem `return` tamsayılar döndürmek için anahtar sözcüğünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="942a2-156">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[SimpleMathClass#6](snippets/methods/Program.cs#6)]

<span data-ttu-id="942a2-157">Bir yöntemden döndürülen bir değer kullanmak için, çağırma yöntemi yöntemi tek bir değer olan her yerde, aynı türde bir değer yeterli olacak şekilde kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-157">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="942a2-158">Dönüş değerini bir değişkene de atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="942a2-158">You can also assign the return value to a variable.</span></span> <span data-ttu-id="942a2-159">Örneğin, aşağıdaki iki kod örneği aynı hedefi yerine getirmektedir:</span><span class="sxs-lookup"><span data-stu-id="942a2-159">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[SquareANumberWithAddTwoNumbersUsingLocalVariable#7](snippets/methods/Program.cs#7)]

[!code-csharp[SquareANumberWithAddTwoNumbersInTheSameLine#8](snippets/methods/Program.cs#8)]

<span data-ttu-id="942a2-160">Bu durumda, `result` bir değeri depolamak için yerel bir değişken kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="942a2-160">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="942a2-161">Kodun okunabilirliğini yardımcı olabilir veya metodun tüm kapsamı için bağımsız değişkenin özgün değerini depolamanız gerekirse gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-161">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="942a2-162">Bir yöntemden başvuruya göre döndürülen bir değeri kullanmak için, değerini değiştirmek istiyorsanız bir [ref yerel](ref-returns.md#ref-locals) değişkeni bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="942a2-162">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="942a2-163">Örneğin, `Planet.GetEstimatedDistance` yöntemi <xref:System.Double> başvuruya göre bir değer döndürürse, bunu aşağıdaki gibi kodla bir ref yerel değişkeni olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="942a2-163">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant
```

<span data-ttu-id="942a2-164">`M`Arama işlevi diziyi içine geçirse, dizinin içeriğini değiştiren bir yöntemden çok boyutlu bir dizi döndürülüyor `M` .</span><span class="sxs-lookup"><span data-stu-id="942a2-164">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="942a2-165">Elde edilen diziyi, `M` iyi stil veya işlevsel akış için öğesinden döndürebilirsiniz, ancak C# tüm başvuru türlerini değere göre geçirdiğinden ve dizi başvurusunun değeri dizi işaretçisiyse, bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="942a2-165">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="942a2-166">Yönteminde `M` , dizinin içeriğinde yapılan tüm değişiklikler, aşağıdaki örnekte gösterildiği gibi diziye başvuran herhangi bir kod tarafından Observable ' tır:</span><span class="sxs-lookup"><span data-stu-id="942a2-166">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example:</span></span>

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

<span data-ttu-id="942a2-167">Daha fazla bilgi için bkz. [Return](../../language-reference/keywords/return.md).</span><span class="sxs-lookup"><span data-stu-id="942a2-167">For more information, see [return](../../language-reference/keywords/return.md).</span></span>

## <a name="async-methods"></a><span data-ttu-id="942a2-168">Zaman uyumsuz yöntemler</span><span class="sxs-lookup"><span data-stu-id="942a2-168">Async methods</span></span>

<span data-ttu-id="942a2-169">Async özelliğini kullanarak, açık geri çağırmaları kullanmadan zaman uyumsuz yöntemleri çağırabilir veya kodunuzu birden çok yöntemde veya Lambda ifadelerinde el ile böedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="942a2-169">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="942a2-170">[Zaman uyumsuz](../../language-reference/keywords/async.md) değiştiriciyle bir yöntemi işaretlerseniz, yönteminde [await](../../language-reference/operators/await.md) işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="942a2-170">If you mark a method with the [async](../../language-reference/keywords/async.md) modifier, you can use the [await](../../language-reference/operators/await.md) operator in the method.</span></span> <span data-ttu-id="942a2-171">Denetim zaman uyumsuz yöntemde bir await ifadesine ulaştığında denetim çağırana döner ve beklenen görev tamamlanana kadar yöntemdeki ilerleme durumu askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="942a2-171">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="942a2-172">Görev tamamlandığında, yürütme yöntemi içinde çalışmaya çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-172">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="942a2-173">Zaman uyumsuz bir yöntem, henüz tamamlanmamış olan ilk beklemiş nesneyle karşılaştığında çağırana döner veya zaman uyumsuz yöntemin sonuna kadar, hangisi önce gerçekleşiyorsa.</span><span class="sxs-lookup"><span data-stu-id="942a2-173">An async method returns to the caller when either it encounters the first awaited object that's not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="942a2-174">Zaman uyumsuz bir yöntem,, veya void dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="942a2-174">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="942a2-175">Void dönüş türü birincil olarak, bir void dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="942a2-175">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="942a2-176">Void döndüren zaman uyumsuz bir yöntem beklenemez ve void döndüren bir yöntemi çağıran yöntemin aldığı özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="942a2-176">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="942a2-177">Aşağıdaki örnekte, `DelayAsync` dönüş türüne sahip bir zaman uyumsuz yöntem <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="942a2-177">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="942a2-178">`DelayAsync` , `return` bir tamsayı döndüren bir ifadeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="942a2-178">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="942a2-179">Bu nedenle, öğesinin yöntem bildirimi `DelayAsync` bir dönüş türüne sahip olmalıdır `Task<int>` .</span><span class="sxs-lookup"><span data-stu-id="942a2-179">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="942a2-180">Dönüş türü olduğu için `Task<int>` , `await` içindeki ifadesinin değerlendirmesi `DoSomethingAsync` aşağıdaki deyim tarafından gösterildiği gibi bir tamsayı oluşturur: `int result = await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="942a2-180">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>

<span data-ttu-id="942a2-181">`Main`Yöntemi, dönüş türüne sahip bir zaman uyumsuz metoda bir örnektir <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="942a2-181">The `Main` method is an example of an async method that has a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="942a2-182">`DoSomethingAsync`Yöntemine gider ve tek bir satırla ifade edildiğinden, `async` ve `await` anahtar sözcüklerini atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-182">It goes to the `DoSomethingAsync` method, and because it is expressed with a single line, it can omit the `async` and `await` keywords.</span></span> <span data-ttu-id="942a2-183">`DoSomethingAsync`Zaman uyumsuz bir yöntem olduğundan, çağrının görevi `DoSomethingAsync` beklenmelidir, çünkü aşağıdaki deyimde gösterildiği gibi: `await DoSomethingAsync();` .</span><span class="sxs-lookup"><span data-stu-id="942a2-183">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span>

:::code language="csharp" source="snippets/classes-and-structs/methods/Program.cs":::

<span data-ttu-id="942a2-184">Zaman uyumsuz bir yöntem herhangi bir [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi bildiremez, ancak bu parametrelere sahip yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="942a2-184">An async method can't declare any [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

<span data-ttu-id="942a2-185">Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. Async ve await ile zaman uyumsuz [dönüş türleri](../concepts/async/async-return-types.md) [ile zaman uyumsuz programlama](../concepts/async/index.md) .</span><span class="sxs-lookup"><span data-stu-id="942a2-185">For more information about async methods, see [Asynchronous programming with async and await](../concepts/async/index.md) and [Async return types](../concepts/async/async-return-types.md).</span></span>

## <a name="expression-body-definitions"></a><span data-ttu-id="942a2-186">İfade gövdesi tanımları</span><span class="sxs-lookup"><span data-stu-id="942a2-186">Expression body definitions</span></span>

<span data-ttu-id="942a2-187">Yalnızca bir ifadenin sonucuyla hemen dönen veya yöntemin gövdesi olarak tek bir deyimi olan yöntem tanımlarının olması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="942a2-187">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span> <span data-ttu-id="942a2-188">Kullanarak bu tür yöntemleri tanımlamaya yönelik bir sözdizimi kısayolu vardır `=>` :</span><span class="sxs-lookup"><span data-stu-id="942a2-188">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="942a2-189">Yöntemi `void` bir zaman uyumsuz yöntem döndürürse veya ise, yöntemin gövdesi bir deyim ifadesi olmalıdır (Lambdalar ile aynı).</span><span class="sxs-lookup"><span data-stu-id="942a2-189">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span> <span data-ttu-id="942a2-190">Özellikler ve Dizin oluşturucular için, bunların salt okunmaları ve `get` erişimci anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="942a2-190">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>

## <a name="iterators"></a><span data-ttu-id="942a2-191">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="942a2-191">Iterators</span></span>

<span data-ttu-id="942a2-192">Yineleyici, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="942a2-192">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="942a2-193">Bir yineleyici, her öğeyi birer birer döndürmek için [yield return](../../language-reference/keywords/yield.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="942a2-193">An iterator uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="942a2-194">Bir [yield return](../../language-reference/keywords/yield.md) ifadesine ulaşıldığında, koddaki geçerli konum hatırlanır.</span><span class="sxs-lookup"><span data-stu-id="942a2-194">When a [yield return](../../language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="942a2-195">Yineleyici bir sonraki sefer çağrıldığında, yürütme o konumdan yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="942a2-195">Execution is restarted from that location when the iterator is called the next time.</span></span>

<span data-ttu-id="942a2-196">Bir [foreach](../../language-reference/keywords/foreach-in.md) ifadesi kullanarak istemci kodundan bir yineleyici çağırın.</span><span class="sxs-lookup"><span data-stu-id="942a2-196">You call an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

<span data-ttu-id="942a2-197">Yineleyicinin dönüş türü <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="942a2-197">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="942a2-198">Daha fazla bilgi için bkz. [yineleyiciler](../concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="942a2-198">For more information, see [Iterators](../concepts/iterators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="942a2-199">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="942a2-199">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="942a2-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="942a2-200">See also</span></span>

- [<span data-ttu-id="942a2-201">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="942a2-201">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="942a2-202">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="942a2-202">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="942a2-203">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="942a2-203">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="942a2-204">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="942a2-204">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)
- [<span data-ttu-id="942a2-205">Devralma</span><span class="sxs-lookup"><span data-stu-id="942a2-205">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="942a2-206">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="942a2-206">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="942a2-207">params</span><span class="sxs-lookup"><span data-stu-id="942a2-207">params</span></span>](../../language-reference/keywords/params.md)
- [<span data-ttu-id="942a2-208">return</span><span class="sxs-lookup"><span data-stu-id="942a2-208">return</span></span>](../../language-reference/keywords/return.md)
- [<span data-ttu-id="942a2-209">out</span><span class="sxs-lookup"><span data-stu-id="942a2-209">out</span></span>](../../language-reference/keywords/out.md)
- [<span data-ttu-id="942a2-210">ref</span><span class="sxs-lookup"><span data-stu-id="942a2-210">ref</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="942a2-211">Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="942a2-211">Passing Parameters</span></span>](passing-parameters.md)
