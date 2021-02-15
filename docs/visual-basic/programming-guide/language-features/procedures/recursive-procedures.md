---
description: 'Daha fazla bilgi edinin: özyinelemeli yordamlar (Visual Basic)'
title: Özyinelemeli Yordamlar
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 378b279a6664cd494fb2e26ff3276afcea56cc16
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466568"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="59af6-103">Özyinelemeli Yordamlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59af6-103">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="59af6-104">*Özyinelemeli* yordam kendisini çağıran bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="59af6-104">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="59af6-105">Genel olarak, Visual Basic kodu yazmak için en etkili yol değildir.</span><span class="sxs-lookup"><span data-stu-id="59af6-105">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="59af6-106">Aşağıdaki yordam, orijinal bağımsız değişkeninin faktöriyelini hesaplamak için özyineleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="59af6-106">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="59af6-107">Özyinelemeli yordamlarla ilgili konular</span><span class="sxs-lookup"><span data-stu-id="59af6-107">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="59af6-108">**Koşulları sınırlandırma**.</span><span class="sxs-lookup"><span data-stu-id="59af6-108">**Limiting Conditions**.</span></span> <span data-ttu-id="59af6-109">Özyineleme 'yi sonlandıran en az bir koşul için test etmek üzere yinelemeli bir yordam tasarlaması gerekir ve ayrıca makul sayıda özyinelemeli çağrı içinde böyle bir koşulun karşılanmadığı durumu da işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="59af6-109">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="59af6-110">Başarısız olmadan karşılanabilecek en az bir koşul olmadan, yordamınız sonsuz bir döngüde yürütmenin yüksek bir riskini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="59af6-110">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="59af6-111">**Bellek kullanımı**.</span><span class="sxs-lookup"><span data-stu-id="59af6-111">**Memory Usage**.</span></span> <span data-ttu-id="59af6-112">Uygulamanızın yerel değişkenler için sınırlı miktarda alanı vardır.</span><span class="sxs-lookup"><span data-stu-id="59af6-112">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="59af6-113">Her bir yordam kendi kendine her çağırdığında, yerel değişkenlerinin ek kopyaları için bu alanın daha fazlasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="59af6-113">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="59af6-114">Bu işlem süresiz olarak devam ederse, bir hataya neden olur <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="59af6-114">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="59af6-115">**Verimlilik**.</span><span class="sxs-lookup"><span data-stu-id="59af6-115">**Efficiency**.</span></span> <span data-ttu-id="59af6-116">Özyineleme için neredeyse her zaman bir döngü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59af6-116">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="59af6-117">Döngü, bağımsız değişken geçirme, ek depolama başlatma ve değer döndürme ek yüküne sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="59af6-117">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="59af6-118">Performans özyinelemeli çağrılar olmadan çok daha iyi olabilir.</span><span class="sxs-lookup"><span data-stu-id="59af6-118">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="59af6-119">**Karşılıklı özyineleme**.</span><span class="sxs-lookup"><span data-stu-id="59af6-119">**Mutual Recursion**.</span></span> <span data-ttu-id="59af6-120">İki yordam de varsa, çok kötü performans veya sonsuz bir döngü gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59af6-120">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="59af6-121">Böyle bir tasarım, tek bir özyinelemeli yordamla aynı sorunları sunar, ancak algılaması ve hata ayıklaması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="59af6-121">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="59af6-122">**Parantez Ile çağırma**.</span><span class="sxs-lookup"><span data-stu-id="59af6-122">**Calling with Parentheses**.</span></span> <span data-ttu-id="59af6-123">Bir `Function` yordam yinelemeli olarak çağırdığında, bağımsız değişken listesi olmasa bile, parantez ile yordam adını izlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="59af6-123">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="59af6-124">Aksi takdirde, işlev adı işlevin dönüş değerini temsil eden olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="59af6-124">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="59af6-125">**Test ediliyor**.</span><span class="sxs-lookup"><span data-stu-id="59af6-125">**Testing**.</span></span> <span data-ttu-id="59af6-126">Özyinelemeli bir yordam yazarsanız, her zaman sınırlandırma koşullarını karşıladığından emin olmak için bunu dikkatle sınamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="59af6-126">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="59af6-127">Ayrıca çok fazla özyinelemeli çağrı olduğundan belleği tükendiğinizden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="59af6-127">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="59af6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59af6-128">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="59af6-129">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="59af6-129">Procedures</span></span>](index.md)
- [<span data-ttu-id="59af6-130">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="59af6-130">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="59af6-131">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="59af6-131">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="59af6-132">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="59af6-132">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="59af6-133">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="59af6-133">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="59af6-134">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="59af6-134">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="59af6-135">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="59af6-135">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="59af6-136">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="59af6-136">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="59af6-137">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="59af6-137">Loop Structures</span></span>](../control-flow/loop-structures.md)
