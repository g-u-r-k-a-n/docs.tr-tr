---
title: Çöp Toplama ve Performans
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 833bf46b973988196fea37da18bac9923ecd6dcc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141374"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="1d2dc-102">Çöp Toplama ve Performans</span><span class="sxs-lookup"><span data-stu-id="1d2dc-102">Garbage Collection and Performance</span></span>

<a name="top"></a><span data-ttu-id="1d2dc-103">Bu konuda çöp toplama ve bellek kullanımı ile ilgili sorunlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="1d2dc-104">Yönetilen yığınla ilgili sorunları ele alır ve çöp toplamanın uygulamalarınız üzerindeki etkisinin nasıl en aza indirgenebileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="1d2dc-105">Her başlıkta, problemleri araştırmak için kullanabileceğiniz prosedürlerin bağlantıları yer alır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-105">Each issue has links to procedures that you can use to investigate problems.</span></span>

<span data-ttu-id="1d2dc-106">Bu konu aşağıdaki bölümleri içermektedir:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-106">This topic contains the following sections:</span></span>

- [<span data-ttu-id="1d2dc-107">Performans analizi araçları</span><span class="sxs-lookup"><span data-stu-id="1d2dc-107">Performance Analysis Tools</span></span>](#performance_analysis_tools)

- [<span data-ttu-id="1d2dc-108">Performans sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="1d2dc-108">Troubleshooting Performance Issues</span></span>](#troubleshooting_performance_issues)

- [<span data-ttu-id="1d2dc-109">Sorun giderme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1d2dc-109">Troubleshooting Guidelines</span></span>](#troubleshooting_guidelines)

- [<span data-ttu-id="1d2dc-110">Performans denetimi yordamları</span><span class="sxs-lookup"><span data-stu-id="1d2dc-110">Performance Check Procedures</span></span>](#performance_check_procedures)

<a name="performance_analysis_tools"></a>

## <a name="performance-analysis-tools"></a><span data-ttu-id="1d2dc-111">Performans Analiz Araçları</span><span class="sxs-lookup"><span data-stu-id="1d2dc-111">Performance Analysis Tools</span></span>

<span data-ttu-id="1d2dc-112">Aşağıdaki bölümlerde, bellek kullanımı ve çöp toplama sorunlarını araştırmak için kullanılabilen araçlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-112">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="1d2dc-113">Bu konunun ilerleyen kısımlarında sunulan [yordamlar](#performance_check_procedures) Bu araçlara başvurur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-113">The [procedures](#performance_check_procedures) provided later in this topic refer to these tools.</span></span>

<a name="perf_counters"></a>

### <a name="memory-performance-counters"></a><span data-ttu-id="1d2dc-114">Bellek Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="1d2dc-114">Memory Performance Counters</span></span>

<span data-ttu-id="1d2dc-115">Performans verilerini toplamak için performans sayaçlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-115">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="1d2dc-116">Yönergeler için bkz. [çalışma zamanı profili oluşturma](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-116">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="1d2dc-117">Performans sayaçlarının .NET CLR bellek kategorisi, [.NET Framework performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md)bölümünde açıklandığı gibi, çöp toplayıcı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-117">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

<a name="sos"></a>

### <a name="debugging-with-sos"></a><span data-ttu-id="1d2dc-118">SOS ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1d2dc-118">Debugging with SOS</span></span>

<span data-ttu-id="1d2dc-119">Yönetilen yığında nesneleri incelemek için [Windows hata ayıklayıcı (WinDbg)](/windows-hardware/drivers/debugger/index) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-119">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="1d2dc-120">WinDbg 'yi yüklemek için, [Windows Için hata ayıklama araçları 'Nı karşıdan yükle](/windows-hardware/drivers/debugger/debugger-download-tools) sayfasından Windows Için hata ayıklama araçları 'nı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-120">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

<a name="etw"></a>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="1d2dc-121">Çöp Toplama ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="1d2dc-121">Garbage Collection ETW Events</span></span>

<span data-ttu-id="1d2dc-122">Windows için olay izleme (ETW), .NET Framework tarafından sağlanan ve profil oluşturma ile hata ayıklama desteğini tamamlayan bir izleme sistemidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-122">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="1d2dc-123">.NET Framework 4 ' ten başlayarak, [atık toplama ETW olayları](../../../docs/framework/performance/garbage-collection-etw-events.md) , yönetilen yığının istatistiksel bir görünüm noktasından çözümlenmesi için yararlı bilgiler yakalar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-123">Starting with the .NET Framework 4, [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="1d2dc-124">Örneğin, çöp toplama olayı gerçekleşmek üzereyken oluşturulan `GCStart_V1` olayı, aşağıdaki bilgileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-124">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="1d2dc-125">Hangi nesne neslinin toplandığı.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-125">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="1d2dc-126">Çöp toplama işlemini neyin tetiklediği.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-126">What triggered the garbage collection.</span></span>

- <span data-ttu-id="1d2dc-127">Çöp toplama işleminin türü (eşzamanlı veya eşzamansız).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-127">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="1d2dc-128">ETW olay günlüğü verimlidir ve çöp toplamayla ilgili hiçbir performans sorununu gizlemez.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-128">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="1d2dc-129">Bir işlem, ETW olaylarıyla birlikte kendi olaylarını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-129">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="1d2dc-130">Günlüğe kaydedildiğinde, yığın problemlerinin nasıl ve ne zaman oluştuğunu belirlemek için hem uygulamanın olayları hem de çöp toplama olayları eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-130">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="1d2dc-131">Örneğin bir sunucu uygulaması, olayları bir istemci isteğinin başında ve sonunda sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-131">For example, a server application could provide events at the start and end of a client request.</span></span>

<a name="profiling_api"></a>

### <a name="the-profiling-api"></a><span data-ttu-id="1d2dc-132">Profil oluşturma API 'SI</span><span class="sxs-lookup"><span data-stu-id="1d2dc-132">The Profiling API</span></span>

<span data-ttu-id="1d2dc-133">Ortak dil çalışma zamanı (CLR) profil oluşturma arabirimleri, çöp toplama işlemi sırasında etkilenen nesneler hakkında detaylı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-133">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="1d2dc-134">Bir çöp toplama işlemi başladığında ve bittiğinde bir profil oluşturucu bildirim alabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-134">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="1d2dc-135">Her nesildeki nesnelerin bir tanımlaması dahil olmak üzere yönetilen yığındaki nesneler hakkında raporlar sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-135">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="1d2dc-136">Daha fazla bilgi için bkz. [profil oluşturma genel bakış](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-136">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="1d2dc-137">Profil oluşturucular kapsamlı bilgi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-137">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="1d2dc-138">Ancak karmaşık profil oluşturucular, bir uygulamanın davranışını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-138">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="1d2dc-139">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="1d2dc-139">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="1d2dc-140">.NET Framework 4 ' te başlayarak, uygulama etki alanı kaynak izleme (ARM), ana bilgisayarların uygulama etki alanı tarafından CPU ve bellek kullanımını izlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-140">Starting with the .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="1d2dc-141">Daha fazla bilgi için bkz. [uygulama etki alanı kaynak izleme](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-141">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>

[<span data-ttu-id="1d2dc-142">Başa dön</span><span class="sxs-lookup"><span data-stu-id="1d2dc-142">Back to top</span></span>](#top)

<a name="troubleshooting_performance_issues"></a>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="1d2dc-143">Performans Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="1d2dc-143">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="1d2dc-144">İlk adım, [sorunun gerçekten çöp toplama olup olmadığını belirlemektir](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-144">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="1d2dc-145">Eğer sorunun bu olduğunu belirlerseniz, aşağıdaki listeden sorunu gidermeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-145">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="1d2dc-146">Yetersiz bellek özel durumu oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="1d2dc-146">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="1d2dc-147">İşlem çok fazla bellek kullanıyor</span><span class="sxs-lookup"><span data-stu-id="1d2dc-147">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="1d2dc-148">Çöp toplayıcı nesneleri yeterince hızlı geri kazanmıyor</span><span class="sxs-lookup"><span data-stu-id="1d2dc-148">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="1d2dc-149">Yönetilen yığın çok parçalanmış</span><span class="sxs-lookup"><span data-stu-id="1d2dc-149">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="1d2dc-150">Çöp toplama duraklamaları çok uzun</span><span class="sxs-lookup"><span data-stu-id="1d2dc-150">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="1d2dc-151">Nesil 0 çok büyük</span><span class="sxs-lookup"><span data-stu-id="1d2dc-151">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="1d2dc-152">Çöp toplama sırasında CPU kullanımı çok yüksek</span><span class="sxs-lookup"><span data-stu-id="1d2dc-152">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="1d2dc-153">Sorun: Bir Yetersiz Bellek Özel Durumu Oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="1d2dc-153">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="1d2dc-154">Yönetilen bir <xref:System.OutOfMemoryException> oluşturulması için iki meşru durum vardır:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-154">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="1d2dc-155">Sanal bellek tükeniyor.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-155">Running out of virtual memory.</span></span>

  <span data-ttu-id="1d2dc-156">Çöp toplayıcısı önceden belirlenmiş bir boyutun segmentlerindeki sistemden bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-156">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="1d2dc-157">Eğer bir ayırma işlemi için ek bir segment gerekirse, ancak işlemin sanal bellek alanının bitişiğinde boş bir blok kalmamışsa, yönetilen yığın için ayırma başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-157">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="1d2dc-158">Ayrılacak yeterli fiziksel belleğe sahip olmama.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-158">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="1d2dc-159">Performans denetimleri</span><span class="sxs-lookup"><span data-stu-id="1d2dc-159">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="1d2dc-160">Yetersiz bellek özel durumunun yönetilip yönetilmediğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-160">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="1d2dc-161">Ne kadar sanal bellek ayrılacağını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-161">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="1d2dc-162">Yeterli fiziksel bellek olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-162">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="1d2dc-163">Özel durumun meşru olmadığını belirlerseniz, aşağıdaki bilgilerle Microsoft Müşteri Hizmetleri ve Destek birimiyle iletişime geçin:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-163">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="1d2dc-164">Yönetilen yetersiz bellek özel durumu olan yığın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-164">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="1d2dc-165">Tam bellek dökümü.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-165">Full memory dump.</span></span>

- <span data-ttu-id="1d2dc-166">Sanal veya fiziksel belleğin bir sorun olmadığını gösteren veriler dahil olmak üzere, meşru bir yetersiz bellek özel durumu olmadığını kanıtlayan veriler.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-166">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="1d2dc-167">Sorun: İşlem Çok Fazla Bellek Kullanıyor</span><span class="sxs-lookup"><span data-stu-id="1d2dc-167">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="1d2dc-168">Yaygın bir varsayım, Windows Görev Yöneticisi 'nin **performans** sekmesindeki bellek kullanımının çok fazla bellek kullanıldığını gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-168">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="1d2dc-169">Ancak, bu ekran çalışan kümeyle ilgilidir; sanal bellek kullanımı hakkında bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-169">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="1d2dc-170">Eğer sorunun yönetilen yığından kaynaklı olduğunu belirlerseniz, herhangi bir düzen olup olmadığını belirlemek için yönetilen yığını zamanla ölçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-170">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="1d2dc-171">Eğer problemin yönetilen yığından kaynaklanmadığını belirlerseniz, yerel hata ayıklama kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-171">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="1d2dc-172">Performans denetimleri</span><span class="sxs-lookup"><span data-stu-id="1d2dc-172">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="1d2dc-173">Ne kadar sanal bellek ayrılacağını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-173">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="1d2dc-174">Yönetilen yığının ne kadar bellek kullandığını saptayın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-174">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="1d2dc-175">Yönetilen yığının ne kadar bellek ayırdığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-175">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="1d2dc-176">2. nesil büyük nesneleri belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-176">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="1d2dc-177">Nesnelere başvuruları belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-177">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="1d2dc-178">Sorun: Atık Toplayıcısı Nesneleri Yeterince Hızlı Geri Kazanmıyor</span><span class="sxs-lookup"><span data-stu-id="1d2dc-178">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="1d2dc-179">Çöp toplama işlemi için nesnelerin beklendiği kadar hızlı geri kazanılmadığı anlaşıldığında, bu nesnelere yapılan güçlü atıflar olup olmadığını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-179">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="1d2dc-180">Etkin olmayan nesneye ait sonlandırıcının çalıştırılmadığını gösteren etkin olmayan bir nesne içeren nesilde hiç çöp toplama olmaması durumunda da bu sorunla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-180">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="1d2dc-181">Örneğin, bir tek iş parçacıklı bölme (STA) uygulamasını çalıştırdığınızda ve sonlandırıcı sıraya hizmet veren iş parçacığı bu uygulamaya çağrılamadığında mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-181">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="1d2dc-182">Performans denetimleri</span><span class="sxs-lookup"><span data-stu-id="1d2dc-182">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="1d2dc-183">Nesnelere başvuruları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-183">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="1d2dc-184">Sonlandırıcının çalıştırılıp çalıştırılmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-184">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="1d2dc-185">Sonlandırılmayı bekleyen nesneler olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-185">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="1d2dc-186">Sorun: Yönetilen Yığın Çok Parçalanmış</span><span class="sxs-lookup"><span data-stu-id="1d2dc-186">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="1d2dc-187">Parçalanma düzeyi, boş alanın nesil için ayrılan toplam belleğe oranı olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-187">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="1d2dc-188">Nesil 2 için, kabul edilebilir parçalanma düzeyi %20'den fazla değildir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-188">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="1d2dc-189">Nesil 2 çok fazla büyüyebildiğinden, parçalanma oranı mutlak değerden daha önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-189">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="1d2dc-190">Nesil 0, yeni nesnelerin ayrıldığı nesil olduğundan, içerisinde fazla boş alan olması problem değildir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-190">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="1d2dc-191">Parçalanma, sıkıştırılmış olmadığından her zaman büyük nesne yığınında oluşur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-191">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="1d2dc-192">Bitişik olan boş nesneler, büyük nesne ayırma isteklerini karşılamak için doğal olarak tek bir boşluk içine daraltılır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-192">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="1d2dc-193">Nesil 1 ve nesil 2'de parçalanma bir sorun olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-193">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="1d2dc-194">Eğer bu nesiller çöp toplama sonrasında büyük bir boş alana sahipse, uygulamanın nesne kullanımının değiştirilmesi gerekebilir ve uzun zamanlı nesnelerin kullanım sürelerini yeniden değerlendirmeyi göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-194">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="1d2dc-195">Aşırı nesne sabitlenmesi parçalanmayı arttırabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-195">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="1d2dc-196">Eğer parçalanma yüksekse, çok fazla nesne sabitlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-196">If fragmentation is high, too many objects could be pinned.</span></span>

<span data-ttu-id="1d2dc-197">Sanal belleğin parçalanması toplamanın segment eklemesini engelliyorsa, bunun sebebi aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-197">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="1d2dc-198">Birçok küçük derlemenin sık sık yüklenmesi ve kaldırılması.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-198">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="1d2dc-199">Yönetilemeyen kodla karşılıklı çalışılırken COM nesnelerinde çok fazla atıf tutulması.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-199">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="1d2dc-200">Büyük nesne yığınının sık sık yığın segmentlerinin ayrılmasına ve boşaltılmasına neden olan büyük geçici nesnelerin oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-200">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="1d2dc-201">Bir uygulama CLR'yi barındırdığı sırada çöp toplayıcıdan segmentlerini tutmasını isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-201">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="1d2dc-202">Bu, segment ayırma sıklığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-202">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="1d2dc-203">Bu, [startup_flags sabit LISTESININ](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)STARTUP_HOARD_GC_VM bayrağını kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-203">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="1d2dc-204">Performans denetimleri</span><span class="sxs-lookup"><span data-stu-id="1d2dc-204">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="1d2dc-205">Yönetilen yığında boş alan miktarını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-205">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="1d2dc-206">Sabitlenmiş nesne sayısını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-206">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="1d2dc-207">Eğer parçalanma için meşru bir neden olmadığını düşünüyorsanız, Microsoft Müşteri Hizmetleri ve Destek'le iletişime geçin.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-207">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="1d2dc-208">Sorun: Atık Toplama Duraksamaları Çok Uzun</span><span class="sxs-lookup"><span data-stu-id="1d2dc-208">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="1d2dc-209">Çöp toplama gerçek zamanlı olarak çalıştığından, bir uygulamanın bazı duraklamalara izin vermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-209">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="1d2dc-210">Yazılımsal olarak gerçek zamanlı çalışmanın bir kriteri, işlemlerin %95'inin zamanında bitmesi gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-210">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="1d2dc-211">Eşzamanlı çöp toplamada, bir toplama işlemi sırasında yönetilen iş parçacıklarının çalışmasına izin verilir, bu ise çok az duraklama olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-211">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="1d2dc-212">Kısa ömürlü çöp toplama işlemleri (nesil 0 ve 1) yalnızca birkaç milisaniye sürdüğünden, duraksamaların azaltılması genellikle mantıklı değildir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-212">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="1d2dc-213">Ancak, bir uygulama tarafından yapılan ayırma isteklerinin düzenini değiştirerek nesil 2 koleksiyonlarındaki duraksamaları azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-213">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="1d2dc-214">Diğer bir, daha doğru yöntem ise [çöp toplama ETW olaylarını](../../../docs/framework/performance/garbage-collection-etw-events.md)kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-214">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="1d2dc-215">Bir olay dizisine ait zaman damgalarının farklarını ekleyerek koleksiyonlar için zamanlamaları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-215">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="1d2dc-216">Tüm koleksiyon dizisi, yürütme altyapısının askıya alınmasını, çöp toplamanın kendisini ve yürütme altyapısının sürdürülmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-216">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="1d2dc-217">Bir sunucunun bir nesil 2 koleksiyonuna sahip olup olmadığını ve başka bir sunucuya yeniden yönlendirme isteklerinin duraklamalar ile ilgili sorunları kolayca yapıp yapmadığını anlamak için [çöp toplama bildirimlerini](../../../docs/standard/garbage-collection/notifications.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-217">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="1d2dc-218">Performans denetimleri</span><span class="sxs-lookup"><span data-stu-id="1d2dc-218">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="1d2dc-219">Çöp koleksiyonundaki sürenin uzunluğunu belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-219">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="1d2dc-220">Çöp toplamaya neyin neden olduğunu belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-220">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="1d2dc-221">Sorun: Nesil 0 Çok Büyük</span><span class="sxs-lookup"><span data-stu-id="1d2dc-221">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="1d2dc-222">Özellikle iş istasyonu çöp toplama yerine sunucu çöp toplamayı kullandığınızda, nesil 0, 64 bit bir sistem üzerinde genellikle çok sayıda nesneye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-222">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="1d2dc-223">Bunun sebebi, bir nesil 0 atık temizleme işlemini tetikleme eşiğinin bu ortamlarda daha yüksek olması ve nesil 0 toplama işlemlerinin çok daha fazla büyüyebilecek olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-223">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="1d2dc-224">Bir çöp toplama tetiklenmeden önce bir uygulama daha fazla bellek ayırırsa performans artar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-224">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="1d2dc-225">Sorun: Bir Atık Toplama İşlemi Sırasında CPU Kullanımı Çok Yüksek</span><span class="sxs-lookup"><span data-stu-id="1d2dc-225">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="1d2dc-226">Çöp toplama sırasında CPU kullanımı yüksek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-226">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="1d2dc-227">Eğer bir çöp toplama işlemi sırasında önemli miktarda işlem süresi harcanırsa, toplama işlemi çok sık gerçekleşiyordur veya çok uzun sürüyordur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-227">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="1d2dc-228">Yönetilen yığındaki nesnelerin arttırılmış ayırma oranı, çöp toplamanın daha sık gerçekleşmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-228">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="1d2dc-229">Ayırma oranının azaltılması çöp toplamaların sıklığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-229">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="1d2dc-230">`Allocated Bytes/second` performans sayacını kullanarak ayırma oranlarını izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-230">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="1d2dc-231">Daha fazla bilgi için [.NET Framework performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-231">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="1d2dc-232">Bir koleksiyonun süresi, öncelikle ayırma sonrası varlığını sürdüren nesnelerin sayısında bir etmendir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-232">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="1d2dc-233">Toplanacak çok nesne kaldıysa çöp toplayıcının büyük miktarda belleği gözden geçirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-233">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="1d2dc-234">Dışarıda kalanların sıkıştırılması, zaman alan bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-234">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="1d2dc-235">Bir toplama sırasında kaç nesnenin işlendiğini belirlemek için belirli bir nesle yönelik bir çöp toplamanın sonundaki hata ayıklayıcıda bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-235">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="1d2dc-236">Performans denetimleri</span><span class="sxs-lookup"><span data-stu-id="1d2dc-236">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="1d2dc-237">Yüksek CPU kullanımının çöp toplamadan kaynaklanıp kaynaklanmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-237">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="1d2dc-238">Çöp toplamanın sonunda bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-238">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

[<span data-ttu-id="1d2dc-239">Başa dön</span><span class="sxs-lookup"><span data-stu-id="1d2dc-239">Back to top</span></span>](#top)

<a name="troubleshooting_guidelines"></a>

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="1d2dc-240">Sorun Giderme Kılavuzları</span><span class="sxs-lookup"><span data-stu-id="1d2dc-240">Troubleshooting Guidelines</span></span>

<span data-ttu-id="1d2dc-241">Bu bölümde, araştırmalarınıza başlamadan önce göz önünde bulundurmanız gereken yönergeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-241">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="1d2dc-242">İş İstasyonu veya Sunucu Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="1d2dc-242">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="1d2dc-243">Doğru çöp toplama türünü kullanıp kullanmadığınızı belirleyin.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-243">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="1d2dc-244">Uygulamanız birden çok iş parçacığı ve nesne örneği kullanıyorsa, iş istasyonu çöp toplama yerine sunucu çöp toplama kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-244">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="1d2dc-245">İş istasyonu çöp toplama, bir uygulamanın birden çok örneğinin kendi çöp toplama iş parçacıklarını çalıştırmasını ve CPU süresi için birbirleriyle yarışmasını gerektirirken sunucu çöp toplama, birden çok iş parçacığında çalışır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-245">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="1d2dc-246">Bir hizmet gibi düşük yüke sahip ve arka planda seyrek olarak çalışan bir uygulama, eşzamanlı çöp toplama özelliği devre dışı bırakılmış iş istasyonu çöp toplamayı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-246">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="1d2dc-247">Yönetilen Yığın Boyutu Ne Zaman Ölçülmeli</span><span class="sxs-lookup"><span data-stu-id="1d2dc-247">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="1d2dc-248">Bir profil oluşturucu kullanmıyorsanız, performans sorunlarını etkili bir biçimde tanılamak için tutarlı bir ölçüm düzeni oluşturmanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-248">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="1d2dc-249">Bir zamanlama oluşturmak için aşağıdaki noktaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-249">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="1d2dc-250">Bir nesil 2 çöp toplamanın ardından ölçerseniz, yönetilen bütün yığın atıktan arınmış olacaktır (etkin olmayan nesneler).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-250">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="1d2dc-251">Bir nesil 0 çöp toplamanın hemen ardından ölçerseniz nesil 1 ve 2'deki nesneler henüz toplanmamış olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-251">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="1d2dc-252">Bir çöp toplamadan hemen önce ölçerseniz, çöp toplama başlamadan önce mümkün olduğunca fazla ayırmayı ölçersiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-252">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="1d2dc-253">Çöp toplama veri yapıları gezinme için geçerli bir durumda olmadığından ve size tam sonuçlar vermeyebileceğinden çöp toplama sırasında ölçüm yapmak çeşitli sorunlara yol açar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-253">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="1d2dc-254">Bu tasarım gereğidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-254">This is by design.</span></span>

- <span data-ttu-id="1d2dc-255">Eşzamanlı çöp toplama özellikli iş istasyonu çöp toplama kullandığınızda, geri kazanılan nesneler sıkıştırılmayacağından, yığın boyutu aynı veya daha büyük olabilir (parçalanma boyutu daha büyük gösterebilir).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-255">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="1d2dc-256">Nesil 2'deki eşzamanlı çöp toplama, fiziksel bellek yükü çok fazla olduğunda geciktirilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-256">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="1d2dc-257">Aşağıdaki yordam, yönetilen yığını ölçmek için nasıl bir kesme noktası ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-257">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="1d2dc-258">Çöp toplamanın sonunda bir kesme noktası ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-258">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="1d2dc-259">SOS hata ayıklama uzantısı yüklü olan WinDbg'lerde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-259">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="1d2dc-260">**BP mscorwks! WKS:: GCHeap:: Restart "j (DWO) (mscorwks! WKS:: GCHeap:: GcCondemnedGeneration) = = 2) ' KB '; ' g ' "**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-260">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="1d2dc-261">Burada **GcCondemnedGeneration** , istenen nesil olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-261">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="1d2dc-262">Bu komut özel simgeler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-262">This command requires private symbols.</span></span>

  <span data-ttu-id="1d2dc-263">Bu komut, derleme 2 nesneleri atık toplama için geri alındıktan sonra, **restart** yürütüldüğünde kesmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-263">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="1d2dc-264">Sunucu çöp toplama işleminde, yalnızca bir iş parçacığı **yeniden**çağırır. bu nedenle kesme noktası yalnızca 2. nesil atık toplama sırasında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-264">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

[<span data-ttu-id="1d2dc-265">Başa dön</span><span class="sxs-lookup"><span data-stu-id="1d2dc-265">Back to top</span></span>](#top)

<a name="performance_check_procedures"></a>

## <a name="performance-check-procedures"></a><span data-ttu-id="1d2dc-266">Performans Denetim Prosedürleri</span><span class="sxs-lookup"><span data-stu-id="1d2dc-266">Performance Check Procedures</span></span>

<span data-ttu-id="1d2dc-267">Bu bölümde, performans sorunlarınızın sebeplerini ortadan kaldırmak için aşağıdaki yordamlar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-267">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="1d2dc-268">Sorunun çöp toplamadan kaynaklanıp kaynaklanmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-268">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="1d2dc-269">Yetersiz bellek özel durumunun yönetilip yönetilmediğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-269">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="1d2dc-270">Ne kadar sanal bellek ayrılacağını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-270">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="1d2dc-271">Yeterli fiziksel bellek olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-271">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="1d2dc-272">Yönetilen yığının ne kadar bellek kullandığını saptayın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-272">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="1d2dc-273">Yönetilen yığının ne kadar bellek ayırdığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-273">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="1d2dc-274">2. nesil büyük nesneleri belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-274">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="1d2dc-275">Nesnelere başvuruları belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-275">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="1d2dc-276">Sonlandırıcının çalıştırılıp çalıştırılmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-276">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="1d2dc-277">Sonlandırılmayı bekleyen nesneler olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-277">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="1d2dc-278">Yönetilen yığında boş alan miktarını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-278">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="1d2dc-279">Sabitlenmiş nesne sayısını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-279">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="1d2dc-280">Çöp koleksiyonundaki sürenin uzunluğunu belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-280">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="1d2dc-281">Ne bir çöp toplama tetikleyeceğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-281">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="1d2dc-282">Yüksek CPU kullanımının çöp toplamadan kaynaklanıp kaynaklanmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-282">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="1d2dc-283">Sorunun çöp toplamadan kaynaklanıp kaynaklanmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-283">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="1d2dc-284">Şu iki bellek performans sayacını inceleyin:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-284">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="1d2dc-285">**GC 'de% Time**.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-285">**% Time in GC**.</span></span> <span data-ttu-id="1d2dc-286">Son çöp toplama döngüsünden sonra gerçekleşen bir çöp toplamaya harcanan süresinin yüzdesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-286">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="1d2dc-287">Bu sayacı kullanarak çöp toplayıcısının yönetilen yığın alanı açmak için ne kadar süre harcadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-287">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="1d2dc-288">Eğer çöp toplamaya harcanan süre göreceli olarak düşükse, bu, yönetilen yığın dışında bir kaynak problemi olduğunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-288">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="1d2dc-289">Bu sayaç, süreçte eş zamanlı veya arka plan çöp toplama işlemleri varsa düzgün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-289">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="1d2dc-290">**Toplam kaydedilmiş bayt**sayısı.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-290">**# Total committed Bytes**.</span></span> <span data-ttu-id="1d2dc-291">Çöp toplayıcısı tarafından o an yürütülen sanal bellek miktarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-291">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="1d2dc-292">Bu sayacı kullanarak çöp toplayıcı tarafından uygulamanızın kullandığı belleğin aşırı bir kısmının kullanılıp kullanılmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-292">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="1d2dc-293">Çoğu bellek performans sayacı her çöp toplamanın sonunda güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-293">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="1d2dc-294">Bu nedenle, hakkında bilgi almak istediğiniz geçerli koşulları yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-294">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="1d2dc-295">Yetersiz bellek özel durumunun yönetilip yönetilmediğini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-295">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="1d2dc-296">SOS hata ayıklayıcı uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında, yazdırma özel durumu (**PE**) komutunu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-296">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="1d2dc-297">**! PE**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-297">**!pe**</span></span>

    <span data-ttu-id="1d2dc-298">Eğer özel durum yönetiliyorsa, aşağıdaki örnekte gösterildiği gibi, istisna türü <xref:System.OutOfMemoryException> olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-298">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="1d2dc-299">Eğer çıktıda bir özel durum belirtilmezse, bellek yetmezliği özel durumunun hangi iş parçacığından kaynaklandığını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-299">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="1d2dc-300">Bütün iş parçacıklarını çağrı yığınlarıyla birlikte göstermek için hata ayıklayıcısına aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-300">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="1d2dc-301">**~\*KB**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-301">**~\*kb**</span></span>

    <span data-ttu-id="1d2dc-302">Özel durum çağrısı yapan yığınlı iş parçacığı, `RaiseTheException` bağımsız değişkeni tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-302">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="1d2dc-303">Bu yönetilen özel durum nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-303">This is the managed exception object.</span></span>

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="1d2dc-304">İç içe özel durumların dökümünü almak için aşağıdaki komutu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-304">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="1d2dc-305">**! PE-iç içe**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-305">**!pe -nested**</span></span>

    <span data-ttu-id="1d2dc-306">Eğer herhangi bir özel durum bulamazsanız, bellek yetmezliği özel durumu, yönetilmeyen koddan kaynaklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-306">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="1d2dc-307">Ne kadar sanal belleğin ayrılabileceğini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-307">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="1d2dc-308">SOS hata ayıklama uzantısı yüklenmiş WinDbg'de, en büyük boş bölgeyi almak için şu komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-308">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="1d2dc-309">**! Adres-Özet**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-309">**!address -summary**</span></span>

  <span data-ttu-id="1d2dc-310">En büyük boş bölge aşağıdaki çıktıda gösterildiği gibi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-310">The largest free region is displayed as shown in the following output.</span></span>

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="1d2dc-311">Bu örnekte, en büyük boş bölge yaklaşık olarak 24000 KB büyüklüğündedir (onaltılık sistemde 3A980).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-311">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="1d2dc-312">Bu bölgenin boyutu, çöp toplayıcının bir segment için ihtiyaç duyduğu boyuttan daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-312">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="1d2dc-313">veya</span><span class="sxs-lookup"><span data-stu-id="1d2dc-313">-or-</span></span>

- <span data-ttu-id="1d2dc-314">**Vmstat** komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-314">Use the **vmstat** command:</span></span>

  <span data-ttu-id="1d2dc-315">**! vmstat**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-315">**!vmstat**</span></span>

  <span data-ttu-id="1d2dc-316">En büyük boş bölge, aşağıdaki çıktıda görüldüğü üzere, MAXIMUM sütunundaki en büyük değerdir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-316">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="1d2dc-317">Yeterli fiziksel bellek olup olmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-317">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="1d2dc-318">Windows Görev Yöneticisi'ni başlatın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-318">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="1d2dc-319">**Performans** sekmesinde, taahhüt edilen değere bakın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-319">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="1d2dc-320">(Windows 7 ' de **sistem grubundaki** **işlemeye (KB)** bakın.)</span><span class="sxs-lookup"><span data-stu-id="1d2dc-320">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="1d2dc-321">**Toplam** **sınıra**yakınsa fiziksel belleği azalmış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-321">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="1d2dc-322">Yönetilen yığının ne kadar bellek kullandığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-322">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="1d2dc-323">Yönetilen yığının kullandığı bayt sayısını elde etmek için `# Total committed bytes` bellek performans sayacını kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-323">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="1d2dc-324">Çöp toplayıcı yığınların hepsini aynı zamanda değil, ihtiyaç duyulan bir segmentte yürütür.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-324">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="1d2dc-325">`# Bytes in all Heaps` performans sayacı yönetilen yığın tarafından kullanılan gerçek bellek kullanımını göstermediğinden, bu sayacı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-325">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="1d2dc-326">Bu değere bir neslin boyutu dahildir ve aslında onun eşik sınırı, yani, eğer nesil nesnelerle doluysa bir çöp toplama işlemini başlatan boyutu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-326">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="1d2dc-327">Bu nedenle, bu değer genellikle sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-327">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="1d2dc-328">Yönetilen yığının ne kadar bellek ayırdığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-328">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="1d2dc-329">`# Total reserved bytes` bellek performans sayacını kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-329">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="1d2dc-330">Çöp toplayıcı bu belleği kesimlerde ayırır ve bir segmentin **eeheap** komutunu kullanarak nereden başlayacağını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-330">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="1d2dc-331">Çöp toplayıcı 'nın her segment için ayırdığı bellek miktarını belirleyebilseniz de, kesim boyutu uygulamaya özgüdür ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-331">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="1d2dc-332">Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-332">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="1d2dc-333">SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-333">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="1d2dc-334">**! eeheap-GC**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-334">**!eeheap -gc**</span></span>

  <span data-ttu-id="1d2dc-335">Sonuç aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-335">The result is as follows.</span></span>

  ```console
  Number of GC Heaps: 2
  ------------------------------
  Heap 0 (002db550)
  generation 0 starts at 0x02abe29c
  generation 1 starts at 0x02abdd08
  generation 2 starts at 0x02ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  02ab0000 02ab0038  02aceff4 0x0001efbc(126908)
  Large object heap starts at 0x0aab0038
    segment    begin allocated     size
  0aab0000 0aab0038  0aab2278 0x00002240(8768)
  Heap Size   0x211fc(135676)
  ------------------------------
  Heap 1 (002dc958)
  generation 0 starts at 0x06ab1bd8
  generation 1 starts at 0x06ab1bcc
  generation 2 starts at 0x06ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  06ab0000 06ab0038  06ab3be4 0x00003bac(15276)
  Large object heap starts at 0x0cab0038
    segment    begin allocated     size
  0cab0000 0cab0038  0cab0048 0x00000010(16)
  Heap Size    0x3bbc(15292)
  ------------------------------
  GC Heap Size   0x24db8(150968)
  ```

  <span data-ttu-id="1d2dc-336">"Segment" ifadesiyle gösterilen adresler, segmentlerin başlangıç adresleridir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-336">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="1d2dc-337">Nesil 2'deki büyük nesneleri belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-337">To determine large objects in generation 2</span></span>

- <span data-ttu-id="1d2dc-338">SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-338">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="1d2dc-339">**! dumpheap – stat**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-339">**!dumpheap –stat**</span></span>

  <span data-ttu-id="1d2dc-340">Yönetilen yığın büyükse, **dumpheap** işleminin tamamlanması biraz zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-340">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="1d2dc-341">Analize çıktının son satırlarından başlayabilirsiniz çünkü en çok alan kullanan nesneler burada listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-341">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="1d2dc-342">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-342">For example:</span></span>

  ```console
  2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo
  00155f80      533     15216804      Free
  7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary
  2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo
  79124228   121143     29064120 System.Object[]
  035f0ee4    81626     35588936 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    40182     90664128 System.Collections.Hashtable+bucket[]
  790fa3e0  3154024    137881448 System.String
  Total 8454945 objects
  ```

  <span data-ttu-id="1d2dc-343">En son listelenen nesne bir dizedir ve en çok yeri o kaplar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-343">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="1d2dc-344">Dize nesnelerinin nasıl optimize edilebileceğini görmek için uygulamanızı inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-344">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="1d2dc-345">150-200 bayt arasındaki dizeleri görmek için, aşağıdakini yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-345">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="1d2dc-346">**! dumpheap-tür System. String-min 150-max 200**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-346">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="1d2dc-347">Sonuçların bir örneği aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-347">An example of the results is as follows.</span></span>

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="1d2dc-348">ID için dize yerine tamsayı kullanmak daha verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-348">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="1d2dc-349">Aynı dize binlerce kez yineleniyorsa, dize kopyasını kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-349">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="1d2dc-350">Dize kopyası kullanımı hakkında daha fazla bilgi edinmek için, <xref:System.String.Intern%2A?displayProperty=nameWithType> yöntemine yönelik referans konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-350">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="1d2dc-351">Nesnelere olan atıfları belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-351">To determine references to objects</span></span>

- <span data-ttu-id="1d2dc-352">SOS hata ayıklama uzantısı yüklenmiş WinDbg'de, nesnelere yapılan atıfları listelemek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-352">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="1d2dc-353">**! gcroot**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-353">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="1d2dc-354">Belirli bir nesneye yapılan atıfları belirlemek için, şu adresleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-354">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="1d2dc-355">**! gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-355">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="1d2dc-356">Yığınlar üzerinde bulunan kökler yanlış pozitif olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-356">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="1d2dc-357">Daha fazla bilgi edinmek için `!help gcroot` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-357">For more information, use the command `!help gcroot`.</span></span>

  ```console
  ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->
  19010b78(DemoApp.FormDemoApp)->
  19011158(System.Windows.Forms.PropertyStore)->
  … [omitted]
  1c3745ec(System.Data.DataTable)->
  1c3747a8(System.Data.DataColumnCollection)->
  1c3747f8(System.Collections.Hashtable)->
  1c376590(System.Collections.Hashtable+bucket[])->
  1c376c98(System.Data.DataColumn)->
  1c37b270(System.Data.Common.DoubleStorage)->
  1c37b2ac(System.Double[])
  Scan Thread 0 OSTHread 99c
  Scan Thread 6 OSTHread 484
  ```

  <span data-ttu-id="1d2dc-358">**Gcroot** komutunun tamamlanması uzun zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-358">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="1d2dc-359">Çöp toplama tarafından iade alınmayan her nesne yaşayan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-359">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="1d2dc-360">Bu, bazı kökin doğrudan veya dolaylı olarak nesneye tutulduğu anlamına gelir, bu nedenle, **gcroot** nesne için yol bilgilerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-360">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="1d2dc-361">Döndürülen grafikleri ve bu nesnelere neden hala atıf yapıldığını incelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-361">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="1d2dc-362">Bir sonlandırıcının çalıştırılıp çalıştırılmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-362">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="1d2dc-363">Aşağıdaki kodu içeren bir test programı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-363">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="1d2dc-364">Test işleminin sorunu çözmesi, sorunun, o nesnelere yönelik sonlandırıcılar askıya alındığı için çöp toplayıcının nesneleri iade almamasından kaynaklandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-364">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="1d2dc-365"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> yöntemi, işlemlerini tamamlaması ve problemi gidermesi için sonlandırıcıları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-365">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="1d2dc-366">Sonlandırılmayı bekleyen nesneler olup olmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-366">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="1d2dc-367">SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-367">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="1d2dc-368">**! finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-368">**!finalizequeue**</span></span>

    <span data-ttu-id="1d2dc-369">Sonlandırılmaya hazır olan nesnelerinin sayısına bakın</span><span class="sxs-lookup"><span data-stu-id="1d2dc-369">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="1d2dc-370">Eğer sayı yüksekse, o sonlandırıcıların niye ilerlemediğini veya yeterince hızlı olmadığını incelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-370">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="1d2dc-371">İş parçacıklarının bir çıktısını almak için, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-371">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="1d2dc-372">**iş parçacıkları-özel**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-372">**threads -special**</span></span>

    <span data-ttu-id="1d2dc-373">Bu komut aşağıdaki gibi bir çıktı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-373">This command provides output such as the following.</span></span>

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="1d2dc-374">Sonlandırıcı iş parçacığı, varsa, o an çalışmakta olan sonlandırıcıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-374">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="1d2dc-375">Bir sonlandırıcı iş parçacığı herhangi bir sonlandırıcı çalıştırmıyorsa, ona işini söyleyecek bir olay bekliyordur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-375">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="1d2dc-376">Çoğu zaman sonlandırıcı iş parçacığını bu durumda görürsünüz çünkü THREAD_HIGHEST_PRIORITY'de çalışır ve varsa çalışan sonlandırıcıları çok hızlı sonlandırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-376">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="1d2dc-377">Yönetilen yığında ne kadar boş alan olduğunu belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-377">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="1d2dc-378">SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-378">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="1d2dc-379">**! dumpheap-tür serbest stat**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-379">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="1d2dc-380">Bu komut, aşağıdaki örnekte de gösterildiği gibi, yönetilen yığındaki tüm boş nesnelerin toplam boyutunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-380">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="1d2dc-381">Nesil 0'daki boş alanı belirlemek için, nesle göre bellek tüketimi bilgilerini öğrenmek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-381">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="1d2dc-382">**! eeheap-GC**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-382">**!eeheap -gc**</span></span>

  <span data-ttu-id="1d2dc-383">Bu komut, aşağıdakine benzer bir çıktı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-383">This command displays output similar to the following.</span></span> <span data-ttu-id="1d2dc-384">Son satır kısa ömürlü segmenti gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-384">The last line shows the ephemeral segment.</span></span>

  ```console
  Heap 0 (0015ad08)
  generation 0 starts at 0x49521f8c
  generation 1 starts at 0x494d7f64
  generation 2 starts at 0x007f0038
  ephemeral segment allocation context: none
  segment  begin     allocated  size
  00178250 7a80d84c  7a82f1cc   0x00021980(137600)
  00161918 78c50e40  78c7056c   0x0001f72c(128812)
  007f0000 007f0038  047eed28   0x03ffecf0(67103984)
  3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)
  46120000 46120038  49e05d04   0x03ce5ccc(63855820)
  ```

- <span data-ttu-id="1d2dc-385">Nesil 0 tarafından kullanılan alanı hesaplayın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-385">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="1d2dc-386">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-386">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="1d2dc-387">Sonuç aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-387">The result is as follows.</span></span> <span data-ttu-id="1d2dc-388">Nesil 0 yaklaşık olarak 9 MB.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-388">Generation 0 is approximately 9 MB.</span></span>

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="1d2dc-389">Aşağıdaki komut, nesil 0 aralığındaki boş alanların dökümünü verir:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-389">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="1d2dc-390">**! dumpheap-tür ücretsiz-stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-390">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="1d2dc-391">Sonuç aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-391">The result is as follows.</span></span>

  ```console
  ------------------------------
  Heap 0
  total 409 objects
  ------------------------------
  Heap 1
  total 0 objects
  ------------------------------
  Heap 2
  total 0 objects
  ------------------------------
  Heap 3
  total 0 objects
  ------------------------------
  total 409 objects
  Statistics:
        MT    Count TotalSize Class Name
  0015a498      409   7296540      Free
  Total 409 objects
  ```

  <span data-ttu-id="1d2dc-392">Bu çıktı, yığının nesil 0 bölümünün nesneler için 9 MB alan kullandığını 7 MB boş alana sahip olduğunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-392">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="1d2dc-393">Bu çözümleme nesil 0'ın parçalanmaya ne kadar katkıda bulunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-393">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="1d2dc-394">Bu yığın kullanımının miktarı, uzun zamanlı nesnelerden kaynaklanan parçalanma nedenlerinin toplam miktarından çıkarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-394">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="1d2dc-395">Sabitlenen nesne sayısını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-395">To determine the number of pinned objects</span></span>

- <span data-ttu-id="1d2dc-396">SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-396">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="1d2dc-397">**! GCHandles**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-397">**!gchandles**</span></span>

  <span data-ttu-id="1d2dc-398">Görüntülenen istatistikler, aşağıdaki örnekte gösterildiği gibi, sabitlenen işleyicilerin sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-398">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="1d2dc-399">Bir çöp toplama işleminde sürenin uzunluğunu belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-399">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="1d2dc-400">`% Time in GC` bellek performans sayacını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-400">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="1d2dc-401">Değer, örnek bir zaman aralığı kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-401">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="1d2dc-402">Her çöp toplama işlemi sonrası sayaçlar güncellendiğinden, ikisi arasında bir toplama işlemi gerçekleşmediyse geçerli örnek öncekiyle aynı değere sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-402">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="1d2dc-403">Toplama süresi, örnek zaman aralığının yüzde değeri ile çarpılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-403">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="1d2dc-404">Aşağıdaki veriler, 8 saniyelik bir çalışma için ikişer saniyelik dört örnek aralığını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-404">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="1d2dc-405">`Gen0`, `Gen1`, ve `Gen2` sütunları, o nesil için bu aralıkta kaç çöp toplama işlemi gerçekleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-405">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="1d2dc-406">Çöp toplama işleminin ne zaman gerçekleştiği bu bilgilerde yer almaz, ancak belirli bir zaman aralığında gerçekleşen çöp toplama işlemi sayısını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-406">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="1d2dc-407">En kötü durumu varsayarak, onuncu nesil 0 çöp toplama ikinci aralığının başlangıcında, on birinci nesil 0 çöp toplama ise beşinci aralığın sonunda bitmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-407">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="1d2dc-408">Onuncu çöp toplama işleminin sonuyla on birinci işlemin sonu arasında geçen süre, yaklaşık 2 saniyedir ve performans sayacı %3'ü gösterdiğinden, on birinci nesil 0 çöp toplamanın süresi (2 saniye \* 3% = 60 ms)'dir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-408">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="1d2dc-409">Bu örnekte 5 periyot vardır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-409">In this example, there are 5 periods.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="1d2dc-410">İkinci nesil 2 çöp toplama, üçüncü aralık sırasında başlamış ve beşinci aralıkta bitmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-410">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="1d2dc-411">En kötü durumu varsayarak, son çöp toplama işlemi, ikinci aralığın başlangıcında biten bir nesil 0 toplama işlemine aittir ve nesil 2 çöp toplama, beşinci aralığın sonunda bitmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-411">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="1d2dc-412">Bu nedenle, nesil 0 çöp toplamanın sonu ile nesil 2 çöp toplamanın sonu arasında geçen süre 4 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-412">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="1d2dc-413">`% Time in GC` sayacı %20 olduğundan, nesil 2 çöp toplama en fazla (4 saniye \* 20% = 800 ms) sürmüş olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-413">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="1d2dc-414">Alternatif olarak, çöp toplama [ETW olaylarını](../../../docs/framework/performance/garbage-collection-etw-events.md)kullanarak bir çöp toplamanın uzunluğunu belirleyebilir ve çöp toplama süresini anlamak için bilgileri çözümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-414">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="1d2dc-415">Örneğin, aşağıdaki veriler, eş zamanlı olmayan bir çöp toplama işlemi sırasında meydana gelen bir olay dizisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-415">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  <span data-ttu-id="1d2dc-416">Yönetilen iş parçacığını askıya almak 26 us sürüyor (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-416">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="1d2dc-417">Çöp toplama işleminin kendisi 4,8 ms sürmüş (`GCEnd_V1` – `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-417">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="1d2dc-418">Yönetilen parçacığını devam ettirmek 21 us sürüyor (`GCRestartEEEnd` – `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-418">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="1d2dc-419">Aşağıdaki çıktıda bir arkaplan çöp toplama örneği verilmiştir ve işlem, iş parçacığı ve olay alanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-419">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="1d2dc-420">(Tüm veriler gösterilmemektedir.)</span><span class="sxs-lookup"><span data-stu-id="1d2dc-420">(Not all data is shown.)</span></span>

  ```console
  timestamp(us)    event name            process    thread    event field
  42504385        GCSuspendEEBegin_V1    Test.exe    4372             1
  42504648        GCSuspendEEEnd         Test.exe    4372
  42504816        GCStart_V1             Test.exe    4372        102019
  42504907        GCStart_V1             Test.exe    4372        102020
  42514170        GCEnd_V1               Test.exe    4372
  42514204        GCHeapStats            Test.exe    4372        102020
  42832052        GCRestartEEBegin       Test.exe    4372
  42832136        GCRestartEEEnd         Test.exe    4372
  63685394        GCSuspendEEBegin_V1    Test.exe    4744             6
  63686347        GCSuspendEEEnd         Test.exe    4744
  63784294        GCRestartEEBegin       Test.exe    4744
  63784407        GCRestartEEEnd         Test.exe    4744
  89931423        GCEnd_V1               Test.exe    4372        102019
  89931464        GCHeapStats            Test.exe    4372
  ```

  <span data-ttu-id="1d2dc-421">Son alan `GCStart_V1` olduğundan, 42504816'daki `1` olayı, bunun bir arkaplan çöp toplama olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-421">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="1d2dc-422">Bu çöp toplama Hayır olur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-422">This becomes garbage collection No.</span></span> <span data-ttu-id="1d2dc-423">102019.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-423">102019.</span></span>

  <span data-ttu-id="1d2dc-424">`GCStart` olayı, bir arkaplan çöp toplama işlemi başlamadan önce geçici bir çöp toplama işlemine ihtiyaç duyulduğu için gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-424">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="1d2dc-425">Bu çöp toplama Hayır olur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-425">This becomes garbage collection No.</span></span> <span data-ttu-id="1d2dc-426">102020.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-426">102020.</span></span>

  <span data-ttu-id="1d2dc-427">42514170 konumunda çöp toplama No.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-427">At 42514170, garbage collection No.</span></span> <span data-ttu-id="1d2dc-428">102020 bitiyor.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-428">102020 finishes.</span></span> <span data-ttu-id="1d2dc-429">Yönetilen iş parçacıkları bu noktada yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-429">The managed threads are restarted at this point.</span></span> <span data-ttu-id="1d2dc-430">Bu, arkaplan çöp toplama işlemini tetikleyen 4372 numaralı iş parçacığı üzerinde tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-430">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="1d2dc-431">4744 numaralı iş parçacığında bir askıya alma meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-431">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="1d2dc-432">Bu, arkaplan çöp toplamanın yönetilen iş parçacıklarını askıya almasının gerektiği tek zamandır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-432">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="1d2dc-433">Bu süre yaklaşık olarak 99 ms'dir ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-433">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="1d2dc-434">Arkaplan çöp toplama için `GCEnd` olayı 89931423'tedir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-434">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="1d2dc-435">Bu, arkaplan çöp toplamanın yaklaşık 47 saniye sürdüğü anlamına gelir ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="1d2dc-435">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="1d2dc-436">Yönetilen iş parçacıkları çalışırken, belirli bir sayıda geçici çöp toplama işleminin gerçekleştiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-436">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="1d2dc-437">Bir çöp toplama işlemini neyin tetiklediğini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-437">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="1d2dc-438">Hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında, bütün iş parçacıklarını çağrı yığınlarıyla birlikte görmek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-438">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="1d2dc-439">**~\*KB**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-439">**~\*kb**</span></span>

  <span data-ttu-id="1d2dc-440">Bu komut, aşağıdakine benzer bir çıktı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-440">This command displays output similar to the following.</span></span>

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="1d2dc-441">Çöp toplama işlemine işletim sisteminden kaynaklanan bir düşük bellek bildirimi yol açmışsa, çağrı yığını benzerdir ama iş parçacığı sonlandırıcı iş parçacığıdır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-441">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="1d2dc-442">Sonlandırıcı iş parçacığı zaman uyumsuz bir düşük bellek bildirimi alır ve çöp toplama işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-442">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="1d2dc-443">Çöp toplama işlemine bellek ayırma yol açtıysa, yığın aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-443">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

  ```console
  0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration
  0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1
  0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18
  0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b
  0012f310 7a02ae4c mscorwks!Alloc+0x60
  0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd
  0012f424 300027f4 mscorwks!JIT_NewArr1+0x148
  000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c
  0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153
  ```

  <span data-ttu-id="1d2dc-444">Bir tam zamanında yardımcı olan (`JIT_New*`), sonunda `GCHeap::GarbageCollectGeneration` komutuna çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-444">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="1d2dc-445">Eğer nesil 2 çöp toplamaya ayırmaların neden olduğunu belirlerseniz, nesil 2 bir çöp toplama işlemi tarafından hangi nesnelerin toplandığını ve bunlardan nasıl kaçınabileceğinizi belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-445">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="1d2dc-446">Yani, nesil 2 bir çöp toplama işleminin başıyla ve sonu arasındaki farkı ve nesil 2'ye ait bir toplama işlemine neden olan nesneleri belirlemeniz faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-446">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="1d2dc-447">Örneğin, nesil 2'ye ait bir toplama işleminin başlangıcını görmek için hata ayıklayıcıya aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-447">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="1d2dc-448">**! dumpheap – stat**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-448">**!dumpheap –stat**</span></span>

  <span data-ttu-id="1d2dc-449">Örnek çıktı (en çok alan kullanan nesneleri göstermek için kısaltılmıştır):</span><span class="sxs-lookup"><span data-stu-id="1d2dc-449">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    31857      9862328 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  00155f80    21248     12256296      Free
  79103b6c   297003     13068132 System.Threading.ReaderWriterLock
  7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary
  7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  035f0ee4    89192     38887712 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  7912c444    91616     71887080 System.Double[]
  791242ec    32451     82462728 System.Collections.Hashtable+bucket[]
  790fa3e0  2459154    112128436 System.String
  Total 6471774 objects
  ```

  <span data-ttu-id="1d2dc-450">Nesil 2 sonunda komutu yineleyin:</span><span class="sxs-lookup"><span data-stu-id="1d2dc-450">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="1d2dc-451">**! dumpheap – stat**</span><span class="sxs-lookup"><span data-stu-id="1d2dc-451">**!dumpheap –stat**</span></span>

  <span data-ttu-id="1d2dc-452">Örnek çıktı (en çok alan kullanan nesneleri göstermek için kısaltılmıştır):</span><span class="sxs-lookup"><span data-stu-id="1d2dc-452">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    26648      9314256 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  79103b6c   296770     13057880 System.Threading.ReaderWriterLock
  7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary
  7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  00155f80    13806     34007212      Free
  035f0ee4    89187     38885532 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    32370     82359768 System.Collections.Hashtable+bucket[]
  790fa3e0  2440020    111341808 System.String
  Total 6417525 objects
  ```

  <span data-ttu-id="1d2dc-453">Çıktının sonunda `double[]` nesneleri kaybolduğundan, bunların toplandığını anlayabiliriz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-453">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="1d2dc-454">Bu nesneler yaklaşık olarak 70 MB.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-454">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="1d2dc-455">Geri kalan nesneler pek değişmemiş.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-455">The remaining objects did not change much.</span></span> <span data-ttu-id="1d2dc-456">Bu nedenle, bu nesil 2 çöp toplama işleminin meydana gelmesinin nedeni, bu `double[]` nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-456">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="1d2dc-457">Bir sonraki adımınız, `double[]` nesnelerinin neden orada olduğu ve neden öldüğünü belirlemek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-457">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="1d2dc-458">Kod geliştiricisinden bu nesnelerin nereden geldiğini sorabilir veya **gcroot** komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-458">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="1d2dc-459">Yüksek CPU kullanımına çöp toplamanın sebep olup olmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1d2dc-459">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="1d2dc-460">`% Time in GC` bellek performans sayaç değeriyle işlem süresini karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-460">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="1d2dc-461">`% Time in GC` değeri işlem süresiyle aynı anda artıyorsa, yüksek CPU kullanımına çöp toplama işlemi neden oluyor demektir.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-461">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="1d2dc-462">Böyle olmuyorsa, yüksek kullanımın nerede meydana geldiğini bulmak için uygulamayı profilleyin.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-462">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d2dc-463">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d2dc-463">See also</span></span>

- [<span data-ttu-id="1d2dc-464">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="1d2dc-464">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
