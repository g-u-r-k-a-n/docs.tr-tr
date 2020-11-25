---
title: Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: 2ae1c514185152dd709fe06018df513fb54b874b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726723"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="0686d-102">Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="0686d-102">Interop with Other Asynchronous Patterns and Types</span></span>

<span data-ttu-id="0686d-103">.NET 'teki zaman uyumsuz desenlerin kısa bir geçmişi:</span><span class="sxs-lookup"><span data-stu-id="0686d-103">A brief history of asynchronous patterns in .NET:</span></span>

- <span data-ttu-id="0686d-104">.NET Framework 1,0 <xref:System.IAsyncResult> , başka bir deyişle, [zaman uyumsuz programlama MODELI (APM)](asynchronous-programming-model-apm.md)veya model olarak da bilinen modeli kullanıma sunmuştur `Begin/End` .</span><span class="sxs-lookup"><span data-stu-id="0686d-104">.NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>
- <span data-ttu-id="0686d-105">.NET Framework 2,0, [olay tabanlı zaman uyumsuz düzene (EAP)](event-based-asynchronous-pattern-eap.md)eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0686d-105">.NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>
- <span data-ttu-id="0686d-106">.NET Framework 4, hem APM hem de EAP 'nin yerine geçen [görev tabanlı zaman uyumsuz desen (TAP)](task-based-asynchronous-pattern-tap.md)tarafından sunulmuştur ve önceki desenlerden kolayca geçiş yordamları oluşturma yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0686d-106">.NET Framework 4 introduced the [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md), which supersedes both APM and EAP and provides the ability to easily build migration routines from the earlier patterns.</span></span>
  
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="0686d-107">Görevler ve zaman uyumsuz programlama modeli (APM)</span><span class="sxs-lookup"><span data-stu-id="0686d-107">Tasks and the Asynchronous Programming Model (APM)</span></span>

### <a name="from-apm-to-tap"></a><span data-ttu-id="0686d-108">APM 'den dokunarak</span><span class="sxs-lookup"><span data-stu-id="0686d-108">From APM to TAP</span></span>  

 <span data-ttu-id="0686d-109">[Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md) modeli yapılandırılmış olduğundan, bir APM UYGULAMASıNı bir dokunma uygulama olarak göstermek için bir sarmalayıcı oluşturmak oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="0686d-109">Because the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md) pattern is structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="0686d-110">.NET Framework 4 ve sonraki sürümler, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> Bu çeviriyi sağlamak için yöntem aşırı yüklemeleri biçiminde yardımcı yordamlar içerir.</span><span class="sxs-lookup"><span data-stu-id="0686d-110">.NET Framework 4 and later versions include helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="0686d-111"><xref:System.IO.Stream> <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> Zaman uyumlu yöntemin APM 'sini temsil eden sınıfını ve yöntemlerini göz önünde bulundurun <xref:System.IO.Stream.Read%2A> :</span><span class="sxs-lookup"><span data-stu-id="0686d-111">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="0686d-112"><xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType>Bu işlem için BIR dokunma sarmalayıcısı uygulamak için yöntemini aşağıdaki şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0686d-112">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="0686d-113">Bu uygulama şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="0686d-113">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
### <a name="from-tap-to-apm"></a><span data-ttu-id="0686d-114">DOKUNARAK APM 'ye</span><span class="sxs-lookup"><span data-stu-id="0686d-114">From TAP to APM</span></span>  

 <span data-ttu-id="0686d-115">Mevcut altyapınızda APM deseninin kullanılması bekleniyorsa, bir dokunarak uygulama alıp APM uygulamasının beklendiği yerde kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0686d-115">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="0686d-116">Görevler oluşturulabildikleri için ve <xref:System.Threading.Tasks.Task> sınıfı <xref:System.IAsyncResult> arabirimini uyguladığı için, bunu yapmak amacıyla daha basit bir yardımcı işlev kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0686d-116">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="0686d-117">Aşağıdaki kod, sınıfının bir uzantısını kullanır <xref:System.Threading.Tasks.Task%601> , ancak genel olmayan görevler için neredeyse özdeş bir işlevi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0686d-117">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="0686d-118">Şimdi, aşağıdaki dokunma uygulamasına sahip olduğunuz bir durumu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0686d-118">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="0686d-119">Bu APM uygulamasını sağlamak istiyorsanız:</span><span class="sxs-lookup"><span data-stu-id="0686d-119">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="0686d-120">Aşağıdaki örnek, APM 'ye bir geçişi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="0686d-120">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="0686d-121">Görevler ve olay tabanlı zaman uyumsuz model (EAP)</span><span class="sxs-lookup"><span data-stu-id="0686d-121">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  

 <span data-ttu-id="0686d-122">Bir [olay tabanlı zaman uyumsuz model (EAP)](event-based-asynchronous-pattern-eap.md) uygulamasını sarmalama, bir APM deseninin sarmalanması dışında daha KARMAŞıKTıR çünkü EAP deseninin APM düzeninden daha fazla çeşitlemesi ve daha az yapısı vardır.</span><span class="sxs-lookup"><span data-stu-id="0686d-122">Wrapping an [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="0686d-123">Göstermek için aşağıdaki kod yöntemini sarmalar `DownloadStringAsync` .</span><span class="sxs-lookup"><span data-stu-id="0686d-123">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="0686d-124">`DownloadStringAsync` bir URI 'yi kabul eder, `DownloadProgressChanged` İlerlemede birden fazla istatistik raporlamak için olayı indirme sırasında başlatır ve `DownloadStringCompleted` tamamlandığında olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="0686d-124">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="0686d-125">Nihai sonuç, belirtilen URI 'deki sayfanın içeriğini içeren bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="0686d-125">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="0686d-126">Görevler ve bekleme tutamaçları</span><span class="sxs-lookup"><span data-stu-id="0686d-126">Tasks and Wait Handles</span></span>  
  
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="0686d-127">Bekleme tanıtıcılarından dokunarak</span><span class="sxs-lookup"><span data-stu-id="0686d-127">From Wait Handles to TAP</span></span>  

 <span data-ttu-id="0686d-128">Wait tutamaçları zaman uyumsuz bir model uygulamasa da, gelişmiş geliştiriciler <xref:System.Threading.WaitHandle> <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> bir bekleme tutamacı ayarlandığında, zaman uyumsuz bildirimler için sınıfını ve yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0686d-128">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="0686d-129"><xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A>Bir bekleme tanıtıcısından herhangi bir zaman uyumlu bekleme için görev tabanlı bir alternatif sağlamak üzere yöntemini kaydırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0686d-129">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="0686d-130">Bu yöntemle, mevcut <xref:System.Threading.WaitHandle> uygulamaları zaman uyumsuz metotlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0686d-130">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="0686d-131">Örneğin, belirli bir zamanda yürütülen zaman uyumsuz işlemlerin sayısını azaltmak istiyorsanız, bir semafor (bir <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> nesne) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0686d-131">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="0686d-132">Semaforun sayısını *n* olarak başlatarak, semaforda bir işlem gerçekleştirmek istediğiniz zaman ve bir işlemle işiniz bittiğinde semaforu serbest *bırakmak için,* eş zamanlı olarak çalışan işlem sayısını ortadan kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0686d-132">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore's count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you're done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="0686d-133">Ayrıca, bekleme tanıtıcılarını içermeyen ve bunun yerine görevlerle tamamen çalışabilen bir zaman uyumsuz semafor oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0686d-133">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="0686d-134">Bunu yapmak için, üzerine veri yapıları oluşturmak için [görev tabanlı zaman uyumsuz model tükettiği](consuming-the-task-based-asynchronous-pattern.md) gibi teknikleri kullanabilirsiniz <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="0686d-134">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="0686d-135">DOKUNARAK bekleme tutamaçlarından</span><span class="sxs-lookup"><span data-stu-id="0686d-135">From TAP to Wait Handles</span></span>  

 <span data-ttu-id="0686d-136">Daha önce belirtildiği gibi, <xref:System.Threading.Tasks.Task> sınıfı uygular <xref:System.IAsyncResult> ve bu uygulama <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> tamamlandığında ayarlanacak bir bekleme tutamacı döndüren bir özelliği kullanıma sunar <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="0686d-136">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="0686d-137">Bir <xref:System.Threading.WaitHandle> için aşağıdaki şekilde bir edinebilirsiniz <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="0686d-137">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="0686d-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0686d-138">See also</span></span>

- [<span data-ttu-id="0686d-139">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="0686d-139">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="0686d-140">Görev Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="0686d-140">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="0686d-141">Görev Tabanlı Zaman Uyumsuz Desen Kullanma</span><span class="sxs-lookup"><span data-stu-id="0686d-141">Consuming the Task-based Asynchronous Pattern</span></span>](consuming-the-task-based-asynchronous-pattern.md)
