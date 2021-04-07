---
title: .NET 'e bağımlılık ekleme
description: .NET 'in bağımlılık ekleme ve nasıl kullanılacağı hakkında bilgi edinin.
author: IEvangelist
ms.author: dapine
ms.date: 10/28/2020
ms.topic: overview
ms.openlocfilehash: 0b5526f24f3ac658123acd030c3adf32c346422a
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079524"
---
# <a name="dependency-injection-in-net"></a>.NET 'e bağımlılık ekleme

.NET bağımlılık ekleme (dı) yazılım tasarımı modelini destekler, bu, sınıflar ve bunların bağımlılıkları arasında [denetimin INVERSION (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) elde etmek için bir tekniktir. .NET ' te bağımlılık ekleme, yapılandırma, günlük oluşturma ve seçenekler düzeniyle birlikte [birinci sınıf bir vatandaşlık](https://en.wikipedia.org/wiki/First-class_citizen).

*Bağımlılık* , başka bir nesnenin bağımlı olduğu bir nesnedir. Aşağıdaki sınıfı, `MessageWriter` `Write` diğer sınıfların bağımlı olduğu bir yöntemle inceleyin:

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

Bir sınıf, `MessageWriter` yöntemini kullanmak için sınıfının bir örneğini oluşturabilir `Write` . Aşağıdaki örnekte, `MessageWriter` sınıfı sınıfının bir bağımlılığı olur `Worker` :

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

Sınıfı oluşturur ve doğrudan `MessageWriter` sınıfa bağlıdır. Önceki örnekte olduğu gibi sabit kodlu bağımlılıklar sorunlu olur ve aşağıdaki nedenlerden dolayı kaçınılması gerekir:

- `MessageWriter`Farklı bir uygulamayla değiştirmek için, `Worker` sınıfın değiştirilmesi gerekir.
- `MessageWriter`Bağımlılıkları varsa, sınıf tarafından da yapılandırılmalıdır `Worker` . Uygulamasına bağlı olarak, birden çok sınıfı olan büyük bir projede `MessageWriter` yapılandırma kodu uygulama genelinde dağılmış hale gelir.
- Bu uygulamanın birim testi zordur. Uygulamanın `MessageWriter` Bu yaklaşım ile mümkün olmayan bir sahte veya saplama sınıfı kullanması gerekir.

Bağımlılık ekleme bu sorunları şu şekilde giderir:

- Bağımlılık uygulamasını soyutlamak için bir arabirim veya temel sınıf kullanımı.
- Bir hizmet kapsayıcısına bağımlılığın kaydı. .NET, yerleşik bir hizmet kapsayıcısı sağlar <xref:System.IServiceProvider> . Hizmetler genellikle uygulamanın başlangıcında kaydedilir ve bir öğesine eklenir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> . Tüm hizmetler eklendikten sonra, <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> hizmet kapsayıcısını oluşturmak için kullanırsınız.
- Hizmetin kullanıldığı sınıf oluşturucusuna *ekleme* . Çerçeve, bağımlılığın bir örneğini oluşturma ve artık gerekli olmadığında bu uygulamayı atma sorumluluğunu alır.

Örnek olarak, `IMessageWriter` arabirim `Write` yöntemini tanımlar:

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

Bu arabirim somut bir tür tarafından uygulanır, `MessageWriter` :

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

Örnek kod, `IMessageWriter` hizmeti somut tür ile kaydeder `MessageWriter` . <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>Yöntemi, hizmeti tek bir isteğin ömrü olan kapsamlı bir yaşam süresine kaydeder. [Hizmet yaşam süreleri](#service-lifetimes) Bu makalenin ilerleyen kısımlarında açıklanmıştır.

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

Örnek uygulamada, `IMessageWriter` hizmet istenir ve yöntemi çağırmak için kullanılır `Write` :

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

Dı modelini kullanarak çalışan hizmeti:

- Somut türü kullanmaz `MessageWriter` , yalnızca `IMessageWriter` onu uygulayan arabirim. Bu, denetleyicinin, denetleyiciyi değiştirmeden kullandığı uygulamayı değiştirmeyi kolaylaştırır.
- Bir örneği oluşturmaz `MessageWriter` , bu, dı kapsayıcısı tarafından oluşturulur.

Arabirim uygulanması, `IMessageWriter` yerleşik günlük API 'si kullanılarak artırılabilir:

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

Updated `ConfigureServices` yöntemi yeni `IMessageWriter` uygulamayı kaydeder:

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

`LoggingMessageWriter`<xref:Microsoft.Extensions.Logging.ILogger%601>, oluşturucuda istediği öğesine bağlıdır. `ILogger<TCategoryName>`[Framework tarafından sağlanmış bir hizmettir](#framework-provided-services).

Bağımlılık ekleme işlemini zincirleme bir biçimde kullanmak olağan dışı değildir. Her istenen bağımlılık, kendi bağımlılıklarını ister. Kapsayıcı grafikteki bağımlılıkları çözer ve tamamen çözümlenen hizmeti döndürür. Çözümlenmesi gereken, genellikle *bağımlılık ağacı*, *bağımlılık grafiği* veya *nesne grafiği* olarak adlandırılan toplu bağımlılıklar kümesi.

Kapsayıcı, `ILogger<TCategoryName>` [(genel) açık türlerden](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types)yararlanarak çözümlenir, her [(genel) oluşturulan türü](/dotnet/csharp/language-reference/language-specification/types#constructed-types)kaydetme ihtiyacını ortadan kaldırır.

Bağımlılık ekleme terminolojisi ' nde bir hizmet:

- Genellikle hizmet gibi diğer nesnelere hizmet sağlayan bir nesnedir `IMessageWriter` .
- Bir Web hizmetiyle ilgili değildir, ancak hizmet bir Web hizmeti kullanabilir.

Çerçeve, güçlü bir günlük sistemi sağlar. `IMessageWriter`Yukarıdaki örneklerde gösterilen uygulamalar, günlüğü uygulamamak için değil temel dı 'yi göstermek için yazılmıştır. Çoğu uygulamanın Günlükçüler yazması gerekmez. Aşağıdaki kod, yalnızca `Worker` ' ın `ConfigureServices` barındırılan bir hizmet olarak kaydedilmesini gerektiren varsayılan günlük kaydını kullanmayı göstermektedir <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> :

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

Yukarıdaki kodu kullanarak, `ConfigureServices` Framework tarafından günlüğe kaydetme sağlandığı için güncelleştirmeniz gerekmez.

## <a name="register-groups-of-services-with-extension-methods"></a>Uzantı yöntemleriyle hizmet gruplarını kaydet

Microsoft uzantıları, bir grup ilgili hizmeti kaydetmek için bir kural kullanır. Kural, `Add{GROUP_NAME}` bir Framework özelliği için gereken tüm hizmetleri kaydetmek için tek bir genişletme yöntemi kullanmaktır. Örneğin, <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> genişletme yöntemi, seçenekleri kullanmak için gereken tüm hizmetleri kaydeder.

## <a name="framework-provided-services"></a>Framework tarafından sunulan hizmetler

`ConfigureServices`Yöntemi, platform özellikleri dahil olmak üzere uygulamanın kullandığı hizmetleri kaydeder. Başlangıçta, `IServiceCollection` için belirtilen, `ConfigureServices` [konağın nasıl yapılandırıldığına](generic-host.md#host-configuration)bağlı olarak Framework tarafından tanımlanan hizmetlere sahiptir. .NET şablonlarına dayalı uygulamalar için Framework yüzlerce hizmeti kaydeder.

Aşağıdaki tabloda, bu çerçeve kayıtlı hizmetlerinin küçük bir örneği listelenmektedir:

| Hizmet Türü                                                                       | Ömür  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | Adet |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | Adet |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | Adet |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | Adet |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | Larsa |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | Adet |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | Adet |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | Adet |

## <a name="service-lifetimes"></a>Hizmet yaşam süreleri

Hizmetler aşağıdaki yaşam sürelerinin biriyle kaydedilebilir:

- Larsa
- Yayıl
- Adet

Aşağıdaki bölümlerde, önceki yaşam sürelerinin her biri açıklanır. Kayıtlı her hizmet için uygun bir yaşam süresi seçin.

### <a name="transient"></a>Larsa

Geçici ömür Hizmetleri, hizmet kapsayıcısından her istenilişinde oluşturulur. Bu ömür, hafif ve durumsuz hizmetler için en iyi şekilde kullanılır. Geçici Hizmetleri ile kaydedin <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> .

İstekleri işleyen uygulamalarda, geçici hizmetler isteğin sonuna atıldı.

### <a name="scoped"></a>Yayıl

Web uygulamaları için kapsamlı bir yaşam süresi, hizmetlerin istemci isteği başına bir kez oluşturulduğunu belirtir (bağlantı). Kapsamlı hizmetleri ile kaydedin <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> .

İstekleri işleyen uygulamalarda, kapsamlı hizmetler isteğin sonuna atıldı.

Entity Framework Core kullanılırken, <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> genişletme yöntemi, `DbContext` Varsayılan olarak kapsamlı yaşam süresine sahip türleri kaydeder.

> [!NOTE]
> Kapsamlı bir hizmeti tek bir ***hizmetten çözmeyin*** ve örneğin geçici bir hizmet aracılığıyla dolaylı olarak geçmemeye dikkat edin. Bu, sonraki istekleri işlerken hizmetin yanlış duruma gelmesine neden olabilir. Şunları yapabilirsiniz:
>
> - Tek bir hizmeti kapsamlı veya geçici bir hizmetten çözümleyin.
> - Kapsamlı bir hizmeti başka bir kapsamlı veya geçici hizmetten çözün.

Varsayılan olarak, geliştirme ortamında, bir hizmetin daha uzun bir yaşam süresine sahip başka bir hizmetten çözülmesi bir özel durum oluşturur. Daha fazla bilgi için bkz. [kapsam doğrulaması](#scope-validation).

### <a name="singleton"></a>Adet

Tek yaşam süresi Hizmetleri şu şekilde oluşturulur:

- İlk kez istenirler.
- Geliştirici tarafından doğrudan kapsayıcıya bir uygulama örneği sağlarken. Bu yaklaşım nadiren gereklidir.

Bağımlılık ekleme kapsayıcısından gelen hizmet uygulamasının sonraki tüm istekleri aynı örneği kullanır. Uygulama tek davranış gerektiriyorsa, hizmet kapsayıcısının hizmetin ömrünü yönetmesine izin verin. Tek tasarım modelini uygulamayın ve tek bir atma kodu sağlayın. Hizmetler, kapsayıcıyı hizmetten çözümleyen kodla hiçbir şekilde atılmamalıdır. Bir tür veya fabrika tek bir olarak kayıtlıysa, kapsayıcı kendiliğinden otomatik olarak atar.

İle Singleton hizmetlerini kaydettirin <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> . Tek hizmetler iş parçacığı güvenli olmalıdır ve genellikle durum bilgisiz hizmetlerde kullanılır.

İstekleri işleyen uygulamalarda, uygulama kapatılırken bırakıldığında tek hizmetler silinir <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> . Uygulama kapatılıncaya kadar bellek yayımlanmadığı için, tek bir hizmetle bellek kullanımını göz önünde bulundurun.

## <a name="service-registration-methods"></a>Hizmet kayıt yöntemleri

Framework, belirli senaryolarda yararlı olan hizmet kayıt uzantısı yöntemleri sağlar:

| Yöntem | Automatic<br>object<br>elden | Birden çok<br>uygulamalar | Geçiş bağımsız değişkenleri |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br>Örnek:<br><br>`services.AddSingleton<IMyDep, MyDep>();` | Yes | Yes | Hayır |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br>Örnekler:<br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | Yes | Yes | Yes |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br>Örnek:<br><br>`services.AddSingleton<MyDep>();` | Yes | Hayır | Hayır |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br>Örnekler:<br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | Hayır | Yes | Yes |
| `AddSingleton(new {IMPLEMENTATION})`<br><br>Örnekler:<br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | Hayır | Hayır | Yes |

Tür çıkarma hakkında daha fazla bilgi için [Hizmetler 'In aktiften çıkarılması](dependency-injection-guidelines.md#disposal-of-services) bölümüne bakın.

Hizmeti yalnızca bir uygulama türüyle kaydetmek, bu hizmeti aynı uygulama ve hizmet türüyle kaydetmeye eşdeğerdir. Bu, bir hizmetin birden çok uygulamasının açık bir hizmet türü kullanmayan yöntemler kullanılarak kaydedilamamasının nedenleridir. Bu yöntemler bir hizmetin birden fazla *örneğini* kaydedebilir, ancak hepsi aynı *uygulama* türüne sahip olur.

Yukarıdaki hizmet kayıt yöntemlerinden herhangi biri aynı hizmet türünün birden çok hizmet örneğini kaydetmek için kullanılabilir. Aşağıdaki örnekte, `AddSingleton` hizmet türü olarak ile iki kez çağırılır `IMessageWriter` . İçin ikinci çağrı, `AddSingleton` olarak çözümlendikten önceki bir öncekini geçersiz kılar `IMessageWriter` ve aracılığıyla birden çok hizmet çözümlendiğinde bir öncekini ekler `IEnumerable<IMessageWriter>` . Hizmetler, ile çözümlendiklerinde kaydedildikleri sırada görüntülenir `IEnumerable<{SERVICE}>` .

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/Program.cs" highlight="19-24":::

Önceki örnek kaynak kodu, öğesinin iki uygulamalarını kaydeder `IMessageWriter` .

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/ExampleService.cs" highlight="9-18":::

`ExampleService`İki Oluşturucu parametresini tanımlar; tek bir `IMessageWriter` ve bir `IEnumerable<IMessageWriter>` . Tek, kayıtlı `IMessageWriter` olan en son uygulama, `IEnumerable<IMessageWriter>` Tüm kayıtlı uygulamaları temsil eder.

Framework Ayrıca, `TryAdd{LIFETIME}` yalnızca kayıtlı bir uygulama olmadığında hizmeti kaydeden genişletme yöntemleri de sağlar.

Aşağıdaki örnekte, `AddSingleton` `ConsoleMessageWriter` için bir uygulama olarak Yazmaçları çağrısı `IMessageWriter` . `TryAddSingleton` `IMessageWriter` Zaten kayıtlı bir uygulamaya sahip olduğundan, çağrısının bir etkisi yoktur:

```csharp
services.AddSingleton<IMessageWriter, ConsoleMessageWriter>();
services.TryAddSingleton<IMessageWriter, LoggingMessageWriter>();
```

`TryAddSingleton`Zaten eklendiği için hiçbir etkisi yoktur ve "TRY" başarısız olur. Aşağıdaki işlemi yapılır `ExampleService` :

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

Daha fazla bilgi için bkz.

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

[TryAddEnumerable (ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) yöntemleri, yalnızca *aynı türde* bir uygulama olmadığında hizmeti kaydeder. Aracılığıyla birden çok hizmet çözümlenir `IEnumerable<{SERVICE}>` . Hizmetleri kaydederken, aynı türden biri zaten eklenmediyse bir örnek ekleyin. Kitaplık yazarları `TryAddEnumerable` , kapsayıcıda bir uygulamanın birden çok kopyasını kaydetmemek için kullanır.

Aşağıdaki örnekte, `TryAddEnumerable` `MessageWriter` için bir uygulama olarak kaydeden ilk çağrı `IMessageWriter1` . İçin ikinci çağrı kaydettirir `MessageWriter` `IMessageWriter2` . `IMessageWriter1`Zaten kayıtlı bir uygulamasına sahip olduğundan, üçüncü çağrının etkisi yoktur `MessageWriter` :

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

Hizmet kaydı, aynı türde birden çok uygulama kaydedilirken genellikle sıralı olarak bağımsızdır.

`IServiceCollection` bir <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> nesne koleksiyonudur. Aşağıdaki örnek, oluşturma ve ekleme yoluyla bir hizmetin nasıl kaydedileceği gösterilmektedir `ServiceDescriptor` :

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

Yerleşik `Add{LIFETIME}` Yöntemler aynı yaklaşımı kullanır. Örneğin, bkz. [Addkapsamlıdır kaynak kodu](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).

### <a name="constructor-injection-behavior"></a>Oluşturucu Ekleme davranışı

Hizmetler, kullanılarak çözülebilir:

- <xref:System.IServiceProvider>
- <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:
  - Kapsayıcıda kayıtlı olmayan nesneler oluşturur.
  - Bazı Framework özellikleriyle kullanılır.

Oluşturucular bağımlılık ekleme tarafından sağlanmayan bağımsız değişkenleri kabul edebilir, ancak bağımsız değişkenlerin varsayılan değerleri ataması gerekir.

Hizmetler veya tarafından çözümlendiğinde `IServiceProvider` `ActivatorUtilities` , Oluşturucu Ekleme *ortak* bir Oluşturucu gerektirir.

Hizmetler tarafından çözümlendiğinde `ActivatorUtilities` , Oluşturucu ekleme yalnızca bir adet geçerli oluşturucunun var olmasını gerektirir. Oluşturucu aşırı yüklemeleri desteklenir, ancak bağımsız değişkenleri bağımlılık ekleme tarafından yerine yalnızca bir aşırı yükleme bulunabilir.

## <a name="scope-validation"></a>Kapsam doğrulaması

Uygulama `Development` ortamda çalışır ve konağı oluşturmak Için [Createdefaultbuilder](generic-host.md#default-builder-settings) ' ı çağırırsa, varsayılan hizmet sağlayıcısı şunları doğrulamak için denetimler gerçekleştirir:

- Kapsamlı hizmetler kök hizmet sağlayıcısından çözümlenmez.
- Kapsamlı hizmetler tekton 'a eklenmiş değildir.

Kök hizmet sağlayıcısı <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> çağrıldığında oluşturulur. Kök hizmet sağlayıcısının ömrü, sağlayıcının uygulamayla başladığı ve uygulama kapandığında bırakıldığı uygulamanın ömrüne karşılık gelir.

Kapsamlı hizmetler kendilerini oluşturan kapsayıcı tarafından atılmış. Kök kapsayıcıda kapsamlı bir hizmet oluşturulduysa, hizmetin ömrü, uygulama kapandığında yalnızca kök kapsayıcı tarafından atıldığı için etkin bir şekilde tek bir yükseltilir. Hizmet kapsamlarını doğrulamak, çağrıldığında bu durumları yakalar `BuildServiceProvider` .

## <a name="see-also"></a>Ayrıca bkz.

- [.NET ' te bağımlılık ekleme 'yi kullanma](dependency-injection-usage.md)
- [Bağımlılık ekleme yönergeleri](dependency-injection-guidelines.md)
- [ASP.NET Core bağımlılık ekleme](/aspnet/core/fundamentals/dependency-injection)
- [Dı uygulaması geliştirme için NDC Konferansı desenleri](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [Açık bağımlılıklar ilkesi](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [Denetim kapsayıcıları ve bağımlılık ekleme deseninin Inversion 'ı (Marwler)](https://www.martinfowler.com/articles/injection.html)
- [GitHub.com/DotNet/Extensions](https://github.com/dotnet/extensions/issues) deposu 'nda dı hataları oluşturulmalıdır
