---
title: Yordam Aşırı Yüklemesi
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 41a971896fe726cbe9849fd46334910e7288afe0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352594"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="966e2-102">Yordam Aşırı Yüklemesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="966e2-102">Procedure Overloading (Visual Basic)</span></span>

<span data-ttu-id="966e2-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span><span class="sxs-lookup"><span data-stu-id="966e2-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="966e2-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span><span class="sxs-lookup"><span data-stu-id="966e2-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="966e2-105">You do this by varying the parameter list.</span><span class="sxs-lookup"><span data-stu-id="966e2-105">You do this by varying the parameter list.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="966e2-106">Overloading Rules</span><span class="sxs-lookup"><span data-stu-id="966e2-106">Overloading Rules</span></span>

<span data-ttu-id="966e2-107">When you overload a procedure, the following rules apply:</span><span class="sxs-lookup"><span data-stu-id="966e2-107">When you overload a procedure, the following rules apply:</span></span>

- <span data-ttu-id="966e2-108">**Same Name**.</span><span class="sxs-lookup"><span data-stu-id="966e2-108">**Same Name**.</span></span> <span data-ttu-id="966e2-109">Each overloaded version must use the same procedure name.</span><span class="sxs-lookup"><span data-stu-id="966e2-109">Each overloaded version must use the same procedure name.</span></span>

- <span data-ttu-id="966e2-110">**Different Signature**.</span><span class="sxs-lookup"><span data-stu-id="966e2-110">**Different Signature**.</span></span> <span data-ttu-id="966e2-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span><span class="sxs-lookup"><span data-stu-id="966e2-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>

  - <span data-ttu-id="966e2-112">Number of parameters</span><span class="sxs-lookup"><span data-stu-id="966e2-112">Number of parameters</span></span>

  - <span data-ttu-id="966e2-113">Order of the parameters</span><span class="sxs-lookup"><span data-stu-id="966e2-113">Order of the parameters</span></span>

  - <span data-ttu-id="966e2-114">Data types of the parameters</span><span class="sxs-lookup"><span data-stu-id="966e2-114">Data types of the parameters</span></span>

  - <span data-ttu-id="966e2-115">Number of type parameters (for a generic procedure)</span><span class="sxs-lookup"><span data-stu-id="966e2-115">Number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="966e2-116">Return type (only for a conversion operator)</span><span class="sxs-lookup"><span data-stu-id="966e2-116">Return type (only for a conversion operator)</span></span>

  <span data-ttu-id="966e2-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span><span class="sxs-lookup"><span data-stu-id="966e2-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="966e2-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span><span class="sxs-lookup"><span data-stu-id="966e2-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>

- <span data-ttu-id="966e2-119">**Items Not Part of Signature**.</span><span class="sxs-lookup"><span data-stu-id="966e2-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="966e2-120">You cannot overload a procedure without varying the signature.</span><span class="sxs-lookup"><span data-stu-id="966e2-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="966e2-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span><span class="sxs-lookup"><span data-stu-id="966e2-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>

  - <span data-ttu-id="966e2-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span><span class="sxs-lookup"><span data-stu-id="966e2-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

  - <span data-ttu-id="966e2-123">Parameter or type parameter names</span><span class="sxs-lookup"><span data-stu-id="966e2-123">Parameter or type parameter names</span></span>

  - <span data-ttu-id="966e2-124">Type parameter constraints (for a generic procedure)</span><span class="sxs-lookup"><span data-stu-id="966e2-124">Type parameter constraints (for a generic procedure)</span></span>

  - <span data-ttu-id="966e2-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span><span class="sxs-lookup"><span data-stu-id="966e2-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

  - <span data-ttu-id="966e2-126">Whether it returns a value</span><span class="sxs-lookup"><span data-stu-id="966e2-126">Whether it returns a value</span></span>

  - <span data-ttu-id="966e2-127">The data type of the return value (except for a conversion operator)</span><span class="sxs-lookup"><span data-stu-id="966e2-127">The data type of the return value (except for a conversion operator)</span></span>

  <span data-ttu-id="966e2-128">The items in the preceding list are not part of the signature.</span><span class="sxs-lookup"><span data-stu-id="966e2-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="966e2-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span><span class="sxs-lookup"><span data-stu-id="966e2-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>

- <span data-ttu-id="966e2-130">**Late-Bound Arguments**.</span><span class="sxs-lookup"><span data-stu-id="966e2-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="966e2-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="966e2-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>

## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="966e2-132">Multiple Versions of a Procedure</span><span class="sxs-lookup"><span data-stu-id="966e2-132">Multiple Versions of a Procedure</span></span>

<span data-ttu-id="966e2-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span><span class="sxs-lookup"><span data-stu-id="966e2-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="966e2-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span><span class="sxs-lookup"><span data-stu-id="966e2-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a><span data-ttu-id="966e2-135">Overloaded Versions</span><span class="sxs-lookup"><span data-stu-id="966e2-135">Overloaded Versions</span></span>

<span data-ttu-id="966e2-136">An alternative is to overload a single procedure name.</span><span class="sxs-lookup"><span data-stu-id="966e2-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="966e2-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span><span class="sxs-lookup"><span data-stu-id="966e2-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a><span data-ttu-id="966e2-138">Additional Overloads</span><span class="sxs-lookup"><span data-stu-id="966e2-138">Additional Overloads</span></span>

<span data-ttu-id="966e2-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span><span class="sxs-lookup"><span data-stu-id="966e2-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="966e2-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span><span class="sxs-lookup"><span data-stu-id="966e2-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>

## <a name="advantages-of-overloading"></a><span data-ttu-id="966e2-141">Advantages of Overloading</span><span class="sxs-lookup"><span data-stu-id="966e2-141">Advantages of Overloading</span></span>

<span data-ttu-id="966e2-142">The advantage of overloading a procedure is in the flexibility of the call.</span><span class="sxs-lookup"><span data-stu-id="966e2-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="966e2-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span><span class="sxs-lookup"><span data-stu-id="966e2-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="966e2-144">The following example illustrates this:</span><span class="sxs-lookup"><span data-stu-id="966e2-144">The following example illustrates this:</span></span>

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a><span data-ttu-id="966e2-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="966e2-145">See also</span></span>

- [<span data-ttu-id="966e2-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="966e2-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="966e2-147">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="966e2-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="966e2-148">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="966e2-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="966e2-149">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="966e2-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="966e2-150">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="966e2-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="966e2-151">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="966e2-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="966e2-152">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="966e2-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="966e2-153">Overloads</span><span class="sxs-lookup"><span data-stu-id="966e2-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="966e2-154">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="966e2-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
