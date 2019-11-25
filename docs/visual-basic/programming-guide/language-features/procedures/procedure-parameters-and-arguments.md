---
title: Parametreler ve Bağımsız Değişkenler
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 7dfbbcb39cf7bb05c8a62a7a252e425f287c9a09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352577"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="963ec-102">Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="963ec-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="963ec-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span><span class="sxs-lookup"><span data-stu-id="963ec-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="963ec-104">A procedure that performs repeated or shared tasks uses different information for each call.</span><span class="sxs-lookup"><span data-stu-id="963ec-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="963ec-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span><span class="sxs-lookup"><span data-stu-id="963ec-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="963ec-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span><span class="sxs-lookup"><span data-stu-id="963ec-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="963ec-107">The procedure's declaration defines its parameters.</span><span class="sxs-lookup"><span data-stu-id="963ec-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="963ec-108">You can define a procedure with no parameters, one parameter, or more than one.</span><span class="sxs-lookup"><span data-stu-id="963ec-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="963ec-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span><span class="sxs-lookup"><span data-stu-id="963ec-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="963ec-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span><span class="sxs-lookup"><span data-stu-id="963ec-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="963ec-111">The calling code supplies the arguments when it calls the procedure.</span><span class="sxs-lookup"><span data-stu-id="963ec-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="963ec-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span><span class="sxs-lookup"><span data-stu-id="963ec-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="963ec-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span><span class="sxs-lookup"><span data-stu-id="963ec-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="963ec-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span><span class="sxs-lookup"><span data-stu-id="963ec-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="963ec-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span><span class="sxs-lookup"><span data-stu-id="963ec-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Diagram that shows passing an argument to a parameter](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="963ec-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="963ec-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="963ec-118">Parameter Data Type</span><span class="sxs-lookup"><span data-stu-id="963ec-118">Parameter Data Type</span></span>  
 <span data-ttu-id="963ec-119">You define a data type for a parameter by using the `As` clause in its declaration.</span><span class="sxs-lookup"><span data-stu-id="963ec-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="963ec-120">For example, the following function accepts a string and an integer.</span><span class="sxs-lookup"><span data-stu-id="963ec-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="963ec-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span><span class="sxs-lookup"><span data-stu-id="963ec-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="963ec-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span><span class="sxs-lookup"><span data-stu-id="963ec-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="963ec-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span><span class="sxs-lookup"><span data-stu-id="963ec-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="963ec-124">Supply only arguments with data types that widen to the parameter data type;</span><span class="sxs-lookup"><span data-stu-id="963ec-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="963ec-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span><span class="sxs-lookup"><span data-stu-id="963ec-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="963ec-126">Use a conversion keyword to explicitly convert the data type.</span><span class="sxs-lookup"><span data-stu-id="963ec-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="963ec-127">Tür ParameTReleri</span><span class="sxs-lookup"><span data-stu-id="963ec-127">Type Parameters</span></span>  
 <span data-ttu-id="963ec-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span><span class="sxs-lookup"><span data-stu-id="963ec-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="963ec-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span><span class="sxs-lookup"><span data-stu-id="963ec-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="963ec-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="963ec-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963ec-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="963ec-131">See also</span></span>

- [<span data-ttu-id="963ec-132">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="963ec-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="963ec-133">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="963ec-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="963ec-134">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="963ec-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="963ec-135">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="963ec-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="963ec-136">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="963ec-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="963ec-137">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="963ec-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="963ec-138">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="963ec-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="963ec-139">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="963ec-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="963ec-140">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="963ec-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="963ec-141">Type Conversions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="963ec-141">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
