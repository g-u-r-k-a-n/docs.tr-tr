---
title: 'Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: 67863346046b0c400529b87355c11f97d0c3f01f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827093"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="51dfe-102">Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="51dfe-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="51dfe-103">Bu makaledeki örnekte, kaynak dizideki genişletme yöntemi kullanılarak basit bir paralel dil tümleşik sorgu (LINQ) sorgusunun oluşturulması <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> ve yöntemi kullanılarak sorgu yürütülmesi gösterilmektedir <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="51dfe-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51dfe-104">Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="51dfe-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="51dfe-105">C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="51dfe-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51dfe-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="51dfe-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="51dfe-107">Bu örnek, sonuç sırasının sıralaması önemli olmadığında herhangi bir paralel LINQ sorgusunun oluşturulması ve yürütülmesi için temel düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="51dfe-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="51dfe-108">Sıralanmamış sorgular genellikle sıralanmış sorgulardan daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="51dfe-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="51dfe-109">Sorgu, kaynağı birden çok iş parçacığında zaman uyumsuz olarak yürütülen görevlere bölümler.</span><span class="sxs-lookup"><span data-stu-id="51dfe-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="51dfe-110">Her görevin tamamlandığı sıra, yalnızca bölümdeki öğeleri işlemek için gereken iş miktarına değil, aynı zamanda işletim sisteminin her bir iş parçacığını nasıl zamanlıyor gibi dış faktörlerden de farklı olur.</span><span class="sxs-lookup"><span data-stu-id="51dfe-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="51dfe-111">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="51dfe-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="51dfe-112">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="51dfe-112">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="51dfe-113">Bir sorgudaki öğelerin sıralamasını koruma hakkında daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ sorgusunda sıralamayı denetleme](how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="51dfe-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51dfe-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51dfe-114">See also</span></span>

- [<span data-ttu-id="51dfe-115">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="51dfe-115">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
