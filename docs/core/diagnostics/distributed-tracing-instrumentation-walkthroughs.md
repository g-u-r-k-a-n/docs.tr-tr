---
title: Dağıtılmış izleme araçları ekleme-.NET
description: .NET uygulamalarında dağıtılmış izlemeleri işaretlemek için bir öğretici
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: eeb065d1ac39dd34d9b27e2ad63195818d0d6493
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111574"
---
# <a name="adding-distributed-tracing-instrumentation"></a><span data-ttu-id="04c5e-103">Dağıtılmış izleme araçları ekleme</span><span class="sxs-lookup"><span data-stu-id="04c5e-103">Adding distributed tracing instrumentation</span></span>

<span data-ttu-id="04c5e-104">**Bu makale şu şekilde geçerlidir: ✔️** .net Core 2,1 ve üzeri sürümleri **ve** .NET Framework 4,5 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="04c5e-104">**This article applies to: ✔️** .NET Core 2.1 and later versions **and** .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="04c5e-105">.NET uygulamaları, <xref:System.Diagnostics.Activity?displayProperty=nameWithType> Dağıtılmış izleme telemetrisi oluşturmak için API kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-105">.NET applications can be instrumented using the <xref:System.Diagnostics.Activity?displayProperty=nameWithType> API to produce distributed tracing telemetry.</span></span> <span data-ttu-id="04c5e-106">Bazı araçlar standart .NET kitaplıklarında yerleşik olarak bulunur, ancak kodunuzun daha kolay diagnosable sağlamak için daha fazla eklemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04c5e-106">Some instrumentation is built-in to standard .NET libraries but you may want to add more to make your code more easily diagnosable.</span></span> <span data-ttu-id="04c5e-107">Bu öğreticide, yeni özel dağıtılmış izleme araçları ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="04c5e-107">In this tutorial you will add new custom distributed tracing instrumentation.</span></span> <span data-ttu-id="04c5e-108">Bu izleme tarafından üretilen Telemetriyi kaydetme hakkında daha fazla bilgi edinmek için [koleksiyon öğreticisine](distributed-tracing-instrumentation-walkthroughs.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="04c5e-108">See [the collection tutorial](distributed-tracing-instrumentation-walkthroughs.md) to learn more about recording the telemetry produced by this instrumentation.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04c5e-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="04c5e-109">Prerequisites</span></span>

- <span data-ttu-id="04c5e-110">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download/dotnet) veya sonraki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="04c5e-110">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>

## <a name="an-initial-app"></a><span data-ttu-id="04c5e-111">İlk uygulama</span><span class="sxs-lookup"><span data-stu-id="04c5e-111">An initial app</span></span>

<span data-ttu-id="04c5e-112">İlk olarak, Opentelemetri kullanarak telemetri toplayan, ancak henüz hiç izleme olmayan bir örnek uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="04c5e-112">First you will create a sample app that collects telemetry using OpenTelemetry, but doesn't yet have any instrumentation.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="04c5e-113">.NET 5 ve üstünü hedefleyen uygulamalar, gereken dağıtılmış izleme API 'Lerini zaten içeriyor.</span><span class="sxs-lookup"><span data-stu-id="04c5e-113">Applications that target .NET 5 and later already have the necessary distributed tracing APIs included.</span></span> <span data-ttu-id="04c5e-114">Eski .NET sürümlerini hedefleyen uygulamalar için [System. Diagnostics. DiagnosticSource NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) sürüm 5 veya üstünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="04c5e-114">For apps targeting older .NET versions add the [System.Diagnostics.DiagnosticSource NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5 or greater.</span></span>

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

<span data-ttu-id="04c5e-115">Telemetriyi toplamak için kullanılacak [opentelemetri](https://www.nuget.org/packages/OpenTelemetry/) ve [opentelemetri. ctelemetriyi](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="04c5e-115">Add the [OpenTelemetry](https://www.nuget.org/packages/OpenTelemetry/) and [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet packages which will be used to collect the telemetry.</span></span>

```dotnetcli
dotnet add package OpenTelemetry
dotnet add package OpenTelemetry.Exporter.Console
```

<span data-ttu-id="04c5e-116">Oluşturulan program. cs içeriğini bu örnek kaynakla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="04c5e-116">Replace the contents of the generated Program.cs with this example source:</span></span>

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static async Task Main(string[] args)
        {
            using var tracerProvider = Sdk.CreateTracerProviderBuilder()
                .SetResourceBuilder(ResourceBuilder.CreateDefault().AddService("MySample"))
                .AddSource("Sample.DistributedTracing")
                .AddConsoleExporter()
                .Build();

            await DoSomeWork("banana", 8);
            Console.WriteLine("Example work done");
        }

        // All the functions below simulate doing some arbitrary work
        static async Task DoSomeWork(string foo, int bar)
        {
            await StepOne();
            await StepTwo();
        }

        static async Task StepOne()
        {
            await Task.Delay(500);
        }

        static async Task StepTwo()
        {
            await Task.Delay(1000);
        }
    }
}
```

<span data-ttu-id="04c5e-117">Uygulamanın henüz bir izleme yok, bu nedenle görüntülenecek izleme bilgisi yok:</span><span class="sxs-lookup"><span data-stu-id="04c5e-117">The app has no instrumentation yet so there is no trace information to display:</span></span>

```dotnetcli
> dotnet run
Example work done
```

#### <a name="best-practices"></a><span data-ttu-id="04c5e-118">En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="04c5e-118">Best Practices</span></span>

<span data-ttu-id="04c5e-119">Yalnızca uygulama geliştiricilerinin, bu örnekteki Opentelemetri gibi dağıtılmış izleme telemetrisini toplamak için isteğe bağlı bir 3. taraf kitaplığına başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-119">Only app developers need to reference an optional 3rd party library for collecting the distributed trace telemetry, such as OpenTelemetry in this example.</span></span> <span data-ttu-id="04c5e-120">.NET kitaplığı yazarları, .NET çalışma zamanının parçası olan System. Diagnostics. DiagnosticSource içindeki API 'Lere özel olarak güvenir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-120">.NET library authors can exclusively rely on APIs in System.Diagnostics.DiagnosticSource which is part of .NET runtime.</span></span> <span data-ttu-id="04c5e-121">Bu, kitaplıkların hangi kitaplık veya satıcının telemetri toplamak için kullanılacağı konusunda ne olursa olsun, kitaplıkların çok çeşitli .NET uygulamalarında çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="04c5e-121">This ensures that libraries will run in a wide range of .NET apps, regardless of the app developer's preferences about which library or vendor to use for collecting telemetry.</span></span>

## <a name="adding-basic-instrumentation"></a><span data-ttu-id="04c5e-122">Temel Izleme ekleme</span><span class="sxs-lookup"><span data-stu-id="04c5e-122">Adding Basic Instrumentation</span></span>

<span data-ttu-id="04c5e-123">Uygulamalar ve kitaplıklar, ve sınıflarını kullanarak dağıtılmış izleme araçları ekler <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> <xref:System.Diagnostics.Activity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="04c5e-123">Applications and libraries add distributed tracing instrumentation using the <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> and <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classes.</span></span>

### <a name="activitysource"></a><span data-ttu-id="04c5e-124">Etkinlik kaynağı</span><span class="sxs-lookup"><span data-stu-id="04c5e-124">ActivitySource</span></span>

<span data-ttu-id="04c5e-125">Önce ActivitySource örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="04c5e-125">First create an instance of ActivitySource.</span></span> <span data-ttu-id="04c5e-126">ActivitySource, etkinlik nesneleri oluşturmak ve başlatmak için API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="04c5e-126">ActivitySource provides APIs to create and start Activity objects.</span></span> <span data-ttu-id="04c5e-127">Main () ve using ifadelerine statik ActivitySource değişkenini ekleyin `using System.Diagnostics;` .</span><span class="sxs-lookup"><span data-stu-id="04c5e-127">Add the static ActivitySource variable above Main() and `using System.Diagnostics;` to the using statements.</span></span>

```csharp
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        private static ActivitySource source = new ActivitySource("Sample.DistributedTracing", "1.0.0");

        static async Task Main(string[] args)
        {
            ...    
```

#### <a name="best-practices"></a><span data-ttu-id="04c5e-128">En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="04c5e-128">Best Practices</span></span>

- <span data-ttu-id="04c5e-129">ActivitySource 'u bir kez oluşturun, bir statik değişkende depolayın ve bu örneği gereken sürece kullanın.</span><span class="sxs-lookup"><span data-stu-id="04c5e-129">Create the ActivitySource once, store it in a static variable and use that instance as long as needed.</span></span>
<span data-ttu-id="04c5e-130">Her kitaplık veya kitaplık alt bileşeni kendi kaynağını oluşturabilir (ve genellikle).</span><span class="sxs-lookup"><span data-stu-id="04c5e-130">Each library or library sub-component can (and often should) create its own source.</span></span> <span data-ttu-id="04c5e-131">Uygulama geliştiricilerinin, kaynaklardaki etkinlik telemetrisini bağımsız olarak etkinleştirebilmekte ve devre dışı bırakacağından, mevcut olanı yeniden kullanmak yerine yeni bir kaynak oluşturmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="04c5e-131">Consider creating a new source rather than re-using an existing one if you anticipate app developers would appreciate being able to enable and disable the Activity telemetry in the sources independently.</span></span>

- <span data-ttu-id="04c5e-132">Oluşturucuya geçirilen kaynak adı, diğer kaynaklarla çakışmalardan kaçınmak için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-132">The source name passed to the constructor has to be unique to avoid the conflicts with any other sources.</span></span>
<span data-ttu-id="04c5e-133">Aynı derlemede birden fazla kaynak varsa, derleme adı ve isteğe bağlı olarak bir bileşen adı içeren hiyerarşik bir ad kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-133">It is recommended to use a hierarchical name that contains the assembly name and optionally a component name if there are multiple sources within the same assembly.</span></span> <span data-ttu-id="04c5e-134">Örneğin, `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="04c5e-134">For example, `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="04c5e-135">Bir derleme, 2. bağımsız bir derlemede kod için izleme ekliyor ise, bu ad kodu izlenmekte olan derlemeyi değil, ActivitySource tanımlayan derlemeye dayalı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-135">If an assembly is adding instrumentation for code in a 2nd independent assembly, the name should be based on the assembly that defines the ActivitySource, not the assembly whose code is being instrumented.</span></span>

- <span data-ttu-id="04c5e-136">Sürüm parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-136">The version parameter is optional.</span></span> <span data-ttu-id="04c5e-137">Kitaplığın birden çok sürümünü serbest bırakmanız ve belgelenmiş telemetride değişiklikler yapmanız durumunda sürümü sağlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-137">It is recommended to provide the version in case you release multiple versions of the library and make changes to the instrumented telemetry.</span></span>

> [!NOTE]
> <span data-ttu-id="04c5e-138">Opentelemetri, ' Izleyici ' ve ' span ' diğer terimlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-138">OpenTelemetry uses alternate terms 'Tracer' and 'Span'.</span></span> <span data-ttu-id="04c5e-139">.NET ' ActivitySource ' içinde, Izleyici ve etkinliğin uygulanması ' span ' uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-139">In .NET 'ActivitySource' is the implementation of Tracer and Activity is the implementation of 'Span'.</span></span> <span data-ttu-id="04c5e-140">. NET ' in etkinlik türü uzun ön tarihleri Opentelemetri belirtimi ve özgün .NET adlandırma, .NET ekosistemi ve .NET uygulama uyumluluğu dahilinde tutarlılık için korundu.</span><span class="sxs-lookup"><span data-stu-id="04c5e-140">.NET's Activity type long pre-dates the OpenTelemetry specification and the original .NET naming has been preserved for consistency within the .NET ecosystem and .NET application compatibility.</span></span>

### <a name="activity-creation"></a><span data-ttu-id="04c5e-141">Etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="04c5e-141">Activity Creation</span></span>

<span data-ttu-id="04c5e-142">Etkinlik nesnelerini anlamlı iş birimleri etrafında başlatmak ve durdurmak için ActivitySource nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="04c5e-142">Use the ActivitySource object to Start and Stop Activity objects around meaningful units of work.</span></span> <span data-ttu-id="04c5e-143">DoSomeWork () öğesini burada gösterilen kodla güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="04c5e-143">Update DoSomeWork() with the code shown here:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }
```

<span data-ttu-id="04c5e-144">Uygulamayı çalıştırmak artık günlüğe kaydedilen yeni etkinliği gösterir:</span><span class="sxs-lookup"><span data-stu-id="04c5e-144">Running the app now shows the new Activity being logged:</span></span>

```dotnetcli
> dotnet run
Activity.Id:          00-f443e487a4998c41a6fd6fe88bae644e-5b7253de08ed474f-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:36:51.4720202Z
Activity.Duration:    00:00:01.5025842
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 067f4bb5-a5a8-4898-a288-dec569d6dbef
```

#### <a name="notes"></a><span data-ttu-id="04c5e-145">Notlar</span><span class="sxs-lookup"><span data-stu-id="04c5e-145">Notes</span></span>

- <span data-ttu-id="04c5e-146"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> aynı anda etkinlik oluşturur ve başlatır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-146"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> creates and starts the activity at the same time.</span></span> <span data-ttu-id="04c5e-147">Listelenen kod stili, `using` bloğu yürüttükten sonra oluşturulan etkinlik nesnesini otomatik olarak ortadan kaldırın bloğunu kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="04c5e-147">The listed code pattern is using the `using` block which automatically disposes the created Activity object after executing the block.</span></span> <span data-ttu-id="04c5e-148">Etkinlik nesnesini elden atılırken kodun açıkça çağrılması için bu işlem durdurulur <xref:System.Diagnostics.Activity.Stop?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="04c5e-148">Disposing the Activity object will stop it so the code doesn't need to explicitly call <xref:System.Diagnostics.Activity.Stop?displayProperty=nameWithType>.</span></span>
<span data-ttu-id="04c5e-149">Bu, kodlama modelini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-149">That simplifies the coding pattern.</span></span>

- <span data-ttu-id="04c5e-150"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> , etkinliği kaydeden bir dinleyici olup olmadığını dahili olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="04c5e-150"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> internally determines if there are any listeners recording the Activity.</span></span> <span data-ttu-id="04c5e-151">Kayıtlı bir dinleyici yoksa veya ilgilenmiyor olan dinleyiciler varsa, StartActivity () geri dönerek `null` etkinlik nesnesi oluşturmaktan kaçınacaktır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-151">If there are no registered listeners or there are listeners which are not interested, StartActivity() will return `null` and avoid creating the Activity object.</span></span> <span data-ttu-id="04c5e-152">Bu, kod düzeninin çok sık çağrılan işlevlerde hala kullanılabilmesi için bir performans iyileştirmesidir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-152">This is a performance optimization so that the code pattern can still be used in functions that are called very frequently.</span></span>

## <a name="optional-populate-tags"></a><span data-ttu-id="04c5e-153">İsteğe bağlı: etiketleri doldur</span><span class="sxs-lookup"><span data-stu-id="04c5e-153">Optional: Populate tags</span></span>

<span data-ttu-id="04c5e-154">Etkinlikler, genellikle Tanılama için faydalı olabilecek iş parametrelerini depolamak için kullanılan Etiketler adlı anahtar-değer verilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="04c5e-154">Activities support key-value data called Tags, commonly used to store any parameters of the work that may be useful for diagnostics.</span></span> <span data-ttu-id="04c5e-155">DoSomeWork () öğesini bunları içerecek şekilde güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="04c5e-155">Update DoSomeWork() to include them:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                await StepTwo();
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-2b56072db8cb5a4496a4bfb69f46aa06-7bc4acda3b9cce4d-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:37:31.4949570Z
Activity.Duration:    00:00:01.5417719
Activity.TagObjects:
    foo: banana
    bar: 8
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 25bbc1c3-2de5-48d9-9333-062377fea49c

Example work done
```

#### <a name="best-practices"></a><span data-ttu-id="04c5e-156">En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="04c5e-156">Best Practices</span></span>

- <span data-ttu-id="04c5e-157">Yukarıda belirtildiği gibi, `activity` tarafından döndürülen <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> null olabilir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-157">As mentioned above, `activity` returned by <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> may be null.</span></span> <span data-ttu-id="04c5e-158">Null-coallescing işleci?.</span><span class="sxs-lookup"><span data-stu-id="04c5e-158">The null-coallescing operator ?.</span></span> <span data-ttu-id="04c5e-159">C# ' de, yalnızca <xref:System.Diagnostics.Activity.SetTag%2A?displayProperty=nameWithType> etkinliğin null olmaması durumunda çağırmak için kullanışlı bir kısa süreli.</span><span class="sxs-lookup"><span data-stu-id="04c5e-159">in C# is a convenient short-hand to only invoke <xref:System.Diagnostics.Activity.SetTag%2A?displayProperty=nameWithType> if activity is not null.</span></span> <span data-ttu-id="04c5e-160">Bu davranış yazma ile aynıdır:</span><span class="sxs-lookup"><span data-stu-id="04c5e-160">The behavior is identical to writing:</span></span>

```csharp
if(activity != null)
{
    activity.SetTag("foo", foo);
}
```

- <span data-ttu-id="04c5e-161">Opentelemetri, uygulama işinin ortak türlerini temsil eden etkinliklerde Etiketler ayarlamak için önerilen bir [kurallar](https://github.com/open-telemetry/opentelemetry-specification/tree/main/specification/trace/semantic_conventions) kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="04c5e-161">OpenTelemetry provides a set of recommended [conventions](https://github.com/open-telemetry/opentelemetry-specification/tree/main/specification/trace/semantic_conventions) for setting Tags on Activities that represent common types of application work.</span></span>

- <span data-ttu-id="04c5e-162">İşlevleri yüksek performans gereksinimleriyle belirlerseniz, <xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> etkinlikleri dinleyen kodların herhangi birinin Etiketler gibi ikincil bilgileri okumayı amaçladığı bir ipucu olup olmadığını belirten bir ipucu vardır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-162">If you are instrumenting functions with high performance requirements, <xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> is a hint that indicates whether any of the code listening to Activities intends to read auxilliary information such as Tags.</span></span> <span data-ttu-id="04c5e-163">Hiçbir dinleyici okunmaz, izlenen kodun, CPU döngülerini doldurmasına gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="04c5e-163">If no listener will read it then there is no need for the instrumented code to spend CPU cycles populating it.</span></span> <span data-ttu-id="04c5e-164">Basitlik için bu örnek, bu iyileştirmesi uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="04c5e-164">For simplicity this sample doesn't apply that optimization.</span></span>

## <a name="optional-adding-events"></a><span data-ttu-id="04c5e-165">İsteğe bağlı: olayları ekleme</span><span class="sxs-lookup"><span data-stu-id="04c5e-165">Optional: Adding Events</span></span>

<span data-ttu-id="04c5e-166">Olaylar, etkinliklere ek tanılama verilerinin rastgele bir akışını iliştirebilmek için zaman damgamış iletilerdir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-166">Events are timestamped messages that can attach an arbitrary stream of additional diagnostic data to Activities.</span></span> <span data-ttu-id="04c5e-167">Etkinliğe bazı olaylar ekleyin:</span><span class="sxs-lookup"><span data-stu-id="04c5e-167">Add some events to the Activity:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-82cf6ea92661b84d9fd881731741d04e-33fff2835a03c041-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:39:10.6902609Z
Activity.Duration:    00:00:01.5147582
Activity.TagObjects:
    foo: banana
    bar: 8
Activity.Events:
    Part way there [3/18/2021 10:39:11 AM +00:00]
    Done now [3/18/2021 10:39:12 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: ea7f0fcb-3673-48e0-b6ce-e4af5a86ce4f

Example work done
```

#### <a name="best-practices"></a><span data-ttu-id="04c5e-168">En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="04c5e-168">Best Practices</span></span>

- <span data-ttu-id="04c5e-169">Olaylar, bu mekanizmayı yalnızca bir ila büyüklükteki sayısını kaydetmek için uygun hale getiren, bir bellek içi listede depolanır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-169">Events are stored in an in-memory list until they can be transmitted which makes this mechanism only suitable for recording a modest number of events.</span></span> <span data-ttu-id="04c5e-170">Bu görevde odaklanmış bir günlüğe kaydetme API 'SI kullanan büyük veya sınırsız miktarda olay için, [ILogger](https://docs.microsoft.com/aspnet/core/fundamentals/logging/) gibi daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-170">For a large or unbounded volume of events using a logging API focused on this task such as [ILogger](https://docs.microsoft.com/aspnet/core/fundamentals/logging/) is a better choice.</span></span> <span data-ttu-id="04c5e-171">ILogger Ayrıca, uygulama geliştiricisinin dağıtılmış izlemeyi kullanmasına bakılmaksızın günlüğe kaydetme bilgilerinin kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="04c5e-171">ILogger also ensures that the logging information will be available regardless whether the app developer opts to use distributed tracing.</span></span>
<span data-ttu-id="04c5e-172">ILogger, etkin etkinlik kimliklerinin otomatik olarak yakalanmasını destekler, böylece bu API ile günlüğe kaydedilen iletiler yine de Dağıtılmış izleme ile bağıntılı olabilir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-172">ILogger supports automatically capturing the active Activity IDs so messages logged via that API can still be correlated with the distributed trace.</span></span>

## <a name="optional-adding-status"></a><span data-ttu-id="04c5e-173">İsteğe bağlı: durum ekleme</span><span class="sxs-lookup"><span data-stu-id="04c5e-173">Optional: Adding Status</span></span>

<span data-ttu-id="04c5e-174">Opentelemetri, her etkinliğin işin geçiş/başarısız sonucunu temsil eden bir [durum](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#set-status) rapormasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-174">OpenTelemetry allows each Activity to report a [Status](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#set-status) that represents the pass/fail result of the work.</span></span> <span data-ttu-id="04c5e-175">.NET şu anda bu amaçla kesin türü belirtilmiş bir API 'ye sahip değildir ancak Etiketler kullanılarak oluşturulmuş bir kural vardır:</span><span class="sxs-lookup"><span data-stu-id="04c5e-175">.NET does not currently have a strongly typed API for this purpose but there is an established convention using Tags:</span></span>

- <span data-ttu-id="04c5e-176">`otel.status_code` , depolamak için kullanılan etiket adıdır `StatusCode` .</span><span class="sxs-lookup"><span data-stu-id="04c5e-176">`otel.status_code` is the Tag name used to store `StatusCode`.</span></span> <span data-ttu-id="04c5e-177">StatusCode etiketinin değerleri, "UNSET", "OK" veya "ERROR" dizelerinden biri olmalıdır ve numaralandırmalar, ve durum kodu için sırasıyla buna karşılık `Unset` gelir `Ok` `Error` .</span><span class="sxs-lookup"><span data-stu-id="04c5e-177">Values for the StatusCode tag must be one of the strings "UNSET", "OK", or "ERROR", which correspond respectively to the enums `Unset`, `Ok`, and `Error` from StatusCode.</span></span>
- <span data-ttu-id="04c5e-178">`otel.status_description` , isteğe bağlı olarak depolamak için kullanılan etiket adıdır `Description`</span><span class="sxs-lookup"><span data-stu-id="04c5e-178">`otel.status_description` is the Tag name used to store the optional `Description`</span></span>

<span data-ttu-id="04c5e-179">Şu durumu ayarlamak için DoSomeWork () öğesini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="04c5e-179">Update DoSomeWork() to set status:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));
                
                // Pretend something went wrong
                activity?.SetTag("otel.status_code", "ERROR");
                activity?.SetTag("otel.status_description", "Use this text give more information about the error");
            }
        }
```

## <a name="optional-add-additional-activities"></a><span data-ttu-id="04c5e-180">İsteğe bağlı: ek etkinlikler ekleme</span><span class="sxs-lookup"><span data-stu-id="04c5e-180">Optional: Add Additional Activities</span></span>

<span data-ttu-id="04c5e-181">Etkinlikler, daha büyük bir iş biriminin bölümlerini betimleyen iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-181">Activities can be nested to describe portions of a larger unit of work.</span></span> <span data-ttu-id="04c5e-182">Bu, özellikle, belirli dış bağımlılıklardan gelen hızlı bir şekilde yürütülemeyebilir veya daha iyi yerelleştirilmesine izin veren kod bölümlerinin etrafında yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-182">This can be particularly valuable around portions of code that might not execute quickly or to better localize failures that come from specific external dependencies.</span></span> <span data-ttu-id="04c5e-183">Bu örnek her yöntemde bir etkinlik kullansa da yalnızca ek kod simge durumuna küçültülmüş olabilir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-183">Although this sample uses an Activity in every method, that is solely because extra code has been minimized.</span></span> <span data-ttu-id="04c5e-184">Her yöntemde etkinlik kullanan daha büyük ve daha gerçekçi bir projede, önerilmez.</span><span class="sxs-lookup"><span data-stu-id="04c5e-184">In a larger and more realistic project using an Activity in every method would produce extremely verbose traces so it is not recommended.</span></span>

<span data-ttu-id="04c5e-185">Bu ayrı adımların etrafında daha fazla izleme eklemek için StepOne ve StepTwo güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="04c5e-185">Update StepOne and StepTwo to add more tracing around these separate steps:</span></span>

```csharp
        static async Task StepOne()
        {
            using (Activity activity = source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity activity = source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-39cac574e8fda44b-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepOne
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4278822Z
Activity.Duration:    00:00:00.5051364
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-4ccccb6efdc59546-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepTwo
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.9441095Z
Activity.Duration:    00:00:01.0052729
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4256627Z
Activity.Duration:    00:00:01.5286408
Activity.TagObjects:
    foo: banana
    bar: 8
    otel.status_code: ERROR
    otel.status_description: Use this text give more information about the error
Activity.Events:
    Part way there [3/18/2021 10:40:51 AM +00:00]
    Done now [3/18/2021 10:40:52 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Example work done
```

<span data-ttu-id="04c5e-186">Her iki StepOne ve StepTwo, SomeWork 'e başvuran bir parentID içerir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-186">Notice that both StepOne and StepTwo include a ParentId that refers to SomeWork.</span></span> <span data-ttu-id="04c5e-187">Konsol, iç içe geçmiş iş ağaçlarının harika bir görselleştirmesi değildir, ancak [zipa](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/src/OpenTelemetry.Exporter.Zipkin/README.md) gıbı birçok GUI Görüntüleyici bunu bir Gantt grafiği olarak gösterebilir:</span><span class="sxs-lookup"><span data-stu-id="04c5e-187">The console is not a great visualization of nested trees of work, but many GUI viewers such as [Zipkin](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/src/OpenTelemetry.Exporter.Zipkin/README.md) can show this as a Gantt chart:</span></span>

<span data-ttu-id="04c5e-188">[![Zipkaya Gantt grafiği](media/zipkin-nested-activities.jpg)](media/zipkin-nested-activities.jpg)</span><span class="sxs-lookup"><span data-stu-id="04c5e-188">[![Zipkin Gantt chart](media/zipkin-nested-activities.jpg)](media/zipkin-nested-activities.jpg)</span></span>

### <a name="optional-activitykind"></a><span data-ttu-id="04c5e-189">İsteğe bağlı: ActivityKind</span><span class="sxs-lookup"><span data-stu-id="04c5e-189">Optional: ActivityKind</span></span>

<span data-ttu-id="04c5e-190">Etkinlikler <xref:System.Diagnostics.Activity.Kind%2A?displayProperty=nameWithType> , etkinlik, üst ve alt öğeleri arasındaki ilişkiyi açıklayan bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-190">Activities have an <xref:System.Diagnostics.Activity.Kind%2A?displayProperty=nameWithType> property which describes the relationship between the Activity, its parent and its children.</span></span> <span data-ttu-id="04c5e-191">Varsayılan olarak, tüm yeni etkinlikler, <xref:System.Diagnostics.ActivityKind.Internal> uzak üst veya alt öğeleri olmayan bir uygulama içinde iç işlem olan etkinliklere uygun olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="04c5e-191">By default all new Activities are set to <xref:System.Diagnostics.ActivityKind.Internal> which is appropriate for Activities that are an internal operation within an application with no remote parent or children.</span></span> <span data-ttu-id="04c5e-192">Diğer türleri üzerinde tür parametresi kullanılarak ayarlanabilir <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="04c5e-192">Other kinds can be set using the kind parameter on <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="04c5e-193"><xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType>Diğer seçenekler için bkz..</span><span class="sxs-lookup"><span data-stu-id="04c5e-193">See <xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> for other options.</span></span>

### <a name="optional-links"></a><span data-ttu-id="04c5e-194">İsteğe bağlı: bağlantılar</span><span class="sxs-lookup"><span data-stu-id="04c5e-194">Optional: Links</span></span>

<span data-ttu-id="04c5e-195">Toplu işlem sistemlerinde iş gerçekleştiğinde tek bir etkinlik, her birinin kendi izleme kimliği olan aynı anda birçok farklı istek adına işi temsil edebilir. Etkinlik tek bir üst öğeye sahip olacak şekilde kısıtlanmış olsa da, kullanarak ek izleme kimliklerine bağlanabilir <xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="04c5e-195">When work occurs in batch processing systems a single Activity might represent work on behalf of many different requests simultaneously, each of which has its own trace-id. Although Activity is restricted to have a single parent, it can link to additional trace-ids using <xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType>.</span></span> <span data-ttu-id="04c5e-196">Her ActivityLink, <xref:System.Diagnostics.ActivityContext> bağlanmakta olan etkinlik HAKKıNDAKI kimlik bilgilerini depolayan bir ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="04c5e-196">Each ActivityLink is populated with an <xref:System.Diagnostics.ActivityContext> that stores ID information about the Activity being linked to.</span></span> <span data-ttu-id="04c5e-197">ActivityContext, kullanarak işlem içi etkinlik nesnelerinden alınabilir <xref:System.Diagnostics.Activity.Context%2A?displayProperty=nameWithType> veya kullanılarak serileştirilmiş kimlik bilgileri ayrıştırılabilir <xref:System.Diagnostics.ActivityContext.Parse(System.String,System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="04c5e-197">ActivityContext can be retrieved from in-process Activity objects using <xref:System.Diagnostics.Activity.Context%2A?displayProperty=nameWithType> or it can be parsed from serialized id information using <xref:System.Diagnostics.ActivityContext.Parse(System.String,System.String)?displayProperty=nameWithType>.</span></span>

```csharp
void DoBatchWork(ActivityContext[] requestContexts)
{
    // Assume each context in requestContexts encodes the trace-id that was sent with a request
    using(Activity activity = s_source.StartActivity(name: "BigBatchOfWork",
                                                     kind: ActivityKind.Internal,
                                                     parentContext: null,
                                                     links: requestContexts.Select(ctx => new ActivityLink(ctx))
    {
        // do the batch of work here
    }
}
```

<span data-ttu-id="04c5e-198">İsteğe bağlı eklenebilen olayların ve etiketlerin aksine, StartActivity () sırasında bağlantıların eklenmesi ve daha sonra sabit olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="04c5e-198">Unlike events and Tags that can be added on-demand, links must be added during StartActivity() and are immutable afterwards.</span></span>
