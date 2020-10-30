---
title: .NET 'e bağımlılık ekleme
description: .NET 'in bağımlılık ekleme ve nasıl kullanılacağı hakkında bilgi edinin.
author: IEvangelist
ms.author: dapine
ms.date: 10/28/2020
ms.topic: overview
ms.openlocfilehash: 2199f51ab13bedd50af747ce33ceee7b6eaefd8f
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063149"
---
# <a name="dependency-injection-in-net"></a><span data-ttu-id="cc664-103">.NET 'e bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="cc664-103">Dependency injection in .NET</span></span>

<span data-ttu-id="cc664-104">.NET bağımlılık ekleme (dı) yazılım tasarımı modelini destekler, bu, sınıflar ve bunların bağımlılıkları arasında [denetimin INVERSION (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) elde etmek için bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="cc664-104">.NET supports the dependency injection (DI) software design pattern, which is a technique for achieving [Inversion of Control (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) between classes and their dependencies.</span></span> <span data-ttu-id="cc664-105">.NET ' te bağımlılık ekleme, yapılandırma, günlük oluşturma ve seçenekler düzeniyle birlikte [birinci sınıf bir vatandaşlık](https://en.wikipedia.org/wiki/First-class_citizen).</span><span class="sxs-lookup"><span data-stu-id="cc664-105">Dependency injection in .NET is a [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen), along with configuration, logging, and the options pattern.</span></span>

<span data-ttu-id="cc664-106">*Bağımlılık* , başka bir nesnenin bağımlı olduğu bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="cc664-106">A *dependency* is an object that another object depends on.</span></span> <span data-ttu-id="cc664-107">Aşağıdaki sınıfı, `MessageWriter` `Write` diğer sınıfların bağımlı olduğu bir yöntemle inceleyin:</span><span class="sxs-lookup"><span data-stu-id="cc664-107">Examine the following `MessageWriter` class with a `Write` method that other classes depend on:</span></span>

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

<span data-ttu-id="cc664-108">Bir sınıf, `MessageWriter` yöntemini kullanmak için sınıfının bir örneğini oluşturabilir `Write` .</span><span class="sxs-lookup"><span data-stu-id="cc664-108">A class can create an instance of the `MessageWriter` class to make use of its `Write` method.</span></span> <span data-ttu-id="cc664-109">Aşağıdaki örnekte, `MessageWriter` sınıfı sınıfının bir bağımlılığı olur `Worker` :</span><span class="sxs-lookup"><span data-stu-id="cc664-109">In the following example, the `MessageWriter` class is a dependency of the `Worker` class:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="cc664-110">Sınıfı oluşturur ve doğrudan `MessageWriter` sınıfa bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cc664-110">The class creates and directly depends on the `MessageWriter` class.</span></span> <span data-ttu-id="cc664-111">Önceki örnekte olduğu gibi sabit kodlu bağımlılıklar sorunlu olur ve aşağıdaki nedenlerden dolayı kaçınılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="cc664-111">Hard-coded dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:</span></span>

- <span data-ttu-id="cc664-112">`MessageWriter`Farklı bir uygulamayla değiştirmek için, `MessageService` sınıfın değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc664-112">To replace `MessageWriter` with a different implementation, the `MessageService` class must be modified.</span></span>
- <span data-ttu-id="cc664-113">`MessageWriter`Bağımlılıkları varsa, sınıf tarafından da yapılandırılmalıdır `MessageService` .</span><span class="sxs-lookup"><span data-stu-id="cc664-113">If `MessageWriter` has dependencies, they must also be configured by the `MessageService` class.</span></span> <span data-ttu-id="cc664-114">Uygulamasına bağlı olarak, birden çok sınıfı olan büyük bir projede `MessageWriter` yapılandırma kodu uygulama genelinde dağılmış hale gelir.</span><span class="sxs-lookup"><span data-stu-id="cc664-114">In a large project with multiple classes depending on `MessageWriter`, the configuration code becomes scattered across the app.</span></span>
- <span data-ttu-id="cc664-115">Bu uygulamanın birim testi zordur.</span><span class="sxs-lookup"><span data-stu-id="cc664-115">This implementation is difficult to unit test.</span></span> <span data-ttu-id="cc664-116">Uygulamanın `MessageWriter` Bu yaklaşım ile mümkün olmayan bir sahte veya saplama sınıfı kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc664-116">The app should use a mock or stub `MessageWriter` class, which isn't possible with this approach.</span></span>

<span data-ttu-id="cc664-117">Bağımlılık ekleme bu sorunları şu şekilde giderir:</span><span class="sxs-lookup"><span data-stu-id="cc664-117">Dependency injection addresses these problems through:</span></span>

- <span data-ttu-id="cc664-118">Bağımlılık uygulamasını soyutlamak için bir arabirim veya temel sınıf kullanımı.</span><span class="sxs-lookup"><span data-stu-id="cc664-118">The use of an interface or base class to abstract the dependency implementation.</span></span>
- <span data-ttu-id="cc664-119">Bir hizmet kapsayıcısına bağımlılığın kaydı.</span><span class="sxs-lookup"><span data-stu-id="cc664-119">Registration of the dependency in a service container.</span></span> <span data-ttu-id="cc664-120">.NET, yerleşik bir hizmet kapsayıcısı sağlar <xref:System.IServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="cc664-120">.NET provides a built-in service container, <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="cc664-121">Hizmetler genellikle uygulamanın başlangıcında kaydedilir ve bir öğesine eklenir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="cc664-121">Services are typically registered at the app's start-up, and appended to an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="cc664-122">Tüm hizmetler eklendikten sonra, <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> hizmet kapsayıcısını oluşturmak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="cc664-122">Once all services are added, you use <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> to create the service container.</span></span>
- <span data-ttu-id="cc664-123">Hizmetin kullanıldığı sınıf oluşturucusuna *ekleme* .</span><span class="sxs-lookup"><span data-stu-id="cc664-123">*Injection* of the service into the constructor of the class where it's used.</span></span> <span data-ttu-id="cc664-124">Çerçeve, bağımlılığın bir örneğini oluşturma ve artık gerekli olmadığında bu uygulamayı atma sorumluluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="cc664-124">The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.</span></span>

<span data-ttu-id="cc664-125">Örnek olarak, `IMessageWriter` arabirim `Write` yöntemini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="cc664-125">As an example, the `IMessageWriter` interface defines the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

<span data-ttu-id="cc664-126">Bu arabirim somut bir tür tarafından uygulanır, `MessageWriter` :</span><span class="sxs-lookup"><span data-stu-id="cc664-126">This interface is implemented by a concrete type, `MessageWriter`:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

<span data-ttu-id="cc664-127">Örnek kod, `IMessageWriter` hizmeti somut tür ile kaydeder `MessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="cc664-127">The sample code registers the `IMessageWriter` service with the concrete type `MessageWriter`.</span></span> <span data-ttu-id="cc664-128"><xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>Yöntemi, hizmeti tek bir isteğin ömrü olan kapsamlı bir yaşam süresine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cc664-128">The <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> method registers the service with a scoped lifetime, the lifetime of a single request.</span></span> <span data-ttu-id="cc664-129">[Hizmet yaşam süreleri](#service-lifetimes) bu konunun ilerleyen kısımlarında açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cc664-129">[Service lifetimes](#service-lifetimes) are described later in this topic.</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

<span data-ttu-id="cc664-130">Örnek uygulamada, `IMessageWriter` hizmet istenir ve yöntemi çağırmak için kullanılır `Write` :</span><span class="sxs-lookup"><span data-stu-id="cc664-130">In the sample app, the `IMessageWriter` service is requested and used to call the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

<span data-ttu-id="cc664-131">Dı modelini kullanarak çalışan hizmeti:</span><span class="sxs-lookup"><span data-stu-id="cc664-131">By using the DI pattern, the worker service:</span></span>

- <span data-ttu-id="cc664-132">Somut türü kullanmaz `MessageWriter` , yalnızca `IMessageWriter` onu uygulayan arabirim.</span><span class="sxs-lookup"><span data-stu-id="cc664-132">Doesn't use the concrete type `MessageWriter`, only the `IMessageWriter` interface that implements it.</span></span> <span data-ttu-id="cc664-133">Bu, denetleyicinin, denetleyiciyi değiştirmeden kullandığı uygulamayı değiştirmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="cc664-133">That makes it easy to change the implementation that the controller uses without modifying the controller.</span></span>
- <span data-ttu-id="cc664-134">Bir örneği oluşturmaz `MessageWriter` , bu, dı kapsayıcısı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cc664-134">Doesn't create an instance of `MessageWriter`, it's created by the DI container.</span></span>

<span data-ttu-id="cc664-135">Arabirim uygulanması, `IMessageWriter` yerleşik günlük API 'si kullanılarak artırılabilir:</span><span class="sxs-lookup"><span data-stu-id="cc664-135">The implementation of the `IMessageWriter` interface can be improved by using the built-in logging API:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

<span data-ttu-id="cc664-136">Updated `ConfigureServices` yöntemi yeni `IMessageWriter` uygulamayı kaydeder:</span><span class="sxs-lookup"><span data-stu-id="cc664-136">The updated `ConfigureServices` method registers the new `IMessageWriter` implementation:</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

<span data-ttu-id="cc664-137">`LoggingMessageWriter`<xref:Microsoft.Extensions.Logging.ILogger%601>, oluşturucuda istediği öğesine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cc664-137">`LoggingMessageWriter` depends on <xref:Microsoft.Extensions.Logging.ILogger%601>, which it requests in the constructor.</span></span> <span data-ttu-id="cc664-138">`ILogger<TCategoryName>`[Framework tarafından sağlanmış bir hizmettir](#framework-provided-services).</span><span class="sxs-lookup"><span data-stu-id="cc664-138">`ILogger<TCategoryName>` is a [framework-provided service](#framework-provided-services).</span></span>

<span data-ttu-id="cc664-139">Bağımlılık ekleme işlemini zincirleme bir biçimde kullanmak olağan dışı değildir.</span><span class="sxs-lookup"><span data-stu-id="cc664-139">It's not unusual to use dependency injection in a chained fashion.</span></span> <span data-ttu-id="cc664-140">Her istenen bağımlılık, kendi bağımlılıklarını ister.</span><span class="sxs-lookup"><span data-stu-id="cc664-140">Each requested dependency in turn requests its own dependencies.</span></span> <span data-ttu-id="cc664-141">Kapsayıcı grafikteki bağımlılıkları çözer ve tamamen çözümlenen hizmeti döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc664-141">The container resolves the dependencies in the graph and returns the fully resolved service.</span></span> <span data-ttu-id="cc664-142">Çözümlenmesi gereken, genellikle *bağımlılık ağacı* , *bağımlılık grafiği* veya *nesne grafiği* olarak adlandırılan toplu bağımlılıklar kümesi.</span><span class="sxs-lookup"><span data-stu-id="cc664-142">The collective set of dependencies that must be resolved is typically referred to as a *dependency tree* , *dependency graph* , or *object graph* .</span></span>

<span data-ttu-id="cc664-143">Kapsayıcı, `ILogger<TCategoryName>` [(genel) açık türlerden](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types)yararlanarak çözümlenir, her [(genel) oluşturulan türü](/dotnet/csharp/language-reference/language-specification/types#constructed-types)kaydetme ihtiyacını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cc664-143">The container resolves `ILogger<TCategoryName>` by taking advantage of [(generic) open types](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminating the need to register every [(generic) constructed type](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span></span>

<span data-ttu-id="cc664-144">Bağımlılık ekleme terminolojisi ' nde bir hizmet:</span><span class="sxs-lookup"><span data-stu-id="cc664-144">In dependency injection terminology, a service:</span></span>

- <span data-ttu-id="cc664-145">Genellikle hizmet gibi diğer nesnelere hizmet sağlayan bir nesnedir `IMessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="cc664-145">Is typically an object that provides a service to other objects, such as the `IMessageWriter` service.</span></span>
- <span data-ttu-id="cc664-146">Bir Web hizmetiyle ilgili değildir, ancak hizmet bir Web hizmeti kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="cc664-146">Is not related to a web service, although the service may use a web service.</span></span>

<span data-ttu-id="cc664-147">Çerçeve, güçlü bir günlük sistemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc664-147">The framework provides a robust logging system.</span></span> <span data-ttu-id="cc664-148">`IMessageWriter`Yukarıdaki örneklerde gösterilen uygulamalar, günlüğü uygulamamak için değil temel dı 'yi göstermek için yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cc664-148">The `IMessageWriter` implementations shown in the preceding examples were written to demonstrate basic DI, not to implement logging.</span></span> <span data-ttu-id="cc664-149">Çoğu uygulamanın Günlükçüler yazması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cc664-149">Most apps shouldn't need to write loggers.</span></span> <span data-ttu-id="cc664-150">Aşağıdaki kod, yalnızca `Worker` ' ın `ConfigureServices` barındırılan bir hizmet olarak kaydedilmesini gerektiren varsayılan günlük kaydını kullanmayı göstermektedir <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> :</span><span class="sxs-lookup"><span data-stu-id="cc664-150">The following code demonstrates using the default logging, which only requires the `Worker` to be registered in `ConfigureServices` as a hosted service <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="cc664-151">Yukarıdaki kodu kullanarak, `ConfigureServices` Framework tarafından günlüğe kaydetme sağlandığı için güncelleştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cc664-151">Using the preceding code, there is no need to update `ConfigureServices`, because logging is provided by the framework.</span></span>

## <a name="register-groups-of-services-with-extension-methods"></a><span data-ttu-id="cc664-152">Uzantı yöntemleriyle hizmet gruplarını kaydet</span><span class="sxs-lookup"><span data-stu-id="cc664-152">Register groups of services with extension methods</span></span>

<span data-ttu-id="cc664-153">Microsoft uzantıları, bir grup ilgili hizmeti kaydetmek için bir kural kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc664-153">Microsoft Extensions uses a convention for registering a group of related services.</span></span> <span data-ttu-id="cc664-154">Kural, `Add{GROUP_NAME}` bir Framework özelliği için gereken tüm hizmetleri kaydetmek için tek bir genişletme yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="cc664-154">The convention is to use a single `Add{GROUP_NAME}` extension method to register all of the services required by a framework feature.</span></span> <span data-ttu-id="cc664-155">Örneğin, <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> genişletme yöntemi, seçenekleri kullanmak için gereken tüm hizmetleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cc664-155">For example, the <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> extension method registers all of the services required for using options.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="cc664-156">Framework tarafından sunulan hizmetler</span><span class="sxs-lookup"><span data-stu-id="cc664-156">Framework-provided services</span></span>

<span data-ttu-id="cc664-157">`ConfigureServices`Yöntemi, platform özellikleri dahil olmak üzere uygulamanın kullandığı hizmetleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cc664-157">The `ConfigureServices` method registers services that the app uses, including platform features.</span></span> <span data-ttu-id="cc664-158">Başlangıçta, `IServiceCollection` için belirtilen, `ConfigureServices` [konağın nasıl yapılandırıldığına](generic-host.md#host-configuration)bağlı olarak Framework tarafından tanımlanan hizmetlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cc664-158">Initially, the `IServiceCollection` provided to `ConfigureServices` has services defined by the framework depending on [how the host was configured](generic-host.md#host-configuration).</span></span> <span data-ttu-id="cc664-159">.NET şablonlarına dayalı uygulamalar için Framework yüzlerce hizmeti kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cc664-159">For apps based on the .NET templates, the framework registers hundreds of services.</span></span>

<span data-ttu-id="cc664-160">Aşağıdaki tabloda, bu çerçeve kayıtlı hizmetlerinin küçük bir örneği listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="cc664-160">The following table lists a small sample of these framework-registered services:</span></span>

| <span data-ttu-id="cc664-161">Hizmet Türü</span><span class="sxs-lookup"><span data-stu-id="cc664-161">Service Type</span></span>                                                                       | <span data-ttu-id="cc664-162">Ömür</span><span class="sxs-lookup"><span data-stu-id="cc664-162">Lifetime</span></span>  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | <span data-ttu-id="cc664-163">Adet</span><span class="sxs-lookup"><span data-stu-id="cc664-163">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | <span data-ttu-id="cc664-164">Adet</span><span class="sxs-lookup"><span data-stu-id="cc664-164">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | <span data-ttu-id="cc664-165">Adet</span><span class="sxs-lookup"><span data-stu-id="cc664-165">Singleton</span></span> |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | <span data-ttu-id="cc664-166">Adet</span><span class="sxs-lookup"><span data-stu-id="cc664-166">Singleton</span></span> |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | <span data-ttu-id="cc664-167">Larsa</span><span class="sxs-lookup"><span data-stu-id="cc664-167">Transient</span></span> |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | <span data-ttu-id="cc664-168">Adet</span><span class="sxs-lookup"><span data-stu-id="cc664-168">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | <span data-ttu-id="cc664-169">Adet</span><span class="sxs-lookup"><span data-stu-id="cc664-169">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | <span data-ttu-id="cc664-170">Adet</span><span class="sxs-lookup"><span data-stu-id="cc664-170">Singleton</span></span> |

## <a name="service-lifetimes"></a><span data-ttu-id="cc664-171">Hizmet yaşam süreleri</span><span class="sxs-lookup"><span data-stu-id="cc664-171">Service lifetimes</span></span>

<span data-ttu-id="cc664-172">Hizmetler aşağıdaki yaşam sürelerinin biriyle kaydedilebilir:</span><span class="sxs-lookup"><span data-stu-id="cc664-172">Services can be registered with one of the following lifetimes:</span></span>

- <span data-ttu-id="cc664-173">Larsa</span><span class="sxs-lookup"><span data-stu-id="cc664-173">Transient</span></span>
- <span data-ttu-id="cc664-174">Yayıl</span><span class="sxs-lookup"><span data-stu-id="cc664-174">Scoped</span></span>
- <span data-ttu-id="cc664-175">Adet</span><span class="sxs-lookup"><span data-stu-id="cc664-175">Singleton</span></span>

<span data-ttu-id="cc664-176">Aşağıdaki bölümlerde, önceki yaşam sürelerinin her biri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="cc664-176">The following sections describe each of the preceding lifetimes.</span></span> <span data-ttu-id="cc664-177">Kayıtlı her hizmet için uygun bir yaşam süresi seçin.</span><span class="sxs-lookup"><span data-stu-id="cc664-177">Choose an appropriate lifetime for each registered service.</span></span>

### <a name="transient"></a><span data-ttu-id="cc664-178">Larsa</span><span class="sxs-lookup"><span data-stu-id="cc664-178">Transient</span></span>

<span data-ttu-id="cc664-179">Geçici ömür Hizmetleri, hizmet kapsayıcısından her istenilişinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cc664-179">Transient lifetime services are created each time they're requested from the service container.</span></span> <span data-ttu-id="cc664-180">Bu ömür, hafif ve durumsuz hizmetler için en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc664-180">This lifetime works best for lightweight, stateless services.</span></span> <span data-ttu-id="cc664-181">Geçici Hizmetleri ile kaydedin <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> .</span><span class="sxs-lookup"><span data-stu-id="cc664-181">Register transient services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span></span>

<span data-ttu-id="cc664-182">İstekleri işleyen uygulamalarda, geçici hizmetler isteğin sonuna atıldı.</span><span class="sxs-lookup"><span data-stu-id="cc664-182">In apps that process requests, transient services are disposed at the end of the request.</span></span>

### <a name="scoped"></a><span data-ttu-id="cc664-183">Yayıl</span><span class="sxs-lookup"><span data-stu-id="cc664-183">Scoped</span></span>

<span data-ttu-id="cc664-184">Web uygulamaları için kapsamlı bir yaşam süresi, hizmetlerin istemci isteği başına bir kez oluşturulduğunu belirtir (bağlantı).</span><span class="sxs-lookup"><span data-stu-id="cc664-184">For web applications a scoped lifetime indicates that services are created once per client request (connection).</span></span> <span data-ttu-id="cc664-185">Kapsamlı hizmetleri ile kaydedin <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> .</span><span class="sxs-lookup"><span data-stu-id="cc664-185">Register scoped services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span></span>

<span data-ttu-id="cc664-186">İstekleri işleyen uygulamalarda, kapsamlı hizmetler isteğin sonuna atıldı.</span><span class="sxs-lookup"><span data-stu-id="cc664-186">In apps that process requests, scoped services are disposed at the end of the request.</span></span>

<span data-ttu-id="cc664-187">Entity Framework Core kullanılırken, <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> genişletme yöntemi, `DbContext` Varsayılan olarak kapsamlı yaşam süresine sahip türleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cc664-187">When using Entity Framework Core, the <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> extension method registers `DbContext` types with a scoped lifetime by default.</span></span>

> [!NOTE]
> <span data-ttu-id="cc664-188">Tek bir kapsamdaki hizmeti bir tekil hizmetten çözümleyin ve örneğin geçici bir hizmet aracılığıyla dolaylı olarak değil, bunun gibi bir **şekilde değil.**</span><span class="sxs-lookup"><span data-stu-id="cc664-188">Do \* **not** _ resolve a scoped service from a singleton and be careful not to do so indirectly, for example, through a transient service.</span></span> <span data-ttu-id="cc664-189">Bu, sonraki istekleri işlerken hizmetin yanlış duruma gelmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc664-189">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="cc664-190">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cc664-190">It's fine to:</span></span>
>
> - <span data-ttu-id="cc664-191">Tek bir hizmeti kapsamlı veya geçici bir hizmetten çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="cc664-191">Resolve a singleton service from a scoped or transient service.</span></span>
> - <span data-ttu-id="cc664-192">Kapsamlı bir hizmeti başka bir kapsamlı veya geçici hizmetten çözün.</span><span class="sxs-lookup"><span data-stu-id="cc664-192">Resolve a scoped service from another scoped or transient service.</span></span>

<span data-ttu-id="cc664-193">Varsayılan olarak, geliştirme ortamında, bir hizmetin daha uzun bir yaşam süresine sahip başka bir hizmetten çözülmesi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc664-193">By default, in the development environment, resolving a service from another service with a longer lifetime throws an exception.</span></span> <span data-ttu-id="cc664-194">Daha fazla bilgi için bkz. [kapsam doğrulaması](#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="cc664-194">For more information, see [Scope validation](#scope-validation).</span></span>

### <a name="singleton"></a><span data-ttu-id="cc664-195">Adet</span><span class="sxs-lookup"><span data-stu-id="cc664-195">Singleton</span></span>

<span data-ttu-id="cc664-196">Tek yaşam süresi Hizmetleri şu şekilde oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="cc664-196">Singleton lifetime services are created either:</span></span>

- <span data-ttu-id="cc664-197">İlk kez istenirler.</span><span class="sxs-lookup"><span data-stu-id="cc664-197">The first time they're requested.</span></span>
- <span data-ttu-id="cc664-198">Geliştirici tarafından doğrudan kapsayıcıya bir uygulama örneği sağlarken.</span><span class="sxs-lookup"><span data-stu-id="cc664-198">By the developer, when providing an implementation instance directly to the container.</span></span> <span data-ttu-id="cc664-199">Bu yaklaşım nadiren gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cc664-199">This approach is rarely needed.</span></span>

<span data-ttu-id="cc664-200">Bağımlılık ekleme kapsayıcısından gelen hizmet uygulamasının sonraki tüm istekleri aynı örneği kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc664-200">Every subsequent request of the service implementation from the dependency injection container uses the same instance.</span></span> <span data-ttu-id="cc664-201">Uygulama tek davranış gerektiriyorsa, hizmet kapsayıcısının hizmetin ömrünü yönetmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="cc664-201">If the app requires singleton behavior, allow the service container to manage the service's lifetime.</span></span> <span data-ttu-id="cc664-202">Tek tasarım modelini uygulamayın ve tek bir atma kodu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="cc664-202">Don't implement the singleton design pattern and provide code to dispose of the singleton.</span></span> <span data-ttu-id="cc664-203">Hizmetler, kapsayıcıyı hizmetten çözümleyen kodla hiçbir şekilde atılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cc664-203">Services should never be disposed by code that resolved the service from the container.</span></span> <span data-ttu-id="cc664-204">Bir tür veya fabrika tek bir olarak kayıtlıysa, kapsayıcı kendiliğinden otomatik olarak atar.</span><span class="sxs-lookup"><span data-stu-id="cc664-204">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="cc664-205">İle Singleton hizmetlerini kaydettirin <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> .</span><span class="sxs-lookup"><span data-stu-id="cc664-205">Register singleton services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span></span> <span data-ttu-id="cc664-206">Tek hizmetler iş parçacığı güvenli olmalıdır ve genellikle durum bilgisiz hizmetlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc664-206">Singleton services must be thread safe and are often used in stateless services.</span></span>

<span data-ttu-id="cc664-207">İstekleri işleyen uygulamalarda, uygulama kapatılırken bırakıldığında tek hizmetler silinir <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="cc664-207">In apps that process requests, singleton services are disposed when the <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> is disposed on application shutdown.</span></span> <span data-ttu-id="cc664-208">Uygulama kapatılıncaya kadar bellek yayımlanmadığı için, tek bir hizmetle bellek kullanımını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="cc664-208">Because memory is not released until the app is shut down, consider memory use with a singleton service.</span></span>

> [!WARNING]
> <span data-ttu-id="cc664-209">Kapsamlı bir hizmeti tek bir _*_sunucudan çözümleyin._*_</span><span class="sxs-lookup"><span data-stu-id="cc664-209">Do _*_not_*_ resolve a scoped service from a singleton.</span></span> <span data-ttu-id="cc664-210">Bu, sonraki istekleri işlerken hizmetin yanlış duruma gelmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc664-210">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="cc664-211">Tek bir hizmeti kapsamlı veya geçici bir hizmetten çözümlemek çok iyidir.</span><span class="sxs-lookup"><span data-stu-id="cc664-211">It's fine to resolve a singleton service from a scoped or transient service.</span></span>

## <a name="service-registration-methods"></a><span data-ttu-id="cc664-212">Hizmet kayıt yöntemleri</span><span class="sxs-lookup"><span data-stu-id="cc664-212">Service registration methods</span></span>

<span data-ttu-id="cc664-213">Framework, belirli senaryolarda yararlı olan hizmet kayıt uzantısı yöntemleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="cc664-213">The framework provides service registration extension methods that are useful in specific scenarios:</span></span>

| <span data-ttu-id="cc664-214">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cc664-214">Method</span></span> | <span data-ttu-id="cc664-215">Automatic</span><span class="sxs-lookup"><span data-stu-id="cc664-215">Automatic</span></span><br><span data-ttu-id="cc664-216">object</span><span class="sxs-lookup"><span data-stu-id="cc664-216">object</span></span><br><span data-ttu-id="cc664-217">elden</span><span class="sxs-lookup"><span data-stu-id="cc664-217">disposal</span></span> | <span data-ttu-id="cc664-218">Birden çok</span><span class="sxs-lookup"><span data-stu-id="cc664-218">Multiple</span></span><br><span data-ttu-id="cc664-219">uygulamalar</span><span class="sxs-lookup"><span data-stu-id="cc664-219">implementations</span></span> | <span data-ttu-id="cc664-220">Geçiş bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cc664-220">Pass args</span></span> |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br><span data-ttu-id="cc664-221">Örnek:</span><span class="sxs-lookup"><span data-stu-id="cc664-221">Example:</span></span><br><br>`services.AddSingleton<IMyDep, MyDep>();` | <span data-ttu-id="cc664-222">Yes</span><span class="sxs-lookup"><span data-stu-id="cc664-222">Yes</span></span> | <span data-ttu-id="cc664-223">Yes</span><span class="sxs-lookup"><span data-stu-id="cc664-223">Yes</span></span> | <span data-ttu-id="cc664-224">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc664-224">No</span></span> |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br><span data-ttu-id="cc664-225">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="cc664-225">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | <span data-ttu-id="cc664-226">Yes</span><span class="sxs-lookup"><span data-stu-id="cc664-226">Yes</span></span> | <span data-ttu-id="cc664-227">Yes</span><span class="sxs-lookup"><span data-stu-id="cc664-227">Yes</span></span> | <span data-ttu-id="cc664-228">Yes</span><span class="sxs-lookup"><span data-stu-id="cc664-228">Yes</span></span> |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br><span data-ttu-id="cc664-229">Örnek:</span><span class="sxs-lookup"><span data-stu-id="cc664-229">Example:</span></span><br><br>`services.AddSingleton<MyDep>();` | <span data-ttu-id="cc664-230">Yes</span><span class="sxs-lookup"><span data-stu-id="cc664-230">Yes</span></span> | <span data-ttu-id="cc664-231">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc664-231">No</span></span> | <span data-ttu-id="cc664-232">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc664-232">No</span></span> |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br><span data-ttu-id="cc664-233">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="cc664-233">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | <span data-ttu-id="cc664-234">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc664-234">No</span></span> | <span data-ttu-id="cc664-235">Yes</span><span class="sxs-lookup"><span data-stu-id="cc664-235">Yes</span></span> | <span data-ttu-id="cc664-236">Yes</span><span class="sxs-lookup"><span data-stu-id="cc664-236">Yes</span></span> |
| `AddSingleton(new {IMPLEMENTATION})`<br><br><span data-ttu-id="cc664-237">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="cc664-237">Examples:</span></span><br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | <span data-ttu-id="cc664-238">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc664-238">No</span></span> | <span data-ttu-id="cc664-239">Hayır</span><span class="sxs-lookup"><span data-stu-id="cc664-239">No</span></span> | <span data-ttu-id="cc664-240">Yes</span><span class="sxs-lookup"><span data-stu-id="cc664-240">Yes</span></span> |

<span data-ttu-id="cc664-241">Tür çıkarma hakkında daha fazla bilgi için [Hizmetler 'In aktiften çıkarılması](dependency-injection-guidelines.md#disposal-of-services) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cc664-241">For more information on type disposal, see the [Disposal of services](dependency-injection-guidelines.md#disposal-of-services) section.</span></span>

<span data-ttu-id="cc664-242">Hizmeti yalnızca bir uygulama türüyle kaydetmek, bu hizmeti aynı uygulama ve hizmet türüyle kaydetmeye eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cc664-242">Registering a service with only an implementation type is equivalent to registering that service with the same implementation and service type.</span></span> <span data-ttu-id="cc664-243">Bu, bir hizmetin birden çok uygulamasının açık bir hizmet türü kullanmayan yöntemler kullanılarak kaydedilamamasının nedenleridir.</span><span class="sxs-lookup"><span data-stu-id="cc664-243">This is why multiple implementations of a service cannot be registered using the methods that don't take an explicit service type.</span></span> <span data-ttu-id="cc664-244">Bu yöntemler bir hizmetin birden çok _instances \* kaydını yapabilir, ancak hepsi aynı *uygulama* türüne sahip olur.</span><span class="sxs-lookup"><span data-stu-id="cc664-244">These methods can register multiple _instances\* of a service, but they will all have the same *implementation* type.</span></span>

<span data-ttu-id="cc664-245">Yukarıdaki hizmet kayıt yöntemlerinden herhangi biri aynı hizmet türünün birden çok hizmet örneğini kaydetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc664-245">Any of the above service registration methods can be used to register multiple service instances of the same service type.</span></span> <span data-ttu-id="cc664-246">Aşağıdaki örnekte, `AddSingleton` hizmet türü olarak ile iki kez çağırılır `IMessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="cc664-246">In the following example, `AddSingleton` is called twice with `IMessageWriter` as the service type.</span></span> <span data-ttu-id="cc664-247">İçin ikinci çağrı, `AddSingleton` olarak çözümlendikten önceki bir öncekini geçersiz kılar `IMessageWriter` ve aracılığıyla birden çok hizmet çözümlendiğinde bir öncekini ekler `IEnumerable<IMessageWriter>` .</span><span class="sxs-lookup"><span data-stu-id="cc664-247">The second call to `AddSingleton` overrides the previous one when resolved as `IMessageWriter` and adds to the previous one when multiple services are resolved via `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="cc664-248">Hizmetler, ile çözümlendiklerinde kaydedildikleri sırada görüntülenir `IEnumerable<{SERVICE}>` .</span><span class="sxs-lookup"><span data-stu-id="cc664-248">Services appear in the order they were registered when resolved via `IEnumerable<{SERVICE}>`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/Program.cs" highlight="19-24":::

<span data-ttu-id="cc664-249">Önceki örnek kaynak kodu, öğesinin iki uygulamalarını kaydeder `IMessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="cc664-249">The preceding sample source code registers two implementations of the `IMessageWriter`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/ExampleService.cs" highlight="9-18":::

<span data-ttu-id="cc664-250">`ExampleService`İki Oluşturucu parametresini tanımlar; tek bir `IMessageWriter` ve bir `IEnumerable<IMessageWriter>` .</span><span class="sxs-lookup"><span data-stu-id="cc664-250">The `ExampleService` defines two constructor parameters; a single `IMessageWriter`, and an `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="cc664-251">Tek `IMessageWriter` şey kayıtlı olan en son uygudır, ancak `IEnumerable<IMessageWriter>` Tüm kayıtlı uygulamaları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc664-251">The single `IMessageWriter` is the last implemenation to have been registered, whereas the `IEnumerable<IMessageWriter>` represents all registered implementations.</span></span>

<span data-ttu-id="cc664-252">Framework Ayrıca, `TryAdd{LIFETIME}` yalnızca kayıtlı bir uygulama olmadığında hizmeti kaydeden genişletme yöntemleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc664-252">The framework also provides `TryAdd{LIFETIME}` extension methods, which register the service only if there isn't already an implementation registered.</span></span>

<span data-ttu-id="cc664-253">Aşağıdaki örnekte, `AddSingleton` `ConsoleMessageWriter` için bir uygulama olarak Yazmaçları çağrısı `IMessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="cc664-253">In the following example, the call to `AddSingleton` registers `ConsoleMessageWriter` as an implementation for `IMessageWriter`.</span></span> <span data-ttu-id="cc664-254">`TryAddSingleton` `IMessageWriter` Zaten kayıtlı bir uygulamaya sahip olduğundan, çağrısının bir etkisi yoktur:</span><span class="sxs-lookup"><span data-stu-id="cc664-254">The call to `TryAddSingleton` has no effect because `IMessageWriter` already has a registered implementation:</span></span>

```csharp
services.AddSingleton<IMessageWriter, ConsoleMessageWriter>();
services.TryAddSingleton<IMessageWriter, LoggingMessageWriter>();
```

<span data-ttu-id="cc664-255">`TryAddSingleton`Zaten eklendiği için hiçbir etkisi yoktur ve "TRY" başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="cc664-255">The `TryAddSingleton` has no effect, as it was already added and the "try" will fail.</span></span> <span data-ttu-id="cc664-256">Aşağıdaki işlemi yapılır `ExampleService` :</span><span class="sxs-lookup"><span data-stu-id="cc664-256">The `ExampleService` would assert the following:</span></span>

```csharp
public class ExampleService
{
    public ExampleService(
        IMessageWriter messageWriter,
        IEnumerable<IMessageWriter> messageWriters)
    {
        Trace.Assert(messageWriter is ConsoleMessageWriter);
        Trace.Assert(messageWriters.Single() is ConsoleMessageWriter);
    }
}
```

<span data-ttu-id="cc664-257">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="cc664-257">For more information, see:</span></span>

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

<span data-ttu-id="cc664-258">[TryAddEnumerable (ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) yöntemleri, yalnızca *aynı türde* bir uygulama olmadığında hizmeti kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cc664-258">The [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) methods register the service only if there isn't already an implementation *of the same type* .</span></span> <span data-ttu-id="cc664-259">Aracılığıyla birden çok hizmet çözümlenir `IEnumerable<{SERVICE}>` .</span><span class="sxs-lookup"><span data-stu-id="cc664-259">Multiple services are resolved via `IEnumerable<{SERVICE}>`.</span></span> <span data-ttu-id="cc664-260">Hizmetleri kaydederken, aynı türden biri zaten eklenmediyse bir örnek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc664-260">When registering services, add an instance if one of the same types hasn't already been added.</span></span> <span data-ttu-id="cc664-261">Kitaplık yazarları `TryAddEnumerable` , kapsayıcıda bir uygulamanın birden çok kopyasını kaydetmemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc664-261">Library authors use `TryAddEnumerable` to avoid registering multiple copies of an implementation in the container.</span></span>

<span data-ttu-id="cc664-262">Aşağıdaki örnekte, `TryAddEnumerable` `MessageWriter` için bir uygulama olarak kaydeden ilk çağrı `IMessageWriter1` .</span><span class="sxs-lookup"><span data-stu-id="cc664-262">In the following example, the first call to `TryAddEnumerable` registers `MessageWriter` as an implementation for `IMessageWriter1`.</span></span> <span data-ttu-id="cc664-263">İçin ikinci çağrı kaydettirir `MessageWriter` `IMessageWriter2` .</span><span class="sxs-lookup"><span data-stu-id="cc664-263">The second call registers `MessageWriter` for `IMessageWriter2`.</span></span> <span data-ttu-id="cc664-264">`IMessageWriter1`Zaten kayıtlı bir uygulamasına sahip olduğundan, üçüncü çağrının etkisi yoktur `MessageWriter` :</span><span class="sxs-lookup"><span data-stu-id="cc664-264">The third call has no effect because `IMessageWriter1` already has a registered implementation of `MessageWriter`:</span></span>

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

<span data-ttu-id="cc664-265">Hizmet kaydı, aynı türde birden çok uygulama kaydedilirken genellikle sıralı olarak bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="cc664-265">Service registration is generally order independent except when registering multiple implementations of the same type.</span></span>

<span data-ttu-id="cc664-266">`IServiceCollection` bir <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> nesne koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="cc664-266">`IServiceCollection` is a collection of <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objects.</span></span> <span data-ttu-id="cc664-267">Aşağıdaki örnek, oluşturma ve ekleme yoluyla bir hizmetin nasıl kaydedileceği gösterilmektedir `ServiceDescriptor` :</span><span class="sxs-lookup"><span data-stu-id="cc664-267">The following example shows how to register a service by creating and adding a `ServiceDescriptor`:</span></span>

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

<span data-ttu-id="cc664-268">Yerleşik `Add{LIFETIME}` Yöntemler aynı yaklaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc664-268">The built-in `Add{LIFETIME}` methods use the same approach.</span></span> <span data-ttu-id="cc664-269">Örneğin, bkz. [Addkapsamlıdır kaynak kodu](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span><span class="sxs-lookup"><span data-stu-id="cc664-269">For example, see the [AddScoped source code](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span></span>

### <a name="constructor-injection-behavior"></a><span data-ttu-id="cc664-270">Oluşturucu Ekleme davranışı</span><span class="sxs-lookup"><span data-stu-id="cc664-270">Constructor injection behavior</span></span>

<span data-ttu-id="cc664-271">Hizmetler, kullanılarak çözülebilir:</span><span class="sxs-lookup"><span data-stu-id="cc664-271">Services can be resolved by using:</span></span>

- <xref:System.IServiceProvider>
- <span data-ttu-id="cc664-272"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span><span class="sxs-lookup"><span data-stu-id="cc664-272"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span></span>
  - <span data-ttu-id="cc664-273">Kapsayıcıda kayıtlı olmayan nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc664-273">Creates objects that aren't registered in the container.</span></span>
  - <span data-ttu-id="cc664-274">Bazı Framework özellikleriyle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc664-274">Used with some framework features.</span></span>

<span data-ttu-id="cc664-275">Oluşturucular bağımlılık ekleme tarafından sağlanmayan bağımsız değişkenleri kabul edebilir, ancak bağımsız değişkenlerin varsayılan değerleri ataması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc664-275">Constructors can accept arguments that aren't provided by dependency injection, but the arguments must assign default values.</span></span>

<span data-ttu-id="cc664-276">Hizmetler veya tarafından çözümlendiğinde `IServiceProvider` `ActivatorUtilities` , Oluşturucu Ekleme *ortak* bir Oluşturucu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cc664-276">When services are resolved by `IServiceProvider` or `ActivatorUtilities`, constructor injection requires a *public* constructor.</span></span>

<span data-ttu-id="cc664-277">Hizmetler tarafından çözümlendiğinde `ActivatorUtilities` , Oluşturucu ekleme yalnızca bir adet geçerli oluşturucunun var olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cc664-277">When services are resolved by `ActivatorUtilities`, constructor injection requires that only one applicable constructor exists.</span></span> <span data-ttu-id="cc664-278">Oluşturucu aşırı yüklemeleri desteklenir, ancak bağımsız değişkenleri bağımlılık ekleme tarafından yerine yalnızca bir aşırı yükleme bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="cc664-278">Constructor overloads are supported, but only one overload can exist whose arguments can all be fulfilled by dependency injection.</span></span>

## <a name="scope-validation"></a><span data-ttu-id="cc664-279">Kapsam doğrulaması</span><span class="sxs-lookup"><span data-stu-id="cc664-279">Scope validation</span></span>

<span data-ttu-id="cc664-280">Uygulama `Development` ortamda çalışır ve konağı oluşturmak Için [Createdefaultbuilder](generic-host.md#default-builder-settings) ' ı çağırırsa, varsayılan hizmet sağlayıcısı şunları doğrulamak için denetimler gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="cc664-280">When the app runs in the `Development` environment and calls [CreateDefaultBuilder](generic-host.md#default-builder-settings) to build the host, the default service provider performs checks to verify that:</span></span>

- <span data-ttu-id="cc664-281">Kapsamlı hizmetler kök hizmet sağlayıcısından çözümlenmez.</span><span class="sxs-lookup"><span data-stu-id="cc664-281">Scoped services aren't resolved from the root service provider.</span></span>
- <span data-ttu-id="cc664-282">Kapsamlı hizmetler tekton 'a eklenmiş değildir.</span><span class="sxs-lookup"><span data-stu-id="cc664-282">Scoped services aren't injected into singletons.</span></span>

<span data-ttu-id="cc664-283">Kök hizmet sağlayıcısı <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> çağrıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cc664-283">The root service provider is created when <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> is called.</span></span> <span data-ttu-id="cc664-284">Kök hizmet sağlayıcısının ömrü, sağlayıcının uygulamayla başladığı ve uygulama kapandığında bırakıldığı uygulamanın ömrüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="cc664-284">The root service provider's lifetime corresponds to the app's lifetime when the provider starts with the app and is disposed when the app shuts down.</span></span>

<span data-ttu-id="cc664-285">Kapsamlı hizmetler kendilerini oluşturan kapsayıcı tarafından atılmış.</span><span class="sxs-lookup"><span data-stu-id="cc664-285">Scoped services are disposed by the container that created them.</span></span> <span data-ttu-id="cc664-286">Kök kapsayıcıda kapsamlı bir hizmet oluşturulduysa, hizmetin ömrü, uygulama kapandığında yalnızca kök kapsayıcı tarafından atıldığı için etkin bir şekilde tek bir yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="cc664-286">If a scoped service is created in the root container, the service's lifetime is effectively promoted to singleton because it's only disposed by the root container when the app shuts down.</span></span> <span data-ttu-id="cc664-287">Hizmet kapsamlarını doğrulamak, çağrıldığında bu durumları yakalar `BuildServiceProvider` .</span><span class="sxs-lookup"><span data-stu-id="cc664-287">Validating service scopes catches these situations when `BuildServiceProvider` is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc664-288">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc664-288">See also</span></span>

- [<span data-ttu-id="cc664-289">.NET ' te bağımlılık ekleme 'yi kullanma</span><span class="sxs-lookup"><span data-stu-id="cc664-289">Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
- [<span data-ttu-id="cc664-290">Bağımlılık ekleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="cc664-290">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
- [<span data-ttu-id="cc664-291">ASP.NET Core bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="cc664-291">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
- [<span data-ttu-id="cc664-292">Dı uygulaması geliştirme için NDC Konferansı desenleri</span><span class="sxs-lookup"><span data-stu-id="cc664-292">NDC Conference Patterns for DI app development</span></span>](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [<span data-ttu-id="cc664-293">Açık bağımlılıklar ilkesi</span><span class="sxs-lookup"><span data-stu-id="cc664-293">Explicit dependencies principle</span></span>](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [<span data-ttu-id="cc664-294">Denetim kapsayıcıları ve bağımlılık ekleme deseninin Inversion 'ı (Marwler)</span><span class="sxs-lookup"><span data-stu-id="cc664-294">Inversion of control containers and the dependency injection pattern (Martin Fowler)</span></span>](https://www.martinfowler.com/articles/injection.html)
- <span data-ttu-id="cc664-295">[GitHub.com/DotNet/Extensions](https://github.com/dotnet/extensions/issues) deposu 'nda dı hataları oluşturulmalıdır</span><span class="sxs-lookup"><span data-stu-id="cc664-295">DI bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
