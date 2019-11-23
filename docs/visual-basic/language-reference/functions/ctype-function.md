---
title: CType İşlevi
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 18b2d5a28cd6ef885ba8d237da6764dbbd108b59
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348090"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="f7bed-102">CType İşlevi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7bed-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="f7bed-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span><span class="sxs-lookup"><span data-stu-id="f7bed-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7bed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7bed-104">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="f7bed-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f7bed-105">Parts</span></span>

<span data-ttu-id="f7bed-106">`expression` Any valid expression.</span><span class="sxs-lookup"><span data-stu-id="f7bed-106">`expression` Any valid expression.</span></span> <span data-ttu-id="f7bed-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span><span class="sxs-lookup"><span data-stu-id="f7bed-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="f7bed-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span><span class="sxs-lookup"><span data-stu-id="f7bed-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="f7bed-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7bed-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="f7bed-110">You can also use the following functions to perform a type conversion:</span><span class="sxs-lookup"><span data-stu-id="f7bed-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="f7bed-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span><span class="sxs-lookup"><span data-stu-id="f7bed-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="f7bed-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f7bed-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>
> - <span data-ttu-id="f7bed-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f7bed-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="f7bed-114">These operators require that one type inherit from or implement the other type.</span><span class="sxs-lookup"><span data-stu-id="f7bed-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="f7bed-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span><span class="sxs-lookup"><span data-stu-id="f7bed-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="f7bed-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span><span class="sxs-lookup"><span data-stu-id="f7bed-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="f7bed-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span><span class="sxs-lookup"><span data-stu-id="f7bed-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="f7bed-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span><span class="sxs-lookup"><span data-stu-id="f7bed-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="f7bed-119">If a conversion fails at run time, the appropriate exception is thrown.</span><span class="sxs-lookup"><span data-stu-id="f7bed-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="f7bed-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span><span class="sxs-lookup"><span data-stu-id="f7bed-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="f7bed-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span><span class="sxs-lookup"><span data-stu-id="f7bed-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="f7bed-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span><span class="sxs-lookup"><span data-stu-id="f7bed-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="f7bed-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span><span class="sxs-lookup"><span data-stu-id="f7bed-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="f7bed-124">This makes `CType` act as an *overloaded operator*.</span><span class="sxs-lookup"><span data-stu-id="f7bed-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="f7bed-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span><span class="sxs-lookup"><span data-stu-id="f7bed-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="f7bed-126">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="f7bed-126">Overloading</span></span>

<span data-ttu-id="f7bed-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span><span class="sxs-lookup"><span data-stu-id="f7bed-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="f7bed-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span><span class="sxs-lookup"><span data-stu-id="f7bed-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="f7bed-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f7bed-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="f7bed-130">Converting Dynamic Objects</span><span class="sxs-lookup"><span data-stu-id="f7bed-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="f7bed-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span><span class="sxs-lookup"><span data-stu-id="f7bed-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="f7bed-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span><span class="sxs-lookup"><span data-stu-id="f7bed-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="f7bed-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7bed-133">Example</span></span>

<span data-ttu-id="f7bed-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span><span class="sxs-lookup"><span data-stu-id="f7bed-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="f7bed-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="f7bed-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7bed-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7bed-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="f7bed-137">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f7bed-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f7bed-138">Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f7bed-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="f7bed-139">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7bed-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="f7bed-140">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="f7bed-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="f7bed-141">Type Conversion in the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f7bed-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
