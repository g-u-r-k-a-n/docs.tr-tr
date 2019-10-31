---
title: 'Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
ms.openlocfilehash: 33098878764c2f8a8c1f83a122028da40b984243
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137968"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="63d5a-102">Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme</span><span class="sxs-lookup"><span data-stu-id="63d5a-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="63d5a-103">Aşağıdaki örnek, eş zamanlı görevlerin bir <xref:System.Threading.Barrier>nasıl eşitleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="63d5a-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63d5a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="63d5a-104">Example</span></span>  
 <span data-ttu-id="63d5a-105">Aşağıdaki programın amacı, sözcüklerin reshuffle için rastgele bir algoritma kullanarak her biri çözümün yarısını aynı aşamada bulması için iki iş parçacığı için kaç tane yineleme (veya aşama) gerektiğini saymadır.</span><span class="sxs-lookup"><span data-stu-id="63d5a-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="63d5a-106">Her bir iş parçacığı, sözcüklerini karmasına başladıktan sonra, ikinci sonuçları, tam tümcenin doğru sözcük düzeninde işlenip işlenmeyeceğini görmek için karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="63d5a-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="63d5a-107"><xref:System.Threading.Barrier>, tüm görevler Engellene ulaşana kadar paralel işlemdeki bireysel görevlerin devam etmesini önleyen bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="63d5a-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="63d5a-108">Bir paralel işlem aşamalar halinde oluştuğunda ve her aşama görevler arasında eşitleme gerektiriyorsa faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="63d5a-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="63d5a-109">Bu örnekte, işlem için iki aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="63d5a-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="63d5a-110">İlk aşamada, her görev arabelleğin bölümünü verilerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="63d5a-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="63d5a-111">Her görev bölümünün doldurmasını bitirdiğinde, görev engelin devam etmeye hazırlanmasına işaret eder ve sonra bekler.</span><span class="sxs-lookup"><span data-stu-id="63d5a-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="63d5a-112">Tüm görevler engeli işaret ettikleri zaman engellenmemiş ve ikinci aşama başlatılır.</span><span class="sxs-lookup"><span data-stu-id="63d5a-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="63d5a-113">İkinci aşama, her görevin bu noktada oluşturulan tüm verilere erişmesini gerektirdiğinden, engeli gereklidir.</span><span class="sxs-lookup"><span data-stu-id="63d5a-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="63d5a-114">Engel olmadan, tamamlanacak ilk görevler henüz başka görevler tarafından doldurulmamış olan arabelleklerden okumayı deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="63d5a-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="63d5a-115">Herhangi bir sayıda aşamayı bu şekilde eşzamanlı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63d5a-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d5a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63d5a-116">See also</span></span>

- [<span data-ttu-id="63d5a-117">Paralel Programlama için Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="63d5a-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
