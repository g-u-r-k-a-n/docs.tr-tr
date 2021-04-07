---
description: Fixed ekstresi-C# başvurusu
title: Fixed ekstresi-C# başvurusu
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 2af9c4311e8326d6df933ec5d4c38354fe021e5c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497573"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="694b6-103">fixed Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="694b6-103">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="694b6-104">`fixed`İfade, çöp toplayıcısının taşınabilir bir değişkenin yerini değiştirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="694b6-104">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="694b6-105">`fixed`Deyime yalnızca [güvenli olmayan](unsafe.md) bir bağlamda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="694b6-105">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="694b6-106">`fixed` [Sabit boyutlu arabellekler](../unsafe-code.md#fixed-size-buffers)oluşturmak için anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="694b6-106">You can also use the `fixed` keyword to create [fixed size buffers](../unsafe-code.md#fixed-size-buffers).</span></span>

<span data-ttu-id="694b6-107">`fixed`İfade, yönetilen bir değişkene bir işaretçi ayarlar ve deyimin yürütülmesi sırasında bu değişkene "PIN" koyar.</span><span class="sxs-lookup"><span data-stu-id="694b6-107">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="694b6-108">Taşınabilir olarak yönetilen değişkenlere yönelik işaretçiler yalnızca bir bağlamda yararlıdır `fixed` .</span><span class="sxs-lookup"><span data-stu-id="694b6-108">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="694b6-109">Bağlam olmadan `fixed` çöp toplama, değişkenleri tahmin edilmemiş şekilde yeniden konumlandırmaya yönelik olabilir.</span><span class="sxs-lookup"><span data-stu-id="694b6-109">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="694b6-110">C# derleyicisi yalnızca bir ifadede yönetilen değişkene bir işaretçi atamanızı sağlar `fixed` .</span><span class="sxs-lookup"><span data-stu-id="694b6-110">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#1)]

<span data-ttu-id="694b6-111">Bir diziyi, dizeyi, sabit boyutlu arabelleği veya bir değişkenin adresini kullanarak bir işaretçiyi başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="694b6-111">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="694b6-112">Aşağıdaki örnek, değişken adreslerinin, dizilerin ve dizelerin kullanımını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="694b6-112">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](snippets/FixedKeywordExamples.cs#2)]

<span data-ttu-id="694b6-113">C# 7,3 ' den başlayarak, `fixed` ifade diziler, dizeler, sabit boyutlu arabellekler veya yönetilmeyen değişkenlerin ötesinde ek türler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="694b6-113">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="694b6-114">Adlı bir yöntemi uygulayan herhangi bir tür `GetPinnableReference` sabitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="694b6-114">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="694b6-115">, `GetPinnableReference` `ref` [Yönetilmeyen türde](../builtin-types/unmanaged-types.md)bir değişken döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="694b6-115">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="694b6-116">.Net <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> Core 2,0 ' de sunulan .net türleri bu düzenin kullanımını ve sabitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="694b6-116">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="694b6-117">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="694b6-117">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="694b6-118">Bu modele katılması gereken türler oluşturuyorsanız, bu <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> düzenin uygulanması örneği için bkz..</span><span class="sxs-lookup"><span data-stu-id="694b6-118">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="694b6-119">Aynı türde olan birden çok işaretçi tek bir bildirimde başlatılabilir:</span><span class="sxs-lookup"><span data-stu-id="694b6-119">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="694b6-120">Farklı türlerin işaretçilerini başlatmak için `fixed` Aşağıdaki örnekte gösterildiği gibi deyimlerini iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="694b6-120">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](snippets/FixedKeywordExamples.cs#3)]

<span data-ttu-id="694b6-121">Deyimdeki kod yürütüldükten sonra, sabitlenmiş değişkenler sabitlenir ve çöp toplamaya tabidir.</span><span class="sxs-lookup"><span data-stu-id="694b6-121">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="694b6-122">Bu nedenle, bu değişkenleri deyimin dışında işaret etmez `fixed` .</span><span class="sxs-lookup"><span data-stu-id="694b6-122">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="694b6-123">Bildiriminde belirtilen değişkenler, `fixed` Bu ifadeye göre kapsamlandırılır ve daha kolay hale getirir:</span><span class="sxs-lookup"><span data-stu-id="694b6-123">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="694b6-124">`fixed`Deyimlerde başlatılan işaretçiler salt okunur değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="694b6-124">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="694b6-125">İşaretçi değerini değiştirmek istiyorsanız, ikinci bir işaretçi değişkeni bildirmeniz ve bunu değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="694b6-125">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="694b6-126">İfadede belirtilen değişken `fixed` değiştirilemez:</span><span class="sxs-lookup"><span data-stu-id="694b6-126">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="694b6-127">Yığın üzerinde bellek ayırabilirsiniz, burada çöp toplamaya tabi değildir ve bu nedenle sabitlenmiş olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="694b6-127">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="694b6-128">Bunu yapmak için bir [ `stackalloc` ifade](../operators/stackalloc.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="694b6-128">To do that, use a [`stackalloc` expression](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="694b6-129">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="694b6-129">C# language specification</span></span>

<span data-ttu-id="694b6-130">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [fixed deyimin](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="694b6-130">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="694b6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="694b6-131">See also</span></span>

- [<span data-ttu-id="694b6-132">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="694b6-132">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="694b6-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="694b6-133">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="694b6-134">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="694b6-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="694b6-135">olmayabilecek</span><span class="sxs-lookup"><span data-stu-id="694b6-135">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="694b6-136">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="694b6-136">Pointer types</span></span>](../unsafe-code.md#pointer-types)
- [<span data-ttu-id="694b6-137">Sabit boyutlu arabellekler</span><span class="sxs-lookup"><span data-stu-id="694b6-137">Fixed Size Buffers</span></span>](../unsafe-code.md#fixed-size-buffers)
