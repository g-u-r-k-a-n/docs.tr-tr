---
title: Tamsayı Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343990"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="ada49-102">Integer data type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ada49-102">Integer data type (Visual Basic)</span></span>

<span data-ttu-id="ada49-103">Değer olarak -2.147.483.648 ile 2.147.483.647 arasında değişen imzalı 32 bitlik (4 bayt) tamsayıları tutar.</span><span class="sxs-lookup"><span data-stu-id="ada49-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ada49-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ada49-104">Remarks</span></span>

 <span data-ttu-id="ada49-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span><span class="sxs-lookup"><span data-stu-id="ada49-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="ada49-106">Diğer tamsayı türlerinin bellekten yüklenmesi ve belleğe depolanması daha yavaştır.</span><span class="sxs-lookup"><span data-stu-id="ada49-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="ada49-107">The default value of `Integer` is 0.</span><span class="sxs-lookup"><span data-stu-id="ada49-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="ada49-108">Literal assignments</span><span class="sxs-lookup"><span data-stu-id="ada49-108">Literal assignments</span></span>

<span data-ttu-id="ada49-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span><span class="sxs-lookup"><span data-stu-id="ada49-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ada49-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span><span class="sxs-lookup"><span data-stu-id="ada49-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ada49-111">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span><span class="sxs-lookup"><span data-stu-id="ada49-111">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="ada49-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span><span class="sxs-lookup"><span data-stu-id="ada49-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ada49-113">Decimal literals have no prefix.</span><span class="sxs-lookup"><span data-stu-id="ada49-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ada49-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="ada49-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="ada49-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span><span class="sxs-lookup"><span data-stu-id="ada49-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ada49-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ada49-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="ada49-117">Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="ada49-117">Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="ada49-118">Programlama ipuçları</span><span class="sxs-lookup"><span data-stu-id="ada49-118">Programming tips</span></span>

- <span data-ttu-id="ada49-119">**Interop Considerations.**</span><span class="sxs-lookup"><span data-stu-id="ada49-119">**Interop Considerations.**</span></span> <span data-ttu-id="ada49-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span><span class="sxs-lookup"><span data-stu-id="ada49-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="ada49-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="ada49-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="ada49-122">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="ada49-122">**Widening.**</span></span> <span data-ttu-id="ada49-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span><span class="sxs-lookup"><span data-stu-id="ada49-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="ada49-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span><span class="sxs-lookup"><span data-stu-id="ada49-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="ada49-125">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="ada49-125">**Type Characters.**</span></span> <span data-ttu-id="ada49-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span><span class="sxs-lookup"><span data-stu-id="ada49-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="ada49-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ada49-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
- <span data-ttu-id="ada49-128">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="ada49-128">**Framework Type.**</span></span> <span data-ttu-id="ada49-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span><span class="sxs-lookup"><span data-stu-id="ada49-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="ada49-130">Aralık</span><span class="sxs-lookup"><span data-stu-id="ada49-130">Range</span></span>

<span data-ttu-id="ada49-131">Tamsayı türünde bir değişkeni, bu türe ilişkin aralık dışında bir sayıya ayarlamaya çalışırsanız hata meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="ada49-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="ada49-132">Bir kesir olarak ayarlamaya çalışırsanız, sayı en yakın tamsayı değerine yukarı veya aşağı yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="ada49-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="ada49-133">Sayı iki tamsayı değerine de eşit yakınlıkta ise, değer en yakın çift tamsayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="ada49-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="ada49-134">Bu davranış, bir orta nokta değerini tek bir yönde sürekli olarak yuvarlamaktan kaynaklanan yuvarlama hatalarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="ada49-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="ada49-135">Aşağıdaki kod, yuvarlama örneklerini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ada49-135">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="ada49-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ada49-136">See also</span></span>

- <xref:System.Int32?displayProperty=nameWithType>
- [<span data-ttu-id="ada49-137">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="ada49-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="ada49-138">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ada49-138">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="ada49-139">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ada49-139">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="ada49-140">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ada49-140">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="ada49-141">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="ada49-141">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="ada49-142">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="ada49-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
