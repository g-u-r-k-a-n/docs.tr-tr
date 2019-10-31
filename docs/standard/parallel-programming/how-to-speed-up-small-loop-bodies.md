---
title: 'Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
ms.openlocfilehash: 29d7fa8200ddd972c1a5c98ea6f30a7c8ff732e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139755"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="6cf0f-102">Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma</span><span class="sxs-lookup"><span data-stu-id="6cf0f-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="6cf0f-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngüsünün küçük bir gövdesi olduğunda, [for](../../csharp/language-reference/keywords/for.md) döngüsü C# ve Visual Basic [for](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) döngüsü gibi eşdeğer sıralı döngüden daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="6cf0f-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="6cf0f-104">Verilerin bölümlenmesi ve her döngü yinelemesinde bir temsilciyi çağırma maliyeti nedeniyle daha yavaş performans oluşur.</span><span class="sxs-lookup"><span data-stu-id="6cf0f-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="6cf0f-105"><xref:System.Collections.Concurrent.Partitioner> sınıfı, bu tür senaryolara yönelik olarak, temsilci gövdesi için sıralı bir döngü sağlamanıza olanak tanıyan <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> yöntemini sağlar, böylece her yineleme için bir kez değil, her bölüm için bir kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6cf0f-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="6cf0f-106">Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="6cf0f-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cf0f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cf0f-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="6cf0f-108">Bu örnekte gösterilen yaklaşım, döngü en az miktarda iş gerçekleştirdiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="6cf0f-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="6cf0f-109">Çalışma daha pahalı hale geldiği için, varsayılan bölümleyici ile bir <xref:System.Threading.Tasks.Parallel.For%2A> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngüsü kullanarak büyük olasılıkla aynı veya daha iyi bir performans alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="6cf0f-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf0f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cf0f-110">See also</span></span>

- [<span data-ttu-id="6cf0f-111">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="6cf0f-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="6cf0f-112">PLINQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="6cf0f-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="6cf0f-113">Yineleyiciler (C#)</span><span class="sxs-lookup"><span data-stu-id="6cf0f-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="6cf0f-114">Yineleyiciler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cf0f-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="6cf0f-115">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="6cf0f-115">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
