---
title: 'Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: e562c0f5ec01380c792b4dc064554171cfb007e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339955"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="7340b-102">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7340b-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="7340b-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span><span class="sxs-lookup"><span data-stu-id="7340b-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="7340b-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span><span class="sxs-lookup"><span data-stu-id="7340b-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="7340b-105">In other cases, the procedure can change only its local copy of an argument.</span><span class="sxs-lookup"><span data-stu-id="7340b-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="7340b-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="7340b-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="7340b-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span><span class="sxs-lookup"><span data-stu-id="7340b-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="7340b-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span><span class="sxs-lookup"><span data-stu-id="7340b-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="7340b-109">Changing the Underlying Value</span><span class="sxs-lookup"><span data-stu-id="7340b-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="7340b-110">To change the underlying value of a procedure argument in the calling code</span><span class="sxs-lookup"><span data-stu-id="7340b-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="7340b-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span><span class="sxs-lookup"><span data-stu-id="7340b-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="7340b-112">In the calling code, pass a modifiable programming element as the argument.</span><span class="sxs-lookup"><span data-stu-id="7340b-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="7340b-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span><span class="sxs-lookup"><span data-stu-id="7340b-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="7340b-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span><span class="sxs-lookup"><span data-stu-id="7340b-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="7340b-115">See the example further down for a demonstration.</span><span class="sxs-lookup"><span data-stu-id="7340b-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="7340b-116">Changing Local Copies</span><span class="sxs-lookup"><span data-stu-id="7340b-116">Changing Local Copies</span></span>  
 <span data-ttu-id="7340b-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span><span class="sxs-lookup"><span data-stu-id="7340b-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="7340b-118">However, the procedure can change its local copy of such an argument.</span><span class="sxs-lookup"><span data-stu-id="7340b-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="7340b-119">To change the copy of a procedure argument in the procedure code</span><span class="sxs-lookup"><span data-stu-id="7340b-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="7340b-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span><span class="sxs-lookup"><span data-stu-id="7340b-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="7340b-121">veya</span><span class="sxs-lookup"><span data-stu-id="7340b-121">-or-</span></span>  
  
     <span data-ttu-id="7340b-122">In the calling code, enclose the argument in parentheses in the argument list.</span><span class="sxs-lookup"><span data-stu-id="7340b-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="7340b-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="7340b-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="7340b-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span><span class="sxs-lookup"><span data-stu-id="7340b-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="7340b-125">The underlying value in the calling code is not changed.</span><span class="sxs-lookup"><span data-stu-id="7340b-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7340b-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="7340b-126">Example</span></span>  
 <span data-ttu-id="7340b-127">The following example shows two procedures that take an array variable and operate on its elements.</span><span class="sxs-lookup"><span data-stu-id="7340b-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="7340b-128">The `increase` procedure simply adds one to each element.</span><span class="sxs-lookup"><span data-stu-id="7340b-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="7340b-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span><span class="sxs-lookup"><span data-stu-id="7340b-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="7340b-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="7340b-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="7340b-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="7340b-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="7340b-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="7340b-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="7340b-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span><span class="sxs-lookup"><span data-stu-id="7340b-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="7340b-134">Because `n` is a reference type, `replace` can also change its members.</span><span class="sxs-lookup"><span data-stu-id="7340b-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="7340b-135">You can prevent the procedure from modifying the variable itself in the calling code.</span><span class="sxs-lookup"><span data-stu-id="7340b-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="7340b-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="7340b-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7340b-137">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7340b-137">Compiling the Code</span></span>  
 <span data-ttu-id="7340b-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span><span class="sxs-lookup"><span data-stu-id="7340b-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="7340b-139">The default in Visual Basic is to pass arguments by value.</span><span class="sxs-lookup"><span data-stu-id="7340b-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="7340b-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span><span class="sxs-lookup"><span data-stu-id="7340b-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="7340b-141">This makes your code easier to read.</span><span class="sxs-lookup"><span data-stu-id="7340b-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7340b-142">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="7340b-142">.NET Framework Security</span></span>  
 <span data-ttu-id="7340b-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span><span class="sxs-lookup"><span data-stu-id="7340b-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="7340b-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span><span class="sxs-lookup"><span data-stu-id="7340b-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7340b-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7340b-145">See also</span></span>

- [<span data-ttu-id="7340b-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="7340b-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7340b-147">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="7340b-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7340b-148">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="7340b-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="7340b-149">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="7340b-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="7340b-150">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="7340b-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="7340b-151">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="7340b-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="7340b-152">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="7340b-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="7340b-153">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama</span><span class="sxs-lookup"><span data-stu-id="7340b-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="7340b-154">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="7340b-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="7340b-155">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="7340b-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
