---
title: Integral sayısal türleri-C# başvurusu
description: İntegral sayısal türlerin her biri için aralığı, depolama boyutunu ve kullanımları öğrenin.
ms.date: 03/17/2021
f1_keywords:
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- short_CSharpKeyword
- ushort_CSharpKeyword
- int_CSharpKeyword
- uint_CSharpKeyword
- long_CSharpKeyword
- ulong_CSharpKeyword
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 02b1451dc3aa22dfe27181b0e9160d198349107c
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760177"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="52db2-103">Integral sayısal türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="52db2-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="52db2-104">*İntegral sayısal türleri* tamsayı sayılarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52db2-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="52db2-105">Tüm integral sayısal türleri [değer türlerdir](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="52db2-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="52db2-106">Bunlar ayrıca [basit türlerdir](value-types.md#built-in-value-types) ve [değişmez değerler](#integer-literals)ile başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="52db2-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="52db2-107">Tüm integral sayısal türler [Aritmetik](../operators/arithmetic-operators.md), [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="52db2-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="52db2-108">İntegral türlerinin özellikleri</span><span class="sxs-lookup"><span data-stu-id="52db2-108">Characteristics of the integral types</span></span>

<span data-ttu-id="52db2-109">C# aşağıdaki önceden tanımlanmış integral türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="52db2-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="52db2-110">C# türü/anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="52db2-110">C# type/keyword</span></span>|<span data-ttu-id="52db2-111">Aralık</span><span class="sxs-lookup"><span data-stu-id="52db2-111">Range</span></span>|<span data-ttu-id="52db2-112">Boyut</span><span class="sxs-lookup"><span data-stu-id="52db2-112">Size</span></span>|<span data-ttu-id="52db2-113">.NET türü</span><span class="sxs-lookup"><span data-stu-id="52db2-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="52db2-114">-128-127</span><span class="sxs-lookup"><span data-stu-id="52db2-114">-128 to 127</span></span>|<span data-ttu-id="52db2-115">İmzalanan 8 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="52db2-116">0-255</span><span class="sxs-lookup"><span data-stu-id="52db2-116">0 to 255</span></span>|<span data-ttu-id="52db2-117">İşaretsiz 8 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="52db2-118">-32.768-32.767</span><span class="sxs-lookup"><span data-stu-id="52db2-118">-32,768 to 32,767</span></span>|<span data-ttu-id="52db2-119">İmzalanan 16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="52db2-120">0-65.535</span><span class="sxs-lookup"><span data-stu-id="52db2-120">0 to 65,535</span></span>|<span data-ttu-id="52db2-121">İşaretsiz 16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="52db2-122">-2.147.483.648-2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="52db2-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="52db2-123">İmzalanan 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="52db2-124">0-4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="52db2-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="52db2-125">İşaretsiz 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="52db2-126">-9223372036854775808-9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="52db2-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="52db2-127">İmzalanan 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="52db2-128">0-18446744073709551615</span><span class="sxs-lookup"><span data-stu-id="52db2-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="52db2-129">İşaretsiz 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|`nint`|<span data-ttu-id="52db2-130">Platforma bağlıdır</span><span class="sxs-lookup"><span data-stu-id="52db2-130">Depends on platform</span></span>|<span data-ttu-id="52db2-131">İmzalanan 32 bit veya 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-131">Signed 32-bit or 64-bit integer</span></span>|<xref:System.IntPtr?displayProperty=nameWithType>|
|`nuint`|<span data-ttu-id="52db2-132">Platforma bağlıdır</span><span class="sxs-lookup"><span data-stu-id="52db2-132">Depends on platform</span></span>|<span data-ttu-id="52db2-133">İşaretsiz 32 bit veya 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="52db2-133">Unsigned 32-bit or 64-bit integer</span></span>|<xref:System.UIntPtr?displayProperty=nameWithType>|

<span data-ttu-id="52db2-134">Son iki hariç tüm tablo satırlarında, en soldaki sütundan her bir C# Type anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="52db2-134">In all of the table rows except the last two, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="52db2-135">Anahtar sözcüğü ve .NET tür adı, değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="52db2-135">The keyword and .NET type name are interchangeable.</span></span> <span data-ttu-id="52db2-136">Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:</span><span class="sxs-lookup"><span data-stu-id="52db2-136">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="52db2-137">`nint` `nuint` Tablonun son iki satırı içindeki ve türleri yerel boyutlu tamsayılardır.</span><span class="sxs-lookup"><span data-stu-id="52db2-137">The `nint` and `nuint` types in the last two rows of the table are native-sized integers.</span></span> <span data-ttu-id="52db2-138">Bunlar, belirtilen .NET türleri tarafından dahili olarak temsil edilir, ancak her durumda anahtar sözcüğü ve .NET türü birbirini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="52db2-138">They are represented internally by the indicated .NET types, but in each case the keyword and the .NET type are not interchangeable.</span></span> <span data-ttu-id="52db2-139">Derleyici, `nint` ve için ve `nuint` işaretçi türleri için sağlamayan tamsayı türleri olarak işlemler ve dönüştürmeler sağlar `System.IntPtr` `System.UIntPtr` .</span><span class="sxs-lookup"><span data-stu-id="52db2-139">The compiler provides operations and conversions for `nint` and `nuint` as integer types that it doesn't provide for the pointer types `System.IntPtr` and `System.UIntPtr`.</span></span> <span data-ttu-id="52db2-140">Daha fazla bilgi için bkz. [ `nint` ve `nuint` türleri](nint-nuint.md).</span><span class="sxs-lookup"><span data-stu-id="52db2-140">For more information, see [`nint` and `nuint` types](nint-nuint.md).</span></span>

<span data-ttu-id="52db2-141">Yerel boyutlu tamsayı türleri hakkında daha fazla bilgi için bkz. [ `nint` ve `nuint` ](nint-nuint.md).</span><span class="sxs-lookup"><span data-stu-id="52db2-141">For information about the native-sized integer types, see [`nint` and `nuint`](nint-nuint.md).</span></span>

<span data-ttu-id="52db2-142">Her integral türünün varsayılan değeri sıfırdır `0` .</span><span class="sxs-lookup"><span data-stu-id="52db2-142">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="52db2-143">Yerel ölçekli türler hariç tüm integral türlerin her biri, `MinValue` `MaxValue` Bu türün en düşük ve en büyük değerini sağlayan sabitler içerir.</span><span class="sxs-lookup"><span data-stu-id="52db2-143">Each of the integral types except the native-sized types has `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="52db2-144"><xref:System.Numerics.BigInteger?displayProperty=nameWithType>Üst veya alt sınır olmadan işaretli bir tamsayıyı temsil etmek için yapıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="52db2-144">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="52db2-145">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="52db2-145">Integer literals</span></span>

<span data-ttu-id="52db2-146">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="52db2-146">Integer literals can be</span></span>

- <span data-ttu-id="52db2-147">*Decimal*: herhangi bir ön ek olmadan</span><span class="sxs-lookup"><span data-stu-id="52db2-147">*decimal*: without any prefix</span></span>
- <span data-ttu-id="52db2-148">*onaltılı*: `0x` veya `0X` öneki</span><span class="sxs-lookup"><span data-stu-id="52db2-148">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="52db2-149">*ikili*: `0b` veya `0B` önekiyle (C# 7,0 ve üzeri sürümlerde kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="52db2-149">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="52db2-150">Aşağıdaki kod, her birine bir örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="52db2-150">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="52db2-151">Yukarıdaki örnek ayrıca `_` C# 7,0 ile başlayarak desteklenen bir *rakam ayırıcısı* olarak kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="52db2-151">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="52db2-152">Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52db2-152">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="52db2-153">Bir tamsayı sabit değerinin türü, soneki tarafından aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="52db2-153">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="52db2-154">Değişmez değerin son eki yoksa, türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `int` , `uint` , `long` , `ulong` .</span><span class="sxs-lookup"><span data-stu-id="52db2-154">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="52db2-155">Sabit değer veya tarafından sonekli ise `U` `u` , türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `uint` , `ulong` .</span><span class="sxs-lookup"><span data-stu-id="52db2-155">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="52db2-156">Sabit değer veya tarafından sonekli ise `L` `l` , türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `long` , `ulong` .</span><span class="sxs-lookup"><span data-stu-id="52db2-156">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="52db2-157">Küçük harfli harfi `l` sonek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52db2-157">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="52db2-158">Ancak, bu bir derleyici uyarısı oluşturur, çünkü harf `l` rakamla karışıyor olabilir `1` .</span><span class="sxs-lookup"><span data-stu-id="52db2-158">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="52db2-159">`L`Açıklık için kullanın.</span><span class="sxs-lookup"><span data-stu-id="52db2-159">Use `L` for clarity.</span></span>

- <span data-ttu-id="52db2-160">Sabit değer,,,,,, veya ile sonsabitidir, `UL` `Ul` `uL` `ul` `LU` `Lu` `lU` `lu` türü `ulong` .</span><span class="sxs-lookup"><span data-stu-id="52db2-160">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="52db2-161">Bir tamsayı değişmez değeri ile temsil edilen değer aşarsa <xref:System.UInt64.MaxValue?displayProperty=nameWithType> , bir derleyici hatası [CS1021](../../misc/cs1021.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="52db2-161">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="52db2-162">Bir tamsayı sabit değerinin belirlenen türü ise `int` ve değişmez değer tarafından temsil edilen değer hedef türün aralığı içindeyse, değer örtük olarak,,,,, veya olarak dönüştürülebilir `sbyte` `byte` `short` `ushort` `uint` `ulong` `nint` `nuint` :</span><span class="sxs-lookup"><span data-stu-id="52db2-162">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, `nint` or `nuint`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="52db2-163">Yukarıdaki örnekte gösterildiği gibi, değişmez değerin değeri hedef türü Aralık içinde değilse, bir derleyici hatası [CS0031](../../misc/cs0031.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="52db2-163">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="52db2-164">Ayrıca, bir tamsayı değişmez değeri ile temsil edilen değeri, değişmez değer türü dışında bir türe dönüştürmek için bir cast da kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="52db2-164">You can also use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="52db2-165">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="52db2-165">Conversions</span></span>

<span data-ttu-id="52db2-166">Herhangi bir integral sayısal türü diğer tüm integral sayısal türlerine dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52db2-166">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="52db2-167">Hedef türü kaynak türünün tüm değerlerini depolayabiliyorsanız, dönüştürme örtük olur.</span><span class="sxs-lookup"><span data-stu-id="52db2-167">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="52db2-168">Aksi takdirde, açık bir dönüştürme gerçekleştirmek için bir [atama ifadesi](../operators/type-testing-and-cast.md#cast-expression) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="52db2-168">Otherwise, you need to use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span> <span data-ttu-id="52db2-169">Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="52db2-169">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="52db2-170">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="52db2-170">C# language specification</span></span>

<span data-ttu-id="52db2-171">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="52db2-171">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="52db2-172">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="52db2-172">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="52db2-173">Tamsayı sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="52db2-173">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="52db2-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52db2-174">See also</span></span>

- [<span data-ttu-id="52db2-175">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="52db2-175">C# reference</span></span>](../index.md)
- [<span data-ttu-id="52db2-176">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="52db2-176">Value types</span></span>](value-types.md)
- [<span data-ttu-id="52db2-177">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="52db2-177">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="52db2-178">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="52db2-178">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="52db2-179">.NET Sayısal Değerleri</span><span class="sxs-lookup"><span data-stu-id="52db2-179">Numerics in .NET</span></span>](../../../standard/numerics.md)
