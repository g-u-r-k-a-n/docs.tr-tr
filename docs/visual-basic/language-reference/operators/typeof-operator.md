---
title: TypeOf İşleci
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350887"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="0374c-102">TypeOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0374c-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="0374c-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span><span class="sxs-lookup"><span data-stu-id="0374c-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="0374c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0374c-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="0374c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0374c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0374c-106">Returned.</span><span class="sxs-lookup"><span data-stu-id="0374c-106">Returned.</span></span> <span data-ttu-id="0374c-107">A `Boolean` value.</span><span class="sxs-lookup"><span data-stu-id="0374c-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="0374c-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0374c-108">Required.</span></span> <span data-ttu-id="0374c-109">Any expression that evaluates to a reference type.</span><span class="sxs-lookup"><span data-stu-id="0374c-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="0374c-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0374c-110">Required.</span></span> <span data-ttu-id="0374c-111">Any data type name.</span><span class="sxs-lookup"><span data-stu-id="0374c-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0374c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0374c-112">Remarks</span></span>  
 <span data-ttu-id="0374c-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span><span class="sxs-lookup"><span data-stu-id="0374c-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="0374c-114">The compatibility depends on the type category of `typename`.</span><span class="sxs-lookup"><span data-stu-id="0374c-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="0374c-115">The following table shows how compatibility is determined.</span><span class="sxs-lookup"><span data-stu-id="0374c-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="0374c-116">Type category of `typename`</span><span class="sxs-lookup"><span data-stu-id="0374c-116">Type category of `typename`</span></span>|<span data-ttu-id="0374c-117">Compatibility criterion</span><span class="sxs-lookup"><span data-stu-id="0374c-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="0374c-118">örneği</span><span class="sxs-lookup"><span data-stu-id="0374c-118">Class</span></span>|<span data-ttu-id="0374c-119">`objectexpression` is of type `typename` or inherits from `typename`</span><span class="sxs-lookup"><span data-stu-id="0374c-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="0374c-120">Yapı</span><span class="sxs-lookup"><span data-stu-id="0374c-120">Structure</span></span>|<span data-ttu-id="0374c-121">`objectexpression` is of type `typename`</span><span class="sxs-lookup"><span data-stu-id="0374c-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="0374c-122">Arabirim</span><span class="sxs-lookup"><span data-stu-id="0374c-122">Interface</span></span>|<span data-ttu-id="0374c-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span><span class="sxs-lookup"><span data-stu-id="0374c-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="0374c-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span><span class="sxs-lookup"><span data-stu-id="0374c-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="0374c-125">Otherwise, `result` is `False`.</span><span class="sxs-lookup"><span data-stu-id="0374c-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="0374c-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span><span class="sxs-lookup"><span data-stu-id="0374c-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="0374c-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span><span class="sxs-lookup"><span data-stu-id="0374c-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0374c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="0374c-128">Example</span></span>  
 <span data-ttu-id="0374c-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span><span class="sxs-lookup"><span data-stu-id="0374c-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="0374c-130">The variable `refInteger` has a run-time type of `Integer`.</span><span class="sxs-lookup"><span data-stu-id="0374c-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="0374c-131">It is compatible with `Integer` but not with `Double`.</span><span class="sxs-lookup"><span data-stu-id="0374c-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="0374c-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="0374c-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="0374c-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="0374c-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="0374c-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="0374c-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0374c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0374c-135">See also</span></span>

- [<span data-ttu-id="0374c-136">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="0374c-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="0374c-137">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="0374c-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="0374c-138">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0374c-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="0374c-139">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0374c-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0374c-140">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="0374c-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0374c-141">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="0374c-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
