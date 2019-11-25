---
title: 'How to: Declare and Call a Default Property'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: b01188ed8a9ff4da95a6975dcac3509625fdffb2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349678"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="b4b86-102">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="b4b86-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="b4b86-103">A *default property* is a class or structure property that your code can access without specifying it.</span><span class="sxs-lookup"><span data-stu-id="b4b86-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="b4b86-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span><span class="sxs-lookup"><span data-stu-id="b4b86-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="b4b86-105">A class or structure can have at most one default property.</span><span class="sxs-lookup"><span data-stu-id="b4b86-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="b4b86-106">However, you can overload a default property and have more than one version of it.</span><span class="sxs-lookup"><span data-stu-id="b4b86-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="b4b86-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="b4b86-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="b4b86-108">To declare a default property</span><span class="sxs-lookup"><span data-stu-id="b4b86-108">To declare a default property</span></span>  
  
1. <span data-ttu-id="b4b86-109">Declare the property in the normal way.</span><span class="sxs-lookup"><span data-stu-id="b4b86-109">Declare the property in the normal way.</span></span> <span data-ttu-id="b4b86-110">Do not specify the `Shared` or `Private` keyword.</span><span class="sxs-lookup"><span data-stu-id="b4b86-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="b4b86-111">Include the `Default` keyword in the property declaration.</span><span class="sxs-lookup"><span data-stu-id="b4b86-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="b4b86-112">Specify at least one parameter for the property.</span><span class="sxs-lookup"><span data-stu-id="b4b86-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="b4b86-113">You cannot define a default property that does not take at least one argument.</span><span class="sxs-lookup"><span data-stu-id="b4b86-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="b4b86-114">To call a default property</span><span class="sxs-lookup"><span data-stu-id="b4b86-114">To call a default property</span></span>  
  
1. <span data-ttu-id="b4b86-115">Declare a variable of the containing class or structure type.</span><span class="sxs-lookup"><span data-stu-id="b4b86-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="b4b86-116">Use the variable name alone in an expression where you would normally include the property name.</span><span class="sxs-lookup"><span data-stu-id="b4b86-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="b4b86-117">Follow the variable name with an argument list in parentheses.</span><span class="sxs-lookup"><span data-stu-id="b4b86-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="b4b86-118">A default property must take at least one argument.</span><span class="sxs-lookup"><span data-stu-id="b4b86-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="b4b86-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span><span class="sxs-lookup"><span data-stu-id="b4b86-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="b4b86-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span><span class="sxs-lookup"><span data-stu-id="b4b86-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="b4b86-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span><span class="sxs-lookup"><span data-stu-id="b4b86-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="b4b86-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4b86-122">Example</span></span>  
 <span data-ttu-id="b4b86-123">The following example declares a default property on a class.</span><span class="sxs-lookup"><span data-stu-id="b4b86-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="b4b86-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4b86-124">Example</span></span>  
 <span data-ttu-id="b4b86-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span><span class="sxs-lookup"><span data-stu-id="b4b86-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="b4b86-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span><span class="sxs-lookup"><span data-stu-id="b4b86-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="b4b86-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span><span class="sxs-lookup"><span data-stu-id="b4b86-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b4b86-128">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b4b86-128">Robust Programming</span></span>  
 <span data-ttu-id="b4b86-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span><span class="sxs-lookup"><span data-stu-id="b4b86-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="b4b86-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span><span class="sxs-lookup"><span data-stu-id="b4b86-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="b4b86-131">This can lead to compiler errors or subtle run-time logic errors.</span><span class="sxs-lookup"><span data-stu-id="b4b86-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="b4b86-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span><span class="sxs-lookup"><span data-stu-id="b4b86-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="b4b86-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span><span class="sxs-lookup"><span data-stu-id="b4b86-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="b4b86-134">Because of these disadvantages, you should consider not defining default properties.</span><span class="sxs-lookup"><span data-stu-id="b4b86-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="b4b86-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span><span class="sxs-lookup"><span data-stu-id="b4b86-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b86-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4b86-136">See also</span></span>

- [<span data-ttu-id="b4b86-137">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="b4b86-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b4b86-138">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="b4b86-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b4b86-139">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="b4b86-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="b4b86-140">Default</span><span class="sxs-lookup"><span data-stu-id="b4b86-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)
- [<span data-ttu-id="b4b86-141">Differences Between Properties and Variables in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4b86-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="b4b86-142">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b4b86-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="b4b86-143">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="b4b86-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="b4b86-144">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="b4b86-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="b4b86-145">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="b4b86-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="b4b86-146">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="b4b86-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
