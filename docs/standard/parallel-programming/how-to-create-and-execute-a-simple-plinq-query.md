---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: basit bir PLıNQ sorgusu oluşturma ve yürütme'
title: 'Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: 7f9147dce03bceb07085e84ed5bc9967ce08c17c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702060"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="2d3e2-103">Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="2d3e2-103">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="2d3e2-104">Bu makaledeki örnekte, kaynak dizideki genişletme yöntemi kullanılarak basit bir paralel dil tümleşik sorgu (LINQ) sorgusunun oluşturulması <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> ve yöntemi kullanılarak sorgu yürütülmesi gösterilmektedir <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2d3e2-104">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d3e2-105">Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d3e2-105">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="2d3e2-106">C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="2d3e2-106">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d3e2-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d3e2-107">Example</span></span>  

 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="2d3e2-108">Bu örnek, sonuç sırasının sıralaması önemli olmadığında herhangi bir paralel LINQ sorgusunun oluşturulması ve yürütülmesi için temel düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d3e2-108">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="2d3e2-109">Sıralanmamış sorgular genellikle sıralanmış sorgulardan daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="2d3e2-109">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="2d3e2-110">Sorgu, kaynağı birden çok iş parçacığında zaman uyumsuz olarak yürütülen görevlere bölümler.</span><span class="sxs-lookup"><span data-stu-id="2d3e2-110">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="2d3e2-111">Her görevin tamamlandığı sıra, yalnızca bölümdeki öğeleri işlemek için gereken iş miktarına değil, aynı zamanda işletim sisteminin her bir iş parçacığını nasıl zamanlıyor gibi dış faktörlerden de farklı olur.</span><span class="sxs-lookup"><span data-stu-id="2d3e2-111">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="2d3e2-112">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2d3e2-112">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="2d3e2-113">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="2d3e2-113">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="2d3e2-114">Bir sorgudaki öğelerin sıralamasını koruma hakkında daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ sorgusunda sıralamayı denetleme](how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="2d3e2-114">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d3e2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d3e2-115">See also</span></span>

- [<span data-ttu-id="2d3e2-116">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2d3e2-116">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
