---
title: Parametre Listesi
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: ec4ce0f12b540478d889832fb18f1ef008613f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346477"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="d7e74-102">Parametre Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7e74-102">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="d7e74-103">Specifies the parameters a procedure expects when it is called.</span><span class="sxs-lookup"><span data-stu-id="d7e74-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="d7e74-104">Multiple parameters are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="d7e74-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="d7e74-105">The following is the syntax for one parameter.</span><span class="sxs-lookup"><span data-stu-id="d7e74-105">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7e74-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7e74-106">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="d7e74-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d7e74-107">Parts</span></span>

`attributelist`  
<span data-ttu-id="d7e74-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d7e74-108">Optional.</span></span> <span data-ttu-id="d7e74-109">List of attributes that apply to this parameter.</span><span class="sxs-lookup"><span data-stu-id="d7e74-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="d7e74-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span><span class="sxs-lookup"><span data-stu-id="d7e74-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="d7e74-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d7e74-111">Optional.</span></span> <span data-ttu-id="d7e74-112">Specifies that this parameter is not required when the procedure is called.</span><span class="sxs-lookup"><span data-stu-id="d7e74-112">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="d7e74-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d7e74-113">Optional.</span></span> <span data-ttu-id="d7e74-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span><span class="sxs-lookup"><span data-stu-id="d7e74-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="d7e74-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d7e74-115">Optional.</span></span> <span data-ttu-id="d7e74-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span><span class="sxs-lookup"><span data-stu-id="d7e74-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="d7e74-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d7e74-117">Optional.</span></span> <span data-ttu-id="d7e74-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span><span class="sxs-lookup"><span data-stu-id="d7e74-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="d7e74-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span><span class="sxs-lookup"><span data-stu-id="d7e74-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="d7e74-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d7e74-120">Required.</span></span> <span data-ttu-id="d7e74-121">Name of the local variable representing the parameter.</span><span class="sxs-lookup"><span data-stu-id="d7e74-121">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="d7e74-122">Required if `Option Strict` is `On`.</span><span class="sxs-lookup"><span data-stu-id="d7e74-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="d7e74-123">Data type of the local variable representing the parameter.</span><span class="sxs-lookup"><span data-stu-id="d7e74-123">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="d7e74-124">Required for `Optional` parameters.</span><span class="sxs-lookup"><span data-stu-id="d7e74-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="d7e74-125">Any constant or constant expression that evaluates to the data type of the parameter.</span><span class="sxs-lookup"><span data-stu-id="d7e74-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="d7e74-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="d7e74-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7e74-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7e74-127">Remarks</span></span>

<span data-ttu-id="d7e74-128">Parameters are surrounded by parentheses and separated by commas.</span><span class="sxs-lookup"><span data-stu-id="d7e74-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="d7e74-129">A parameter can be declared with any data type.</span><span class="sxs-lookup"><span data-stu-id="d7e74-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="d7e74-130">If you do not specify `parametertype`, it defaults to `Object`.</span><span class="sxs-lookup"><span data-stu-id="d7e74-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="d7e74-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span><span class="sxs-lookup"><span data-stu-id="d7e74-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="d7e74-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d7e74-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="d7e74-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span><span class="sxs-lookup"><span data-stu-id="d7e74-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="d7e74-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span><span class="sxs-lookup"><span data-stu-id="d7e74-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="d7e74-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span><span class="sxs-lookup"><span data-stu-id="d7e74-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="d7e74-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d7e74-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="d7e74-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span><span class="sxs-lookup"><span data-stu-id="d7e74-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="d7e74-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="d7e74-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="d7e74-139">Kurallar</span><span class="sxs-lookup"><span data-stu-id="d7e74-139">Rules</span></span>

- <span data-ttu-id="d7e74-140">**Parentheses.**</span><span class="sxs-lookup"><span data-stu-id="d7e74-140">**Parentheses.**</span></span> <span data-ttu-id="d7e74-141">If you specify a parameter list, you must enclose it in parentheses.</span><span class="sxs-lookup"><span data-stu-id="d7e74-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="d7e74-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span><span class="sxs-lookup"><span data-stu-id="d7e74-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="d7e74-143">This improves the readability of your code by clarifying that the element is a procedure.</span><span class="sxs-lookup"><span data-stu-id="d7e74-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="d7e74-144">**Optional Parameters.**</span><span class="sxs-lookup"><span data-stu-id="d7e74-144">**Optional Parameters.**</span></span> <span data-ttu-id="d7e74-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span><span class="sxs-lookup"><span data-stu-id="d7e74-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="d7e74-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span><span class="sxs-lookup"><span data-stu-id="d7e74-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="d7e74-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="d7e74-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="d7e74-148">**Parameter Arrays.**</span><span class="sxs-lookup"><span data-stu-id="d7e74-148">**Parameter Arrays.**</span></span> <span data-ttu-id="d7e74-149">You must specify `ByVal` for a `ParamArray` parameter.</span><span class="sxs-lookup"><span data-stu-id="d7e74-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="d7e74-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span><span class="sxs-lookup"><span data-stu-id="d7e74-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="d7e74-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="d7e74-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="d7e74-152">**Passing Mechanism.**</span><span class="sxs-lookup"><span data-stu-id="d7e74-152">**Passing Mechanism.**</span></span> <span data-ttu-id="d7e74-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span><span class="sxs-lookup"><span data-stu-id="d7e74-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="d7e74-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span><span class="sxs-lookup"><span data-stu-id="d7e74-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="d7e74-155">**Parameter Names.**</span><span class="sxs-lookup"><span data-stu-id="d7e74-155">**Parameter Names.**</span></span> <span data-ttu-id="d7e74-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span><span class="sxs-lookup"><span data-stu-id="d7e74-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="d7e74-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d7e74-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="d7e74-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7e74-158">Example</span></span>

<span data-ttu-id="d7e74-159">The following example shows a `Function` procedure that defines two parameters.</span><span class="sxs-lookup"><span data-stu-id="d7e74-159">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="d7e74-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7e74-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="d7e74-161">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="d7e74-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d7e74-162">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="d7e74-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d7e74-163">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="d7e74-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="d7e74-164">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="d7e74-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="d7e74-165">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="d7e74-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="d7e74-166">Attributes overview</span><span class="sxs-lookup"><span data-stu-id="d7e74-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="d7e74-167">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="d7e74-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
