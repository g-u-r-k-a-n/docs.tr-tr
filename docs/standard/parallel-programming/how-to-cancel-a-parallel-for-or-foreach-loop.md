---
title: 'Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme'
description: ParallelOptions parametresindeki yöntemine bir iptal belirteci nesnesi sağlayarak .NET 'teki bir Parallel. for veya Parallel. ForEach döngüsünü iptal edin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: 842873afcba1bba3a00ccaa8c95310bd1efd3a92
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713320"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="b8de0-103">Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme</span><span class="sxs-lookup"><span data-stu-id="b8de0-103">How to: Cancel a Parallel.For or ForEach Loop</span></span>

<span data-ttu-id="b8de0-104"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Ve yöntemleri, iptal <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> belirteçlerini kullanarak iptali destekler.</span><span class="sxs-lookup"><span data-stu-id="b8de0-104">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="b8de0-105">Genel olarak iptal hakkında daha fazla bilgi için bkz. [iptal](../threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="b8de0-105">For more information about cancellation in general, see [Cancellation](../threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="b8de0-106">Paralel bir döngüde, <xref:System.Threading.CancellationToken> <xref:System.Threading.Tasks.ParallelOptions> parametresini parametresindeki yöntemine sağlarsınız ve sonra paralel çağrıyı bir try-catch bloğuna çevrelemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b8de0-106">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8de0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8de0-107">Example</span></span>  

 <span data-ttu-id="b8de0-108">Aşağıdaki örnek, bir çağrısının nasıl iptal edildiğini gösterir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b8de0-108">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8de0-109">Bir çağrıya aynı yaklaşımı uygulayabilirsiniz <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b8de0-109">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="b8de0-110">İptaline işaret eden belirteç örnekte belirtilen belirteçtir <xref:System.Threading.Tasks.ParallelOptions> . paralel döngü, tek bir iptal işlemi oluşturur <xref:System.OperationCanceledException> .</span><span class="sxs-lookup"><span data-stu-id="b8de0-110">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="b8de0-111">Başka bir belirteç iptaline neden olursa, döngü bir <xref:System.AggregateException> InnerException olarak bir oluşturacak <xref:System.OperationCanceledException> şekilde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8de0-111">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8de0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8de0-112">See also</span></span>

- [<span data-ttu-id="b8de0-113">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="b8de0-113">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="b8de0-114">PLıNQ ve TPL 'deki lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b8de0-114">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
