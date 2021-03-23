---
title: ASP.NET Core MVC uygulamaları geliştirme
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın ASP.NET Core MVC uygulamaları geliştirme
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
no-loc:
- Blazor
- WebAssembly
ms.openlocfilehash: 494e73bd32ac6793d355b6828408b61bb09ca880
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873126"
---
# <a name="develop-aspnet-core-mvc-apps"></a>ASP.NET Core MVC uygulamaları geliştirin

> "İlk kez bu hakkı almak önemli değildir. Bu, son kez doğru bir şekilde almak için önemlidir. "
> _-Andrew Hunt ve David Thomas_

ASP.NET Core, bulutta iyileştirilmiş Modern Web uygulamaları oluşturmak için platformlar arası, açık kaynaklı bir çerçevedir. ASP.NET Core uygulamalar basit ve modüler olduğundan, bağımlılık ekleme desteği sayesinde daha fazla test ve bakım olanağı sağlanır. Görüntüleme tabanlı uygulamalara ek olarak Modern Web API 'Leri oluşturmayı destekleyen MVC ile birlikte ASP.NET Core, kurumsal web uygulamaları oluşturmak için kullanabileceğiniz güçlü bir çerçevedir.

## <a name="mvc-and-razor-pages"></a>MVC ve Razor Pages

ASP.NET Core MVC, Web tabanlı API 'Ler ve uygulamalar oluşturmak için yararlı olan birçok özellik sunar. MVC terimi, Kullanıcı isteklerine birkaç parçaya yanıt verme sorumluluklarını kesen bir kullanıcı arabirimi modeli olan "model-görünüm-denetleyicisi" için temsil eder. Bu düzenin yanı sıra, Razor Pages olarak ASP.NET Core uygulamalarında özellikler de uygulayabilirsiniz. Razor Pages, MVC ASP.NET Core yerleşik olarak bulunur ve yönlendirme, model bağlama, filtreler, yetkilendirme vb. için aynı özellikleri kullanır. Bununla birlikte, denetleyiciler, modeller, görünümler, vb. için ayrı klasörler ve dosyalar olması yerine, Razor Pages tek bir klasöre ("/Pages") konur, bu klasördeki göreli konumlarına göre rota ve istekleri denetleyici eylemleri yerine işleyicilerle işleyebilir. Sonuç olarak, Razor Pages ile çalışırken, ihtiyacınız olan tüm dosya ve sınıflar genellikle Web projesi genelinde yayılmaz.

Yeni bir ASP.NET Core uygulaması oluşturduğunuzda, derlemek istediğiniz uygulama türü için bir plana sahip olmanız gerekir. Visual Studio 'da çeşitli şablonlardan seçim yapmanız gerekir. En yaygın üç proje şablonu Web API 'SI, Web uygulaması ve Web uygulaması (Model-View-Controller). Bu kararı yalnızca bir proje oluştururken yapmanız mümkün olsa da, geri alınamaz bir karardır. Web API projesi standart model-görünüm-denetleyici denetleyicileri kullanır; varsayılan olarak yalnızca görünümler eksiktir. Benzer şekilde, varsayılan Web uygulaması şablonu Razor Pages kullanır ve aynı zamanda bir görünümler klasörü eksiktir. Görünüm tabanlı davranışı desteklemek için bu projelere daha sonra bir görünümler klasörü ekleyebilirsiniz. Web API ve model-görünüm-denetleyicisi projeleri varsayılan olarak bir Pages klasörü içermez, ancak daha sonra Razor Pages tabanlı davranışı desteklemek için bir tane ekleyebilirsiniz. Üç farklı türde varsayılan kullanıcı etkileşimini desteklemek için bu üç şablonu düşünebilirsiniz: veri (Web API 'SI), sayfa tabanlı ve görünüm tabanlı. Ancak isterseniz, tek bir proje içinde Bu şablonların herhangi birini veya tümünü karıştırabilir ve eşleştirebilirsiniz.

### <a name="why-razor-pages"></a>Neden Razor Pages?

Razor Pages, Visual Studio 'da yeni Web uygulamaları için varsayılan yaklaşımdır. Razor Pages, SPA olmayan formlar gibi sayfa tabanlı uygulama özelliklerini oluşturmanın daha basit bir yolunu sunar. Denetleyiciler ve görünümleri kullanarak, uygulamaların birçok farklı bağımlılıklarla çalışan çok büyük denetleyicileri olması ve modelleri görüntülemesi ve birçok farklı görünüm döndürdüğünden yaygındır. Bu, daha karmaşıklığa neden olur ve genellikle tek sorumluluk Ilkesini veya açık/kapalı Ilkeleri etkili bir şekilde izleyen denetleyicilerle sonuçlanmıştır. Razor Pages, Razor işaretlemesi ile bir Web uygulamasındaki belirli bir mantıksal "sayfa" için sunucu tarafı mantığını kapsülleyerek bu sorunu giderir. Sunucu tarafı mantığı olmayan bir Razor sayfası yalnızca bir Razor dosyasından (örneğin, "Index. cshtml") yer alabilir. Ancak, önemsiz olmayan Razor Pages ilişkili bir sayfa modeli sınıfına sahip olur. Bu, kurala göre ". cs" uzantısıyla Razor dosyası ile aynı ada sahiptir (örneğin, "Index. cshtml. cs").

Bir Razor sayfasının sayfa modeli, bir MVC denetleyicisinin ve viewmodelinin sorumluluklarını birleştirir. İstekleri denetleyici eylem yöntemleriyle işlemek yerine, "OnGet ()" gibi sayfa modeli işleyicileri, ilişkili sayfaları varsayılan olarak işlenerek yürütülür. Razor Pages, ASP.NET Core MVC 'nin tüm mimari özelliklerini sağlamaya devam ederken, tek tek sayfaları bir ASP.NET Core uygulamasında oluşturma işlemini basitleştirir. Bu, yeni sayfa tabanlı işlevselliği için iyi bir varsayılan seçenektir.

### <a name="when-to-use-mvc"></a>MVC ne zaman kullanılır?

Web API 'Leri oluşturuyorsanız, MVC deseninin Razor Pages kullanmayı deneenden daha anlamlı hale gelir. Projeniz yalnızca Web API uç noktalarını kullanıma sunacaktır, ideal olarak Web API proje şablonundan başlamanız gerekir. Aksi takdirde, denetleyiciler ve ilgili API uç noktalarını herhangi bir ASP.NET Core uygulamasına eklemek kolaydır. Var olan bir uygulamayı ASP.NET MVC 5 veya daha önceki bir sürümden ASP.NET Core MVC 'ye geçiriyorsanız ve en az çaba ile devam etmek istiyorsanız, görünüm tabanlı MVC yaklaşımını kullanın. İlk geçişi yaptıktan sonra, yeni özellikler için Razor Pages benimsemek ve hatta toptan bir geçiş olarak, bunun mantıklı olup olmadığını değerlendirebilirsiniz.

Razor Pages veya MVC görünümlerini kullanarak Web uygulamanızı oluşturmayı tercih etmeksizin, uygulamanız benzer performansa sahip olur ve bağımlılık ekleme, filtreler, model bağlama, doğrulama vb. için destek içerir.

## <a name="mapping-requests-to-responses"></a>İstekleri yanıtlara eşleme

ASP.NET Core uygulamalar gelen istekleri giden yanıtlara eşler. Düşük düzeyde bu eşleme, ara yazılım ile yapılır ve basit ASP.NET Core uygulamalar ve mikro hizmetler yalnızca özel ara yazılım olabilir. ASP.NET Core MVC kullanırken, _yollar_, _denetleyiciler_ ve _Eylemler_ açısından biraz daha yüksek bir düzeyde çalışabilirsiniz. Her gelen istek, uygulamanın yönlendirme tablosuyla karşılaştırılır ve eşleşen bir yol bulunursa, isteği işlemek için ilişkili eylem yöntemi (bir denetleyiciye ait) çağırılır. Eşleşen yol bulunmazsa, bir hata işleyicisi (Bu durumda NotFound sonucu döndüren) çağırılır.

ASP.NET Core MVC uygulamaları geleneksel yollar, öznitelik yolları veya her ikisini kullanabilir. Geleneksel yollar kodda tanımlanmıştır ve aşağıdaki örnekte olduğu gibi sözdizimi kullanılarak yönlendirme _kurallarını_ belirtin:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Bu örnekte, yönlendirme tablosuna "default" adlı bir yol eklenmiştir. , Ve için yer tutucular içeren bir yol şablonu tanımlar `controller` `action` `id` . `controller`Ve yer `action` tutucuları, varsayılan olarak belirtilmiştir ( `Home` ve `Index` sırasıyla) ve `id` yer tutucusu isteğe bağlıdır (bir "?" öğesinin virtuale tarafından). Burada tanımlanan kural, bir isteğin ilk bölümünün denetleyicinin adına, eylemin ikinci bölümüne karşılık gelmesi ve gerekirse üçüncü bir parçanın bir KIMLIK parametresini temsil etmesi gerektiğini belirtir. Geleneksel yollar, genellikle, sınıfındaki yönteminde olduğu gibi, uygulama için bir yerde tanımlanır `Configure` `Startup` .

Öznitelik yolları, genel olarak belirtitense, denetleyicilere ve eylemlere doğrudan uygulanır. Bu yaklaşım, belirli bir yönteme bakarken bu çok daha keşfedilebilir hale getirme avantajına sahiptir, ancak yönlendirme bilgilerinin uygulamada tek bir yerde tutulmadığından emin olur. Öznitelik rotalarıyla, belirli bir eylem için kolayca birden çok yol belirtebilir ve ayrıca, denetleyiciler ve Eylemler arasındaki yolları birleştirebilirsiniz. Örnek:

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
}
```

Yollar [HttpGet] ve benzer özniteliklerde belirtilebilir ve ayrı [Route] öznitelikleri ekleme gereksinimini ortadan kaldırabilirsiniz. Öznitelik yolları, aşağıda gösterildiği gibi denetleyicinin veya eylem adlarının yinelenmesi gereksinimini azaltmak için belirteçleri de kullanabilir:

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Razor Pages öznitelik yönlendirme kullanmaz. Bir Razor sayfasına yönelik ek yol şablonu bilgilerini yönergesinin bir parçası olarak belirtebilirsiniz `@page` :

```csharp
@page "{id:int}"
```

Önceki örnekte, söz konusu sayfa bir tamsayı parametresiyle bir rota ile eşleşir `id` . Örneğin, kökünde bulunan *Products. cshtml* sayfasında `/Pages` Bu yol olacaktır:

```csharp
"/Products/123"
```

Verilen bir istek bir rota ile eşleştirildiği halde, eylem yöntemi çağrılmadan önce ASP.NET Core MVC, istek üzerinde [model bağlama](/aspnet/core/mvc/models/model-binding) ve [model doğrulaması](/aspnet/core/mvc/models/validation) gerçekleştirir. Model bağlama, gelen HTTP verilerini çağrılacak eylem metodunun parametreleri olarak belirtilen .NET türlerine dönüştürmekten sorumludur. Örneğin, eylem yöntemi bir parametre beklediğinde `int id` , model bağlama isteğin bir parçası olarak sağlanmış bir değerden bu parametreyi sağlamaya çalışacaktır. Bunu yapmak için model bağlama, postalanan bir formdaki değerleri, yolun kendisindeki değerleri ve sorgu dizesi değerlerini arar. Bir `id` değerin bulunduğu varsayıldığında, eylem yöntemine geçirilmeden önce tamsayıya dönüştürülür.

Modeli bağladıktan sonra ancak eylem yöntemini çağırmadan önce, model doğrulaması oluşur. Model doğrulama, model türü üzerinde isteğe bağlı öznitelikleri kullanır ve sağlanan model nesnesinin belirli veri gereksinimlerine uygun olduğundan emin olmanıza yardımcı olabilir. Belirli değerler gerekli olarak belirtilebilir veya belirli bir uzunluk veya sayısal aralığa, vb. sınırlı olabilir. Doğrulama öznitelikleri belirtilmişse ancak model gereksinimlerine uygun değilse, ModelState. IsValid özelliği false olur ve başarısız doğrulama kuralları kümesi, isteği yapan istemciye gönderilmek üzere kullanılabilir olacaktır.

Model doğrulaması kullanıyorsanız, uygulamanızın geçersiz verilerle bozulmadığından emin olmak için herhangi bir durum değiştirme komutunu gerçekleştirmeden önce modelin geçerli olduğundan emin olun. Her eylemde bu doğrulama için kod ekleme gereksinimini ortadan kaldırmak için bir [filtre](/aspnet/core/mvc/controllers/filters) kullanabilirsiniz. ASP.NET Core MVC filtreleri, istek gruplarını ele almanın bir yolunu sunar, böylece ortak ilkeler ve çapraz kesme sorunları hedeflenen bir temele göre uygulanabilir. Filtreler tek tek eylemlere, tüm denetleyicilere veya bir uygulama için genel olarak uygulanabilir.

Web API 'Leri için ASP.NET Core MVC [_içerik anlaşmasını_](/aspnet/core/mvc/models/formatting)destekler ve isteklerin nasıl biçimlendirilmesi gerektiğini belirtmesini sağlar. İstekte belirtilen üstbilgilere göre verileri döndüren eylemler, yanıtı XML, JSON veya desteklenen başka bir biçimde biçimlendirir. Bu özellik, farklı veri biçimi gereksinimlerine sahip birden çok istemci tarafından aynı API 'nin kullanılmasını sağlar.

Web API projeleri, `[ApiController]` tek tek denetleyicilere, bir temel denetleyici sınıfına veya tüm derlemeye uygulanabilecek özniteliği kullanmayı göz önünde bulundurmalıdır. Bu öznitelik otomatik model doğrulama denetimi ekler ve geçersiz bir modele sahip herhangi bir eylem doğrulama hatalarının ayrıntılarına sahip bir BadRequest döndürür. Özniteliği aynı zamanda geleneksel bir yol kullanmak yerine tüm eylemlerin bir öznitelik yoluna sahip olmasını gerektirir ve hatalara yanıt olarak daha ayrıntılı ProblemDetails bilgileri döndürür.

### <a name="keeping-controllers-under-control"></a>Denetimleri denetim altında tutma

Sayfa tabanlı uygulamalar için Razor Pages denetleyicileri çok büyük bir şekilde tutmaya yönelik harika bir iş elde edin. Her bir sayfaya, kendi dosya ve sınıfları yalnızca işleyicisine ayrılmış şekilde verilir. Razor Pages 'nin kullanıma sunulmasından önce, birçok görünüm merkezli uygulamanın birçok farklı eylem ve görünümden sorumlu büyük denetleyici sınıfları vardır. Bu sınıflar doğal olarak çok sayıda sorumluluklara ve bağımlılıklara sahip olacak şekilde büyürken daha zor hale getirir. Görünüm tabanlı denetleyicilerinizi çok büyük büyüdüğünü fark ederseniz, Razor Pages kullanmak için yeniden düzenlemeyi veya bir ortam gibi bir kalıp tanıtmasını düşünün.

Ortalama tasarım stili, aralarında iletişime izin verirken sınıflar arasındaki bağlantı sayısını azaltmak için kullanılır. ASP.NET Core MVC uygulamalarında, bu model genellikle işlem yöntemlerinin çalışması için *işleyiciler* kullanılarak denetleyicileri daha küçük parçalara bölmek için kullanılır. Popüler [mediaTR NuGet paketi](https://www.nuget.org/packages/MediatR/) genellikle bunu gerçekleştirmek için kullanılır. Genellikle, denetleyicilerin her biri belirli bağımlılıklar gerektirebilecek birçok farklı eylem yöntemi vardır. Herhangi bir eylem için gereken tüm bağımlılıkların kümesi denetleyicinin oluşturucusuna geçirilmelidir. MediatR kullanırken, bir denetleyicinin bir örneği olan tek bağımlılığı bir ortam örneğidir. Sonra her eylem, bir işleyici tarafından işlenen bir ileti göndermek için Mediator örneğini kullanır. İşleyici tek bir eyleme özeldir ve bu nedenle yalnızca bu eylem için gereken bağımlılıklara ihtiyaç duyuyor. MediatR kullanan bir denetleyiciye örnek burada gösterilmektedir:

```csharp
public class OrderController : Controller
{
    private readonly IMediator _mediator;

    public OrderController(IMediator mediator)
    {
        _mediator = mediator;
    }

    [HttpGet]
    public async Task<IActionResult> MyOrders()
    {
        var viewModel = await _mediator.Send(new GetMyOrders(User.Identity.Name));

        return View(viewModel);
    }

    // other actions implemented similarly
}
```

`MyOrders`Eylemde, `Send` bir iletiye yapılan çağrı `GetMyOrders` Bu sınıf tarafından işlenir:

```csharp
public class GetMyOrdersHandler : IRequestHandler<GetMyOrders, IEnumerable<OrderViewModel>>
{
    private readonly IOrderRepository _orderRepository;

    public GetMyOrdersHandler(IOrderRepository orderRepository)
    {
        _orderRepository = orderRepository;
    }

    public async Task<IEnumerable<OrderViewModel>> Handle(GetMyOrders request, CancellationToken cancellationToken)
    {
        var specification = new CustomerOrdersWithItemsSpecification(request.UserName);
        var orders = await _orderRepository.ListAsync(specification);

        return orders.Select(o => new OrderViewModel
        {
            OrderDate = o.OrderDate,
            OrderItems = o.OrderItems?.Select(oi => new OrderItemViewModel()
            {
                PictureUrl = oi.ItemOrdered.PictureUri,
                ProductId = oi.ItemOrdered.CatalogItemId,
                ProductName = oi.ItemOrdered.ProductName,
                UnitPrice = oi.UnitPrice,
                Units = oi.Units
            }).ToList(),
            OrderNumber = o.Id,
            ShippingAddress = o.ShipToAddress,
            Total = o.Total()
        });
    }
}
```

Bu yaklaşımın nihai sonucu, denetleyicilerin çok daha küçük olmasını ve öncelikle yönlendirme ve model bağlamasıyla odaklanmasını, ancak belirli bir uç nokta için gereken belirli görevlerden bağımsız işleyicilerin sorumlu olmasını sağlar. Bu yaklaşım ayrıca, API Razor Pages denetleyicilerini, görüntüleme tabanlı denetleyicilere getirmelerini sağlayan [Apiendpoints NuGet paketi](https://www.nuget.org/packages/Ardalis.ApiEndpoints/)kullanılarak MediatR olmadan elde edilebilir.

> ### <a name="references--mapping-requests-to-responses"></a>Başvurular – Istekleri yanıtlara eşleme
>
> - **Denetleyici eylemlerine yönlendirme**\
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Model bağlama**\
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Model doğrulama**\
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Yorsa**\
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **ApiController özniteliği**\
 > <https://docs.microsoft.com/aspnet/core/web-api/>

## <a name="working-with-dependencies"></a>Bağımlılıklarla çalışma

ASP.NET Core, için yerleşik desteğe sahiptir ve dahili olarak [bağımlılık ekleme](/aspnet/core/fundamentals/dependency-injection)olarak bilinen bir tekniğin kullanımını sağlar. Bağımlılık ekleme, bir uygulamanın farklı parçaları arasında gevşek bir şekilde bağlantısı sağlayan bir tekniktir. GEVME bağlantısı, uygulamanın parçalarını yalıtmak daha kolay olduğundan, test veya değişiklik yapılmasına olanak sağlar. Ayrıca, uygulamanın bir bölümündeki değişikliğin uygulamada başka bir yerde beklenmedik bir etkiye sahip olacağını daha da zorlaştırır. Bağımlılık ekleme, bağımlılık Inversion ilkesine dayanır ve genellikle açık/kapalı ilkesini elde etmek için anahtardır. Uygulamanızın bağımlılıklarıyla nasıl çalıştığını değerlendirirken, [statik Cling](https://deviq.com/static-cling/) Code kokusu ' na göz atın ve aphorısm "[Yeni bir tutkalla" olduğunu](https://ardalis.com/new-is-glue)unutmayın.

Sınıflarınızda statik yöntemlere çağrı yapıldığında veya altyapıda yan etkileri veya bağımlılıklar olan statik özelliklere erişmek için statik Cling oluşur. Örneğin, bir statik yöntemi çağıran bir metoda sahipseniz, bu, bir veritabanına yazıyorsa, yönteminiz veritabanına sıkı bir şekilde bağlanmış olur. Bu veritabanı çağrısını kesen her şey, yönteminizi bozacaktır. Bu tür testler, statik çağrıları sahte bir şekilde ticari model oluşturma gerektirdiğinden veya yalnızca bir test veritabanıyla test edilemediğinden, bu tür yöntemlerin test edilmesi oldukça zordur. Altyapı üzerinde hiçbir bağımlılığı olmayan statik çağrılar, özellikle de durum bilgisiz olan çağrılar çağrı yapmak için uygundur ve bir ya da pakararlılığı üzerinde hiçbir etkisi olmaz (Bu kodun, statik çağrının kendisindeki bağlantısı ötesinde).

Birçok geliştirici statik Cling ve küresel durum risklerini anlamakta, ancak doğrudan örnek oluşturma yoluyla kendi kodunu belirli uygulamalara sıkı bir şekilde ister. "Yeni bir tutkalla", anahtar sözcüğünün kullanımı için genel bir Condemnation değil, bu kuponun bir anımsatıcı olması anlamına gelir `new` . Statik yöntem çağrılarında olduğu gibi, dış bağımlılıkları olmayan türlerin yeni örnekleri genellikle uygulama ayrıntılarına sıkı bir şekilde kod içermez veya sınamayı daha zor hale getirir. Ancak, bir sınıfın her örneği oluşturulduğunda, bu belirli bir konumdaki belirli bir örneği sabit koda veya bu örneği bir bağımlılık olarak istemek için daha iyi bir tasarım olup olmadığını göz önünde bulundurmanız gereken kısa bir süre ayırın.

### <a name="declare-your-dependencies"></a>Bağımlılıklarınızı bildirin

ASP.NET Core, yöntem ve sınıfların bağımlılıklarını bildirmek ve bunları bağımsız değişken olarak istiyor. ASP.NET uygulamaları tipik olarak, bir başlangıç sınıfında ayarlanır ve bu, kendisini birçok noktaya bağımlılık ekleme işlemini destekleyecek şekilde yapılandırılmıştır. Başlangıç sınıfınızın bir Oluşturucusu varsa, bu, Oluşturucu aracılığıyla bağımlılık isteğinde bulunabilir, örneğin:

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
            .SetBasePath(env.ContentRootPath)
            .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
            .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

Başlangıç sınıfı, bunun için açık tür gereksinimleri olmaması açısından ilginç değildir. Özel bir başlangıç temel sınıfından kalıtımla almaz ve belirli bir arabirimi uygulamaz. Oluşturucuya bir Oluşturucu verebilir veya Not alabilir ve oluşturucuda istediğiniz sayıda parametre belirtebilirsiniz. Uygulamanız için yapılandırdığınız Web ana bilgisayarı başlatıldığında, kullanmasını söylemekte olduğunuz başlangıç sınıfını çağırır ve başlangıç sınıfının gerektirdiği bağımlılıkları doldurmak için bağımlılık ekleme 'yi kullanır. Kuşkusuz, ASP.NET Core tarafından kullanılan hizmetler kapsayıcısında yapılandırılmamış parametreler istemeniz halinde bir özel durum alırsınız, ancak kapsayıcının ilgili olduğu bağımlılıkları tercih ettiğiniz sürece istediğiniz herhangi bir şey isteyebilirsiniz.

Bağımlılık ekleme, başlangıç örneğini oluştururken ASP.NET Core uygulamalarınıza doğrudan baştan oluşturulmuştur. Başlangıç sınıfı için bu yok durmaz. Yapılandırma yönteminde de bağımlılıklar isteyebilirsiniz:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

ConfigureServices yöntemi bu davranışın istisnadır; yalnızca ıvicecollection türünde tek bir parametre almalıdır. Son olarak, hizmet kapsayıcısına nesne eklemekten sorumlu olduğu ve diğer tüm yapılandırılmış hizmetlere ıvicecollection parametresi aracılığıyla erişimi olduğundan, bağımlılık ekleme işlemini desteklemesi gerçekten gerekli değildir. Bu nedenle, gerekli hizmeti bir parametre olarak isteyerek veya ConfigureServices içindeki ıvicecollection ile çalışarak, başlangıç sınıfının her bölümünde ASP.NET Core Hizmetleri koleksiyonunda tanımlanan bağımlılıklarla çalışabilirsiniz.

> [!NOTE]
> Başlangıç sınıfınız için bazı hizmetlerin kullanılabilir olduğundan emin olmanız gerekiyorsa, bunları CreateDefaultBuilder çağrısının içindeki bir ıwebhostbuilder ve ConfigureServices yöntemi ile yapılandırabilirsiniz.

Başlangıç sınıfı, ASP.NET Core uygulamanızın diğer bölümlerini denetleyicilerden ara yazılıma kendi hizmetlerinize yönelik olarak nasıl yapılandıracağınıza yönelik bir modeldir. Her durumda, doğrudan oluşturmak yerine bağımlılıklarınızı isteyerek ve uygulamanızın tamamında bağımlılık ekleme özelliğinden yararlanarak [Açık bağımlılıklar ilkesini](https://deviq.com/explicit-dependencies-principle/)izlemelisiniz. Uygulamaları, özellikle de altyapıyla çalışan veya yan etkileri olan uygulamaları, doğrudan hizmet ve nesneleri nasıl ve nasıl örneklendirileceğine dikkat edin. Uygulama çekirdekde tanımlanan soyutlamalar ile çalışmayı tercih edin ve belirli uygulama türlerine yönelik başvuruları kodlamaları için bağımsız değişken olarak geçirilmiş olarak geçin.

## <a name="structuring-the-application"></a>Uygulamayı yapılandırma

Tek parçalı uygulamalar genellikle tek bir giriş noktasına sahiptir. ASP.NET Core Web uygulaması söz konusu olduğunda, giriş noktası ASP.NET Core Web projesi olur. Ancak bu, çözümün yalnızca tek bir projeden oluşması anlamına gelmez. Kaygıları ayırmayı izlemek için uygulamayı farklı katmanlara bölmek yararlı olur. Katmanlara bölüntikten sonra, daha iyi kapsülleme elde etmenize yardımcı olacak şekilde klasörlerin ötesine geçme yararlı olur. ASP.NET Core bir uygulamayla bu hedeflere ulaşmak için en iyi yaklaşım, Bölüm 5 ' te ele alınan temiz mimarinin bir çeşitlemesi. Bu yaklaşımda, uygulamanın çözümü UI, altyapı ve ApplicationCore için ayrı kitaplıklar oluşturur.

Bu projelere ek olarak, ayrı test projeleri de dahildir (test, Bölüm 9 ' da ele alınmıştır).

Uygulamanın nesne modeli ve arabirimleri ApplicationCore projesine yerleştirilmelidir. Bu proje mümkün olduğunca az bağımlılıklara sahip olacak ve çözümdeki diğer projelere başvuracaktır. Kalıcı olması gereken iş varlıkları, altyapıya doğrudan bağlı olmayan hizmetler olduğundan, ApplicationCore projesinde tanımlanmıştır.

Kalıcılık gerçekleştirilme veya bildirimlerin bir kullanıcıya nasıl gönderilelebileceği gibi uygulama ayrıntıları altyapı projesinde tutulur. Bu proje, Entity Framework Core gibi uygulamaya özgü paketlere başvuracaktır, ancak proje dışındaki bu uygulamalarla ilgili ayrıntıları göstermemelidir. Altyapı Hizmetleri ve depoları, ApplicationCore projesinde tanımlanan arabirimleri uygulamalıdır ve ApplicationCore 'da tanımlanan varlıkları alma ve depolama konusunda Kalıcılık uygulamalarıdır.

ASP.NET Core UI projesi, herhangi bir kullanıcı arabirimi düzeyi kaygısından sorumludur, ancak iş mantığını veya altyapı ayrıntılarını içermemelidir. Aslında, ideal olarak, iki proje arasında hiçbir bağımlılığın yanlışlıkla tanıtılmamasını sağlamaya yardımcı olacak şekilde altyapı projesine bir bağımlılığı olmamalıdır. Bu, her bir projedeki modül sınıflarında DI kuralları tanımlamanızı sağlayan Autofac gibi bir üçüncü taraf DI kapsayıcısı kullanılarak elde edilebilir.

Uygulamanın uygulama ayrıntılarından ayrılmasıyla ilgili başka bir yaklaşım da uygulamanın mikro hizmetleri çağırması, belki de ayrı bir Docker kapsayıcısında dağıtılması. Bu, zorluklardan daha büyük ayrım sağlar ve iki proje arasında bir tan kullanmaktan farklı, ancak ek karmaşıklığa sahiptir.

### <a name="feature-organization"></a>Özellik organizasyonu

Varsayılan olarak, ASP.NET Core uygulamalar, klasör yapısını denetleyicileri ve görünümleri ve sık sık görünüm modellerini içerecek şekilde düzenler. Bu sunucu tarafı yapıları desteklemeye yönelik istemci tarafı kodu genellikle Wwwroot klasöründe ayrı olarak depolanır. Ancak, belirli bir özellik üzerinde çalışmak bu klasörler arasında atlama gerektirdiğinden, büyük uygulamalar bu kuruluşla ilgili sorunlarla karşılaşabilir. Bu, her bir klasördeki dosya ve alt klasörlerin sayısı arttıkça daha fazla ve çok daha zor bir işlem elde Çözüm Gezgini. Bu soruna yönelik bir çözüm, uygulama kodunu dosya türüne göre değil, _özelliğe_ göre düzenleyeceğiniz bir çözümdür. Bu kuruluş stiline genellikle özellik klasörleri veya [özellik dilimleri](/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc) adı verilir (Ayrıca bkz: [Dikey dilimler](https://deviq.com/vertical-slices/)).

ASP.NET Core MVC bu amaca yönelik alanı destekler. Alanları kullanarak her bir alan klasöründeki ayrı denetleyici ve görünüm klasörü (Ayrıca ilişkili modeller) oluşturabilirsiniz. Şekil 7-1, alan kullanarak örnek bir klasör yapısını gösterir.

![Örnek alan organizasyonu](./media/image7-1.png)

**Şekil 7-1**. Örnek alan organizasyonu

Alanları kullanırken, denetleyicilerinizi ait oldukları alanın adıyla süslemek için öznitelikleri kullanmanız gerekir:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Ayrıca, rotalarınız için alan desteği eklemeniz gerekir:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "areaRoute", pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Alanlara yönelik yerleşik desteğe ek olarak, kendi klasör yapınızı ve özniteliklerin ve özel yolların yerine kurallarınızı de kullanabilirsiniz. Böylece görünümler, denetleyiciler, vb. için ayrı klasörler içermeyen Özellik klasörlerine sahip olabilirsiniz, böylece hiyerarşi düzlebilir ve her bir özellik için tüm ilgili dosyaları tek bir yerde görmeyi kolaylaştırın.

ASP.NET Core davranışını denetlemek için yerleşik kural türlerini kullanır. Bu kurallara göre değişiklik yapabilir veya değiştirebilirsiniz. Örneğin, belirli bir denetleyicinin özellik adını ad alanına göre otomatik olarak alacak bir kural oluşturabilirsiniz (genellikle denetleyicinin bulunduğu klasörle ilişkili olur):

```csharp
public class FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

Bundan sonra, ConfigureServices 'daki uygulamanıza MVC desteği eklediğinizde bu kuralı bir seçenek olarak belirtirsiniz:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC, görünümleri bulmak için de bir kural kullanır. Görünümlerin Özellik klasörlerinizde bulunması için (yukarıdaki FeatureConvention tarafından sunulan özellik adı kullanılarak) özel bir kural ile geçersiz kılabilirsiniz. Bu yaklaşım hakkında daha fazla bilgi alabilir ve MSDN Magazine makalesinden çalışan bir örnek indirebilirsiniz [ASP.NET Core MVC Için özellik dilimleri](/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc).

### <a name="apis-and-blazor-applications"></a>API 'Ler ve Blazor uygulamalar

Uygulamanız güvenli olması gereken bir dizi Web API 'si içeriyorsa, bu API 'ler görünüm veya Razor Pages uygulamanızdan ayrı bir proje olarak yapılandırılmalıdır. Sunucu tarafı Web uygulamanızdan API 'Lerin, özellikle ortak API 'lerin ayrılması birçok avantaj sağlar. Bu uygulamalar genellikle benzersiz dağıtım ve yükleme özelliklerine sahip olur. Ayrıca, tanımlama bilgisi tabanlı kimlik doğrulaması ve API 'Lerin en büyük olasılıkla belirteç tabanlı kimlik doğrulaması kullanan API 'lerden yararlanarak standart form tabanlı uygulamalarla güvenlik için farklı mekanizmalar benimseme olasılığı yüksektir.

Ayrıca, Blazor sunucu veya kullanma gibi uygulamalar Blazor Blazor WebAssembly ayrı projeler olarak oluşturulmalıdır. Uygulamalarda farklı çalışma zamanı özellikleri ve güvenlik modelleri de vardır. Büyük olasılıkla sunucu tarafı Web uygulamasıyla (veya API projesiyle) ortak türleri paylaşmaları olasıdır ve bu türler ortak bir paylaşılan projede tanımlanmalıdır.

Blazor WebAssembly EShopOnWeb 'e yönetici arabiriminin eklenmesi, birkaç yeni proje eklemeye gerek. Blazor WebAssembly Projenin kendisi, `BlazorAdmin` . Tarafından kullanılan `BlazorAdmin` ve belirteç tabanlı kimlik doğrulaması kullanmak için yapılandırılan yeni bir ortak API uç noktası kümesi, `PublicApi` projede tanımlanmıştır. Ve bu projelerin her ikisi tarafından kullanılan bazı paylaşılan türler yeni bir `BlazorShared` projede tutulur.

Bunlardan biri, `BlazorShared` `ApplicationCore` hem hem de gereken herhangi bir türü paylaşmak için kullanılabilen ortak bir proje olduğunda `PublicApi` , neden tek bir proje eklemeli, neden olabilir. `BlazorAdmin` Yanıt, bu projenin tüm uygulamanın iş mantığını içermesi ve bu nedenle gerekenden çok daha büyük olması ve sunucuda güvenli tutulması gereken çok daha fazla olasılıktır. Tarafından başvurulan herhangi bir kitaplığın `BlazorAdmin` , uygulamayı yüklediklerinde kullanıcıların tarayıcılarına indirileceğini unutmayın Blazor .

Arka [uçlar-for-frontends (BFF) modelini](/azure/architecture/patterns/backends-for-frontends)kullanıp kullanmadığını bağlı olarak, uygulama tarafından tüketilen API 'ler Blazor WebAssembly ile %100 türlerini paylaşamaz Blazor . Özellikle, birçok farklı istemci tarafından kullanılması amaçlanan ortak bir API, istemciye özgü paylaşılan bir projede paylaşmak yerine kendi istek ve sonuç türlerini tanımlayabilir. EShopOnWeb örneğinde, `PublicApi` Proje bir ortak API barındırılmakta olduğundan, tüm istek ve yanıt türleri projeden gelmemesi için varsayım yapılır `BlazorShared` .

### <a name="cross-cutting-concerns"></a>Geniş kapsamlı kritik konular

Uygulamalar büyüdükçe, çoğaltmayı ortadan kaldırmak ve tutarlılığı sürdürmek için çapraz kesme sorunlarını ortadan kaldırmak giderek daha da önemli hale gelir. ASP.NET Core uygulamalardaki çapraz kesme kaygılarının bazı örnekleri, çok sayıda diğerleri olsa da, kimlik doğrulama, model doğrulama kuralları, çıktı önbelleği ve hata işleme örnekleridir. ASP.NET Core MVC [filtreleri](/aspnet/core/mvc/controllers/filters) , istek işleme ardışık düzeninde belirli adımlardan önce veya sonra kod çalıştırmanızı sağlar. Örneğin bir filtre, model bağlamadan önce ve sonra, bir eylemden önce ve sonra ya da bir eylem sonucundan önce ve sonra çalışabilir. Ayrıca, ardışık düzenin geri kalanına erişimi denetlemek için bir yetkilendirme filtresi de kullanabilirsiniz. Şekil 7-2, yapılandırılmışsa, istek yürütmenin filtreler aracılığıyla nasıl akacağını gösterir.

![İstek, Yetkilendirme filtreleri, kaynak filtreleri, model bağlama, eylem filtreleri, eylem yürütme ve eylem sonucu dönüştürme, özel durum filtreleri, sonuç filtreleri ve sonuç yürütmesi aracılığıyla işlenir. Bu şekilde, istek yalnızca istemciye gönderilen yanıt haline gelmeden önce sonuç filtreleri ve kaynak filtreleri tarafından işlenir.](./media/image7-2.png)

**Şekil 7-2**. Filtreler ve istek işlem hattı aracılığıyla yürütme isteği.

Filtreler genellikle öznitelik olarak uygulanır, bu sayede bunları denetleyicilere veya eylemlere (veya genel olarak) uygulayabilirsiniz. Bu biçimde eklendiğinde, eylem düzeyinde belirtilen filtreler geçersiz kılınır veya denetleyici düzeyinde belirtilen filtrelerin üzerine inşa edildiğinde, kendilerine genel filtreleri geçersiz kılar. Örneğin, \[ yol \] özniteliği denetleyiciler ve Eylemler arasındaki yolları oluşturmak için kullanılabilir. Benzer şekilde, yetkilendirme denetleyici düzeyinde yapılandırılabilir ve aşağıdaki örnekte gösterildiği gibi ayrı eylemler tarafından geçersiz kılınır:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

İlk yöntem olan oturum açma, denetleyici düzeyinde ayarlanan yetkilendirme filtresini geçersiz kılmak için AllowAnonymous filtresini (özniteliği) kullanır. ForgotPassword eylemi (ve AllowAnonymous özniteliği olmayan sınıfta bulunan başka bir eylem), kimliği doğrulanmış bir istek gerektirir.

Filtreler, API 'Ler için ortak hata işleme ilkeleri biçimindeki yinelemeyi ortadan kaldırmak için kullanılabilir. Örneğin, tipik bir API ilkesi, var olmayan anahtarlara başvuran isteklere NotFound yanıtı ve model doğrulaması başarısız olursa bir BadRequest yanıtı döndürmemelidir. Aşağıdaki örnek, bu iki ilkeyi eylemde gösterir:

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Eylem yöntemlerinizi bunun gibi koşullu kodla karışık hale gelmesine izin vermez. Bunun yerine, ilkeleri gereken şekilde uygulanabilecek filtrelere çekin. Bu örnekte, API 'ye bir komutun gönderilmesi her zaman oluşması gereken model doğrulama denetimi aşağıdaki öznitelikle değiştirilebilir:

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

`ValidateModelAttribute` [Ardalış. ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel) paketini dahil ederek projenize bir NuGet bağımlılığı olarak ekleyebilirsiniz. API 'Ler için, `ApiController` Bu davranışı ayrı bir filtreye gerek olmadan zorlamak için özniteliğini kullanabilirsiniz `ValidateModel` .

Benzer şekilde, bir filtre, bir kaydın mevcut olup olmadığını denetlemek için kullanılabilir ve eylem yürütülmeden önce bir 404 döndürebilir, bu denetimleri eylemde gerçekleştirme gereksinimini ortadan kaldırır. Ortak kuralları kullanıma aldıktan ve çözümünüzü altyapı kodu ve iş mantığını kullanıcı arabiriminden ayırmak üzere düzenledikten sonra, MVC eylem yöntemlerinizi son derece ölçülü olmalıdır:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Filtre uygulama hakkında daha fazla bilgi edinmek ve MSDN Magazine makalesinden, [gerçek dünya ASP.NET Core MVC filtrelerinden](/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters)çalışan bir örneği indirmek için daha fazla bilgi edinebilirsiniz.

> ### <a name="references--structuring-applications"></a>Başvurular – uygulamaları yapılandırma
>
> - **Alanları**\
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Magazine – ASP.NET Core MVC için özellik dilimleri**\
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc>
> - **Yorsa**\
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN Magazine – gerçek dünya ASP.NET Core MVC filtreleri**\
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters>

## <a name="security"></a>Güvenlik

Web uygulamalarının güvenliğini sağlamak, çok sayıda konuyla büyük bir konudur. En temel düzeyinde güvenlik, belirli bir isteğin geldiği kişiyi öğrendiğinizden ve isteğin yalnızca gereken kaynaklara erişimi olduğundan emin olmanızı içerir. Kimlik doğrulaması, isteğin bilinen bir varlıktan geldiği kabul edilmesinin gerekip gerekmediğini görmek için, güvenilir bir veri deposundaki bir istekle girilen kimlik bilgilerini karşılaştırma işlemidir. Yetkilendirme, belirli kaynaklara erişimi kullanıcı kimliğine göre kısıtlama işlemidir. Üçüncü bir güvenlik konusu, isteklerin, en azından [SSL 'nin uygulamanız tarafından kullanıldığından emin](/aspnet/core/security/enforcing-ssl)olmanız gereken üçüncü taraflar tarafından dinleyerek dinleme yaptığı isteklerden korunuyor.

### <a name="identity"></a>Kimlik

ASP.NET Core kimlik, uygulamanız için oturum açma işlevlerini desteklemek için kullanabileceğiniz bir üyelik sistemidir. Bu, yerel kullanıcı hesaplarının yanı sıra Microsoft hesabı, Twitter, Facebook, Google ve daha fazlası gibi sağlayıcılardan dış oturum açma sağlayıcısı desteği için destek içerir. ASP.NET Core kimliğe ek olarak, uygulamanız Windows kimlik doğrulamasını veya [kimlik sunucusu](https://github.com/IdentityServer/IdentityServer4)gibi bir üçüncü taraf kimlik sağlayıcısını kullanabilir.

Bireysel kullanıcı hesapları seçeneği işaretliyse ASP.NET Core kimlik yeni proje şablonlarına dahil edilir. Bu şablon kayıt, oturum açma, dış oturum açma, unutulan parolalar ve ek işlevsellik için destek içerir.

![Kimliği önceden yapılandırılmış olan bireysel kullanıcı hesaplarını seçin](./media/image7-3.png)

**Şekil 7-3**. Kimliği önceden yapılandırılmış olan bireysel kullanıcı hesaplarını seçin.

Kimlik desteği başlangıçta, hem ConfigureServices hem de yapılandırma ' da yapılandırılır:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

Useıdentity 'in configure yönteminde UseMvc 'den önce görünmesi önemlidir. ConfigureServices 'da kimlik yapılandırılırken, AddDefaultTokenProviders için bir çağrı olduğunu fark edeceksiniz. Bu, Web iletişimlerini güvenli hale getirmek için kullanılabilecek belirteçlerle hiçbir şey yapmaz, bunun yerine kullanıcıların kimliklerini onaylamasını sağlamak için SMS veya e-posta aracılığıyla kullanıcılara gönderilebilecek istekleri oluşturan sağlayıcılara başvurur.

[İki öğeli kimlik doğrulamayı yapılandırma](/aspnet/core/security/authentication/2fa) ve resmi ASP.NET Core belgelerinden [dış oturum açma sağlayıcılarını etkinleştirme](/aspnet/core/security/authentication/social/) hakkında daha fazla bilgi edinebilirsiniz.

### <a name="authentication"></a>Kimlik Doğrulaması

Kimlik doğrulama, sisteme kimlerin eriştiğini belirleme işlemidir. Önceki bölümde gösterilen ASP.NET Core kimliği ve yapılandırma yöntemleri kullanıyorsanız, uygulama içindeki bazı kimlik doğrulama varsayılanlarını otomatik olarak yapılandırır. Bununla birlikte, bu Varsayılanları el ile de yapılandırabilir veya AddEntity tarafından ayarlanmış olanları geçersiz kılabilirsiniz. Kimlik kullanıyorsanız, tanımlama bilgisi tabanlı kimlik doğrulamasını varsayılan *Düzen* olarak yapılandırır.

Web tabanlı kimlik doğrulamasında, genellikle bir sistem istemcisinin kimlik doğrulaması sırasında gerçekleştirilebilecek en fazla beş eylem vardır. Bunlar:

- Denetimini. Uygulama içinde kullanmak üzere bir kimlik oluşturmak için istemci tarafından sunulan bilgileri kullanın.
- Sına. Bu eylem, istemcinin kendilerini belirlemesini gerektirmek için kullanılır.
- Yasaklamaz. İstemciye bir eylem gerçekleştirmekten yasaklanmış olduğunu bildirin.
- Oturum açın. Mevcut istemciyi bir şekilde kalıcı hale getirin.
- Oturum kapatma. İstemciyi kalıcılığı kaldırın.

Web uygulamalarında kimlik doğrulaması gerçekleştirmeye yönelik çeşitli yaygın teknikler vardır. Bunlar, şemalar olarak adlandırılır. Belirli bir düzen, Yukarıdaki seçeneklerin bazıları veya tümü için eylem tanımlar. Bazı şemalar yalnızca eylemlerin bir alt kümesini destekler ve desteklemediği işlemleri gerçekleştirmek için ayrı bir şema gerektirebilir. Örneğin, OpenId-Connect (OıDC) şeması, oturum açma veya oturum kapatma desteğini desteklemez, ancak yaygın olarak bu Kalıcılık için tanımlama bilgisi kimlik doğrulaması kullanmak üzere yapılandırılmıştır.

ASP.NET Core uygulamanızda, `DefaultAuthenticateScheme` yukarıda açıklanan eylemlerin her biri için isteğe bağlı özel düzenleri de yapılandırabilirsiniz. Örneğin,, `DefaultChallengeScheme` , `DefaultForbidScheme` vb. Çağırma [`AddIdentity<TUser,TRole>`](https://github.com/dotnet/aspnetcore/blob/release/3.1/src/Identity/Core/src/IdentityServiceCollectionExtensions.cs#L38-L102) , uygulamanın çeşitli yönlerini yapılandırır ve birçok gerekli hizmeti ekler. Ayrıca, kimlik doğrulama düzenini yapılandırmak için bu çağrıyı içerir:

```csharp
services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = IdentityConstants.ApplicationScheme;
    options.DefaultChallengeScheme = IdentityConstants.ApplicationScheme;
    options.DefaultSignInScheme = IdentityConstants.ExternalScheme;
});
```

Bu düzenler, varsayılan olarak kimlik doğrulaması için oturum açma sayfalarında Kalıcılık ve yeniden yönlendirme için tanımlama bilgilerini kullanır. Bu şemalar, Web tarayıcıları aracılığıyla kullanıcılarla etkileşen ancak API 'Ler için önerilmeyen Web uygulamaları için uygundur. Bunun yerine, API 'Ler genellikle JWT taşıyıcı belirteçleri gibi başka bir kimlik doğrulama biçimi kullanır.

Web API 'Leri, `HttpClient` .NET uygulamaları ve diğer çerçevelerde eşdeğer türler gibi kod tarafından kullanılır. Bu istemciler bir API çağrısından kullanılabilir bir yanıt bekler veya varsa, sorun oluştuğunda ne olduğunu belirten bir durum kodudur. Bu istemciler bir tarayıcıdan etkileşim kurmazlar ve bir API 'nin döndürebileceği HTML 'yi işlemez veya bunlarla etkileşime girmezler. Bu nedenle, kimlik doğrulamasından geçirilmezse istemcilerinin oturum açma sayfalarına yönlendirilmesini sağlamak için API uç noktaları için uygun değildir. Başka bir düzen daha uygundur.

API 'Lerin kimlik doğrulamasını yapılandırmak için, `PublicApi` eShopOnWeb Reference uygulamasındaki proje tarafından kullanılan aşağıdaki gibi kimlik doğrulamasını ayarlayabilirsiniz:

```csharp
services.AddAuthentication(config =>
{
    config.DefaultScheme = JwtBearerDefaults.AuthenticationScheme;
})
    .AddJwtBearer(config =>
    {
        config.RequireHttpsMetadata = false;
        config.SaveToken = true;
        config.TokenValidationParameters = new TokenValidationParameters
        {
            ValidateIssuerSigningKey = true,
            IssuerSigningKey = new SymmetricSecurityKey(key),
            ValidateIssuer = false,
            ValidateAudience = false
        };
    });
```

Tek bir proje içinde birden çok farklı kimlik doğrulama düzeni yapılandırmak mümkün olsa da, tek bir varsayılan düzeni yapılandırmak çok basittir. Bu nedenle, eShopOnWeb Reference uygulaması, API 'Lerini, `PublicApi` `Web` uygulamanın görünümlerini ve Razor Pages içeren ana projeden ayrı olarak kendi projesine ayırır.

#### <a name="authentication-in-blazor-apps"></a>Uygulamalarda kimlik doğrulaması Blazor

Blazor Sunucu uygulamaları, diğer ASP.NET Core uygulamalarla aynı kimlik doğrulama özelliklerinden faydalanabilir. BlazorWebAssemblyuygulamalar, tarayıcıda çalıştırıldıklarından, yerleşik kimlik ve kimlik doğrulama sağlayıcılarını kullanamaz. BlazorWebAssemblyuygulamalar Kullanıcı kimlik doğrulama durumunu yerel olarak saklayabilir ve kullanıcıların gerçekleştirebilecekleri eylemleri belirlemek için taleplere erişebilir. Ancak, Blazor WebAssembly Kullanıcılar uygulamayı kolayca atlayıp API 'lerle doğrudan etkileşime girebileceği için tüm kimlik doğrulama ve yetkilendirme denetimleri, uygulamanın içinde uygulanan mantığa bakılmaksızın sunucuda gerçekleştirilmelidir.

> ### <a name="references--authentication"></a>Başvurular – kimlik doğrulaması
>
> - **Kimlik doğrulama eylemleri ve varsayılanlar**\
>   <https://stackoverflow.com/a/52493428>
> - **Maça kimlik doğrulaması ve yetkilendirme**\
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity-api-authorization>
> - **ASP.NET Core Blazor kimlik doğrulaması ve yetkilendirme**\
>   <https://docs.microsoft.com/aspnet/core/blazor/security/>
> - **Güvenlik: ASP.NET Web Forms ve üzerinde kimlik doğrulaması ve yetkilendirme Blazor**\
>   <https://docs.microsoft.com/dotnet/architecture/blazor-for-web-forms-developers/security-authentication-authorization>

### <a name="authorization"></a>Yetkilendirme

En basit yetkilendirme biçimi anonim kullanıcılara erişimin kısıtlanmasını içerir. Bu işlevsellik, \[ \] belirli denetleyicilere veya eylemlere Yetkilendir özniteliği uygulanarak elde edilebilir. Roller kullanılıyorsa, bu öznitelik, aşağıda gösterildiği gibi belirli rollere ait kullanıcılara erişimi kısıtlamak için daha fazla genişletilebilir.

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

Bu durumda, `HRManager` veya `Finance` rollerine (ya da her ikisine) ait olan kullanıcıların SalaryController erişimi olur. Bir kullanıcının birden çok role (yalnızca birkaç tane değil) ait olmasını gerektirmek için, her seferinde gerekli bir rol belirterek özniteliği birden çok kez uygulayabilirsiniz.

Birçok farklı denetleyicilerde ve eylemlerdeki belirli rol kümelerini belirtme, istenmeyen bir tekrarya yol açabilir. En azından, bu dize sabit değerleri için sabitleri tanımlayın ve dizeyi belirtmeniz gereken her yerde sabitleri kullanın. Yetkilendirme kurallarını kapsülleyen yetkilendirme ilkelerini de yapılandırabilir ve sonra Yetkilendir özniteliği uygulanırken ayrı roller yerine ilkeyi belirtebilirsiniz \[ \] :

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

İlkeleri bu şekilde kullanarak, bu işlem için uygulanan belirli rol veya kurallardan sınırlandırılmakta olan eylemlerin türlerini ayırabilirsiniz. Daha sonra, belirli kaynaklara erişmesi gereken yeni bir rol oluşturursanız, her yetkilendirme özniteliğinde her rol listesini güncelleştirmek yerine yalnızca bir ilkeyi güncelleştirebilirsiniz \[ \] .

#### <a name="claims"></a>Talepler

Talepler, kimliği doğrulanmış bir kullanıcının özelliklerini temsil eden ad değer çiftleridir. Örneğin, kullanıcıların çalışan numarasını bir talep olarak saklayabilirsiniz. Talepler, yetkilendirme ilkelerinin bir parçası olarak kullanılabilir. Bu örnekte gösterildiği gibi "EmployeeNumber" adlı bir talebin varlığını gerektiren "EmployeeOnly" adlı bir ilke oluşturabilirsiniz:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

Bu ilke daha sonra \[ \] yukarıda açıklandığı gibi herhangi bir denetleyiciyi ve/veya eylemi korumak için yetkilendir özniteliğiyle birlikte kullanılabilir.

#### <a name="securing-web-apis"></a>Web API 'Lerinin güvenliğini sağlama

Çoğu Web API 'si, belirteç tabanlı bir kimlik doğrulama sistemi uygulamalıdır. Belirteç kimlik doğrulaması durum bilgisiz ve ölçeklenebilir olacak şekilde tasarlandı. Belirteç tabanlı bir kimlik doğrulama sisteminde, istemci ilk olarak kimlik doğrulama sağlayıcısıyla kimlik doğrulaması yapması gerekir. Başarılı olursa, istemciye yalnızca şifreli olarak anlamlı bir karakter dizesi olan bir belirteç verilir. Belirteçler için en yaygın biçim JSON Web Token veya JWT (genellikle "parça" olarak belirlenir). İstemcinin bir API 'ye istek vermesi gerektiğinde, bu belirteci istek üzerine bir başlık olarak ekler. Sunucu daha sonra isteği tamamlamadan önce istek üstbilgisinde bulunan belirteci doğrular. Şekil 7-4 bu işlemi gösterir.

![TokenAuth](./media/image7-4.png)

**Şekil 7-4.** Web API 'Leri için belirteç tabanlı kimlik doğrulaması.

Kendi kimlik doğrulama hizmetinizi oluşturabilir, Azure AD ve OAuth ile tümleştirilebilir veya [IdentityServer](https://github.com/IdentityServer)gibi açık kaynaklı bir aracı kullanarak bir hizmet uygulayabilirsiniz.

JWT belirteçleri Kullanıcı hakkında, istemci veya sunucu üzerinde okunabilen talepler ekleyebilir. Bir JWT belirtecinin içeriğini görüntülemek için [JWT.io](https://jwt.io/) gibi bir araç kullanabilirsiniz. İçerikleri kolayca okunduğundan, gizli verileri JTW belirteçlerinde parolalar veya anahtarlar gibi depolamayın.

SPA belirteçlerini SPA veya Blazor WebAssembly uygulamalarla kullanırken, belirteci istemcide bir yere depolamanız ve sonra her API çağrısına eklemeniz gerekir. Aşağıdaki kodun gösterdiği gibi bu etkinlik genellikle üst bilgi olarak yapılır:

```csharp
// AuthService.cs in BlazorAdmin project of eShopOnWeb
private async Task SetAuthorizationHeader()
{
    var token = await GetToken();
    _httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);
}
```

Yukarıdaki yöntemi çağırdıktan sonra, ile yapılan isteklere `_httpClient` isteğin üst bilgilerine gömülü ve sunucu tarafı API 'sinin istek için kimlik doğrulaması yapmasına ve yetkilendirilemez.

#### <a name="custom-security"></a>Özel Güvenlik

Özellikle şifreleme, Kullanıcı üyeliği veya belirteç oluşturma sisteminin "kendi kendine alınması" konusunda dikkatli olun. Çok sayıda ticari ve açık kaynaklı alternatif vardır ve bu, bir özel uygulamadan daha iyi güvenliğe sahip olur.

> ### <a name="references--security"></a>Başvurular – güvenlik
>
> - **Güvenlik belgelerine genel bakış**\
>   <https://docs.microsoft.com/aspnet/core/security/>
> - **ASP.NET Core uygulamasında SSL zorlama**\
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Kimliğe giriş**\
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Yetkilendirmeye giriş**\
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Azure App Service API Apps için kimlik doğrulaması ve yetkilendirme**\
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **Kimlik sunucusu**\
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>İstemci iletişimi

Web API 'Leri aracılığıyla sayfalara hizmet vermeye ve veri isteklerine yanıt vermeye ek olarak, ASP.NET Core uygulamalar doğrudan bağlantılı istemcilerle iletişim kurabilir. Bu giden iletişim, en yaygın WebSockets olmak üzere çeşitli taşıma teknolojileri kullanabilir. ASP.NET Core SignalR, uygulamalarınıza gerçek zamanlı sunucudan istemciye iletişim işlevselliği eklemeyi basit hale getiren bir kitaplıktır. SignalR, WebSockets dahil olmak üzere çeşitli taşıma teknolojilerini destekler ve geliştiriciden birçok uygulama ayrıntılarını soyutlar.

WebSockets doğrudan veya diğer tekniklerin kullanılması halinde gerçek zamanlı istemci iletişimi, çeşitli uygulama senaryolarında yararlı olur. Bazı örnekler:

- Canlı sohbet odası uygulamaları

- Uygulamaları izleme

- İş ilerleme durumu güncelleştirmeleri

- Bildirimler

- Etkileşimli form uygulamaları

Uygulamalarınıza istemci iletişimi oluştururken genellikle iki bileşen vardır:

- Sunucu tarafı bağlantı Yöneticisi (SignalR hub, WebSocketManager WebSocketHandler)

- İstemci tarafı kitaplığı

İstemciler tarayıcılarla sınırlı değildir: mobil uygulamalar, konsol uygulamaları ve diğer yerel uygulamalar, SignalR/WebSockets kullanarak da iletişim kurabilir. Aşağıdaki basit program, bir sohbet uygulamasına gönderilen tüm içeriği bir WebSocketManager örnek uygulamasının bir parçası olarak konsola bildirir:

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>
        {
            Console.WriteLine($"{arguments[0]} said: {arguments[1]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }

    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }

    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
}
```

Uygulamalarınızın istemci uygulamalarıyla doğrudan iletişim kurmasına dikkat edin ve gerçek zamanlı iletişimin uygulamanızın kullanıcı deneyimini iyileştirip geliştirmeyeceğini göz önünde bulundurun.

> ### <a name="references--client-communication"></a>Başvurular – Istemci Iletişimi
>
> - **ASP.NET Core SignalR**\
>   <https://github.com/dotnet/aspnetcore/tree/main/src/SignalR>
> - **WebSocket Yöneticisi**\
>   <https://github.com/radu-matei/websocket-manager>

## <a name="domain-driven-design--should-you-apply-it"></a>Etki alanı odaklı tasarım – uygulamanız gerekir mi?

Domain-Driven tasarımı (DDD), _iş etki alanı_ üzerinde odaklanan bir yazılım oluşturmaya yönelik çevik bir yaklaşımdır. Gerçek dünya sisteminin nasıl çalıştığı geliştiricilerle ilişkilendirilebilen iş etki alanı uzmanlarındaki iletişim ve etkileşime yönelik ağır bir vurgu koyar. Örneğin, hisse senedi ilgilenen bir sistem oluşturuyorsanız, etki alanı uzmanı deneyimli bir hisse senedi Aracısı olabilir. DDD, büyük ve karmaşık iş sorunlarına yönelik olarak tasarlanmıştır ve genellikle daha küçük, daha basit uygulamalar için uygun değildir. bu da, etki alanının anlaşılmasından ve modellenmesi için yatırım yapın.

Bir DDD yaklaşımına göre yazılım oluştururken ekibiniz (Teknik olmayan hissedarlar ve katkıda bulunanlar dahil), sorun alanı için bir _ubititous dili_ geliştirmelidir. Diğer bir deyişle, modellenen gerçek dünya kavramı, yazılım eşdeğeri ve kavramı kalıcı hale getirmek için mevcut olabilecek tüm yapılar için aynı terminoloji kullanılmalıdır (örneğin, veritabanı tabloları). Bu nedenle, ubititous dilinde açıklanan kavramlar, _etki alanı modelinizin_ temelini oluşturmalıdır.

Etki alanı modeliniz, sistemin davranışını temsil eden birbirleriyle etkileşim kuran nesneler içerir. Bu nesneler aşağıdaki kategorilere ayrılabilir:

- [Varlıklar](https://deviq.com/entity/), bir kimlik iş parçacığına sahip nesneleri temsil eder. Varlıklar genellikle daha sonra alınabilebilecekleri bir anahtarla kalıcı olarak depolanır.

- Birim olarak kalıcı olması gereken nesne gruplarını temsil eden [toplamalar](https://deviq.com/aggregate-pattern/).

- [Değer nesneleri](https://deviq.com/value-object/), özellik değerlerinin toplamının temel alınarak karşılaştırılabilen kavramları temsil eder. Örneğin, bir başlangıç ve bitiş tarihinden oluşan Terterange.

- Sistem içindeki diğer bölümleri ilgilendiren işlemleri temsil eden [etki alanı olayları](https://martinfowler.com/eaaDev/DomainEvent.html).

DDD etki alanı modeli, model içerisindeki karmaşık davranışı kapsüllemelidir. Varlıklar, özellikle de yalnızca özellik koleksiyonları olmamalıdır. Etki alanı modelinde davranış olmadığında ve yalnızca sistemin durumunu temsil ettiğinde, bu, DDD 'da istenmeyen bir [anemik modeli](https://deviq.com/anemic-model/)olarak kabul edilir.

Bu model türlerine ek olarak, DDD genellikle çeşitli desenler kullanır:

- [Depolama](https://deviq.com/repository-pattern/), kalıcılık ayrıntılarını soyutlayan.

- Karmaşık nesne oluşturmayı kapsüllemek için [fabrika](https://en.wikipedia.org/wiki/Factory_method_pattern).

- Karmaşık davranışı ve/veya altyapı uygulama ayrıntılarını kapsüllemek için [Hizmetler](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/).

- [Komutu](https://en.wikipedia.org/wiki/Command_pattern), komut veren komutları ve komutun kendisini yürütmek için.

- Sorgu ayrıntılarını kapsüllemek için [belirtimi](https://deviq.com/specification-pattern/).

DDD Ayrıca, daha önce ele alınan temiz mimarinin kullanımını önerir. böylece, birim testleri kullanılarak kolayca doğrulanabilen, gevşek bir kapsülleme, kapsülleme ve kod sağlar.

### <a name="when-should-you-apply-ddd"></a>DDD ne zaman uygulanır?

DDD, önemli iş (yalnızca teknik değil) karmaşıklığa sahip büyük uygulamalar için uygundur. Uygulamanın etki alanı uzmanları hakkında bilgi sahibi olması gerekir. Veri depolarından çeşitli kayıtların geçerli durumunu depolamanın ve almanın ötesinde iş kurallarını ve etkileşimleri temsil eden etki alanı modelinin kendisinde önemli bir davranış olması gerekir.

### <a name="when-shouldnt-you-apply-ddd"></a>DDD ne zaman uygulamanız gerekir

DDD, modelleme, mimari ve iletişim için, aslında yalnızca CRUD (oluşturma/okuma/güncelleştirme/silme) olan daha küçük uygulamalar veya uygulamalar için gerekmeyebilir. Uygulamanızı DDD ' dan sonra yaklaşımınızı tercih ediyorsanız, ancak etki alanınızı hiçbir davranış olmadan bir anemik modeli olduğunu fark ederseniz, yaklaşımınızı yeniden düşünmek zorunda kalabilirsiniz. Uygulamanız DDD gerektirebilir veya uygulamanızın, veritabanınız veya Kullanıcı arabiriminiz yerine etki alanı modelinde iş mantığını kapsüllemek üzere yeniden düzenlenmesi için yardıma ihtiyacınız olabilir.

Karma yaklaşım yalnızca, uygulamanın işlem veya daha fazla karmaşık alanı için DDD, ancak uygulamanın daha basit CRUD veya salt okunurdur. Örneğin, bir raporu görüntüleyecek veya bir Pano için verileri görselleştirmeye yönelik verileri sorguladığınız takdirde bir toplamanın kısıtlamalarına gerek yoktur. Bu tür gereksinimlere yönelik ayrı, daha basit bir okuma modeline sahip olmak mükemmel bir şekilde kabul edilebilir.

> ### <a name="references--domain-driven-design"></a>Başvurular – Domain-Driven tasarımı
>
> - **Düz Ingilizce (StackOverflow yanıtı)**\
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Dağıtım

ASP.NET Core uygulamanızın nerede barındırıldığından bağımsız olarak dağıtımı sürecinde birkaç adım vardır. İlk adım, CLI komutu kullanılarak yapılabilecek şekilde uygulamayı yayımlamaktır `dotnet publish` . Bu adım, uygulamayı derler ve uygulamayı belirlenmiş bir klasöre çalıştırmak için gereken tüm dosyaları yerleştirir. Visual Studio 'dan dağıtırken, bu adım sizin için otomatik olarak gerçekleştirilir. Yayımla klasörü, uygulama ve bağımlılıkları için. exe ve. dll dosyalarını içerir. Bağımsız bir uygulama de .NET çalışma zamanının bir sürümünü içerir. ASP.NET Core uygulamalar yapılandırma dosyaları, statik istemci varlıkları ve MVC görünümlerini de içerecektir.

ASP.NET Core uygulamalar, uygulama (veya sunucu) kilitlenirse sunucu önyüklendiğinde ve yeniden başlatıldığında başlatılmış olması gereken konsol uygulamalardır. İşlem Yöneticisi, bu işlemi otomatikleştirmek için kullanılabilir. ASP.NET Core için en yaygın işlem yöneticileri, Linux ve IIS ya da Windows hizmetinde Windows hizmetinde NGINX ve Apache 'tir.

ASP.NET Core uygulamalar, bir işlem yöneticisi 'ne ek olarak ters proxy sunucusu kullanabilir. Ters proxy sunucusu, Internet 'ten gelen HTTP isteklerini alır ve bazı ön işleme sonrasında Kestrel 'e iletir. Ters proxy sunucuları, uygulama için bir güvenlik katmanı sağlar. Kestrel aynı bağlantı noktasında birden fazla uygulamanın barındırılmasını desteklemez, bu nedenle konak üstbilgileri gibi teknikler aynı bağlantı noktasında ve IP adresinde birden çok uygulamanın barındırılmasına olanak tanımak için kullanılamaz.

![Kestrel to Internet](./media/image7-5.png)

**Şekil 7-5**. Bir ters proxy sunucusu arkasında Kestrel içinde barındırılan ASP.NET

Geriye doğru bir proxy 'nin, SSL/HTTPS kullanarak birden çok uygulamayı güvenli hale getirmek için yararlı olabilecek başka bir senaryo. Bu durumda, yalnızca ters proxy 'nin SSL yapılandırması gerekir. Şekil 7-6 ' de gösterildiği gibi, ters proxy sunucusu ve Kestrel arasındaki iletişim HTTP üzerinden gerçekleşmeyebilir.

![ASP.NET, HTTPS ile güvenli bir ters proxy sunucusu arkasında barındırılan](./media/image7-6.png)

**Şekil 7-6**. ASP.NET, HTTPS ile güvenli bir ters proxy sunucusu arkasında barındırılan

Giderek popüler bir yaklaşım, ASP.NET Core uygulamanızı bir Docker kapsayıcısında barındırırken, daha sonra yerel olarak barındırılabilir veya bulut tabanlı barındırma için Azure 'a dağıtılabilir. Docker kapsayıcısı, Kestrel üzerinde çalışan uygulama kodunuzu içerebilir ve yukarıda gösterildiği gibi bir ters proxy sunucusunun arkasında dağıtılır.

Uygulamanızı Azure 'da barındırıyorsanız, çeşitli hizmetler sağlamak için adanmış bir Sanal Gereç olarak Microsoft Azure Application Gateway kullanabilirsiniz. Tek tek uygulamalar için ters proxy olarak davranmaya ek olarak, Application Gateway aşağıdaki özellikleri de sunabilir:

- HTTP yük dengelemesi

- SSL boşaltması (yalnızca Internet 'e SSL)

- Uçtan uca SSL

- Çoklu site yönlendirme (tek bir Application Gateway en fazla 20 site birleştirme)

- Web uygulaması güvenlik duvarı

- WebSocket desteği

- Gelişmiş Tanılamalar

_[Bölüm 10](development-process-for-azure.md)' da Azure dağıtım seçenekleri hakkında daha fazla bilgi edinin._

> ### <a name="references--deployment"></a>Başvurular – dağıtım
>
> - **Barındırma ve dağıtıma genel bakış**\
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Ters ara sunucu ile Kestrel ne zaman kullanılır?**\
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Docker 'da uygulamaları ASP.NET Core barındırma**\
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Azure Application Gateway 'ye giriş**\
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Önceki](common-client-side-web-technologies.md) 
> [Sonraki](work-with-data-in-asp-net-core-apps.md)
