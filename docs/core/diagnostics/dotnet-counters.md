---
title: DotNet-sayaçlar-.NET Core
description: DotNet-Counter komut satırı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 02/26/2020
ms.openlocfilehash: 71e3c4f0a60960c4e672b95000bc0d67bd427514
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024634"
---
# <a name="dotnet-counters"></a><span data-ttu-id="8453e-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="8453e-103">dotnet-counters</span></span>

<span data-ttu-id="8453e-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="8453e-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="8453e-105">DotNet-sayaçlar 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="8453e-105">Install dotnet-counters</span></span>

<span data-ttu-id="8453e-106">NuGet paketinin en son sürümünü yüklemek için `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8453e-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="8453e-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="8453e-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="8453e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8453e-108">Description</span></span>

<span data-ttu-id="8453e-109">`dotnet-counters`, geçici sistem durumu izleme ve ilk düzey performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="8453e-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="8453e-110">API aracılığıyla yayınlanan performans sayacı değerlerini gözlemleyebilirsiniz <xref:System.Diagnostics.Tracing.EventCounter> .</span><span class="sxs-lookup"><span data-stu-id="8453e-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="8453e-111">Örneğin, veya kullanarak daha ciddi performans araştırmasına gerek olmadan önce kuşkulu bir şey olup olmadığını görmek için, CPU kullanımı veya .NET Core uygulamanızda oluşturulan özel durumların oranı gibi şeyleri hızlıca izleyebilirsiniz `PerfView` `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="8453e-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="8453e-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="8453e-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="8453e-113">DotNet-Counters yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8453e-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8453e-114">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8453e-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="8453e-115">Komutlar</span><span class="sxs-lookup"><span data-stu-id="8453e-115">Commands</span></span>

| <span data-ttu-id="8453e-116">Komut</span><span class="sxs-lookup"><span data-stu-id="8453e-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="8453e-117">DotNet-sayaçlar toplama</span><span class="sxs-lookup"><span data-stu-id="8453e-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="8453e-118">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="8453e-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="8453e-119">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="8453e-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="8453e-120">DotNet-sayaçlar PS 'si</span><span class="sxs-lookup"><span data-stu-id="8453e-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="8453e-121">DotNet-sayaçlar toplama</span><span class="sxs-lookup"><span data-stu-id="8453e-121">dotnet-counters collect</span></span>

<span data-ttu-id="8453e-122">Seçili sayaç değerlerini düzenli olarak toplayın ve işleme sonrası için belirtilen dosya biçimine dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="8453e-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8453e-123">Özeti</span><span class="sxs-lookup"><span data-stu-id="8453e-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="8453e-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="8453e-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="8453e-125">İzlenecek işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8453e-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="8453e-126">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="8453e-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="8453e-127">Sayaçların boşlukla ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="8453e-127">A space separated list of counters.</span></span> <span data-ttu-id="8453e-128">Sayaçlar belirtilebilir `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="8453e-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="8453e-129">`provider_name`Nitelendirme olmadan kullanılırsa `counter_name` , tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8453e-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="8453e-130">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8453e-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="8453e-131">Aktarılacak biçim.</span><span class="sxs-lookup"><span data-stu-id="8453e-131">TThe format to be exported.</span></span> <span data-ttu-id="8453e-132">Şu anda kullanılabilir: CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="8453e-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="8453e-133">Çıktı dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="8453e-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="8453e-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8453e-134">Examples</span></span>

- <span data-ttu-id="8453e-135">Tüm sayaçları 3 saniyelik yenileme aralığında toplayın ve çıkış olarak bir CSV oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8453e-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="8453e-136">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="8453e-136">dotnet-counters list</span></span>

<span data-ttu-id="8453e-137">Sağlayıcıya göre gruplandırılan sayaç adlarının ve açıklamalarının listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8453e-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8453e-138">Özeti</span><span class="sxs-lookup"><span data-stu-id="8453e-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="8453e-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="8453e-139">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> <span data-ttu-id="8453e-140">`Microsoft.AspNetCore.Hosting`Sayaçlar, bu sayaçları destekleyen bir işlem olduğunda (örneğin, konak makinede bir ASP.NET Core uygulama çalışırken) görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8453e-140">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="8453e-141">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="8453e-141">dotnet-counters monitor</span></span>

<span data-ttu-id="8453e-142">Seçili sayaçların değerlerini düzenli aralıklarla yenilemeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8453e-142">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8453e-143">Özeti</span><span class="sxs-lookup"><span data-stu-id="8453e-143">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="8453e-144">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="8453e-144">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="8453e-145">İzlenecek işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8453e-145">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="8453e-146">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="8453e-146">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="8453e-147">Sayaçların boşlukla ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="8453e-147">A space separated list of counters.</span></span> <span data-ttu-id="8453e-148">Sayaçlar belirtilebilir `provider_name[:counter_name]` .</span><span class="sxs-lookup"><span data-stu-id="8453e-148">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="8453e-149">`provider_name`Nitelendirme olmadan kullanılırsa `counter_name` , tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8453e-149">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="8453e-150">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8453e-150">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="8453e-151">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8453e-151">Examples</span></span>

- <span data-ttu-id="8453e-152">Tüm sayaçları `System.Runtime` 3 saniyelik yenileme aralığından izleyin:</span><span class="sxs-lookup"><span data-stu-id="8453e-152">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- <span data-ttu-id="8453e-153">Yalnızca CPU kullanımı ve GC yığın boyutunu izle `System.Runtime` :</span><span class="sxs-lookup"><span data-stu-id="8453e-153">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="8453e-154">`EventCounter`Kullanıcı tanımlı değerleri izleme `EventSource` .</span><span class="sxs-lookup"><span data-stu-id="8453e-154">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="8453e-155">Daha fazla bilgi için bkz. [öğretici: .NET Core 'Da EventCounters kullanarak performansı ölçme](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="8453e-155">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="8453e-156">DotNet-sayaçlar PS 'si</span><span class="sxs-lookup"><span data-stu-id="8453e-156">dotnet-counters ps</span></span>

<span data-ttu-id="8453e-157">İzlenebilecek DotNet işlemlerinin bir listesini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="8453e-157">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8453e-158">Özeti</span><span class="sxs-lookup"><span data-stu-id="8453e-158">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="8453e-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="8453e-159">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
