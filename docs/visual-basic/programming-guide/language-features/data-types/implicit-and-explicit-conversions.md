---
title: Örtük ve Açık Dönüştürmeler
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 2858dafd2531bd846ad89672348d103f385c4511
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393837"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="0bcc5-102">Örtük ve Açık Dönüştürmeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bcc5-102">Implicit and Explicit Conversions (Visual Basic)</span></span>

<span data-ttu-id="0bcc5-103">*Örtük dönüştürme* , kaynak kodunda özel bir sözdizimi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="0bcc5-104">Aşağıdaki örnekte, Visual Basic değerini ' a atamadan önce, değeri örtük olarak `k` tek duyarlıklı kayan noktalı değere dönüştürür `q` .</span><span class="sxs-lookup"><span data-stu-id="0bcc5-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

<span data-ttu-id="0bcc5-105">*Açık dönüştürme* bir tür dönüştürme anahtar sözcüğü kullanır.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="0bcc5-106">Visual Basic, parantez içindeki bir ifadeyi istenen veri türüne döndüren birkaç anahtar sözcük sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="0bcc5-107">Bu anahtar sözcükler işlevler gibi davranır ancak derleyici, kodu satır içi olarak oluşturur, böylece yürütme bir işlev çağrısıyla biraz daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>

<span data-ttu-id="0bcc5-108">Önceki örneğin aşağıdaki uzantısında, `CInt` anahtar sözcüğü `q` öğesine atamadan önce değeri bir tamsayıya dönüştürür `k` .</span><span class="sxs-lookup"><span data-stu-id="0bcc5-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a><span data-ttu-id="0bcc5-109">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0bcc5-109">Conversion Keywords</span></span>

<span data-ttu-id="0bcc5-110">Aşağıdaki tabloda kullanılabilir dönüştürme anahtar sözcükleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-110">The following table shows the available conversion keywords.</span></span>

|<span data-ttu-id="0bcc5-111">Tür dönüştürme anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-111">Type conversion keyword</span></span>|<span data-ttu-id="0bcc5-112">Bir ifadeyi veri türüne dönüştürür</span><span class="sxs-lookup"><span data-stu-id="0bcc5-112">Converts an expression to data type</span></span>|<span data-ttu-id="0bcc5-113">Dönüştürülecek ifadenin izin verilen veri türleri</span><span class="sxs-lookup"><span data-stu-id="0bcc5-113">Allowable data types of expression to be converted</span></span>|
|---|---|---|
|`CBool`|[<span data-ttu-id="0bcc5-114">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-114">Boolean Data Type</span></span>](../../../language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="0bcc5-115">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|
|`CByte`|[<span data-ttu-id="0bcc5-116">Byte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-116">Byte Data Type</span></span>](../../../language-reference/data-types/byte-data-type.md)|<span data-ttu-id="0bcc5-117">Herhangi bir sayısal tür ( `SByte` ve numaralandırılmış türler dahil),, `Boolean` `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CChar`|[<span data-ttu-id="0bcc5-118">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-118">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)|<span data-ttu-id="0bcc5-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-119">`String`, `Object`</span></span>|
|`CDate`|[<span data-ttu-id="0bcc5-120">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-120">Date Data Type</span></span>](../../../language-reference/data-types/date-data-type.md)|<span data-ttu-id="0bcc5-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-121">`String`, `Object`</span></span>|
|`CDbl`|[<span data-ttu-id="0bcc5-122">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-122">Double Data Type</span></span>](../../../language-reference/data-types/double-data-type.md)|<span data-ttu-id="0bcc5-123">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CDec`|[<span data-ttu-id="0bcc5-124">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-124">Decimal Data Type</span></span>](../../../language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="0bcc5-125">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CInt`|[<span data-ttu-id="0bcc5-126">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-126">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)|<span data-ttu-id="0bcc5-127">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CLng`|[<span data-ttu-id="0bcc5-128">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-128">Long Data Type</span></span>](../../../language-reference/data-types/long-data-type.md)|<span data-ttu-id="0bcc5-129">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CObj`|[<span data-ttu-id="0bcc5-130">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-130">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)|<span data-ttu-id="0bcc5-131">Herhangi bir tür</span><span class="sxs-lookup"><span data-stu-id="0bcc5-131">Any type</span></span>|
|`CSByte`|[<span data-ttu-id="0bcc5-132">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-132">SByte Data Type</span></span>](../../../language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="0bcc5-133">Herhangi bir sayısal tür ( `Byte` ve numaralandırılmış türler dahil),, `Boolean` `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CShort`|[<span data-ttu-id="0bcc5-134">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-134">Short Data Type</span></span>](../../../language-reference/data-types/short-data-type.md)|<span data-ttu-id="0bcc5-135">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CSng`|[<span data-ttu-id="0bcc5-136">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-136">Single Data Type</span></span>](../../../language-reference/data-types/single-data-type.md)|<span data-ttu-id="0bcc5-137">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CStr`|[<span data-ttu-id="0bcc5-138">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-138">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)|<span data-ttu-id="0bcc5-139">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `Char` , `Char` dizi, `Date` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|
|`CType`|<span data-ttu-id="0bcc5-140">Virgül () sonrasında belirtilen tür `,`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="0bcc5-141">Bir *Öğesel veri türüne* dönüştürme sırasında (bir öğesel türün dizisi dahil), karşılık gelen dönüştürme anahtar sözcüğü için izin verilen türler</span><span class="sxs-lookup"><span data-stu-id="0bcc5-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="0bcc5-142">*Bileşik veri türüne*dönüştürme yaparken, uyguladığı arabirimler ve devraldığı sınıflar</span><span class="sxs-lookup"><span data-stu-id="0bcc5-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="0bcc5-143">Daha fazla yüklü olan bir sınıfa veya yapıya dönüştürme sırasında `CType` , bu sınıf veya yapı</span><span class="sxs-lookup"><span data-stu-id="0bcc5-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|
|`CUInt`|[<span data-ttu-id="0bcc5-144">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-144">UInteger Data Type</span></span>](../../../language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="0bcc5-145">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CULng`|[<span data-ttu-id="0bcc5-146">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-146">ULong Data Type</span></span>](../../../language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="0bcc5-147">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CUShort`|[<span data-ttu-id="0bcc5-148">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0bcc5-148">UShort Data Type</span></span>](../../../language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="0bcc5-149">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`</span><span class="sxs-lookup"><span data-stu-id="0bcc5-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|

## <a name="the-ctype-function"></a><span data-ttu-id="0bcc5-150">CType Işlevi</span><span class="sxs-lookup"><span data-stu-id="0bcc5-150">The CType Function</span></span>

<span data-ttu-id="0bcc5-151">[CType işlevi](../../../language-reference/functions/ctype-function.md) iki bağımsız değişken üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-151">The [CType Function](../../../language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="0bcc5-152">İlki dönüştürülecek ifade, ikincisi ise hedef veri türü veya nesne sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="0bcc5-153">İlk bağımsız değişkenin bir tür değil bir ifade olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-153">Note that the first argument must be an expression, not a type.</span></span>

<span data-ttu-id="0bcc5-154">`CType`, bir *satır içi işlevdir*, yani derlenmiş kod, genellikle bir işlev çağrısı oluşturmadan dönüştürmeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="0bcc5-155">Bu, performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-155">This improves performance.</span></span>

<span data-ttu-id="0bcc5-156">`CType`Diğer tür dönüştürme anahtar sözcükleriyle bir karşılaştırması için bkz. [DirectCast Işleci](../../../language-reference/operators/directcast-operator.md) ve [TryCast İşleci](../../../language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0bcc5-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../language-reference/operators/trycast-operator.md).</span></span>

### <a name="elementary-types"></a><span data-ttu-id="0bcc5-157">Elemensel türler</span><span class="sxs-lookup"><span data-stu-id="0bcc5-157">Elementary Types</span></span>

<span data-ttu-id="0bcc5-158">Aşağıdaki örnek öğesinin kullanımını gösterir `CType` .</span><span class="sxs-lookup"><span data-stu-id="0bcc5-158">The following example demonstrates the use of `CType`.</span></span>

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a><span data-ttu-id="0bcc5-159">Bileşik türler</span><span class="sxs-lookup"><span data-stu-id="0bcc5-159">Composite Types</span></span>

<span data-ttu-id="0bcc5-160">`CType`Değerleri bileşik veri türlerine ve öğesel türlere dönüştürmek için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="0bcc5-161">Ayrıca, aşağıdaki örnekte olduğu gibi, bir nesne sınıfını arabirimlerinden biri türüne zorlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a><span data-ttu-id="0bcc5-162">Dizi türleri</span><span class="sxs-lookup"><span data-stu-id="0bcc5-162">Array Types</span></span>

<span data-ttu-id="0bcc5-163">`CType`, aşağıdaki örnekte olduğu gibi dizi veri türlerini de dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-163">`CType` can also convert array data types, as in the following example.</span></span>

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

<span data-ttu-id="0bcc5-164">Daha fazla bilgi ve bir örnek için bkz. [dizi dönüştürmeleri](array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="0bcc5-164">For more information and an example, see [Array Conversions](array-conversions.md).</span></span>

### <a name="types-defining-ctype"></a><span data-ttu-id="0bcc5-165">CType tanımlayan türler</span><span class="sxs-lookup"><span data-stu-id="0bcc5-165">Types Defining CType</span></span>

<span data-ttu-id="0bcc5-166">`CType`Tanımladığınız bir sınıf veya yapı üzerinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="0bcc5-167">Bu, değerleri sınıfınızın veya yapınızın türüne ve türünden dönüştürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="0bcc5-168">Daha fazla bilgi ve bir örnek için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0bcc5-168">For more information and an example, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0bcc5-169">Bir dönüştürme anahtar sözcüğüyle kullanılan değerlerin hedef veri türü için geçerli olması gerekir veya bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="0bcc5-170">Örneğin, bir ' a dönüştürmeye çalışırsanız, `Long` `Integer` değeri `Long` veri türü için geçerli aralık dahilinde olmalıdır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="0bcc5-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>

> [!CAUTION]
> <span data-ttu-id="0bcc5-171">`CType`Kaynak türü hedef türünden türemezse, çalışma zamanında bir sınıf türünden diğerine dönüştürme yapmak için belirtme.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="0bcc5-172">Bu tür bir hata <xref:System.InvalidCastException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="0bcc5-173">Ancak, türlerden biri tanımladığınız bir yapı veya sınıf ise ve `CType` Bu yapıda veya sınıfta tanımladıysanız, bir dönüştürme işlemi, gereksinimlerinizi karşılıyorsa başarılı olabilir `CType` .</span><span class="sxs-lookup"><span data-stu-id="0bcc5-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="0bcc5-174">Bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0bcc5-174">See [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

<span data-ttu-id="0bcc5-175">Açık bir dönüştürme gerçekleştirmek, belirli bir veri türüne veya nesne sınıfına bir ifade *atama* olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bcc5-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bcc5-176">See also</span></span>

- [<span data-ttu-id="0bcc5-177">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="0bcc5-177">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="0bcc5-178">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="0bcc5-178">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="0bcc5-179">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0bcc5-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="0bcc5-180">Yapılar</span><span class="sxs-lookup"><span data-stu-id="0bcc5-180">Structures</span></span>](structures.md)
- [<span data-ttu-id="0bcc5-181">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="0bcc5-181">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="0bcc5-182">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0bcc5-182">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0bcc5-183">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="0bcc5-183">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
