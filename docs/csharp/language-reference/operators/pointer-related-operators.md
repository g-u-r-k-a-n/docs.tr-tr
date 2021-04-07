---
title: İşaretçiden ilgili işleçler-C# başvurusu
description: İşaretçilerle çalışırken kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 22cd87a62c92dbfacd0b8ebbdd5cbafb92da73ca
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497365"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="dc7c5-103">İşaretçi ile ilgili işleçler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dc7c5-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="dc7c5-104">İşaretçilerle çalışmak için aşağıdaki işleçleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dc7c5-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="dc7c5-105">Birli [ `&` (Adres-of)](#address-of-operator-) işleci: bir değişkenin adresini almak için</span><span class="sxs-lookup"><span data-stu-id="dc7c5-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="dc7c5-106">Birli [ `*` (işaretçi yöneltme)](#pointer-indirection-operator-) işleci: bir işaretçiye işaret eden değişkeni almak için</span><span class="sxs-lookup"><span data-stu-id="dc7c5-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="dc7c5-107">[ `->` (Üye erişimi)](#pointer-member-access-operator--) ve [ `[]` (öğe erişimi)](#pointer-element-access-operator-) işleçleri</span><span class="sxs-lookup"><span data-stu-id="dc7c5-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="dc7c5-108">Aritmetik işleçler [ `+` , `-` ,, `++` ve `--` ](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="dc7c5-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="dc7c5-109">Karşılaştırma işleçleri,,,, [ `==` `!=` `<` `>` `<=` ve `>=` ](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="dc7c5-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="dc7c5-110">İşaretçi türleri hakkında bilgi için bkz. [işaretçi türleri](../unsafe-code.md#pointer-types).</span><span class="sxs-lookup"><span data-stu-id="dc7c5-110">For information about pointer types, see [Pointer types](../unsafe-code.md#pointer-types).</span></span>

> [!NOTE]
> <span data-ttu-id="dc7c5-111">İşaretçilerle herhangi bir işlem [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="dc7c5-112">Güvenli olmayan bloklar içeren kodun [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks) derleyici seçeneğiyle derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-112">The code that contains unsafe blocks must be compiled with the [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks) compiler option.</span></span>

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a> <span data-ttu-id="dc7c5-113">Address-of işleci &amp;</span><span class="sxs-lookup"><span data-stu-id="dc7c5-113">Address-of operator &amp;</span></span>

<span data-ttu-id="dc7c5-114">Birli `&` işleç, işleneninin adresini döndürür:</span><span class="sxs-lookup"><span data-stu-id="dc7c5-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](snippets/shared/PointerOperators.cs#AddressOf)]

<span data-ttu-id="dc7c5-115">`&`İşlecin işleneni sabit bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="dc7c5-116">*Sabit* değişkenler, [Atık toplayıcısının](../../../standard/garbage-collection/index.md)işleminden etkilenmeyen depolama konumlarında bulunan değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="dc7c5-117">Yukarıdaki örnekte, yerel değişken `number` yığında bulunduğundan sabit bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="dc7c5-118">Çöp toplayıcısından etkilenebilecek (örneğin, yeniden konumlandırılan) depolama konumlarında bulunan değişkenler *Taşınabilir* değişkenler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="dc7c5-119">Nesne alanları ve dizi öğeleri taşınabilir değişkenlerin örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="dc7c5-120">Taşınabilir bir değişkenin adresini, bir [ `fixed` ifadesiyle](../keywords/fixed-statement.md)"düzelmiyor" veya "sabitle" yaparsanız alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-120">You can get the address of a movable variable if you "fix", or "pin", it with a [`fixed` statement](../keywords/fixed-statement.md).</span></span> <span data-ttu-id="dc7c5-121">Alınan adres yalnızca bir deyimin bloğunun içinde geçerlidir `fixed` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-121">The obtained address is valid only inside the block of a `fixed` statement.</span></span> <span data-ttu-id="dc7c5-122">Aşağıdaki örnek, bir `fixed` deyimin ve işlecin nasıl kullanılacağını gösterir `&` :</span><span class="sxs-lookup"><span data-stu-id="dc7c5-122">The following example shows how to use a `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](snippets/shared/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="dc7c5-123">Bir sabit veya bir değerin adresini alamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="dc7c5-124">Sabit ve taşınabilir değişkenler hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sabit ve taşınabilir değişkenler](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="dc7c5-125">Binary `&` işleci, Boolean işlenenlerinin [mantıksal ve](boolean-logical-operators.md#logical-and-operator-) işlecini ya da tam sayı işlenenlerinin [bit düzeyinde mantıksal ve](bitwise-and-shift-operators.md#logical-and-operator-) işlecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="dc7c5-126">İşaretçi yöneltme işleci \*</span><span class="sxs-lookup"><span data-stu-id="dc7c5-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="dc7c5-127">Birli işaretçi yöneltme işleci, `*` işleneninin gösterdiği değişkeni edinir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="dc7c5-128">Başvuru operatörü olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="dc7c5-129">`*`İşlecin işleneni bir işaretçi türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](snippets/shared/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="dc7c5-130">`*`İşleci türündeki bir ifadeye uygulayamazsınız `void*` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="dc7c5-131">İkili `*` işleç, sayısal işlenenlerinin [çarpımını](arithmetic-operators.md#multiplication-operator-) hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="dc7c5-132">İşaretçi üyesi erişim işleci-></span><span class="sxs-lookup"><span data-stu-id="dc7c5-132">Pointer member access operator -></span></span>

<span data-ttu-id="dc7c5-133">`->`İşleci [işaretçi yöneltme](#pointer-indirection-operator-) ve [üye erişimini](member-access-operators.md#member-access-expression-)birleştirir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="dc7c5-134">Diğer bir deyişle, `x` türünde bir işaretçisiyse `T*` ve türünün erişilebilir bir üyesi ise, `y` `T` formun bir ifadesi</span><span class="sxs-lookup"><span data-stu-id="dc7c5-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of type `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="dc7c5-135">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="dc7c5-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="dc7c5-136">Aşağıdaki örnek işlecinin kullanımını gösterir `->` :</span><span class="sxs-lookup"><span data-stu-id="dc7c5-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](snippets/shared/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="dc7c5-137">`->`İşleci türündeki bir ifadeye uygulayamazsınız `void*` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="dc7c5-138">İşaretçi öğesi erişim işleci []</span><span class="sxs-lookup"><span data-stu-id="dc7c5-138">Pointer element access operator []</span></span>

<span data-ttu-id="dc7c5-139">İşaretçi türünün bir ifadesi için `p` , formun işaretçi öğesi erişimi `p[n]` olarak değerlendirilir `*(p + n)` , burada,, veya ' a `n` örtülü olarak dönüştürülebilir bir tür olması gerekir `int` `uint` `long` `ulong` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="dc7c5-140">İşaretçilerle işlecin davranışı hakkında daha fazla bilgi için `+` , [bir tam sayı değerinin bir Işaretçi bölümüne eklenmesi veya çıkarılması](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="dc7c5-141">Aşağıdaki örnek, bir işaretçi ve işleçle dizi öğelerine nasıl erişileceğini göstermektedir `[]` :</span><span class="sxs-lookup"><span data-stu-id="dc7c5-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](snippets/shared/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="dc7c5-142">Yukarıdaki örnekte, bir [ `stackalloc` ifade](stackalloc.md) yığında bir bellek bloğu ayırır.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-142">In the preceding example, a [`stackalloc` expression](stackalloc.md) allocates a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="dc7c5-143">İşaretçi öğesi erişim işleci, sınır dışı hataları denetlemez.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="dc7c5-144">`[]`Türünde bir ifadeyle işaretçi öğesi erişimi için kullanamazsınız `void*` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="dc7c5-145">`[]` [Dizi öğesi veya Dizin Oluşturucu erişimi](member-access-operators.md#indexer-operator-)için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-145">You can also use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="dc7c5-146">İşaretçi aritmetik işleçleri</span><span class="sxs-lookup"><span data-stu-id="dc7c5-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="dc7c5-147">İşaretçilerle aşağıdaki aritmetik işlemleri gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dc7c5-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="dc7c5-148">Bir işaretçiye veya işaretçiden tamsayı değer ekleme veya çıkarma</span><span class="sxs-lookup"><span data-stu-id="dc7c5-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="dc7c5-149">İki işaretçileri çıkar</span><span class="sxs-lookup"><span data-stu-id="dc7c5-149">Subtract two pointers</span></span>
- <span data-ttu-id="dc7c5-150">Bir işaretçiyi artırma veya azaltma</span><span class="sxs-lookup"><span data-stu-id="dc7c5-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="dc7c5-151">Bu işlemleri türündeki işaretçilerle gerçekleştiremezsiniz `void*` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="dc7c5-152">Sayısal türlerle desteklenen aritmetik işlemler hakkında daha fazla bilgi için bkz. [Aritmetik işleçler](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc7c5-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="dc7c5-153">Bir işaretçiye veya bir işaretçiye tamsayı değer ekleme veya çıkarma</span><span class="sxs-lookup"><span data-stu-id="dc7c5-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="dc7c5-154">Türünde bir işaretçi `p` ve bir `T*` türün bir ifadesi için `n` örtük olarak dönüştürülebilir,, `int` `uint` `long` , veya `ulong` , toplama ve çıkarma için aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="dc7c5-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="dc7c5-155">Hem hem de `p + n` `n + p` ifadeleri, `T*` tarafından verilen adrese eklenmesinin sonucu olan türünde bir işaretçi üretir `n * sizeof(T)` `p` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="dc7c5-156">`p - n`İfade, `T*` `n * sizeof(T)` tarafından verilen adresten çıkarılmasına neden olan türde bir işaretçi oluşturur `p` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="dc7c5-157">[ `sizeof` İşleci](sizeof.md) bir türün boyutunu bayt cinsinden edinir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="dc7c5-158">Aşağıdaki örnek, `+` bir işaretçi ile işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="dc7c5-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](snippets/shared/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="dc7c5-159">İşaretçi çıkarması</span><span class="sxs-lookup"><span data-stu-id="dc7c5-159">Pointer subtraction</span></span>

<span data-ttu-id="dc7c5-160">İki işaretçi `p1` ve `p2` türü için `T*` , ifadesi `p1 - p2` tarafından verilen `p1` ve `p2` tarafından bölünen adresler arasındaki farkı üretir `sizeof(T)` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="dc7c5-161">Sonucun türü `long` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-161">The type of the result is `long`.</span></span> <span data-ttu-id="dc7c5-162">Diğer bir deyişle, `p1 - p2` olarak hesaplanır `((long)(p1) - (long)(p2)) / sizeof(T)` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="dc7c5-163">Aşağıdaki örnekte işaretçi çıkarma gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dc7c5-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](snippets/shared/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="dc7c5-164">İşaretçi artışı ve azaltma</span><span class="sxs-lookup"><span data-stu-id="dc7c5-164">Pointer increment and decrement</span></span>

<span data-ttu-id="dc7c5-165">`++`Artış işleci, işaretçi işleneni 1 [ekler](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="dc7c5-166">`--`Azaltma işleci, 1 işaretçi işlenenden [çıkartır](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="dc7c5-167">İki tür işleç desteklenir: sonek ( `p++` ve `p--` ) ve ön ek ( `++p` ve `--p` ).</span><span class="sxs-lookup"><span data-stu-id="dc7c5-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="dc7c5-168">Ve sonucu, `p++` `p--` `p` işlemden *önceki* değeridir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="dc7c5-169">Ve sonucu, `++p` `--p` `p` işlemden *sonraki* değeridir.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="dc7c5-170">Aşağıdaki örnek, hem sonek hem de önek artırma işleçlerinin davranışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="dc7c5-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](snippets/shared/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="dc7c5-171">İşaretçi karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="dc7c5-171">Pointer comparison operators</span></span>

<span data-ttu-id="dc7c5-172">,,,, `==` `!=` `<` Ve işleçlerini, `>` gibi `<=` `>=` herhangi bir işaretçi türünün işlenenlerini karşılaştırmak için kullanabilirsiniz `void*` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="dc7c5-173">Bu işleçler, iki işlenen tarafından verilen adresleri işaretsiz tamsayılar gibi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="dc7c5-174">Diğer türlerin işlenenleri için bu işleçlerin davranışı hakkında daha fazla bilgi için bkz. [eşitlik işleçleri](equality-operators.md) ve [karşılaştırma işleçleri](comparison-operators.md) makaleleri.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="dc7c5-175">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="dc7c5-175">Operator precedence</span></span>

<span data-ttu-id="dc7c5-176">Aşağıdaki liste, işaretçinin ilgili işleçlerini en yüksek öncelikten en düşüğe başlayarak sıralar:</span><span class="sxs-lookup"><span data-stu-id="dc7c5-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="dc7c5-177">Sonek artırma `x++` ve azaltma `x--` işleçleri ve `->` ve `[]` işleçleri</span><span class="sxs-lookup"><span data-stu-id="dc7c5-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="dc7c5-178">Ön ek artırma `++x` ve azaltma `--x` işleçleri ve `&` ve `*` işleçleri</span><span class="sxs-lookup"><span data-stu-id="dc7c5-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="dc7c5-179">Eklenebilir `+` ve `-` işleçler</span><span class="sxs-lookup"><span data-stu-id="dc7c5-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="dc7c5-180">Karşılaştırma `<` , `>` , `<=` , ve `>=` işleçler</span><span class="sxs-lookup"><span data-stu-id="dc7c5-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="dc7c5-181">Eşitlik `==` ve `!=` işleçler</span><span class="sxs-lookup"><span data-stu-id="dc7c5-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="dc7c5-182">`()`İşleç önceliğine göre uygulanan değerlendirmenin sırasını değiştirmek için parantez ' nu kullanın.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="dc7c5-183">Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için [c# işleçleri](index.md) makalesinin [operatör önceliği](index.md#operator-precedence) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="dc7c5-184">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="dc7c5-184">Operator overloadability</span></span>

<span data-ttu-id="dc7c5-185">Kullanıcı tanımlı bir tür, işaretçiyle ilgili işleçleri,, `&` `*` `->` ve ile aşırı yükleyemez `[]` .</span><span class="sxs-lookup"><span data-stu-id="dc7c5-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dc7c5-186">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="dc7c5-186">C# language specification</span></span>

<span data-ttu-id="dc7c5-187">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="dc7c5-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="dc7c5-188">Sabit ve taşınabilir değişkenler</span><span class="sxs-lookup"><span data-stu-id="dc7c5-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="dc7c5-189">Address-of işleci</span><span class="sxs-lookup"><span data-stu-id="dc7c5-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="dc7c5-190">İşaretçi yöneltme</span><span class="sxs-lookup"><span data-stu-id="dc7c5-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="dc7c5-191">İşaretçi üye erişimi</span><span class="sxs-lookup"><span data-stu-id="dc7c5-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="dc7c5-192">İşaretçi öğesi erişimi</span><span class="sxs-lookup"><span data-stu-id="dc7c5-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="dc7c5-193">İşaretçi aritmetiği</span><span class="sxs-lookup"><span data-stu-id="dc7c5-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="dc7c5-194">İşaretçi artışı ve azaltma</span><span class="sxs-lookup"><span data-stu-id="dc7c5-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="dc7c5-195">İşaretçi karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="dc7c5-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="dc7c5-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc7c5-196">See also</span></span>

- [<span data-ttu-id="dc7c5-197">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="dc7c5-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dc7c5-198">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="dc7c5-198">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="dc7c5-199">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="dc7c5-199">Pointer types</span></span>](../unsafe-code.md#pointer-types)
- [<span data-ttu-id="dc7c5-200">güvenli olmayan anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dc7c5-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="dc7c5-201">Fixed anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="dc7c5-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="dc7c5-202">stackalloc</span><span class="sxs-lookup"><span data-stu-id="dc7c5-202">stackalloc</span></span>](stackalloc.md)
- [<span data-ttu-id="dc7c5-203">sizeof işleci</span><span class="sxs-lookup"><span data-stu-id="dc7c5-203">sizeof operator</span></span>](sizeof.md)
