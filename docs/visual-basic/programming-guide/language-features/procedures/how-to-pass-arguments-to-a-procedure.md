---
title: 'Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 0267eed7c145988d61de715fd661bd4906d8d57d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344838"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="cadcf-102">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cadcf-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="cadcf-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span><span class="sxs-lookup"><span data-stu-id="cadcf-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="cadcf-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span><span class="sxs-lookup"><span data-stu-id="cadcf-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="cadcf-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span><span class="sxs-lookup"><span data-stu-id="cadcf-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="cadcf-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span><span class="sxs-lookup"><span data-stu-id="cadcf-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="cadcf-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span><span class="sxs-lookup"><span data-stu-id="cadcf-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="cadcf-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="cadcf-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="cadcf-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="cadcf-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="cadcf-110">To pass one or more arguments to a procedure</span><span class="sxs-lookup"><span data-stu-id="cadcf-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="cadcf-111">In the calling statement, follow the procedure name with parentheses.</span><span class="sxs-lookup"><span data-stu-id="cadcf-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="cadcf-112">Inside the parentheses, put an argument list.</span><span class="sxs-lookup"><span data-stu-id="cadcf-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="cadcf-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span><span class="sxs-lookup"><span data-stu-id="cadcf-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="cadcf-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span><span class="sxs-lookup"><span data-stu-id="cadcf-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="cadcf-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span><span class="sxs-lookup"><span data-stu-id="cadcf-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="cadcf-116">If you omit it, the procedure uses the default value defined for that parameter.</span><span class="sxs-lookup"><span data-stu-id="cadcf-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="cadcf-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span><span class="sxs-lookup"><span data-stu-id="cadcf-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="cadcf-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span><span class="sxs-lookup"><span data-stu-id="cadcf-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="cadcf-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span><span class="sxs-lookup"><span data-stu-id="cadcf-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="cadcf-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span><span class="sxs-lookup"><span data-stu-id="cadcf-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="cadcf-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span><span class="sxs-lookup"><span data-stu-id="cadcf-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="cadcf-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span><span class="sxs-lookup"><span data-stu-id="cadcf-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadcf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cadcf-123">See also</span></span>

- [<span data-ttu-id="cadcf-124">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cadcf-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="cadcf-125">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="cadcf-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="cadcf-126">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="cadcf-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="cadcf-127">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="cadcf-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="cadcf-128">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="cadcf-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="cadcf-129">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="cadcf-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="cadcf-130">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="cadcf-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="cadcf-131">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="cadcf-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="cadcf-132">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="cadcf-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="cadcf-133">Object-Oriented Programming (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cadcf-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
