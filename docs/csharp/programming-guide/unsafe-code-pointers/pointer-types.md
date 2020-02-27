---
title: İşaretçi türleri- C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: dc03744559a87a2548c5bee9452c22cd20f337b8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627716"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="3e266-102">İşaretçi türleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3e266-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="3e266-103">Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e266-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="3e266-104">Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="3e266-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="3e266-105">Bir işaretçi türündeki `*` önce belirtilen tür, **başvurulan tür**olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e266-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="3e266-106">Yalnızca [yönetilmeyen bir tür](../../language-reference/builtin-types/unmanaged-types.md) , başvurulan bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e266-106">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="3e266-107">İşaretçi türleri [nesneden](../../language-reference/builtin-types/reference-types.md) devralma ve işaretçi türleri ve `object`arasında dönüştürme yok.</span><span class="sxs-lookup"><span data-stu-id="3e266-107">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="3e266-108">Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3e266-108">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="3e266-109">Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e266-109">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="3e266-110">Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (\*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="3e266-110">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="3e266-111">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3e266-111">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="3e266-112">Bir işaretçi, bir işaretçiye işaret eden bir nesne başvurusu atık olarak toplanabileceğinden, bir başvuruya veya başvuru içeren bir [yapıya](../../language-reference/builtin-types/struct.md) işaret edemez.</span><span class="sxs-lookup"><span data-stu-id="3e266-112">A pointer cannot point to a reference or to a [struct](../../language-reference/builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="3e266-113">Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.</span><span class="sxs-lookup"><span data-stu-id="3e266-113">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="3e266-114">`myType*` türündeki işaretçi değişkeninin değeri, `myType`türünde bir değişkenin adresidir.</span><span class="sxs-lookup"><span data-stu-id="3e266-114">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="3e266-115">Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3e266-115">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="3e266-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e266-116">Example</span></span>|<span data-ttu-id="3e266-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e266-117">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="3e266-118">`p`, tamsayıya yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="3e266-118">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="3e266-119">`p`, tamsayıya yönelik işaretçinin bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="3e266-119">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="3e266-120">`p`, tamsayılara yönelik işaretçilerin tek boyutlu bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="3e266-120">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="3e266-121">`p`, Char için bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="3e266-121">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="3e266-122">`p`, bilinmeyen bir türe yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="3e266-122">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="3e266-123">İşaretçi yöneltme işleci \*, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir.</span><span class="sxs-lookup"><span data-stu-id="3e266-123">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="3e266-124">Örneğin, aşağıdaki bildirimi ele alalım:</span><span class="sxs-lookup"><span data-stu-id="3e266-124">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="3e266-125">İfade `*myVariable`, `myVariable`bulunan adreste bulunan `int` değişkenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e266-125">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="3e266-126">Konular [Sabit bildiriminde](../../language-reference/keywords/fixed-statement.md) ve [işaretçi dönüştürmelerinde birçok işaretçiye](./pointer-conversions.md)örnek vardır.</span><span class="sxs-lookup"><span data-stu-id="3e266-126">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="3e266-127">Aşağıdaki örnek `unsafe` anahtar sözcüğünü ve `fixed` ifadesini kullanır ve iç işaretçinin nasıl artırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e266-127">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="3e266-128">Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e266-128">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="3e266-129">Bu örneklerin [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçenek kümesiyle derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e266-129">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="3e266-130">Yöneltme işlecini `void*`türünde bir işaretçiye uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3e266-130">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="3e266-131">Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e266-131">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="3e266-132">Bir işaretçi `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e266-132">A pointer can be `null`.</span></span> <span data-ttu-id="3e266-133">Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="3e266-133">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="3e266-134">Yöntemler arasında işaretçiler geçirmek tanımsız davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e266-134">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="3e266-135">Bir `in`, `out`veya `ref` parametresi ya da işlev sonucu olarak yerel bir değişkene bir işaretçi döndüren bir yöntem düşünün.</span><span class="sxs-lookup"><span data-stu-id="3e266-135">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="3e266-136">İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.</span><span class="sxs-lookup"><span data-stu-id="3e266-136">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="3e266-137">Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e266-137">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="3e266-138">İşleç/Deyim</span><span class="sxs-lookup"><span data-stu-id="3e266-138">Operator/Statement</span></span>|<span data-ttu-id="3e266-139">Kullanım</span><span class="sxs-lookup"><span data-stu-id="3e266-139">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="3e266-140">İşaretçi yöneltmesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3e266-140">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="3e266-141">Bir yapının bir üyesine bir işaretçi yoluyla erişir.</span><span class="sxs-lookup"><span data-stu-id="3e266-141">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="3e266-142">Bir işaretçiyi dizine ekler.</span><span class="sxs-lookup"><span data-stu-id="3e266-142">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="3e266-143">Bir değişkenin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="3e266-143">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="3e266-144">`++` ve `--`</span><span class="sxs-lookup"><span data-stu-id="3e266-144">`++` and `--`</span></span>|<span data-ttu-id="3e266-145">İşaretçileri artırır ve azaltır.</span><span class="sxs-lookup"><span data-stu-id="3e266-145">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="3e266-146">`+` ve `-`</span><span class="sxs-lookup"><span data-stu-id="3e266-146">`+` and `-`</span></span>|<span data-ttu-id="3e266-147">İşaretçi aritmetiği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3e266-147">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="3e266-148">`==`, `!=`, `<`, `>`, `<=`ve `>=`</span><span class="sxs-lookup"><span data-stu-id="3e266-148">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="3e266-149">İşaretçileri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="3e266-149">Compares pointers.</span></span>|
|[<span data-ttu-id="3e266-150">`stackalloc` işleci</span><span class="sxs-lookup"><span data-stu-id="3e266-150">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="3e266-151">Yığında bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="3e266-151">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="3e266-152">`fixed` ekstresi</span><span class="sxs-lookup"><span data-stu-id="3e266-152">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="3e266-153">Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.</span><span class="sxs-lookup"><span data-stu-id="3e266-153">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="3e266-154">İşaretçi ile ilgili işleçler hakkında daha fazla bilgi için bkz. [işaretçi ile ilgili işleçler](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3e266-154">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3e266-155">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3e266-155">C# language specification</span></span>

<span data-ttu-id="3e266-156">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3e266-156">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e266-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e266-157">See also</span></span>

- [<span data-ttu-id="3e266-158">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3e266-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3e266-159">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="3e266-159">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="3e266-160">İşaretçi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="3e266-160">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="3e266-161">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="3e266-161">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="3e266-162">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="3e266-162">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="3e266-163">unsafe</span><span class="sxs-lookup"><span data-stu-id="3e266-163">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
