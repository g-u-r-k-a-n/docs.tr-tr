---
description: "C 'de yerleşik karakter türü hakkında bilgi edinin #"
title: Char türü-C# başvurusu
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1cb40759b81a1fcedcf5962b57d79cf3a64df561
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471882"
---
# <a name="char-c-reference"></a><span data-ttu-id="cfb44-103">Char (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cfb44-103">char (C# reference)</span></span>

<span data-ttu-id="cfb44-104">`char`Type anahtar sözcüğü, <xref:System.Char?displayProperty=nameWithType> BIR Unicode UTF-16 karakteri temsil eden .net yapı türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="cfb44-104">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="cfb44-105">Tür</span><span class="sxs-lookup"><span data-stu-id="cfb44-105">Type</span></span>|<span data-ttu-id="cfb44-106">Aralık</span><span class="sxs-lookup"><span data-stu-id="cfb44-106">Range</span></span>|<span data-ttu-id="cfb44-107">Boyut</span><span class="sxs-lookup"><span data-stu-id="cfb44-107">Size</span></span>|<span data-ttu-id="cfb44-108">.NET türü</span><span class="sxs-lookup"><span data-stu-id="cfb44-108">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="cfb44-109">U + 0000-U + FFFF</span><span class="sxs-lookup"><span data-stu-id="cfb44-109">U+0000 to U+FFFF</span></span>|<span data-ttu-id="cfb44-110">16 bit</span><span class="sxs-lookup"><span data-stu-id="cfb44-110">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="cfb44-111">Türün varsayılan değeri, yani `char` `\0` u + 0000 olur.</span><span class="sxs-lookup"><span data-stu-id="cfb44-111">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="cfb44-112">`char`Tür [karşılaştırma](../operators/comparison-operators.md), [eşitlik](../operators/equality-operators.md), [artış](../operators/arithmetic-operators.md#increment-operator-)ve [azaltma](../operators/arithmetic-operators.md#decrement-operator---) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="cfb44-112">The `char` type supports [comparison](../operators/comparison-operators.md), [equality](../operators/equality-operators.md), [increment](../operators/arithmetic-operators.md#increment-operator-), and [decrement](../operators/arithmetic-operators.md#decrement-operator---) operators.</span></span> <span data-ttu-id="cfb44-113">Üstelik, `char` işlenenler, [Aritmetik](../operators/arithmetic-operators.md) ve [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md) işleçler için ilgili karakter kodları üzerinde bir işlem gerçekleştirir ve türün sonucunu üretir `int` .</span><span class="sxs-lookup"><span data-stu-id="cfb44-113">Moreover, for `char` operands, [arithmetic](../operators/arithmetic-operators.md) and [bitwise logical](../operators/bitwise-and-shift-operators.md) operators perform an operation on the corresponding character codes and produce the result of the `int` type.</span></span>

<span data-ttu-id="cfb44-114">[Dize](reference-types.md#the-string-type) türü, metni bir dizi değer olarak temsil eder `char` .</span><span class="sxs-lookup"><span data-stu-id="cfb44-114">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="cfb44-115">Değişmez Değerler</span><span class="sxs-lookup"><span data-stu-id="cfb44-115">Literals</span></span>

<span data-ttu-id="cfb44-116">Şunu `char` içeren bir değer belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cfb44-116">You can specify a `char` value with:</span></span>

- <span data-ttu-id="cfb44-117">bir karakter sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="cfb44-117">a character literal.</span></span>
- <span data-ttu-id="cfb44-118">bir Unicode kaçış sırası, bu, `\u` bir karakter kodunun dört symbol onaltılı gösterimi izler.</span><span class="sxs-lookup"><span data-stu-id="cfb44-118">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="cfb44-119">`\x`bir karakter kodunun onaltılı gösteriminden sonra gelen onaltılı kaçış sırası.</span><span class="sxs-lookup"><span data-stu-id="cfb44-119">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/shared/CharType.cs#Literals)]

<span data-ttu-id="cfb44-120">Yukarıdaki örnekte gösterildiği gibi, bir karakter kodunun değerini karşılık gelen değere de çevirebilirsiniz `char` .</span><span class="sxs-lookup"><span data-stu-id="cfb44-120">As the preceding example shows, you can also cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="cfb44-121">Unicode kaçış sırası söz konusu olduğunda, dört onaltılık basamağı de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cfb44-121">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="cfb44-122">Yani, `\u006A` geçerli bir kaçış sırası, `\u06A` ve `\u6A` geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="cfb44-122">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="cfb44-123">Onaltılı kaçış sırası söz konusu olduğunda, öndeki sıfırları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfb44-123">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="cfb44-124">Diğer bir deyişle, `\x006A` , `\x06A` ve `\x6A` kaçış dizileri geçerlidir ve aynı karaktere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="cfb44-124">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="cfb44-125">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="cfb44-125">Conversions</span></span>

<span data-ttu-id="cfb44-126">`char`Türü örtük olarak şu [integral](integral-numeric-types.md) türlerine dönüştürülebilir: `ushort` ,,, `int` `uint` `long` ve `ulong` .</span><span class="sxs-lookup"><span data-stu-id="cfb44-126">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="cfb44-127">Ayrıca, yerleşik [kayan nokta](floating-point-numeric-types.md) sayısal türlerine örtülü olarak dönüştürülebilir: `float` , `double` ve `decimal` .</span><span class="sxs-lookup"><span data-stu-id="cfb44-127">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="cfb44-128">Açık olarak `sbyte` , `byte` ve `short` tam sayı türlerine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="cfb44-128">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="cfb44-129">Diğer türlerden türe örtük dönüştürme yok `char` .</span><span class="sxs-lookup"><span data-stu-id="cfb44-129">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="cfb44-130">Ancak, tüm [integral](integral-numeric-types.md) veya [kayan nokta](floating-point-numeric-types.md) sayısal türleri açıkça dönüştürülebilir `char` .</span><span class="sxs-lookup"><span data-stu-id="cfb44-130">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cfb44-131">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="cfb44-131">C# language specification</span></span>

<span data-ttu-id="cfb44-132">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Integral türler](~/_csharplang/spec/types.md#integral-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cfb44-132">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cfb44-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfb44-133">See also</span></span>

- [<span data-ttu-id="cfb44-134">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="cfb44-134">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cfb44-135">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="cfb44-135">Value types</span></span>](value-types.md)
- [<span data-ttu-id="cfb44-136">Dizeler</span><span class="sxs-lookup"><span data-stu-id="cfb44-136">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="cfb44-137">.NET içinde karakter kodlaması</span><span class="sxs-lookup"><span data-stu-id="cfb44-137">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)
