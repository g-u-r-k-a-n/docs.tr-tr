---
description: 'Hakkında daha fazla bilgi edinin: tür dönüştürme Işlevleri (Visual Basic)'
title: Tür Dönüştürme İşlevleri
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: c2e701b522bbeb32f4f6f448acd78e09b0616f46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731090"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="e2bfe-103">Tür Dönüştürme İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2bfe-103">Type Conversion Functions (Visual Basic)</span></span>

<span data-ttu-id="e2bfe-104">Bu işlevler satır içi olarak derlenir, yani dönüştürme kodu, ifadeyi değerlendiren kodun bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-104">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="e2bfe-105">Bazen dönüştürmeyi gerçekleştirmek için bir yordam çağrısı yoktur ve bu da performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-105">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="e2bfe-106">Her işlev bir ifadeyi belirli bir veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-106">Each function coerces an expression to a specific data type.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2bfe-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2bfe-107">Syntax</span></span>

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a><span data-ttu-id="e2bfe-108">Bölüm</span><span class="sxs-lookup"><span data-stu-id="e2bfe-108">Part</span></span>

`expression`  
<span data-ttu-id="e2bfe-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-109">Required.</span></span> <span data-ttu-id="e2bfe-110">Kaynak veri türünün herhangi bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-110">Any expression of the source data type.</span></span>

## <a name="return-value-data-type"></a><span data-ttu-id="e2bfe-111">Dönüş değeri veri türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-111">Return Value Data Type</span></span>

<span data-ttu-id="e2bfe-112">İşlev adı, aşağıdaki tabloda gösterildiği gibi, döndürdüğü değerin veri türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-112">The function name determines the data type of the value it returns, as shown in the following table.</span></span>

|<span data-ttu-id="e2bfe-113">İşlev adı</span><span class="sxs-lookup"><span data-stu-id="e2bfe-113">Function name</span></span>|<span data-ttu-id="e2bfe-114">Dönüş veri türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-114">Return data type</span></span>|<span data-ttu-id="e2bfe-115">`expression`Bağımsız değişken aralığı</span><span class="sxs-lookup"><span data-stu-id="e2bfe-115">Range for `expression` argument</span></span>|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[<span data-ttu-id="e2bfe-116">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-116">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="e2bfe-117">Herhangi bir geçerli `Char` veya `String` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-117">Any valid `Char` or `String` or numeric expression.</span></span>|
|`CByte`|[<span data-ttu-id="e2bfe-118">Byte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-118">Byte Data Type</span></span>](../data-types/byte-data-type.md)|<span data-ttu-id="e2bfe-119"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) ila <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (işaretsiz); Kesirli parçalar yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="e2bfe-119"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e2bfe-120">Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile kayan nokta ile bayta dönüştürme performansını iyileştirir `CByte` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-120">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e2bfe-121">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-121">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CChar`|[<span data-ttu-id="e2bfe-122">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-122">Char Data Type</span></span>](../data-types/char-data-type.md)|<span data-ttu-id="e2bfe-123">Herhangi `Char` bir geçerli veya `String` ifade; yalnızca ilk karakter `String` dönüştürülür; değer 0 ile 65535 (işaretsiz) olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-123">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|
|`CDate`|[<span data-ttu-id="e2bfe-124">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-124">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="e2bfe-125">Tarih ve saatin geçerli bir gösterimi.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-125">Any valid representation of a date and time.</span></span>|
|`CDbl`|[<span data-ttu-id="e2bfe-126">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-126">Double Data Type</span></span>](../data-types/double-data-type.md)|<span data-ttu-id="e2bfe-127">-1.79769313486231570 e + 308 ile-4.94065645841246544 E-324 arasında negatif değerler için; 4.94065645841246544 e-324-1.79769313486231570 E + 308 arası pozitif değerler için.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-127">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|
|`CDec`|[<span data-ttu-id="e2bfe-128">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-128">Decimal Data Type</span></span>](../data-types/decimal-data-type.md)|<span data-ttu-id="e2bfe-129">+/-79228162514264337593543950335 sıfır ölçekli sayılar, diğer bir deyişle ondalık basamak içermeyen sayılar.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-129">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="e2bfe-130">28 ondalık basamak içeren sayılar için, Aralık +/-7.9228162514264337593543950335 olur.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-130">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="e2bfe-131">Olası en küçük sıfır olmayan sayı 0,0000000000000000000000000001 ' dir (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="e2bfe-131">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|
|`CInt`|[<span data-ttu-id="e2bfe-132">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-132">Integer Data Type</span></span>](../data-types/integer-data-type.md)|<span data-ttu-id="e2bfe-133"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2.147.483.648)- <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647); Kesirli parçalar yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="e2bfe-133"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="e2bfe-134">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını, işlevle tamsayı dönüştürmeye en iyi duruma getirir `CInt` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-134">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e2bfe-135">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-135">See the [CInt Example](#cint-example) section for an example.</span></span> |
|`CLng`|[<span data-ttu-id="e2bfe-136">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-136">Long Data Type</span></span>](../data-types/long-data-type.md)|<span data-ttu-id="e2bfe-137"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9223372036854775808) ila <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807); Kesirli parçalar yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="e2bfe-137"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e2bfe-138">Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile, kayan noktanın performansını 64 bit tamsayı dönüştürmeye en iyi duruma getirir `CLng` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-138">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e2bfe-139">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-139">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CObj`|[<span data-ttu-id="e2bfe-140">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-140">Object Data Type</span></span>](../data-types/object-data-type.md)|<span data-ttu-id="e2bfe-141">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-141">Any valid expression.</span></span>|
|`CSByte`|[<span data-ttu-id="e2bfe-142">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-142">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)|<span data-ttu-id="e2bfe-143"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128)- <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); Kesirli parçalar yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="e2bfe-143"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e2bfe-144">Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile, kayan nokta ile işaretli bayt dönüştürmesinin performansını iyileştirir `CSByte` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-144">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e2bfe-145">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-145">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CShort`|[<span data-ttu-id="e2bfe-146">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-146">Short Data Type</span></span>](../data-types/short-data-type.md)|<span data-ttu-id="e2bfe-147"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32.768)- <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767); Kesirli parçalar yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="e2bfe-147"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e2bfe-148">Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile kayan noktalı 16 bit tam sayı dönüştürmesi performansını en iyi duruma getirir `CShort` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-148">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e2bfe-149">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-149">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CSng`|[<span data-ttu-id="e2bfe-150">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-150">Single Data Type</span></span>](../data-types/single-data-type.md)|<span data-ttu-id="e2bfe-151">-3.402823 e + 38 ila-1.401298 E-45 negatif değerler için; 1.401298 e-45 ile pozitif değerler için 3.402823 E + 38 arası.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-151">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|
|`CStr`|[<span data-ttu-id="e2bfe-152">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-152">String Data Type</span></span>](../data-types/string-data-type.md)|<span data-ttu-id="e2bfe-153">`CStr`Bağımsız değişkene bağlı olarak döndürür `expression` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-153">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="e2bfe-154">Bkz. [CStr işlevi Için dönüş değerleri](return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="e2bfe-154">See [Return Values for the CStr Function](return-values-for-the-cstr-function.md).</span></span>|
|`CUInt`|[<span data-ttu-id="e2bfe-155">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-155">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)|<span data-ttu-id="e2bfe-156"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) ila <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295) (işaretsiz); Kesirli parçalar yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="e2bfe-156"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e2bfe-157">Visual Basic 15,8 ' den başlayarak, Visual Basic kayan noktanın performansını, işlevle işaretsiz tamsayı dönüştürmeye en iyi duruma getirir `CUInt` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-157">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e2bfe-158">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-158">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CULng`|[<span data-ttu-id="e2bfe-159">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-159">ULong Data Type</span></span>](../data-types/ulong-data-type.md)|<span data-ttu-id="e2bfe-160"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0)- <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (işaretsiz); Kesirli parçalar yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="e2bfe-160"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e2bfe-161">Visual Basic 15,8 ' den başlayarak, Visual Basic, kayan noktanın performansını, işlevle işaretsiz uzun tamsayı dönüştürmeye en iyi duruma getirir `CULng` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-161">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e2bfe-162">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-162">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CUShort`|[<span data-ttu-id="e2bfe-163">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2bfe-163">UShort Data Type</span></span>](../data-types/ushort-data-type.md)|<span data-ttu-id="e2bfe-164"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) ila <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65.535) (işaretsiz); Kesirli parçalar yuvarlanır.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="e2bfe-164"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e2bfe-165">Visual Basic 15,8 ' den başlayarak, Visual Basic, işlev ile kayan noktalı işaretsiz 16 bit tam sayı dönüştürmesi performansını en iyi duruma getirir `CUShort` ; daha fazla bilgi Için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-165">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e2bfe-166">Örnek için [CInt örnek](#cint-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-166">See the [CInt Example](#cint-example) section for an example.</span></span>|

<span data-ttu-id="e2bfe-167"><sup>1</sup> kesirli parçalar *banker 'in yuvarlanması* adlı özel bir yuvarlama türüne tabi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-167"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="e2bfe-168">Daha fazla bilgi için "açıklamalar" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-168">See "Remarks" for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2bfe-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2bfe-169">Remarks</span></span>

<span data-ttu-id="e2bfe-170">Bir kural olarak, `ToString()` <xref:System.Convert> veya bağımsız bir tür yapısı ya da sınıf üzerinde gibi .NET Framework yöntemlerine Visual Basic tür dönüştürme işlevlerini tercih etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-170">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="e2bfe-171">Visual Basic işlevleri Visual Basic kodla en iyi etkileşim için tasarlanmıştır ve ayrıca, kaynak kodunuzu daha kısa ve daha kolay okunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-171">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="e2bfe-172">Ayrıca, .NET Framework dönüştürme yöntemleri her zaman Visual Basic işlevlerle aynı sonuçları oluşturmaz, örneğin, öğesine dönüştürme sırasında `Boolean` `Integer` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-172">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="e2bfe-173">Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="e2bfe-173">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

<span data-ttu-id="e2bfe-174">Visual Basic 15,8 ' den itibaren, <xref:System.Single> <xref:System.Double> Aşağıdaki yöntemler tarafından döndürülen veya değeri tamsayı dönüştürme işlevlerinden birine geçirdiğinizde (,,, `CByte` `CShort` ,, `CInt` `CLng` `CSByte` `CUShort` , `CUInt` `CULng` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,</span><span class="sxs-lookup"><span data-stu-id="e2bfe-174">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

<span data-ttu-id="e2bfe-175">Bu iyileştirme, çok sayıda tamsayı dönüştürme yapan kodun hızlı bir şekilde çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-175">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="e2bfe-176">Aşağıdaki örnekte, bu en iyileştirilmiş kayan noktadan tamsayı dönüştürmeleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e2bfe-176">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="e2bfe-177">Davranış</span><span class="sxs-lookup"><span data-stu-id="e2bfe-177">Behavior</span></span>

- <span data-ttu-id="e2bfe-178">**Zorlama.**</span><span class="sxs-lookup"><span data-stu-id="e2bfe-178">**Coercion.**</span></span> <span data-ttu-id="e2bfe-179">Genel olarak, bir işlemin sonucunu varsayılan veri türü yerine belirli bir veri türüne zorlamak için veri türü dönüştürme işlevlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-179">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="e2bfe-180">Örneğin, `CDec` tek duyarlıklı, çift duyarlıklı veya tamsayı aritmetiğinin normalde gerçekleştiğinin ondalık aritmetiğini zorlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-180">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>

- <span data-ttu-id="e2bfe-181">**Dönüştürme başarısız oldu.**</span><span class="sxs-lookup"><span data-stu-id="e2bfe-181">**Failed Conversions.**</span></span> <span data-ttu-id="e2bfe-182">`expression`İşlevine geçirilen, dönüştürülecek veri türü aralığının dışındaysa, bir <xref:System.OverflowException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-182">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>

- <span data-ttu-id="e2bfe-183">**Kesirli parçalar.**</span><span class="sxs-lookup"><span data-stu-id="e2bfe-183">**Fractional Parts.**</span></span> <span data-ttu-id="e2bfe-184">İntegral olmayan bir değeri integral türüne dönüştürdüğünüzde, tamsayı dönüştürme işlevleri ( `CByte` , `CInt` ,, `CLng` `CSByte` , `CShort` , `CUInt` , `CULng` , ve `CUShort` ) Kesirli parçayı kaldırır ve değeri en yakın tamsayıya yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-184">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>

     <span data-ttu-id="e2bfe-185">Kesirli bölüm tam olarak 0,5 ise, tamsayı dönüştürme işlevleri onu en yakın çift tamsayıya yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-185">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="e2bfe-186">Örneğin, 0,5, 0, 1,5 ve 2,5 her ikisi de 2 ' ye yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-186">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="e2bfe-187">Bu bazen Banker yuvarlama olarak adlandırılır ve amacı, bu tür sayıları birlikte eklerken *birikmekte* olan bir sapma için telafi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-187">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>

     <span data-ttu-id="e2bfe-188">`CInt` ve, `CLng` <xref:Microsoft.VisualBasic.Conversion.Int%2A> <xref:Microsoft.VisualBasic.Conversion.Fix%2A> bir sayının kesirli kısmını yuvarlamak yerine kesten ve işlevlerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-188">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="e2bfe-189">Ayrıca, `Fix` ve `Int` her zaman geçirdiğiniz veri türünde bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-189">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>

- <span data-ttu-id="e2bfe-190">**Tarih/saat dönüştürmeleri.**</span><span class="sxs-lookup"><span data-stu-id="e2bfe-190">**Date/Time Conversions.**</span></span> <span data-ttu-id="e2bfe-191"><xref:Microsoft.VisualBasic.Information.IsDate%2A>Bir değerin tarih ve saate dönüştürülebileceğini öğrenmek için işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-191">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="e2bfe-192">`CDate` Tarih değişmez değerlerini ve zaman rakamlarını tanır, ancak sayısal değerleri tanımaz.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-192">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="e2bfe-193">Visual Basic 6,0 `Date` değerini `Date` Visual Basic 2005 veya sonraki sürümlerde bir değere dönüştürmek için <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-193">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="e2bfe-194">**Bağımsız tarih/saat değerleri.**</span><span class="sxs-lookup"><span data-stu-id="e2bfe-194">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="e2bfe-195">[Tarih veri türü](../data-types/date-data-type.md) her zaman hem tarih hem de saat bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-195">The [Date Data Type](../data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="e2bfe-196">Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-196">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="e2bfe-197">Bir `Date` değeri dizeye dönüştürürseniz, `CStr` sonuçta elde edilen dizedeki nötr değerler içermez.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-197">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="e2bfe-198">Örneğin, `#January 1, 0001 9:30:00#` bir dizeye dönüştürürseniz, sonuç "9:30:00 har" olur; tarih bilgileri bastırılır.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-198">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="e2bfe-199">Ancak, tarih bilgileri özgün değerde hala bulunur `Date` ve işlev gibi işlevlerle kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-199">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>

- <span data-ttu-id="e2bfe-200">**Kültür duyarlılığı.**</span><span class="sxs-lookup"><span data-stu-id="e2bfe-200">**Culture Sensitivity.**</span></span> <span data-ttu-id="e2bfe-201">Dizeleri içeren tür dönüştürme işlevleri, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüştürme işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-201">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="e2bfe-202">Örneğin, `CDate` tarih biçimlerini sisteminizin yerel ayara göre tanır.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-202">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="e2bfe-203">Yerel ayarınız için doğru sırada gün, ay ve yıl girmelisiniz veya tarih doğru şekilde yorumlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-203">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="e2bfe-204">Uzun tarih biçimi, "Çarşamba" gibi bir haftanın günü dizesi içeriyorsa tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-204">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>

     <span data-ttu-id="e2bfe-205">Bir değerin dize gösterimine ya da yerel ayarınız tarafından belirtilenden farklı bir biçimde dönüştürmeniz gerekiyorsa Visual Basic tür dönüştürme işlevlerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-205">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="e2bfe-206">Bunu yapmak için, bu `ToString(IFormatProvider)` `Parse(String, IFormatProvider)` değerin türünün ve yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-206">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="e2bfe-207">Örneğin, bir <xref:System.Double.Parse%2A?displayProperty=nameWithType> dizeyi öğesine dönüştürürken `Double` ve <xref:System.Double.ToString%2A?displayProperty=nameWithType> türü bir değeri dizeye dönüştürürken kullanın `Double` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-207">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>

## <a name="ctype-function"></a><span data-ttu-id="e2bfe-208">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="e2bfe-208">CType Function</span></span>

<span data-ttu-id="e2bfe-209">[CType işlevi](ctype-function.md) ikinci bir bağımsız değişken alır, `typename` ve, `expression` `typename` `typename` geçerli bir dönüştürme var olan herhangi bir veri türü, yapı, sınıf veya arabirim olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-209">The [CType Function](ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>

<span data-ttu-id="e2bfe-210">`CType`Diğer tür dönüştürme anahtar sözcükleriyle bir karşılaştırması için bkz. [DirectCast Işleci](../operators/directcast-operator.md) ve [TryCast İşleci](../operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e2bfe-210">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../operators/directcast-operator.md) and [TryCast Operator](../operators/trycast-operator.md).</span></span>

## <a name="cbool-example"></a><span data-ttu-id="e2bfe-211">CBool örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-211">CBool Example</span></span>

<span data-ttu-id="e2bfe-212">Aşağıdaki örnek, `CBool` ifadeleri değerlere dönüştürmek için işlevini kullanır `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-212">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="e2bfe-213">Bir ifade sıfır dışında bir değer olarak değerlendirilirse, değerini `CBool` döndürür `True` ; Aksi takdirde döndürür `False` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-213">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a><span data-ttu-id="e2bfe-214">CByte örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-214">CByte Example</span></span>

<span data-ttu-id="e2bfe-215">Aşağıdaki örnek, `CByte` bir ifadeyi öğesine dönüştürmek için işlevini kullanır `Byte` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-215">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a><span data-ttu-id="e2bfe-216">CChar örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-216">CChar Example</span></span>

<span data-ttu-id="e2bfe-217">Aşağıdaki örnek, `CChar` bir ifadenin ilk karakterini bir türe dönüştürmek için işlevini kullanır `String` `Char` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-217">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

<span data-ttu-id="e2bfe-218">Giriş bağımsız değişkeni `CChar` veri türünde `Char` veya olmalıdır `String` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-218">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="e2bfe-219">`CChar` `CChar` Sayısal bir veri türü kabul edilemediğinden bir sayıyı karaktere dönüştürmek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-219">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="e2bfe-220">Aşağıdaki örnek, bir kod noktasını temsil eden bir sayı edinir (karakter kodu) ve karşılık gelen karaktere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-220">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="e2bfe-221">Bu, <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> `CInt` dizeyi türe dönüştürmek `Integer` ve `ChrW` sayıyı türe dönüştürmek için, basamak dizesini almak için işlevini kullanır `Char` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-221">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a><span data-ttu-id="e2bfe-222">CDate örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-222">CDate Example</span></span>

<span data-ttu-id="e2bfe-223">Aşağıdaki örnek, `CDate` dizeleri değerlere dönüştürmek için işlevini kullanır `Date` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-223">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="e2bfe-224">Genel olarak, sabit kodlama tarihleri ve saatleri dizeler (Bu örnekte gösterildiği gibi) önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-224">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="e2bfe-225">#Feb 12, 1969 # ve #4:45:23 PM # gibi tarih değişmez değerlerini ve zaman değişmez değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-225">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a><span data-ttu-id="e2bfe-226">CDbl örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-226">CDbl Example</span></span>

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a><span data-ttu-id="e2bfe-227">CDec örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-227">CDec Example</span></span>

<span data-ttu-id="e2bfe-228">Aşağıdaki örnek, `CDec` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-228">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a><span data-ttu-id="e2bfe-229">CInt örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-229">CInt Example</span></span>

<span data-ttu-id="e2bfe-230">Aşağıdaki örnek, `CInt` bir değeri öğesine dönüştürmek için işlevini kullanır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-230">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a><span data-ttu-id="e2bfe-231">CLng örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-231">CLng Example</span></span>

<span data-ttu-id="e2bfe-232">Aşağıdaki örnek, `CLng` değerlerini değerine dönüştürmek için işlevini kullanır `Long` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-232">The following example uses the `CLng` function to convert values to `Long`.</span></span>

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a><span data-ttu-id="e2bfe-233">CObj örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-233">CObj Example</span></span>

<span data-ttu-id="e2bfe-234">Aşağıdaki örnek, `CObj` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `Object` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-234">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="e2bfe-235">`Object`Değişken kendisine atanan değere işaret eden yalnızca dört baytlık bir işaretçi içerir `Double` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-235">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a><span data-ttu-id="e2bfe-236">CSByte örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-236">CSByte Example</span></span>

<span data-ttu-id="e2bfe-237">Aşağıdaki örnek, `CSByte` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `SByte` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-237">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a><span data-ttu-id="e2bfe-238">CShort örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-238">CShort Example</span></span>

<span data-ttu-id="e2bfe-239">Aşağıdaki örnek, `CShort` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `Short` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-239">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a><span data-ttu-id="e2bfe-240">CSng örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-240">CSng Example</span></span>

<span data-ttu-id="e2bfe-241">Aşağıdaki örnek, `CSng` değerlerini değerine dönüştürmek için işlevini kullanır `Single` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-241">The following example uses the `CSng` function to convert values to `Single`.</span></span>

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a><span data-ttu-id="e2bfe-242">CStr örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-242">CStr Example</span></span>

<span data-ttu-id="e2bfe-243">Aşağıdaki örnek, `CStr` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `String` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-243">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

<span data-ttu-id="e2bfe-244">Aşağıdaki örnek, `CStr` değerleri değerlere dönüştürmek için işlevini kullanır `Date` `String` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-244">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

<span data-ttu-id="e2bfe-245">`CStr` her zaman `Date` geçerli yerel ayar için standart kısa biçimde (örneğin, "6/15/2003 4:35:47 PM") bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-245">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="e2bfe-246">Ancak, `CStr` Tarih ve 00:00:00 için 1/1/0001 *nötr değerlerini* saat için bastırır.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-246">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>

<span data-ttu-id="e2bfe-247">Tarafından döndürülen değerler hakkında daha fazla ayrıntı için `CStr` bkz. [CStr Işlevi Için dönüş değerleri](return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="e2bfe-247">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](return-values-for-the-cstr-function.md).</span></span>

## <a name="cuint-example"></a><span data-ttu-id="e2bfe-248">CUInt örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-248">CUInt Example</span></span>

<span data-ttu-id="e2bfe-249">Aşağıdaki örnek, `CUInt` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `UInteger` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-249">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a><span data-ttu-id="e2bfe-250">Külörnek örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-250">CULng Example</span></span>

<span data-ttu-id="e2bfe-251">Aşağıdaki örnek, `CULng` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `ULong` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-251">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a><span data-ttu-id="e2bfe-252">CUShort örneği</span><span class="sxs-lookup"><span data-stu-id="e2bfe-252">CUShort Example</span></span>

<span data-ttu-id="e2bfe-253">Aşağıdaki örnek, `CUShort` bir sayısal değeri öğesine dönüştürmek için işlevini kullanır `UShort` .</span><span class="sxs-lookup"><span data-stu-id="e2bfe-253">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a><span data-ttu-id="e2bfe-254">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2bfe-254">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="e2bfe-255">Dönüşüm İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e2bfe-255">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="e2bfe-256">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="e2bfe-256">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
