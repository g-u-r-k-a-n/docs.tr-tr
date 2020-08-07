---
title: Listeler
description: 'Aynı türdeki sıralı, sabit bir öğe serisi olan F # listeleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 236ae77813a3448f159228c5c58d9fe3d024fbd8
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854977"
---
# <a name="lists"></a><span data-ttu-id="c8419-103">Listeler</span><span class="sxs-lookup"><span data-stu-id="c8419-103">Lists</span></span>

<span data-ttu-id="c8419-104">F # ' daki bir liste, aynı türde olan sıralı, sabit bir öğe serisidir.</span><span class="sxs-lookup"><span data-stu-id="c8419-104">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="c8419-105">Listelerde temel işlemleri gerçekleştirmek için, [liste modülündeki](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)işlevleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8419-105">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

> [!NOTE]
> <span data-ttu-id="c8419-106">F # için docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="c8419-106">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="c8419-107">Bozuk bağlantılarla karşılaşırsanız, bunun yerine [F # Çekirdek Kitaplığı belgelerine](https://fsharp.github.io/fsharp-core-docs/) başvurun.</span><span class="sxs-lookup"><span data-stu-id="c8419-107">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="c8419-108">Liste oluşturma ve başlatma</span><span class="sxs-lookup"><span data-stu-id="c8419-108">Creating and Initializing Lists</span></span>

<span data-ttu-id="c8419-109">Aşağıdaki kod satırında gösterildiği gibi, noktalı virgülle ayırarak ve köşeli parantez içine alınmış öğeleri açıkça listeleyerek bir liste tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8419-109">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="c8419-110">Ayrıca, öğelerin arasına satır sonları koyabilirsiniz, bu durumda noktalı virgül isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c8419-110">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="c8419-111">İkinci sözdizimi, öğe başlatma ifadeleri daha uzun olduğunda veya her öğe için bir açıklama eklemek istediğinizde daha okunabilir kod oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8419-111">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="c8419-112">Normalde, tüm liste öğeleri aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8419-112">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="c8419-113">Bir özel durum, öğelerin temel tür olarak belirtildiği bir listenin türetilmiş tür öğelerine sahip olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8419-113">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="c8419-114">Bu nedenle, her ikisi `Button` ve `CheckBox` öğesinden türetiğinden aşağıdakiler kabul edilebilir `Control` .</span><span class="sxs-lookup"><span data-stu-id="c8419-114">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="c8419-115">Ayrıca `..` , aşağıdaki kodda gösterildiği gibi, Aralık işleci () ile ayrılmış tamsayılar tarafından belirtilen bir aralığı kullanarak liste öğelerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8419-115">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="c8419-116">Boş bir liste, aralarında hiçbir şey olmadan köşeli ayraç çifti ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c8419-116">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="c8419-117">Bir liste oluşturmak için bir dizi ifadesi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8419-117">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="c8419-118">Daha fazla bilgi için bkz. [dizi ifadeleri](sequences.md#sequence-expressions) .</span><span class="sxs-lookup"><span data-stu-id="c8419-118">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="c8419-119">Örneğin, aşağıdaki kod, 1 ile 10 arasındaki sayıların karelerinin bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8419-119">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="c8419-120">Listelerle çalışma için işleçler</span><span class="sxs-lookup"><span data-stu-id="c8419-120">Operators for Working with Lists</span></span>

<span data-ttu-id="c8419-121">(Cons) işlecini kullanarak bir listeye öğe ekleyebilirsiniz `::` .</span><span class="sxs-lookup"><span data-stu-id="c8419-121">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="c8419-122">`list1`İse `[2; 3; 4]` , aşağıdaki kod `list2` olarak oluşturulur `[100; 2; 3; 4]` .</span><span class="sxs-lookup"><span data-stu-id="c8419-122">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="c8419-123">Aşağıdaki kodda olduğu gibi işlecini kullanarak uyumlu türleri olan listeleri birleştirebilirsiniz `@` .</span><span class="sxs-lookup"><span data-stu-id="c8419-123">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="c8419-124">, `list1` Ve ise, `[2; 3; 4]` `list2` `[100; 2; 3; 4]` Bu kod olarak oluşturulur `list3` `[2; 3; 4; 100; 2; 3; 4]` .</span><span class="sxs-lookup"><span data-stu-id="c8419-124">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="c8419-125">Listelerde işlem gerçekleştirmeye yönelik işlevler, [liste modülünde](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c8419-125">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="c8419-126">F # içindeki listeler sabit olduğundan, tüm değiştirme işlemleri var olan listeleri değiştirmek yerine yeni listeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8419-126">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="c8419-127">F # içindeki listeler, listedir bağlantılı listeler olarak uygulanır. Bu, yalnızca listenin baş başlarına erişen işlemlerin O (1) ve öğe erişiminin ise O (*n*) olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c8419-127">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="c8419-128">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c8419-128">Properties</span></span>

<span data-ttu-id="c8419-129">Liste türü aşağıdaki özellikleri destekler:</span><span class="sxs-lookup"><span data-stu-id="c8419-129">The list type supports the following properties:</span></span>

|<span data-ttu-id="c8419-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="c8419-130">Property</span></span>|<span data-ttu-id="c8419-131">Tür</span><span class="sxs-lookup"><span data-stu-id="c8419-131">Type</span></span>|<span data-ttu-id="c8419-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8419-132">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="c8419-133">Başlı</span><span class="sxs-lookup"><span data-stu-id="c8419-133">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="c8419-134">İlk öğesi.</span><span class="sxs-lookup"><span data-stu-id="c8419-134">The first element.</span></span>|
|[<span data-ttu-id="c8419-135">Olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="c8419-135">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="c8419-136">Uygun türdeki boş bir liste döndüren statik özellik.</span><span class="sxs-lookup"><span data-stu-id="c8419-136">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="c8419-137">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="c8419-137">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="c8419-138">`true`listede öğe yoksa.</span><span class="sxs-lookup"><span data-stu-id="c8419-138">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="c8419-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="c8419-139">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="c8419-140">Belirtilen dizindeki öğe (sıfır tabanlı).</span><span class="sxs-lookup"><span data-stu-id="c8419-140">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="c8419-141">Uzunluk</span><span class="sxs-lookup"><span data-stu-id="c8419-141">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="c8419-142">Öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="c8419-142">The number of elements.</span></span>|
|[<span data-ttu-id="c8419-143">Kuyruk</span><span class="sxs-lookup"><span data-stu-id="c8419-143">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="c8419-144">İlk öğesi olmayan liste.</span><span class="sxs-lookup"><span data-stu-id="c8419-144">The list without the first element.</span></span>|

<span data-ttu-id="c8419-145">Aşağıda bu özellikleri kullanmaya ilişkin bazı örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c8419-145">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="c8419-146">Listeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="c8419-146">Using Lists</span></span>

<span data-ttu-id="c8419-147">Listelerle programlama, az miktarda kodla karmaşık işlemler gerçekleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8419-147">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="c8419-148">Bu bölümde, işlevsel programlama için önemli olan listelerle ilgili genel işlemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c8419-148">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="c8419-149">Listelerle özyineleme</span><span class="sxs-lookup"><span data-stu-id="c8419-149">Recursion with Lists</span></span>

<span data-ttu-id="c8419-150">Listeler özyinelemeli programlama tekniklerine benzersiz bir şekilde uygundur.</span><span class="sxs-lookup"><span data-stu-id="c8419-150">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="c8419-151">Listenin her öğesinde gerçekleştirilmesi gereken bir işlem düşünün.</span><span class="sxs-lookup"><span data-stu-id="c8419-151">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="c8419-152">Bu işlemi, listenin başından yararlanarak ve sonra listenin kuyruğunu geçirerek, ilk öğe olmayan orijinal listeden oluşan daha küçük bir liste olan bir sonraki özyineleme düzeyine geri dönerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8419-152">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="c8419-153">Bu tür bir özyinelemeli işlevi yazmak için, `::` bir listenin başını bir kuyruklu ayırmanızı sağlayan, model eşleme içinde Cons işlecini () kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8419-153">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="c8419-154">Aşağıdaki kod örneği, bir liste üzerinde işlemler gerçekleştiren özyinelemeli bir işlevi uygulamak için nasıl model eşleştirmesinin kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c8419-154">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="c8419-155">Önceki kod küçük listeler için iyi sonuç verir, ancak daha büyük listeler için yığın taşar.</span><span class="sxs-lookup"><span data-stu-id="c8419-155">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="c8419-156">Aşağıdaki kod, özyinelemeli işlevlerle çalışmaya yönelik standart bir yöntem olan bir biriktirici bağımsız değişkeni kullanarak bu kodda gelişir.</span><span class="sxs-lookup"><span data-stu-id="c8419-156">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="c8419-157">Biriktiricidir bağımsız değişkeninin kullanılması, yığın alanı kaydeden işlev kuyruklu özyinelemeli olur.</span><span class="sxs-lookup"><span data-stu-id="c8419-157">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="c8419-158">İşlevi, `RemoveAllMultiples` iki liste alan özyinelemeli bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="c8419-158">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="c8419-159">İlk liste, katları kaldırılacak olan sayıları ve ikinci liste ise sayıların kaldırılacağı liste olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="c8419-159">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="c8419-160">Aşağıdaki örnekteki kod, bu özyinelemeli işlevi bir listeden tüm asal olmayan sayıları ortadan kaldırmak için kullanır ve sonuç olarak asal sayıların bir listesini bırakır.</span><span class="sxs-lookup"><span data-stu-id="c8419-160">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="c8419-161">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-161">The output is as follows:</span></span>

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="c8419-162">Modül Işlevleri</span><span class="sxs-lookup"><span data-stu-id="c8419-162">Module Functions</span></span>

<span data-ttu-id="c8419-163">[Liste modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) , bir listenin öğelerine erişen işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8419-163">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="c8419-164">Baş öğe, erişimin en hızlı ve en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="c8419-164">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="c8419-165">Özellik [kafasını](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) veya [List. Head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2)modül işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8419-165">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="c8419-166">[Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) özelliğini veya [List. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) işlevini kullanarak bir listenin kuyruğunu erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8419-166">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="c8419-167">Dizine göre bir öğe bulmak için [List. nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8419-167">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="c8419-168">`List.nth`listede yer geçer.</span><span class="sxs-lookup"><span data-stu-id="c8419-168">`List.nth` traverses the list.</span></span> <span data-ttu-id="c8419-169">Bu nedenle, O (*n*).</span><span class="sxs-lookup"><span data-stu-id="c8419-169">Therefore, it is O(*n*).</span></span> <span data-ttu-id="c8419-170">Kodunuz `List.nth` sıklıkla kullanılıyorsa, bir liste yerine bir dizi kullanmayı düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8419-170">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="c8419-171">Dizilerde öğe erişimi O (1).</span><span class="sxs-lookup"><span data-stu-id="c8419-171">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="c8419-172">Listelerde Boole Işlemleri</span><span class="sxs-lookup"><span data-stu-id="c8419-172">Boolean Operations on Lists</span></span>

<span data-ttu-id="c8419-173">[List. IsEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) işlevi bir listenin herhangi bir öğeye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c8419-173">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="c8419-174">[List. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) işlevi bir listenin öğelerine Boole testi uygular ve `true` herhangi bir öğe, testi karşılıyorsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8419-174">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="c8419-175">[List. exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) benzerdir ancak iki listede ardışık öğe çiftlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="c8419-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="c8419-176">Aşağıdaki kod öğesinin kullanımını gösterir `List.exists` .</span><span class="sxs-lookup"><span data-stu-id="c8419-176">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="c8419-177">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-177">The output is as follows:</span></span>

```console
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="c8419-178">Aşağıdaki örnek öğesinin kullanımını gösterir `List.exists2` .</span><span class="sxs-lookup"><span data-stu-id="c8419-178">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="c8419-179">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-179">The output is as follows:</span></span>

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="c8419-180">List [. forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) ' i kullanarak bir listedeki tüm öğelerin bir koşula uyup uymadığını test etmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="c8419-180">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="c8419-181">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-181">The output is as follows:</span></span>

```console
true
false
```

<span data-ttu-id="c8419-182">Benzer şekilde, [List. forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) , iki liste içindeki karşılık gelen konumlarda bulunan tüm öğelerin her bir öğe çiftini Içeren bir Boolean ifade karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c8419-182">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="c8419-183">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-183">The output is as follows:</span></span>

```console
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="c8419-184">Listelerde sıralama Işlemleri</span><span class="sxs-lookup"><span data-stu-id="c8419-184">Sort Operations on Lists</span></span>

<span data-ttu-id="c8419-185">[List. Sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List. sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)ve [List. sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) işlevleri sıralama listeleri.</span><span class="sxs-lookup"><span data-stu-id="c8419-185">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="c8419-186">Sıralama işlevi, bu üç işlevden hangisini kullanacağınızı belirler.</span><span class="sxs-lookup"><span data-stu-id="c8419-186">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="c8419-187">`List.sort`Varsayılan genel karşılaştırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8419-187">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="c8419-188">Genel karşılaştırma, değerleri karşılaştırmak için genel karşılaştırma işlevini temel alan genel işleçleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8419-188">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="c8419-189">Basit sayısal türler, tanımlama grupları, kayıtlar, ayırt edici birleşimler, listeler, diziler ve uygulayan herhangi bir tür gibi çok sayıda öğe türü ile verimli bir şekilde çalışmaktadır `System.IComparable` .</span><span class="sxs-lookup"><span data-stu-id="c8419-189">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="c8419-190">Uygulayan türler için `System.IComparable` , genel karşılaştırma `System.IComparable.CompareTo()` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8419-190">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="c8419-191">Genel karşılaştırma dizelerle de birlikte çalışarak, ancak kültüre bağımsız bir sıralama düzeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8419-191">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="c8419-192">Genel karşılaştırma, işlev türleri gibi desteklenmeyen türlerde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8419-192">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="c8419-193">Ayrıca, varsayılan genel karşılaştırmanın performansı, küçük yapılandırılmış türler için en iyisidir; sıklıkla karşılaştırılması ve sıralanması gereken daha büyük yapılandırılmış türler için, `System.IComparable` yöntemini uygulamayı ve verimli bir uygulama sağlamayı düşünün `System.IComparable.CompareTo()` .</span><span class="sxs-lookup"><span data-stu-id="c8419-193">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="c8419-194">`List.sortBy`sıralama ölçütü olarak kullanılan bir değer döndüren bir işlev alır ve bir `List.sortWith` karşılaştırma işlevini bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="c8419-194">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="c8419-195">Bu ikinci iki işlev, karşılaştırmayı desteklemeyen türlerle çalışırken ya da karşılaştırma, kültüre duyarlı dizeler söz konusu olduğunda olduğu gibi daha karmaşık karşılaştırma semantiği gerektirdiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c8419-195">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="c8419-196">Aşağıdaki örnek öğesinin kullanımını gösterir `List.sort` .</span><span class="sxs-lookup"><span data-stu-id="c8419-196">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="c8419-197">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-197">The output is as follows:</span></span>

```console
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="c8419-198">Aşağıdaki örnek öğesinin kullanımını gösterir `List.sortBy` .</span><span class="sxs-lookup"><span data-stu-id="c8419-198">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="c8419-199">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-199">The output is as follows:</span></span>

```console
[1; -2; 4; 5; 8]
```

<span data-ttu-id="c8419-200">Sonraki örnek öğesinin kullanımını gösterir `List.sortWith` .</span><span class="sxs-lookup"><span data-stu-id="c8419-200">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="c8419-201">Bu örnekte, özel karşılaştırma işlevi öncelikle bir `compareWidgets` özel türün bir alanını ve ardından ilk alanın değerleri eşitse başka bir değeri karşılaştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8419-201">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="c8419-202">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-202">The output is as follows:</span></span>

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="c8419-203">Listelerde arama Işlemleri</span><span class="sxs-lookup"><span data-stu-id="c8419-203">Search Operations on Lists</span></span>

<span data-ttu-id="c8419-204">Listeler için çok sayıda arama işlemi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c8419-204">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="c8419-205">En basit, [List. Find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), belirli bir koşulla eşleşen ilk öğeyi bulmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8419-205">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="c8419-206">Aşağıdaki kod örneği, `List.find` bir listede 5 ' e bölünebilen ilk sayıyı bulmak için kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8419-206">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="c8419-207">Sonuç 5 ' tir.</span><span class="sxs-lookup"><span data-stu-id="c8419-207">The result is 5.</span></span>

<span data-ttu-id="c8419-208">Öğelerin önce dönüştürülmesi gerekiyorsa, bir seçenek döndüren bir işlevi alan [List. Pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2)çağırın ve olan ilk seçenek değerini arar `Some(x)` .</span><span class="sxs-lookup"><span data-stu-id="c8419-208">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="c8419-209">Öğesini döndürmek yerine `List.pick` sonucunu döndürür `x` .</span><span class="sxs-lookup"><span data-stu-id="c8419-209">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="c8419-210">Eşleşen bir öğe bulunamazsa, `List.pick` oluşturur `System.Collections.Generic.KeyNotFoundException` .</span><span class="sxs-lookup"><span data-stu-id="c8419-210">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="c8419-211">Aşağıdaki kod öğesinin kullanımını gösterir `List.pick` .</span><span class="sxs-lookup"><span data-stu-id="c8419-211">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="c8419-212">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-212">The output is as follows:</span></span>

```console
"b"
```

<span data-ttu-id="c8419-213">Başka bir arama işlemleri grubu olan [List. tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) ve related işlevleri, bir seçenek değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8419-213">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="c8419-214">İşlevi, böyle bir öğe varsa bir `List.tryFind` koşulu karşılayan bir listenin ilk öğesini döndürür, ancak değilse seçenek değeri `None` .</span><span class="sxs-lookup"><span data-stu-id="c8419-214">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="c8419-215">Çeşitleme [listesi. tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) , öğenin kendisi yerine, varsa, öğesinin dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8419-215">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="c8419-216">Bu işlevler aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c8419-216">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="c8419-217">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-217">The output is as follows:</span></span>

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="c8419-218">Listelerde aritmetik Işlemler</span><span class="sxs-lookup"><span data-stu-id="c8419-218">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="c8419-219">Toplam ve ortalama gibi yaygın aritmetik işlemler [liste modülüne](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)yerleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c8419-219">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="c8419-220">[List. Sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9)ile çalışmak için liste öğesi türü `+` işleci desteklemelidir ve sıfır değerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8419-220">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="c8419-221">Tüm yerleşik aritmetik türler bu koşulları karşılar.</span><span class="sxs-lookup"><span data-stu-id="c8419-221">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="c8419-222">[List. Average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1)ile çalışmak için, öğe türü, bir geri kalanı olmadan bir bölüm desteklemelidir, bu da integral türlerini dışlar, ancak kayan nokta türlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c8419-222">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="c8419-223">[List. sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) ve [List. averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) işlevleri bir işlevi parametre olarak alır ve bu işlevin sonuçları Sum veya Average değerlerini hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8419-223">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="c8419-224">Aşağıdaki kod,, ve kullanımını gösterir `List.sum` `List.sumBy` `List.average` .</span><span class="sxs-lookup"><span data-stu-id="c8419-224">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="c8419-225">Çıktı `1.000000` .</span><span class="sxs-lookup"><span data-stu-id="c8419-225">The output is `1.000000`.</span></span>

<span data-ttu-id="c8419-226">Aşağıdaki kod öğesinin kullanımını gösterir `List.averageBy` .</span><span class="sxs-lookup"><span data-stu-id="c8419-226">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="c8419-227">Çıktı `5.5` .</span><span class="sxs-lookup"><span data-stu-id="c8419-227">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="c8419-228">Listeler ve tanımlama grupları</span><span class="sxs-lookup"><span data-stu-id="c8419-228">Lists and Tuples</span></span>

<span data-ttu-id="c8419-229">Tanımlama gruplarını içeren listeler, zip ve unzip işlevleri tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c8419-229">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="c8419-230">Bu işlevler, tek değerlerden oluşan iki listeyi tek bir tanımlama grubu içinde birleştirir veya bir tanımlama grubu listesini tek değerlerden oluşan iki listeye ayırır.</span><span class="sxs-lookup"><span data-stu-id="c8419-230">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="c8419-231">En basit [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) işlevi, tek öğelerin iki listesini alır ve dizi kümesi çiftlerinin tek bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8419-231">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="c8419-232">Farklı bir sürüm olan [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), tek öğelerin üç listesini alır ve üç öğesi olan bir tanımlama grubu listesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8419-232">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="c8419-233">Aşağıdaki kod örneği öğesinin kullanımını gösterir `List.zip` .</span><span class="sxs-lookup"><span data-stu-id="c8419-233">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="c8419-234">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-234">The output is as follows:</span></span>

```console
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="c8419-235">Aşağıdaki kod örneği öğesinin kullanımını gösterir `List.zip3` .</span><span class="sxs-lookup"><span data-stu-id="c8419-235">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="c8419-236">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-236">The output is as follows:</span></span>

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="c8419-237">Karşılık gelen unzip sürümleri, [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) ve [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), tanımlama grubu ve dönüş listelerinin listesini alır, burada ilk liste her bir tanımlama grubunda ilk olan tüm öğeleri içerir ve ikinci liste her bir tanımlama grubunun ikinci öğesini içerir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="c8419-237">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="c8419-238">Aşağıdaki kod örneği [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8419-238">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="c8419-239">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-239">The output is as follows:</span></span>

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="c8419-240">Aşağıdaki kod örneği [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8419-240">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="c8419-241">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-241">The output is as follows:</span></span>

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="c8419-242">Liste öğelerinde çalışma</span><span class="sxs-lookup"><span data-stu-id="c8419-242">Operating on List Elements</span></span>

<span data-ttu-id="c8419-243">F #, liste öğelerinde çeşitli işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="c8419-243">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="c8419-244">Listenin her öğesinde bir işlevi çağırmanızı sağlayan en basit [List. iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f).</span><span class="sxs-lookup"><span data-stu-id="c8419-244">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="c8419-245">Her bir öğenin dizininin her öğe için çağrılan işleve bir bağımsız değişken olarak geçirilmesi ve ve işlevlerinin bir birleşimi [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60)olan List. iteri2 ' yi, bu iki listenin öğelerinde bir işlem gerçekleştirmenize olanak sağlayan varyasyonlar Include [List. iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40) `List.iter` [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c) `List.iter2` `List.iteri` .</span><span class="sxs-lookup"><span data-stu-id="c8419-245">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="c8419-246">Aşağıdaki kod örneği bu işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8419-246">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="c8419-247">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-247">The output is as follows:</span></span>

```console
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

<span data-ttu-id="c8419-248">Liste öğelerini dönüştüren başka bir sık kullanılan işlev List [. Map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)olur ve bu, bir listedeki her öğeye bir işlev uygulamanıza ve tüm sonuçların yeni bir listeye yerleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8419-248">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="c8419-249">[List. map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) ve [List. map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) birden çok liste alan değişimlerdir.</span><span class="sxs-lookup"><span data-stu-id="c8419-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="c8419-250">[List. mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) ve [List. mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49)öğesini de kullanabilirsiniz. Buna ek olarak, işlevine her öğenin dizinini geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8419-250">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="c8419-251">Ve arasındaki tek fark `List.mapi2` , `List.mapi` `List.mapi2` iki liste ile birlikte çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="c8419-251">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="c8419-252">Aşağıdaki örnekte [List. Map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c8419-252">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="c8419-253">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-253">The output is as follows:</span></span>

```console
[2; 3; 4]
```

<span data-ttu-id="c8419-254">Aşağıdaki örnek öğesinin kullanımını gösterir `List.map2` .</span><span class="sxs-lookup"><span data-stu-id="c8419-254">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="c8419-255">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-255">The output is as follows:</span></span>

```console
[5; 7; 9]
```

<span data-ttu-id="c8419-256">Aşağıdaki örnek öğesinin kullanımını gösterir `List.map3` .</span><span class="sxs-lookup"><span data-stu-id="c8419-256">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="c8419-257">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-257">The output is as follows:</span></span>

```console
[7; 10; 13]
```

<span data-ttu-id="c8419-258">Aşağıdaki örnek öğesinin kullanımını gösterir `List.mapi` .</span><span class="sxs-lookup"><span data-stu-id="c8419-258">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="c8419-259">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-259">The output is as follows:</span></span>

```console
[1; 3; 5]
```

<span data-ttu-id="c8419-260">Aşağıdaki örnek öğesinin kullanımını gösterir `List.mapi2` .</span><span class="sxs-lookup"><span data-stu-id="c8419-260">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="c8419-261">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-261">The output is as follows:</span></span>

```console
[0; 7; 18]
```

<span data-ttu-id="c8419-262">[List. Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) , `List.map` her öğe bir liste ürettiğinden ve tüm bu listelerin son bir liste ile bitiştirildiği durumlar haricinde gibidir.</span><span class="sxs-lookup"><span data-stu-id="c8419-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="c8419-263">Aşağıdaki kodda, listenin her bir öğesi üç sayı üretir.</span><span class="sxs-lookup"><span data-stu-id="c8419-263">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="c8419-264">Bunların hepsi tek bir listede toplanır.</span><span class="sxs-lookup"><span data-stu-id="c8419-264">These are all collected into one list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="c8419-265">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-265">The output is as follows:</span></span>

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="c8419-266">Ayrıca, Boolean koşulunu alan ve yalnızca verilen koşulu karşılayan öğelerden oluşan yeni bir liste üreten [List. Filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248)öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8419-266">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="c8419-267">Elde edilen liste `[2; 4; 6]` .</span><span class="sxs-lookup"><span data-stu-id="c8419-267">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="c8419-268">Map ve Filter, [List.](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) Select birleşimi, öğeleri aynı anda dönüştürmenizi ve seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8419-268">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="c8419-269">`List.choose`bir listedeki her öğeye bir seçenek döndüren bir işlev uygular ve işlev seçenek değerini döndürdüğünde öğelerin sonuçlarının yeni bir listesini döndürür `Some` .</span><span class="sxs-lookup"><span data-stu-id="c8419-269">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="c8419-270">Aşağıdaki kod, `List.choose` bir sözcük listesinden büyük harfli sözcükler seçmek için kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8419-270">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="c8419-271">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8419-271">The output is as follows:</span></span>

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="c8419-272">Birden çok liste üzerinde çalışma</span><span class="sxs-lookup"><span data-stu-id="c8419-272">Operating on Multiple Lists</span></span>

<span data-ttu-id="c8419-273">Listeler birlikte birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c8419-273">Lists can be joined together.</span></span> <span data-ttu-id="c8419-274">İki listeyi tek tek birleştirmek için [List. Append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426)kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8419-274">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="c8419-275">İkiden fazla listeyi birleştirmek için [List. Concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c)kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8419-275">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="c8419-276">Katlama ve tarama Işlemleri</span><span class="sxs-lookup"><span data-stu-id="c8419-276">Fold and Scan Operations</span></span>

<span data-ttu-id="c8419-277">Bazı liste işlemleri liste öğeleri arasında bağımlılıkları kapsar.</span><span class="sxs-lookup"><span data-stu-id="c8419-277">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="c8419-278">Katlama ve tarama işlemleri, `List.iter` `List.map` her öğe üzerinde bir işlevi çağırmanıza benzer ancak bu işlemler, hesaplama aracılığıyla bilgi taşıyan bir ek parametre sağlar. *accumulator*</span><span class="sxs-lookup"><span data-stu-id="c8419-278">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="c8419-279">`List.fold`Bir liste üzerinde hesaplama gerçekleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8419-279">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="c8419-280">Aşağıdaki kod örneği, çeşitli işlemleri gerçekleştirmek için [List. Fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8419-280">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="c8419-281">Listeye çapraz ve Biriktirici, `acc` Hesaplama ilerledikçe geçen bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="c8419-281">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="c8419-282">İlk bağımsız değişken, biriktiriciden ve List öğesini alır ve bu liste öğesi için hesaplamanın ara sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8419-282">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="c8419-283">İkinci bağımsız değişken, biriktiricinin ilk değeridir.</span><span class="sxs-lookup"><span data-stu-id="c8419-283">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="c8419-284">İşlev adında basamak olan bu işlevlerin sürümleri birden fazla listede çalışır.</span><span class="sxs-lookup"><span data-stu-id="c8419-284">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="c8419-285">Örneğin, [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) iki listede hesaplamalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c8419-285">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="c8419-286">Aşağıdaki örnek öğesinin kullanımını gösterir `List.fold2` .</span><span class="sxs-lookup"><span data-stu-id="c8419-286">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="c8419-287">`List.fold`ve [List. Scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) , `List.fold` ek parametrenin son değerini döndüren ' de farklılık gösterir, ancak `List.scan` ek parametrenin ara değerlerinin (son değeri ile birlikte) listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8419-287">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="c8419-288">Bu işlevlerin her biri, listenin geri alındığı sırada ve bağımsız değişkenlerin sırası farklı olan [List. foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7)gibi bir ters çeşitleme içerir.</span><span class="sxs-lookup"><span data-stu-id="c8419-288">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="c8419-289">Ayrıca, `List.fold` ve aynı `List.foldBack` uzunlukta iki liste alan Çeşitlemeler, [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) ve [List. foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2)' i de vardır.</span><span class="sxs-lookup"><span data-stu-id="c8419-289">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="c8419-290">Her öğe üzerinde yürütülen işlev, bazı eylemler gerçekleştirmek için her iki listedeki ilgili öğeleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c8419-290">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="c8419-291">Aşağıdaki örnekte olduğu gibi, iki listenin öğe türleri farklı olabilir. Bu, bir liste bir banka hesabı için işlem tutarlarını içerir ve diğer liste işlemin türünü içerir: depozito veya çekme al.</span><span class="sxs-lookup"><span data-stu-id="c8419-291">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="c8419-292">Toplama gibi bir hesaplama için, `List.fold` `List.foldBack` sonuç çapraz geçiş sırasına bağlı olmadığından aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c8419-292">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="c8419-293">Aşağıdaki örnekte, `List.foldBack` bir listedeki öğeleri eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8419-293">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="c8419-294">Aşağıdaki örnek, banka hesabı örneğine geri döner.</span><span class="sxs-lookup"><span data-stu-id="c8419-294">The following example returns to the bank account example.</span></span> <span data-ttu-id="c8419-295">Yeni bir işlem türü eklendiğinde bu kez bir vade farkının hesaplanması.</span><span class="sxs-lookup"><span data-stu-id="c8419-295">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="c8419-296">Bitiş bakiyesi artık işlem sırasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c8419-296">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="c8419-297">İşlev [listesi. küçültme](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) biraz benzer ve aynı şekilde, `List.fold` `List.scan` ayrı bir Biriktiricinin etrafında geçiş yerine `List.reduce` iki bağımsız değişken alan bir işlev alır, ancak bu bağımsız değişkenlerden biri yalnızca bir değil, bu bağımsız değişkenlerden biri de, hesaplamanın ara sonucunu depoladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c8419-297">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="c8419-298">`List.reduce`ilk iki liste öğesinde çalışmaya başlar ve sonra işlemin sonucunu Next öğesiyle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8419-298">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="c8419-299">Kendi türüne sahip ayrı bir biriktiricidir çünkü, `List.reduce` `List.fold` yalnızca biriktiricidir ve öğe türü aynı türde olduğunda ' nin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8419-299">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="c8419-300">Aşağıdaki kod öğesinin kullanımını gösterir `List.reduce` .</span><span class="sxs-lookup"><span data-stu-id="c8419-300">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="c8419-301">`List.reduce`Belirtilen listede öğe yoksa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8419-301">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="c8419-302">Aşağıdaki kodda, lambda ifadesine yapılan ilk çağrıya 2 ve 4 bağımsız değişkenleri verilir ve 6, sonraki çağrıya ise 6 ve 10 bağımsız değişkenleri verilir, dolayısıyla sonuç 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="c8419-302">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="c8419-303">Listeler ve diğer koleksiyon türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c8419-303">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="c8419-304">`List`Modülü, hem sıralara hem de dizilere dönüştürme için işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8419-304">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="c8419-305">Bir diziye veya bir diziye dönüştürmek için [List. toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) veya [List. ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0)kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8419-305">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="c8419-306">Bir diziye veya bir diziyi dönüştürmek için [List. ToArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) veya [List. ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032)kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8419-306">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="c8419-307">Ek Işlemler</span><span class="sxs-lookup"><span data-stu-id="c8419-307">Additional Operations</span></span>

<span data-ttu-id="c8419-308">Listelerle ilgili ek işlemler hakkında daha fazla bilgi için bkz. kitaplık başvurusu konu [koleksiyonları. List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="c8419-308">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8419-309">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8419-309">See also</span></span>

- [<span data-ttu-id="c8419-310">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="c8419-310">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c8419-311">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="c8419-311">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="c8419-312">Diziler</span><span class="sxs-lookup"><span data-stu-id="c8419-312">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="c8419-313">Diziler</span><span class="sxs-lookup"><span data-stu-id="c8419-313">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="c8419-314">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c8419-314">Options</span></span>](options.md)
