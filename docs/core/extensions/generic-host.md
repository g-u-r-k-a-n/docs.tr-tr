---
title: .NET genel ana bilgisayar
author: IEvangelist
description: Uygulama başlatma ve ömür yönetiminden sorumlu .NET genel ana bilgisayarı hakkında bilgi edinin.
ms.author: dapine
ms.date: 12/04/2020
ms.openlocfilehash: ddb71b70d15121b7f59899fba38b2bf861219878
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740099"
---
# <a name="net-generic-host"></a><span data-ttu-id="a6a86-103">.NET genel ana bilgisayar</span><span class="sxs-lookup"><span data-stu-id="a6a86-103">.NET Generic Host</span></span>

<span data-ttu-id="a6a86-104">Çalışan hizmeti şablonları bir .NET genel ana bilgisayarı oluşturur <xref:Microsoft.Extensions.Hosting.HostBuilder> .</span><span class="sxs-lookup"><span data-stu-id="a6a86-104">The Worker Service templates create a .NET Generic Host, <xref:Microsoft.Extensions.Hosting.HostBuilder>.</span></span> <span data-ttu-id="a6a86-105">Genel ana bilgisayar, konsol uygulamaları gibi diğer .NET uygulaması türleriyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6a86-105">The Generic Host can be used with other types of .NET applications, such as Console apps.</span></span>

<span data-ttu-id="a6a86-106">*Ana bilgisayar* , bir uygulamanın kaynaklarını kapsülleyen bir nesnedir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="a6a86-106">A *host* is an object that encapsulates an app's resources, such as:</span></span>

- <span data-ttu-id="a6a86-107">Bağımlılık ekleme (dı)</span><span class="sxs-lookup"><span data-stu-id="a6a86-107">Dependency injection (DI)</span></span>
- <span data-ttu-id="a6a86-108">Günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="a6a86-108">Logging</span></span>
- <span data-ttu-id="a6a86-109">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a6a86-109">Configuration</span></span>
- <span data-ttu-id="a6a86-110">`IHostedService` uygulamalarını</span><span class="sxs-lookup"><span data-stu-id="a6a86-110">`IHostedService` implementations</span></span>

<span data-ttu-id="a6a86-111">Bir konak başlatıldığında, <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> <xref:Microsoft.Extensions.Hosting.IHostedService> hizmet kapsayıcısının barındırılan hizmetler koleksiyonunda kayıtlı her bir uygulamasına çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="a6a86-111">When a host starts, it calls <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> on each implementation of <xref:Microsoft.Extensions.Hosting.IHostedService> registered in the service container's collection of hosted services.</span></span> <span data-ttu-id="a6a86-112">Çalışan hizmeti uygulamasında, `IHostedService` örnekleri içeren tüm uygulamaların <xref:Microsoft.Extensions.Hosting.BackgroundService> <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a6a86-112">In a worker service app, all `IHostedService` implementations that contain <xref:Microsoft.Extensions.Hosting.BackgroundService> instances have their <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> methods called.</span></span>

<span data-ttu-id="a6a86-113">Uygulamanın tüm birbirine bağlı kaynaklarını tek bir nesnede dahil etmek için başlıca neden, yaşam süresi yönetimi: uygulama başlatma ve düzgün kapanma üzerinde denetim.</span><span class="sxs-lookup"><span data-stu-id="a6a86-113">The main reason for including all of the app's interdependent resources in one object is lifetime management: control over app startup and graceful shutdown.</span></span> <span data-ttu-id="a6a86-114">Bu, [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet paketi ile sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a6a86-114">This is achieved with the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package.</span></span>

## <a name="set-up-a-host"></a><span data-ttu-id="a6a86-115">Konak ayarlama</span><span class="sxs-lookup"><span data-stu-id="a6a86-115">Set up a host</span></span>

<span data-ttu-id="a6a86-116">Ana bilgisayar genellikle sınıfında kodla yapılandırılır, oluşturulur ve çalıştırılır `Program` .</span><span class="sxs-lookup"><span data-stu-id="a6a86-116">The host is typically configured, built, and run by code in the `Program` class.</span></span> <span data-ttu-id="a6a86-117">`Main`Yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a6a86-117">The `Main` method:</span></span>

- <span data-ttu-id="a6a86-118"><xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder>Bir Oluşturucu nesnesi oluşturmak ve yapılandırmak için bir yöntem çağırır.</span><span class="sxs-lookup"><span data-stu-id="a6a86-118">Calls a <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> method to create and configure a builder object.</span></span>
- <span data-ttu-id="a6a86-119"><xref:Microsoft.Extensions.Hosting.IHostBuilder.Build>Örnek oluşturmak için çağırır <xref:Microsoft.Extensions.Hosting.IHost> .</span><span class="sxs-lookup"><span data-stu-id="a6a86-119">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> to create an <xref:Microsoft.Extensions.Hosting.IHost> instance.</span></span>
- <span data-ttu-id="a6a86-120"><xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> Ana bilgisayar nesnesi üzerinde veya yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a6a86-120">Calls <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> or <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> method on the host object.</span></span>

<span data-ttu-id="a6a86-121">.NET Worker hizmet şablonları, genel bir konak oluşturmak için aşağıdaki kodu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a6a86-121">The .NET Worker Service templates generate the following code to create a Generic Host:</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureServices((hostContext, services) =>
            {
                services.AddHostedService<Worker>();
            });
}
```

## <a name="default-builder-settings"></a><span data-ttu-id="a6a86-122">Varsayılan Oluşturucu ayarları</span><span class="sxs-lookup"><span data-stu-id="a6a86-122">Default builder settings</span></span>

<span data-ttu-id="a6a86-123"><xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>Yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a6a86-123">The <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> method:</span></span>

- <span data-ttu-id="a6a86-124">İçerik kökünü tarafından döndürülen yola ayarlar <xref:System.IO.Directory.GetCurrentDirectory> .</span><span class="sxs-lookup"><span data-stu-id="a6a86-124">Sets the content root to the path returned by <xref:System.IO.Directory.GetCurrentDirectory>.</span></span>
- <span data-ttu-id="a6a86-125">[Ana bilgisayar yapılandırmasını](#host-configuration) şuradan yükler:</span><span class="sxs-lookup"><span data-stu-id="a6a86-125">Loads [host configuration](#host-configuration) from:</span></span>
  - <span data-ttu-id="a6a86-126">Ön eki olan ortam değişkenleri `DOTNET_` .</span><span class="sxs-lookup"><span data-stu-id="a6a86-126">Environment variables prefixed with `DOTNET_`.</span></span>
  - <span data-ttu-id="a6a86-127">Komut satırı bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="a6a86-127">Command-line arguments.</span></span>
- <span data-ttu-id="a6a86-128">Uygulama yapılandırmasını şuradan yükler:</span><span class="sxs-lookup"><span data-stu-id="a6a86-128">Loads app configuration from:</span></span>
  - <span data-ttu-id="a6a86-129">*Üzerindeappsettings.js*.</span><span class="sxs-lookup"><span data-stu-id="a6a86-129">*appsettings.json*.</span></span>
  - <span data-ttu-id="a6a86-130">*appSettings. {Environment}. JSON*.</span><span class="sxs-lookup"><span data-stu-id="a6a86-130">*appsettings.{Environment}.json*.</span></span>
  - <span data-ttu-id="a6a86-131">Uygulama ortamda çalıştığında gizli dizi Yöneticisi `Development` .</span><span class="sxs-lookup"><span data-stu-id="a6a86-131">Secret Manager when the app runs in the `Development` environment.</span></span>
  - <span data-ttu-id="a6a86-132">Ortam değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="a6a86-132">Environment variables.</span></span>
  - <span data-ttu-id="a6a86-133">Komut satırı bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="a6a86-133">Command-line arguments.</span></span>
- <span data-ttu-id="a6a86-134">Aşağıdaki günlük sağlayıcılarını ekler:</span><span class="sxs-lookup"><span data-stu-id="a6a86-134">Adds the following logging providers:</span></span>
  - <span data-ttu-id="a6a86-135">Konsol</span><span class="sxs-lookup"><span data-stu-id="a6a86-135">Console</span></span>
  - <span data-ttu-id="a6a86-136">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a6a86-136">Debug</span></span>
  - <span data-ttu-id="a6a86-137">EventSource</span><span class="sxs-lookup"><span data-stu-id="a6a86-137">EventSource</span></span>
  - <span data-ttu-id="a6a86-138">Olay günlüğü (yalnızca Windows üzerinde çalışırken)</span><span class="sxs-lookup"><span data-stu-id="a6a86-138">EventLog (only when running on Windows)</span></span>
- <span data-ttu-id="a6a86-139">Ortam olduğunda kapsam doğrulaması ve [bağımlılık doğrulaması](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) etkinleştirilir `Development` .</span><span class="sxs-lookup"><span data-stu-id="a6a86-139">Enables scope validation and [dependency validation](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) when the environment is `Development`.</span></span>

<span data-ttu-id="a6a86-140">`ConfigureServices`Yöntemi, örneğe hizmet ekleme özelliğini kullanıma sunar <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a6a86-140">The `ConfigureServices` method exposes the ability to add services to the <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="a6a86-141">Daha sonra, bu hizmetler bağımlılık ekleme yoluyla kullanılabilir hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a6a86-141">Later, these services can be made available from dependency injection.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="a6a86-142">Framework tarafından sunulan hizmetler</span><span class="sxs-lookup"><span data-stu-id="a6a86-142">Framework-provided services</span></span>

<span data-ttu-id="a6a86-143">Aşağıdaki hizmetler otomatik olarak kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="a6a86-143">The following services are registered automatically:</span></span>

- [<span data-ttu-id="a6a86-144">Ihostapplicationlifetime</span><span class="sxs-lookup"><span data-stu-id="a6a86-144">IHostApplicationLifetime</span></span>](#ihostapplicationlifetime)
- [<span data-ttu-id="a6a86-145">Ihostlifetime</span><span class="sxs-lookup"><span data-stu-id="a6a86-145">IHostLifetime</span></span>](#ihostlifetime)
- [<span data-ttu-id="a6a86-146">Ihostenvironment</span><span class="sxs-lookup"><span data-stu-id="a6a86-146">IHostEnvironment</span></span>](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a><span data-ttu-id="a6a86-147">Ihostapplicationlifetime</span><span class="sxs-lookup"><span data-stu-id="a6a86-147">IHostApplicationLifetime</span></span>

<span data-ttu-id="a6a86-148"><xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>Başlatma sonrası ve düzgün kapanma görevlerini işlemek için hizmeti herhangi bir sınıfa ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6a86-148">Inject the <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> service into any class to handle post-startup and graceful shutdown tasks.</span></span> <span data-ttu-id="a6a86-149">Arabirimdeki üç özellik, uygulama başlatma ve uygulama durdurma olay işleyicisi yöntemlerini kaydetmek için kullanılan iptal belirteçleridir.</span><span class="sxs-lookup"><span data-stu-id="a6a86-149">Three properties on the interface are cancellation tokens used to register app start and app stop event handler methods.</span></span> <span data-ttu-id="a6a86-150">Arabirim Ayrıca bir yöntemi içerir <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> .</span><span class="sxs-lookup"><span data-stu-id="a6a86-150">The interface also includes a <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> method.</span></span>

<span data-ttu-id="a6a86-151">Aşağıdaki örnek, `IHostedService` olayları kaydeden bir uygulamasıdır `IHostApplicationLifetime` :</span><span class="sxs-lookup"><span data-stu-id="a6a86-151">The following example is an `IHostedService` implementation that registers `IHostApplicationLifetime` events:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

<span data-ttu-id="a6a86-152">Çalışan hizmeti şablonu, uygulamayı eklemek için değiştirilebilir `ExampleHostedService` :</span><span class="sxs-lookup"><span data-stu-id="a6a86-152">The Worker Service template could be modified to add the `ExampleHostedService` implementation:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

<span data-ttu-id="a6a86-153">Uygulama aşağıdaki örnek çıktıyı Yazar:</span><span class="sxs-lookup"><span data-stu-id="a6a86-153">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a><span data-ttu-id="a6a86-154">Ihostlifetime</span><span class="sxs-lookup"><span data-stu-id="a6a86-154">IHostLifetime</span></span>

<span data-ttu-id="a6a86-155"><xref:Microsoft.Extensions.Hosting.IHostLifetime>Uygulama, ana bilgisayar başladığında ve durdurulduğunda denetler.</span><span class="sxs-lookup"><span data-stu-id="a6a86-155">The <xref:Microsoft.Extensions.Hosting.IHostLifetime> implementation controls when the host starts and when it stops.</span></span> <span data-ttu-id="a6a86-156">Kaydedilen son uygulama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6a86-156">The last implementation registered is used.</span></span>

<span data-ttu-id="a6a86-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` Varsayılan `IHostLifetime` uygulama.</span><span class="sxs-lookup"><span data-stu-id="a6a86-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` is the default `IHostLifetime` implementation.</span></span> <span data-ttu-id="a6a86-158">`ConsoleLifetime`:</span><span class="sxs-lookup"><span data-stu-id="a6a86-158">`ConsoleLifetime`:</span></span>

- <span data-ttu-id="a6a86-159"><kbd>CTRL</kbd> + <kbd>C</kbd>, [sigint](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT)veya [sigterm](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) 'i dinler ve <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> başlatma işlemini başlatmak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="a6a86-159">Listens for <kbd>Ctrl</kbd>+<kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT), or [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) and calls <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> to start the shutdown process.</span></span>
- <span data-ttu-id="a6a86-160">Ve gibi uzantıları kaldırır `RunAsync` `WaitForShutdownAsync` .</span><span class="sxs-lookup"><span data-stu-id="a6a86-160">Unblocks extensions such as `RunAsync` and `WaitForShutdownAsync`.</span></span>

## <a name="ihostenvironment"></a><span data-ttu-id="a6a86-161">Ihostenvironment</span><span class="sxs-lookup"><span data-stu-id="a6a86-161">IHostEnvironment</span></span>

<span data-ttu-id="a6a86-162"><xref:Microsoft.Extensions.Hosting.IHostEnvironment>Aşağıdaki ayarlarla ilgili bilgi almak için hizmeti bir sınıfa ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a6a86-162">Inject the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> service into a class to get information about the following settings:</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a><span data-ttu-id="a6a86-163">Konak yapılandırması</span><span class="sxs-lookup"><span data-stu-id="a6a86-163">Host configuration</span></span>

<span data-ttu-id="a6a86-164">Ana bilgisayar yapılandırması, uygulamanın özellikleri için kullanılır <xref:Microsoft.Extensions.Hosting.IHostEnvironment> .</span><span class="sxs-lookup"><span data-stu-id="a6a86-164">Host configuration is used for the properties of the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> implementation.</span></span>

<span data-ttu-id="a6a86-165">Ana Bilgisayar Yapılandırması içinde [HostBuilderContext.Configurlama](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) tarafından kullanılabilir <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> .</span><span class="sxs-lookup"><span data-stu-id="a6a86-165">Host configuration is available from [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) inside <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>.</span></span> <span data-ttu-id="a6a86-166">Sonra `ConfigureAppConfiguration` , `HostBuilderContext.Configuration` uygulama yapılandırması ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a6a86-166">After `ConfigureAppConfiguration`, `HostBuilderContext.Configuration` is replaced with the app config.</span></span>

<span data-ttu-id="a6a86-167">Konak yapılandırması eklemek için üzerinde öğesini <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> çağırın `IHostBuilder` .</span><span class="sxs-lookup"><span data-stu-id="a6a86-167">To add host configuration, call <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="a6a86-168">`ConfigureHostConfiguration` , eklenebilir sonuçlarla birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6a86-168">`ConfigureHostConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="a6a86-169">Ana bilgisayar, belirli bir anahtardaki bir değeri en son belirleyen seçeneği kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6a86-169">The host uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="a6a86-170">Aşağıdaki örnek ana bilgisayar yapılandırması oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a6a86-170">The following example creates host configuration:</span></span>

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="19-25":::

## <a name="app-configuration"></a><span data-ttu-id="a6a86-171">Uygulama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="a6a86-171">App configuration</span></span>

<span data-ttu-id="a6a86-172">Uygulama yapılandırması, üzerinde çağırarak oluşturulur <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> `IHostBuilder` .</span><span class="sxs-lookup"><span data-stu-id="a6a86-172">App configuration is created by calling <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="a6a86-173">`ConfigureAppConfiguration` , eklenebilir sonuçlarla birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6a86-173">`ConfigureAppConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="a6a86-174">Uygulama, belirli bir anahtardaki bir değeri en son belirleyen seçeneği kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6a86-174">The app uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="a6a86-175">Tarafından oluşturulan yapılandırma, `ConfigureAppConfiguration` sonraki işlemler ve dı hizmeti olarak [HostBuilderContext.Config](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) bir hizmet olarak sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6a86-175">The configuration created by `ConfigureAppConfiguration` is available at [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) for subsequent operations and as a service from DI.</span></span> <span data-ttu-id="a6a86-176">Konak yapılandırması, uygulama yapılandırmasına de eklenir.</span><span class="sxs-lookup"><span data-stu-id="a6a86-176">The host configuration is also added to the app configuration.</span></span>

<span data-ttu-id="a6a86-177">Daha fazla bilgi için bkz. [.net 'Teki yapılandırma](configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a6a86-177">For more information, see [Configuration in .NET](configuration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6a86-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6a86-178">See also</span></span>

- [<span data-ttu-id="a6a86-179">.NET 'teki yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a6a86-179">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="a6a86-180">ASP.NET Core Web ana bilgisayarı</span><span class="sxs-lookup"><span data-stu-id="a6a86-180">ASP.NET Core Web Host</span></span>](/aspnet/core/fundamentals/host/web-host)
- <span data-ttu-id="a6a86-181">Genel ana bilgisayar hataları [GitHub.com/DotNet/Extensions](https://github.com/dotnet/extensions/issues) deposu 'nda oluşturulmalıdır</span><span class="sxs-lookup"><span data-stu-id="a6a86-181">Generic host bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
