---
title: 'Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: 349cc8d78e9a080d720e09a7e3e5e314752605c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106954"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="beddd-102">Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="beddd-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="beddd-103">Aşağıdaki örnek, kaynak dizideki <xref:System.Linq.ParallelEnumerable.AsParallel%2A> genişletme yöntemi kullanılarak basit bir paralel LINQ sorgusunun nasıl oluşturulacağını ve <xref:System.Linq.ParallelEnumerable.ForAll%2A> yöntemi kullanılarak sorgunun nasıl yürütüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="beddd-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="beddd-104">Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="beddd-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="beddd-105">Veya Visual Basic içindeki C# lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="beddd-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="beddd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="beddd-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="beddd-107">Bu örnek, sonuç sırasının sıralaması önemli olmadığında herhangi bir paralel LINQ sorgusunun oluşturulması ve yürütülmesi için temel düzeni gösterir; Sıralanmamış sorgular genellikle sıralanmış sorgulardan daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="beddd-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="beddd-108">Sorgu, kaynağı birden çok iş parçacığında zaman uyumsuz olarak yürütülen görevlere bölümler.</span><span class="sxs-lookup"><span data-stu-id="beddd-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="beddd-109">Her görevin tamamlandığı sıra, yalnızca bölümdeki öğeleri işlemek için gereken iş miktarına değil, aynı zamanda işletim sisteminin her bir iş parçacığını nasıl zamanlıyor gibi dış faktörlerden de farklı olur.</span><span class="sxs-lookup"><span data-stu-id="beddd-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="beddd-110">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="beddd-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="beddd-111">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="beddd-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="beddd-112">Bir sorgudaki öğelerin sıralamasını koruma hakkında daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ sorgusunda sıralamayı denetleme](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="beddd-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beddd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="beddd-113">See also</span></span>

- [<span data-ttu-id="beddd-114">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="beddd-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
