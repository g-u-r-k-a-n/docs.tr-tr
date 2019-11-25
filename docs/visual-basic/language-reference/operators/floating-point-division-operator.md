---
title: / İşleci
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 537d8b0c703b59743f1a7c531448118058707645
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331049"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ad59d-102">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad59d-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="ad59d-103">Divides two numbers and returns a floating-point result.</span><span class="sxs-lookup"><span data-stu-id="ad59d-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad59d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad59d-104">Syntax</span></span>  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="ad59d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ad59d-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="ad59d-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ad59d-106">Required.</span></span> <span data-ttu-id="ad59d-107">Any numeric expression.</span><span class="sxs-lookup"><span data-stu-id="ad59d-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="ad59d-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ad59d-108">Required.</span></span> <span data-ttu-id="ad59d-109">Any numeric expression.</span><span class="sxs-lookup"><span data-stu-id="ad59d-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="ad59d-110">Supported Types</span><span class="sxs-lookup"><span data-stu-id="ad59d-110">Supported Types</span></span>  
 <span data-ttu-id="ad59d-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ad59d-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="ad59d-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="ad59d-112">Result</span></span>  
 <span data-ttu-id="ad59d-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span><span class="sxs-lookup"><span data-stu-id="ad59d-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="ad59d-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span><span class="sxs-lookup"><span data-stu-id="ad59d-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad59d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad59d-115">Remarks</span></span>  
 <span data-ttu-id="ad59d-116">The data type of the result depends on the types of the operands.</span><span class="sxs-lookup"><span data-stu-id="ad59d-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="ad59d-117">The following table shows how the data type of the result is determined.</span><span class="sxs-lookup"><span data-stu-id="ad59d-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="ad59d-118">Operand data types</span><span class="sxs-lookup"><span data-stu-id="ad59d-118">Operand data types</span></span>|<span data-ttu-id="ad59d-119">Result data type</span><span class="sxs-lookup"><span data-stu-id="ad59d-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="ad59d-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="ad59d-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="ad59d-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="ad59d-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="ad59d-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="ad59d-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="ad59d-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span><span class="sxs-lookup"><span data-stu-id="ad59d-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="ad59d-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span><span class="sxs-lookup"><span data-stu-id="ad59d-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="ad59d-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span><span class="sxs-lookup"><span data-stu-id="ad59d-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="ad59d-126">This can throw an exception if the result does not fit in that type.</span><span class="sxs-lookup"><span data-stu-id="ad59d-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="ad59d-127">In particular, see "Attempted Division by Zero" on this Help page.</span><span class="sxs-lookup"><span data-stu-id="ad59d-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="ad59d-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span><span class="sxs-lookup"><span data-stu-id="ad59d-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="ad59d-129">Attempted Division by Zero</span><span class="sxs-lookup"><span data-stu-id="ad59d-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="ad59d-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span><span class="sxs-lookup"><span data-stu-id="ad59d-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="ad59d-131">The following table shows the possible behaviors.</span><span class="sxs-lookup"><span data-stu-id="ad59d-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="ad59d-132">Operand data types</span><span class="sxs-lookup"><span data-stu-id="ad59d-132">Operand data types</span></span>|<span data-ttu-id="ad59d-133">Behavior if `expression2` is zero</span><span class="sxs-lookup"><span data-stu-id="ad59d-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="ad59d-134">Floating-point (`Single` or `Double`)</span><span class="sxs-lookup"><span data-stu-id="ad59d-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="ad59d-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span><span class="sxs-lookup"><span data-stu-id="ad59d-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="ad59d-136">Throws <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="ad59d-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="ad59d-137">Integral (signed or unsigned)</span><span class="sxs-lookup"><span data-stu-id="ad59d-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="ad59d-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="ad59d-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ad59d-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="ad59d-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ad59d-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="ad59d-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ad59d-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ad59d-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad59d-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad59d-142">Example</span></span>  
 <span data-ttu-id="ad59d-143">This example uses the `/` operator to perform floating-point division.</span><span class="sxs-lookup"><span data-stu-id="ad59d-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="ad59d-144">The result is the quotient of the two operands.</span><span class="sxs-lookup"><span data-stu-id="ad59d-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="ad59d-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span><span class="sxs-lookup"><span data-stu-id="ad59d-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="ad59d-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span><span class="sxs-lookup"><span data-stu-id="ad59d-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad59d-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad59d-147">See also</span></span>

- [<span data-ttu-id="ad59d-148">/= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad59d-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="ad59d-149">\ Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad59d-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="ad59d-150">İşleç Sonuçlarının Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="ad59d-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [<span data-ttu-id="ad59d-151">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="ad59d-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="ad59d-152">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad59d-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ad59d-153">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="ad59d-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ad59d-154">Arithmetic Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad59d-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
