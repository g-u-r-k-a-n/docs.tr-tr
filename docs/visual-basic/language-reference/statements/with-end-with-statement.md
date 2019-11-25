---
title: With...End With Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: eb8790d0d8f82232a4b10e4e0e30165745c065c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352730"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="01e10-102">With...End With Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01e10-102">With...End With Statement (Visual Basic)</span></span>

<span data-ttu-id="01e10-103">Deyimlerin, nesne veya yapı üyelerine erişim sağlarken basitleştirilmiş bir sözdizimi kullanabilmesi için sürekli olarak tek bir nesneye veya yapıya başvuran bir dizi deyim yürütür.</span><span class="sxs-lookup"><span data-stu-id="01e10-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="01e10-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span><span class="sxs-lookup"><span data-stu-id="01e10-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>

## <a name="syntax"></a><span data-ttu-id="01e10-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01e10-105">Syntax</span></span>

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a><span data-ttu-id="01e10-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="01e10-106">Parts</span></span>

|<span data-ttu-id="01e10-107">Terim</span><span class="sxs-lookup"><span data-stu-id="01e10-107">Term</span></span>|<span data-ttu-id="01e10-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="01e10-108">Definition</span></span>|
|---|---|
|`objectExpression`|<span data-ttu-id="01e10-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="01e10-109">Required.</span></span> <span data-ttu-id="01e10-110">Nesne olarak değerlendirilen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="01e10-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="01e10-111">İfade rasgele karmaşık olabilir ve yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="01e10-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="01e10-112">İfade, basit türler de dahil olmak üzere herhangi bir veri türü olarak değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="01e10-112">The expression can evaluate to any data type, including elementary types.</span></span>|
|`statements`|<span data-ttu-id="01e10-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="01e10-113">Optional.</span></span> <span data-ttu-id="01e10-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span><span class="sxs-lookup"><span data-stu-id="01e10-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|
|`End With`|<span data-ttu-id="01e10-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="01e10-115">Required.</span></span> <span data-ttu-id="01e10-116">Terminates the definition of the `With` block.</span><span class="sxs-lookup"><span data-stu-id="01e10-116">Terminates the definition of the `With` block.</span></span>|

## <a name="remarks"></a><span data-ttu-id="01e10-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01e10-117">Remarks</span></span>

<span data-ttu-id="01e10-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span><span class="sxs-lookup"><span data-stu-id="01e10-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="01e10-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span><span class="sxs-lookup"><span data-stu-id="01e10-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>

<span data-ttu-id="01e10-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span><span class="sxs-lookup"><span data-stu-id="01e10-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>

<span data-ttu-id="01e10-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span><span class="sxs-lookup"><span data-stu-id="01e10-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>

- <span data-ttu-id="01e10-122">Karmaşık ifadenin üyelerine birden çok kez başvuruda bulunmak için sonucu geçici bir değişkene atamanıza veya karmaşık ifadeyi birden çok kez değerlendirmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="01e10-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>

- <span data-ttu-id="01e10-123">Yinelenen niteleyici ifadeleri ortadan kaldırarak kodunuzu daha okunur hale getirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01e10-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>

<span data-ttu-id="01e10-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span><span class="sxs-lookup"><span data-stu-id="01e10-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="01e10-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span><span class="sxs-lookup"><span data-stu-id="01e10-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="01e10-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span><span class="sxs-lookup"><span data-stu-id="01e10-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="01e10-127">İki durumda da sorun şudur: Yapı yalnızca çağrı yığınında mevcuttur ve değiştirilmiş bir yapı üyesinin bu durumlarda, programdaki diğer herhangi bir kodun değişikliği gözlemleyebileceği şekilde bir konuma yazabilmesinin hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="01e10-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>

<span data-ttu-id="01e10-128">The `objectExpression` is evaluated once, upon entry into the block.</span><span class="sxs-lookup"><span data-stu-id="01e10-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="01e10-129">You can't reassign the `objectExpression` from within the `With` block.</span><span class="sxs-lookup"><span data-stu-id="01e10-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>

<span data-ttu-id="01e10-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span><span class="sxs-lookup"><span data-stu-id="01e10-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="01e10-131">Diğer nesnelerin yöntemlerini ve özelliklerini kullanabilirsiniz, ancak bunları nesne adlarıyla nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="01e10-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>

<span data-ttu-id="01e10-132">You can place one `With...End With` statement within another.</span><span class="sxs-lookup"><span data-stu-id="01e10-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="01e10-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span><span class="sxs-lookup"><span data-stu-id="01e10-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="01e10-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span><span class="sxs-lookup"><span data-stu-id="01e10-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>

<span data-ttu-id="01e10-135">You can't branch into a `With` statement block from outside the block.</span><span class="sxs-lookup"><span data-stu-id="01e10-135">You can't branch into a `With` statement block from outside the block.</span></span>

<span data-ttu-id="01e10-136">Blok bir döngü içermediği sürece deyimler yalnızca bir kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="01e10-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="01e10-137">Farklı türlerde denetim yapılarını iç içe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01e10-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="01e10-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="01e10-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

> [!NOTE]
> <span data-ttu-id="01e10-139">You can use the `With` keyword in object initializers also.</span><span class="sxs-lookup"><span data-stu-id="01e10-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="01e10-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="01e10-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>
>
> <span data-ttu-id="01e10-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span><span class="sxs-lookup"><span data-stu-id="01e10-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>

## <a name="example"></a><span data-ttu-id="01e10-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="01e10-142">Example</span></span>

<span data-ttu-id="01e10-143">In the following example, each `With` block executes a series of statements on a single object.</span><span class="sxs-lookup"><span data-stu-id="01e10-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a><span data-ttu-id="01e10-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="01e10-144">Example</span></span>

<span data-ttu-id="01e10-145">The following example nests `With…End With` statements.</span><span class="sxs-lookup"><span data-stu-id="01e10-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="01e10-146">Within the nested `With` statement, the syntax refers to the inner object.</span><span class="sxs-lookup"><span data-stu-id="01e10-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="01e10-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01e10-147">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="01e10-148">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="01e10-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="01e10-149">Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="01e10-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="01e10-150">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="01e10-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
