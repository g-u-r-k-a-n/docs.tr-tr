---
title: Shared
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349125"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="aaef3-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aaef3-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="aaef3-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span><span class="sxs-lookup"><span data-stu-id="aaef3-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaef3-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aaef3-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="aaef3-105">When to Use Shared</span><span class="sxs-lookup"><span data-stu-id="aaef3-105">When to Use Shared</span></span>  
 <span data-ttu-id="aaef3-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span><span class="sxs-lookup"><span data-stu-id="aaef3-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="aaef3-107">This is useful, for example, if the value of a variable applies to the entire application.</span><span class="sxs-lookup"><span data-stu-id="aaef3-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="aaef3-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span><span class="sxs-lookup"><span data-stu-id="aaef3-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="aaef3-109">Sharing does not alter the access level of a member.</span><span class="sxs-lookup"><span data-stu-id="aaef3-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="aaef3-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span><span class="sxs-lookup"><span data-stu-id="aaef3-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="aaef3-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="aaef3-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="aaef3-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="aaef3-112">Rules</span></span>  
  
- <span data-ttu-id="aaef3-113">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="aaef3-113">**Declaration Context.**</span></span> <span data-ttu-id="aaef3-114">You can use `Shared` only at module level.</span><span class="sxs-lookup"><span data-stu-id="aaef3-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="aaef3-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span><span class="sxs-lookup"><span data-stu-id="aaef3-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="aaef3-116">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="aaef3-116">**Combined Modifiers.**</span></span> <span data-ttu-id="aaef3-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="aaef3-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
- <span data-ttu-id="aaef3-118">**Accessing.**</span><span class="sxs-lookup"><span data-stu-id="aaef3-118">**Accessing.**</span></span> <span data-ttu-id="aaef3-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span><span class="sxs-lookup"><span data-stu-id="aaef3-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="aaef3-120">You do not even have to create an instance of a class or structure to access its shared members.</span><span class="sxs-lookup"><span data-stu-id="aaef3-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="aaef3-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span><span class="sxs-lookup"><span data-stu-id="aaef3-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- <span data-ttu-id="aaef3-122">**Implicit Sharing.**</span><span class="sxs-lookup"><span data-stu-id="aaef3-122">**Implicit Sharing.**</span></span> <span data-ttu-id="aaef3-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span><span class="sxs-lookup"><span data-stu-id="aaef3-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="aaef3-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span><span class="sxs-lookup"><span data-stu-id="aaef3-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="aaef3-125">Davranış</span><span class="sxs-lookup"><span data-stu-id="aaef3-125">Behavior</span></span>  
  
- <span data-ttu-id="aaef3-126">**Storage.**</span><span class="sxs-lookup"><span data-stu-id="aaef3-126">**Storage.**</span></span> <span data-ttu-id="aaef3-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span><span class="sxs-lookup"><span data-stu-id="aaef3-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="aaef3-128">Similarly, a shared procedure or property holds only one set of local variables.</span><span class="sxs-lookup"><span data-stu-id="aaef3-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
- <span data-ttu-id="aaef3-129">**Accessing through an Instance Variable.**</span><span class="sxs-lookup"><span data-stu-id="aaef3-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="aaef3-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span><span class="sxs-lookup"><span data-stu-id="aaef3-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="aaef3-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span><span class="sxs-lookup"><span data-stu-id="aaef3-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
- <span data-ttu-id="aaef3-132">**Accessing through an Instance Expression.**</span><span class="sxs-lookup"><span data-stu-id="aaef3-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="aaef3-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span><span class="sxs-lookup"><span data-stu-id="aaef3-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="aaef3-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span><span class="sxs-lookup"><span data-stu-id="aaef3-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="aaef3-135">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="aaef3-135">The following example illustrates this.</span></span>  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     <span data-ttu-id="aaef3-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span><span class="sxs-lookup"><span data-stu-id="aaef3-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="aaef3-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span><span class="sxs-lookup"><span data-stu-id="aaef3-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="aaef3-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span><span class="sxs-lookup"><span data-stu-id="aaef3-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="aaef3-139">The `Shared` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="aaef3-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="aaef3-140">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="aaef3-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="aaef3-141">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="aaef3-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="aaef3-142">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="aaef3-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="aaef3-143">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="aaef3-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="aaef3-144">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="aaef3-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="aaef3-145">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="aaef3-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="aaef3-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaef3-146">See also</span></span>

- [<span data-ttu-id="aaef3-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="aaef3-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="aaef3-148">Static</span><span class="sxs-lookup"><span data-stu-id="aaef3-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="aaef3-149">Lifetime in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aaef3-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="aaef3-150">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="aaef3-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="aaef3-151">Yapılar</span><span class="sxs-lookup"><span data-stu-id="aaef3-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="aaef3-152">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="aaef3-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
