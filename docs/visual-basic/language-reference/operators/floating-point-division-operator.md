---
description: Hakkında daha fazla bilgi edinin:/Işleç (Visual Basic)
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
ms.openlocfilehash: 717c8fdc6abae02de555040a3aadb92fed2bfbee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666010"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0ad77-103">/ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ad77-103">/ Operator (Visual Basic)</span></span>

<span data-ttu-id="0ad77-104">İki sayıyı böler ve kayan noktalı bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ad77-104">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ad77-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ad77-105">Syntax</span></span>  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="0ad77-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0ad77-106">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="0ad77-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0ad77-107">Required.</span></span> <span data-ttu-id="0ad77-108">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="0ad77-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="0ad77-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0ad77-109">Required.</span></span> <span data-ttu-id="0ad77-110">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="0ad77-110">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="0ad77-111">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="0ad77-111">Supported Types</span></span>  

 <span data-ttu-id="0ad77-112">İmzasız ve kayan nokta türleri de dahil olmak üzere tüm sayısal türler `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="0ad77-112">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="0ad77-113">Sonuç</span><span class="sxs-lookup"><span data-stu-id="0ad77-113">Result</span></span>  

 <span data-ttu-id="0ad77-114">Sonuç, `expression1` `expression2` kalanı da dahil olmak üzere bölünen tam bölüm.</span><span class="sxs-lookup"><span data-stu-id="0ad77-114">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="0ad77-115">[\ İşleci (Visual Basic)](integer-division-operator.md) , kalanı döndüren tamsayı bölümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ad77-115">The [\ Operator (Visual Basic)](integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ad77-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ad77-116">Remarks</span></span>  

 <span data-ttu-id="0ad77-117">Sonucun veri türü, işlenenlerinin türlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ad77-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="0ad77-118">Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ad77-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="0ad77-119">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="0ad77-119">Operand data types</span></span>|<span data-ttu-id="0ad77-120">Sonuç veri türü</span><span class="sxs-lookup"><span data-stu-id="0ad77-120">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="0ad77-121">Her iki ifade de İntegral veri türleridir[(SByte](../data-types/sbyte-data-type.md), [byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [ushort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="0ad77-121">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="0ad77-122">Tek bir ifade [tek](../data-types/single-data-type.md) bir veri türüdür ve diğeri [Double](../data-types/double-data-type.md) değildir</span><span class="sxs-lookup"><span data-stu-id="0ad77-122">One expression is a [Single](../data-types/single-data-type.md) data type and the other is not a [Double](../data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="0ad77-123">Bir ifade [ondalık](../data-types/decimal-data-type.md) veri türüdür ve diğeri [tek](../data-types/single-data-type.md) veya [çift](../data-types/double-data-type.md) değil</span><span class="sxs-lookup"><span data-stu-id="0ad77-123">One expression is a [Decimal](../data-types/decimal-data-type.md) data type and the other is not a [Single](../data-types/single-data-type.md) or a [Double](../data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="0ad77-124">İki ifade de bir [Double](../data-types/double-data-type.md) veri türüdür</span><span class="sxs-lookup"><span data-stu-id="0ad77-124">Either expression is a [Double](../data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="0ad77-125">Bölüm gerçekleştirilmeden önce, tüm integral sayısal ifadeler iletildiklerinde ' dir `Double` .</span><span class="sxs-lookup"><span data-stu-id="0ad77-125">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="0ad77-126">Sonucu bir integral veri türüne atarsanız, Visual Basic sonucu `Double` Bu türe dönüştürmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="0ad77-126">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="0ad77-127">Bu, sonuç bu türe uygun değilse bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="0ad77-127">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="0ad77-128">Özellikle, bu Yardım sayfasında "sıfıra bölme yapılmaya çalışıldı" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0ad77-128">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="0ad77-129">`expression1`Ya da `expression2` [hiçbir şey](../nothing.md)değerlendirilirse, sıfır olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0ad77-129">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="0ad77-130">Sıfıra bölme denendi</span><span class="sxs-lookup"><span data-stu-id="0ad77-130">Attempted Division by Zero</span></span>  

 <span data-ttu-id="0ad77-131">`expression2`Sıfır olarak değerlendirilirse, `/` işleç farklı işlenen veri türleri için farklı davranır.</span><span class="sxs-lookup"><span data-stu-id="0ad77-131">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="0ad77-132">Aşağıdaki tabloda olası davranışlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ad77-132">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="0ad77-133">İşlenen veri türleri</span><span class="sxs-lookup"><span data-stu-id="0ad77-133">Operand data types</span></span>|<span data-ttu-id="0ad77-134">Sıfır ise davranış `expression2`</span><span class="sxs-lookup"><span data-stu-id="0ad77-134">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="0ad77-135">Kayan nokta ( `Single` veya `Double` )</span><span class="sxs-lookup"><span data-stu-id="0ad77-135">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="0ad77-136"><xref:System.Double.PositiveInfinity> <xref:System.Double.NegativeInfinity> Sıfır ise, sonsuz (veya), ya <xref:System.Double.NaN> da (sayı değil) döndürür `expression1`</span><span class="sxs-lookup"><span data-stu-id="0ad77-136">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="0ad77-137">Oluşturur <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="0ad77-137">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="0ad77-138">Integral (işaretli veya imzasız)</span><span class="sxs-lookup"><span data-stu-id="0ad77-138">Integral (signed or unsigned)</span></span>|<span data-ttu-id="0ad77-139"><xref:System.OverflowException>İntegral türler <xref:System.Double.PositiveInfinity> , veya kabul edilemediğinden integral türüne geri dönüştürme denendi. <xref:System.Double.NegativeInfinity><xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="0ad77-139">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="0ad77-140">`/`İşleç *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0ad77-140">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0ad77-141">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0ad77-141">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0ad77-142">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0ad77-142">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ad77-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ad77-143">Example</span></span>  

 <span data-ttu-id="0ad77-144">Bu örnek, `/` kayan nokta bölme gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ad77-144">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="0ad77-145">Sonuç iki işlenenin bir bölümü olur.</span><span class="sxs-lookup"><span data-stu-id="0ad77-145">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="0ad77-146">Yukarıdaki örnekteki ifadeler 2,5 ve 3,333333 değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ad77-146">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="0ad77-147">`Double`Her iki işlenen de tamsayı sabiti olsa da sonucun her zaman kayan nokta () olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0ad77-147">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad77-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ad77-148">See also</span></span>

- [<span data-ttu-id="0ad77-149">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ad77-149">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="0ad77-150">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ad77-150">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="0ad77-151">İşleç Sonuçlarının Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="0ad77-151">Data Types of Operator Results</span></span>](data-types-of-operator-results.md)
- [<span data-ttu-id="0ad77-152">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="0ad77-152">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="0ad77-153">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="0ad77-153">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0ad77-154">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="0ad77-154">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0ad77-155">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="0ad77-155">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
