---
title: Çevrim Yapıları
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 0a75205a7d52c332094d624d082e5db3e89447f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353922"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="115b9-102">Çevrim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="115b9-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="115b9-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span><span class="sxs-lookup"><span data-stu-id="115b9-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="115b9-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span><span class="sxs-lookup"><span data-stu-id="115b9-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="115b9-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span><span class="sxs-lookup"><span data-stu-id="115b9-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Flow chart that shows a Do...Until loop.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="115b9-107">While Loops</span><span class="sxs-lookup"><span data-stu-id="115b9-107">While Loops</span></span>  
 <span data-ttu-id="115b9-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span><span class="sxs-lookup"><span data-stu-id="115b9-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="115b9-109">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="115b9-109">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="115b9-110">Do Loops</span><span class="sxs-lookup"><span data-stu-id="115b9-110">Do Loops</span></span>  
 <span data-ttu-id="115b9-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span><span class="sxs-lookup"><span data-stu-id="115b9-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="115b9-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span><span class="sxs-lookup"><span data-stu-id="115b9-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="115b9-113">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="115b9-113">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="115b9-114">For Loops</span><span class="sxs-lookup"><span data-stu-id="115b9-114">For Loops</span></span>  
 <span data-ttu-id="115b9-115">The `For`...`Next` construction performs the loop a set number of times.</span><span class="sxs-lookup"><span data-stu-id="115b9-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="115b9-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span><span class="sxs-lookup"><span data-stu-id="115b9-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="115b9-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span><span class="sxs-lookup"><span data-stu-id="115b9-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="115b9-118">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="115b9-118">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="115b9-119">For Each Loops</span><span class="sxs-lookup"><span data-stu-id="115b9-119">For Each Loops</span></span>  
 <span data-ttu-id="115b9-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span><span class="sxs-lookup"><span data-stu-id="115b9-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="115b9-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span><span class="sxs-lookup"><span data-stu-id="115b9-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="115b9-122">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="115b9-122">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="115b9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="115b9-123">See also</span></span>

- [<span data-ttu-id="115b9-124">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="115b9-124">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="115b9-125">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="115b9-125">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="115b9-126">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="115b9-126">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="115b9-127">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="115b9-127">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
