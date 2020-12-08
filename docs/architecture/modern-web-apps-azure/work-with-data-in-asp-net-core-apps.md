---
title: ASP.NET Core uygulamalarda verilerle çalışma
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın ASP.NET Core uygulamalarında verilerle çalışma
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
no-loc:
- Blazor
- WebAssembly
ms.openlocfilehash: 9d85d700ecb8d6cbe7afd8d3c724f499ee5fed71
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851262"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="68953-103">ASP.NET Core uygulamalarında verilerle çalışma</span><span class="sxs-lookup"><span data-stu-id="68953-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="68953-104">"Veriler, en çok değerli bir şeydir ve sistemlerden daha uzun süre sonra kalır."</span><span class="sxs-lookup"><span data-stu-id="68953-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="68953-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="68953-105">Tim Berners-Lee</span></span>

<span data-ttu-id="68953-106">Veri erişimi, neredeyse tüm yazılım uygulamalarının önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="68953-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="68953-107">ASP.NET Core, Entity Framework Core (ve Entity Framework 6 de) dahil olmak üzere çeşitli veri erişim seçeneklerini destekler ve tüm .NET veri erişim çerçevesiyle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="68953-108">Hangi veri erişimi çerçevesinin kullanılacağı seçimi uygulamanın ihtiyaçlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="68953-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="68953-109">Bu seçeneklerin ApplicationCore ve UI projelerinden soyutlanmasıdır ve altyapıdaki uygulama ayrıntılarının kapsüllenmesi, gevşek olarak bağlanmış, test edilebilir yazılımlar üretmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="68953-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="68953-110">Entity Framework Core (ilişkisel veritabanları için)</span><span class="sxs-lookup"><span data-stu-id="68953-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="68953-111">İlişkisel verilerle çalışması gereken yeni bir ASP.NET Core uygulaması yazıyorsanız, uygulamanızın verilerine erişmesi için önerilen yol Entity Framework Core (EF Core).</span><span class="sxs-lookup"><span data-stu-id="68953-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="68953-112">EF Core, .NET geliştiricilerin nesneleri bir veri kaynağından ve veritabanından kalıcı hale getirebilmesine olanak tanıyan bir nesne ilişkisel Eşleyici (O/RM).</span><span class="sxs-lookup"><span data-stu-id="68953-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="68953-113">Geliştiricilerin genellikle yazması gereken çoğu veri erişim kodu gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="68953-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="68953-114">ASP.NET Core gibi EF Core, modüler platformlar arası uygulamaları desteklemek için baştan sona yeniden yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="68953-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="68953-115">Bunu uygulamanıza bir NuGet paketi olarak ekleyin, başlangıçta yapılandırın ve ihtiyacınız olduğunda bağımlılık ekleme yoluyla isteyin.</span><span class="sxs-lookup"><span data-stu-id="68953-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="68953-116">Bir SQL Server veritabanıyla EF Core kullanmak için aşağıdaki DotNet CLı komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="68953-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="68953-117">Test için bir InMemory veri kaynağına yönelik destek eklemek için:</span><span class="sxs-lookup"><span data-stu-id="68953-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="68953-118">DbContext</span><span class="sxs-lookup"><span data-stu-id="68953-118">The DbContext</span></span>

<span data-ttu-id="68953-119">EF Core çalışmak için bir alt sınıfının olması gerekir <xref:Microsoft.EntityFrameworkCore.DbContext> .</span><span class="sxs-lookup"><span data-stu-id="68953-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="68953-120">Bu sınıf, uygulamanızın birlikte çalıştığı varlıkların koleksiyonlarını temsil eden özellikleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="68953-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="68953-121">EShopOnWeb örneği, öğeler, markalar ve türler için koleksiyonlarla bir CatalogContext içerir:</span><span class="sxs-lookup"><span data-stu-id="68953-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="68953-122">DbContext 'in DbContextOptions kabul eden bir oluşturucusu olmalıdır ve bu bağımsız değişkeni temel DbContext oluşturucusuna geçirin.</span><span class="sxs-lookup"><span data-stu-id="68953-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="68953-123">Uygulamanızda yalnızca bir DbContext varsa, DbContextOptions 'ın bir örneğini geçirebilirsiniz, ancak birden fazla tane varsa, \<T> DbContext türünü genel parametre olarak geçirerek genel dbcontextoptions türünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="68953-123">If you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="68953-124">EF Core yapılandırma</span><span class="sxs-lookup"><span data-stu-id="68953-124">Configuring EF Core</span></span>

<span data-ttu-id="68953-125">ASP.NET Core uygulamanızda, genellikle ConfigureServices yönteminizin EF Core yapılandıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="68953-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="68953-126">EF Core, yapılandırmasını kolaylaştırmak için çeşitli faydalı uzantı yöntemlerini destekleyen bir DbContextOptionsBuilder kullanır.</span><span class="sxs-lookup"><span data-stu-id="68953-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="68953-127">Yapılandırmada tanımlı bir bağlantı dizesiyle SQL Server bir veritabanı kullanmak üzere CatalogContext yapılandırmak için, ConfigureServices 'e aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="68953-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="68953-128">Bellek içi veritabanını kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="68953-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="68953-129">EF Core yükledikten sonra bir DbContext alt türü oluşturdunuz ve bunu ConfigureServices içinde yapılandırdıktan sonra, EF Core kullanmaya hazırsınızdır.</span><span class="sxs-lookup"><span data-stu-id="68953-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="68953-130">DbContext türünün bir örneğini, ihtiyacı olan herhangi bir hizmette isteyebilir ve yalnızca bir koleksiyonda olmaları gibi LINQ kullanarak kalıcı varlıklarınız ile çalışmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="68953-131">EF Core, verileri depolamak ve almak için LINQ ifadelerinizi SQL sorgularına çevirme işi yapar.</span><span class="sxs-lookup"><span data-stu-id="68953-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="68953-132">Bir günlükçü yapılandırarak EF Core sorguları, Şekil 8-1 ' de gösterildiği gibi, düzeyinin en az bilgi olarak ayarlandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![EF Core sorguları konsola kaydetme](./media/image8-1.png)

<span data-ttu-id="68953-134">**Şekil 8-1**.</span><span class="sxs-lookup"><span data-stu-id="68953-134">**Figure 8-1**.</span></span> <span data-ttu-id="68953-135">EF Core sorguları konsola kaydetme</span><span class="sxs-lookup"><span data-stu-id="68953-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="68953-136">Verileri getirme ve depolama</span><span class="sxs-lookup"><span data-stu-id="68953-136">Fetching and storing Data</span></span>

<span data-ttu-id="68953-137">EF Core verileri almak için, uygun özelliğe erişir ve sonucu filtrelemek için LINQ 'yi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="68953-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="68953-138">Ayrıca, bir türden diğerine sonucu dönüştürmek için de LINQ 'ı projeksiyonu yapmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="68953-139">Aşağıdaki örnek, adlandırma markalarını, ada göre sıralanmış, etkin özelliklerine göre filtrelenmiş ve bir SelectListItem türü üzerine yansıtılan bir şekilde alır:</span><span class="sxs-lookup"><span data-stu-id="68953-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="68953-140">Sorguyu hemen yürütmek için, yukarıdaki örnekte ToListAsync çağrısını eklemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="68953-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="68953-141">Aksi takdirde, ifade, \<SelectListItem> numaralandırılana kadar yürütülemeyecek bir IQueryable brandItems öğesine atayacaktır.</span><span class="sxs-lookup"><span data-stu-id="68953-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="68953-142">Metotlardan IQueryable sonuçlarının döndürülmesinin olumlu ve olumsuz yönleri vardır.</span><span class="sxs-lookup"><span data-stu-id="68953-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="68953-143">Sorgu EF Core daha fazla değiştirilecek şekilde oluşturulmasına izin verir, ancak sorguya EF Core çevrilemediği bir işleme eklenirse, yalnızca çalışma zamanında oluşan hatalara de yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="68953-144">Veri erişimi gerçekleştiren yönteme filtre geçirmek genellikle daha güvenlidir ve sonuç olarak bir bellek içi koleksiyon (örneğin, liste) geri döndürür \<T> .</span><span class="sxs-lookup"><span data-stu-id="68953-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="68953-145">EF Core, kalıcılığı yaptığı varlıklarda yapılan değişiklikleri izler.</span><span class="sxs-lookup"><span data-stu-id="68953-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="68953-146">İzlenen bir varlıktaki değişiklikleri kaydetmek için, yalnızca DbContext üzerinde SaveChanges metodunu çağırın, bu da varlığı getirmek için kullanılan DbContext örneğinin aynı olduğundan emin olur.</span><span class="sxs-lookup"><span data-stu-id="68953-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="68953-147">Varlık ekleme ve kaldırma, doğrudan uygun DbSet özelliğinde, veritabanı komutlarını yürütmek için SaveChanges çağrısı ile birlikte yapılır.</span><span class="sxs-lookup"><span data-stu-id="68953-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="68953-148">Aşağıdaki örnek, kalıcılığı ekleme, güncelleştirme ve kalıcılığın kaldırılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="68953-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="68953-149">EF Core getirme ve kaydetme için hem zaman uyumlu hem de zaman uyumsuz yöntemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="68953-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="68953-150">Web uygulamalarında, zaman uyumsuz yöntemlerle zaman uyumsuz/await deseninin kullanılması önerilir. bu sayede, veri erişim işlemlerinin tamamlanmasını beklerken Web sunucusu iş parçacıklarının engellenmez.</span><span class="sxs-lookup"><span data-stu-id="68953-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="68953-151">İlgili verileri getirme</span><span class="sxs-lookup"><span data-stu-id="68953-151">Fetching related data</span></span>

<span data-ttu-id="68953-152">EF Core varlıkları aldığında, veritabanında bu varlıkla doğrudan depolanan tüm özellikleri doldurur.</span><span class="sxs-lookup"><span data-stu-id="68953-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="68953-153">İlgili varlıkların listeleri gibi gezinti özellikleri doldurulmaz ve değerleri null olarak ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="68953-154">Bu işlem, isteklerin hızlı bir şekilde işlenmesi ve yanıtları verimli bir şekilde döndürmesi gereken Web uygulamaları için özellikle önemli olan EF Core gerekenden daha fazla veri getirmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="68953-154">This process ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="68953-155">_Ekip yükleme_ kullanarak bir varlıkla ilişkiler dahil etmek için, özelliği gösterildiği gibi, sorgu üzerinde Include Extension metodunu kullanarak belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68953-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="68953-156">Birden çok ilişki ekleyebilirsiniz ve Thenınclude kullanarak alt ilişkiler de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-156">You can include multiple relationships, and you can also include subrelationships using ThenInclude.</span></span> <span data-ttu-id="68953-157">EF Core, sonuçta elde edilen varlık kümesini almak için tek bir sorgu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="68953-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="68953-158">Alternatif olarak, gezinti özelliklerinin gezinti özelliklerini bir '. ' geçirerek dahil edebilirsiniz. `.Include()` uzantı yöntemine ayrılmış dize, örneğin:</span><span class="sxs-lookup"><span data-stu-id="68953-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include("Items.Products")
```

<span data-ttu-id="68953-159">Bir belirtim, filtreleme mantığının yanı sıra döndürülecek verilerin şeklini belirtebilir ve bu da doldurulacak özellikler de dahildir.</span><span class="sxs-lookup"><span data-stu-id="68953-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="68953-160">EShopOnWeb örneği, belirtim içinde bilgi yüklemeyi kapsayan çeşitli özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="68953-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="68953-161">Sorgunun bir parçası olarak belirtiminin nasıl kullanıldığını görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68953-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="68953-162">İlgili verileri yüklemeye yönelik başka bir seçenek de _açık yükleme_ kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="68953-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="68953-163">Açık yükleme, daha önce alınmış bir varlığa ek veri yüklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68953-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="68953-164">Bu yaklaşım veritabanına ayrı bir istek içerdiğinden Web uygulamaları için önerilmez, bu da istek başına yapılan veritabanı gidiş dönüş sayısını en aza indirmelidir.</span><span class="sxs-lookup"><span data-stu-id="68953-164">Since this approach involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="68953-165">_Yavaş yükleme_ , uygulama tarafından başvurulduğundan ilgili verileri otomatik olarak yükleyen bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="68953-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="68953-166">EF Core sürüm 2,1 ' de geç yükleme desteği eklendi.</span><span class="sxs-lookup"><span data-stu-id="68953-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="68953-167">Geç yükleme varsayılan olarak etkin değildir ve yüklemesi gerekir `Microsoft.EntityFrameworkCore.Proxies` .</span><span class="sxs-lookup"><span data-stu-id="68953-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="68953-168">Açık yüklemede olduğu gibi, kullanımı genellikle Web uygulamaları için devre dışı bırakılmalıdır, çünkü kullanımı her Web isteği içinde ek veritabanı sorgularının oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="68953-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="68953-169">Ne yazık ki, yavaş yükleme tarafından tahakkuk eden ek yük, gecikme süresi küçük olduğunda ve genellikle test için kullanılan veri kümelerinin küçük olması durumunda geliştirme sırasında açıklanmamasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="68953-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when the latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="68953-170">Ancak üretimde, daha fazla Kullanıcı, daha fazla veri ve daha fazla gecikmeyle, ek veritabanı istekleri genellikle yavaş yüklemeyi yoğun bir şekilde kullanan Web uygulamaları için düşük performansa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="68953-171">Web uygulamalarında yavaş yükleme varlıklarının olmaması</span><span class="sxs-lookup"><span data-stu-id="68953-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="68953-172">Verileri kapsülleme</span><span class="sxs-lookup"><span data-stu-id="68953-172">Encapsulating data</span></span>

<span data-ttu-id="68953-173">EF Core, modelinizin durumunu doğru bir şekilde kapsüllemek için birkaç özelliği destekler.</span><span class="sxs-lookup"><span data-stu-id="68953-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="68953-174">Etki alanı modellerinde yaygın bir sorun, koleksiyon gezinti özelliklerini herkese açık olarak erişilebilen liste türleri olarak kullanıma sunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="68953-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="68953-175">Bu sorun, tüm ortak çalışmalardan bu koleksiyon türlerinin içeriğini işlemesini sağlar. Bu, koleksiyon ile ilgili önemli iş kurallarını atlayarak büyük olasılıkla nesneyi geçersiz bir durumda bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-175">This problem allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="68953-176">Bu soruna yönelik çözüm, ilgili koleksiyonlara salt okuma erişimi sunmak ve bu örnekte olduğu gibi istemcilerin bunları işleyebilecekleri yolları tanımlamaya yönelik yöntemleri açıkça sağlamaktır:</span><span class="sxs-lookup"><span data-stu-id="68953-176">The solution to this problem is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

<span data-ttu-id="68953-177">Bu varlık türü ortak `List` veya `ICollection` özellik sunmaz, bunun yerine `IReadOnlyCollection` temel alınan liste türünü sarmalayan bir tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="68953-177">This entity type doesn't expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="68953-178">Bu model kullanılırken, şu şekilde bir yedekleme alanı kullanacağınızı Entity Framework Core belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68953-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="68953-179">Etki alanı modelinizi iyileştirebilmeniz için bir başka yol da, kimlik olmayan türler için değer nesnelerinin kullanımı ve yalnızca özelliklerine göre ayırt edilebilir.</span><span class="sxs-lookup"><span data-stu-id="68953-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="68953-180">Bu tür türler, varlıklarınızın özellikleri olarak kullanılması, mantığın ait olduğu değer nesnesine özgü mantığı tutmaya yardımcı olabilir ve aynı kavramı kullanan birden fazla varlık arasında yinelenen mantığdan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="68953-181">Entity Framework Core, türü sahipli bir varlık olarak yapılandırarak aynı tablodaki değer nesnelerini sahip oldukları varlıkla kalıcı hale getirebilirsiniz, örneğin:</span><span class="sxs-lookup"><span data-stu-id="68953-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="68953-182">Bu örnekte, `ShipToAddress` özelliği türündedir `Address` .</span><span class="sxs-lookup"><span data-stu-id="68953-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="68953-183">`Address` , ve gibi çeşitli özelliklere sahip bir değer nesnesidir `Street` `City` .</span><span class="sxs-lookup"><span data-stu-id="68953-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="68953-184">EF Core, `Order` nesneyi özelliği başına tek sütunlu `Address` , her sütun adının özelliğin adıyla sonuna ekleyerek tablosuna eşler.</span><span class="sxs-lookup"><span data-stu-id="68953-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="68953-185">Bu örnekte, `Order` tablosu ve gibi sütunları içerir `ShipToAddress_Street` `ShipToAddress_City` .</span><span class="sxs-lookup"><span data-stu-id="68953-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span> <span data-ttu-id="68953-186">İsterseniz, sahip olunan türleri ayrı tablolarda depolamak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="68953-186">It's also possible to store owned types in separate tables, if desired.</span></span>

<span data-ttu-id="68953-187">[EF Core ' de sahip olan varlık desteği](/ef/core/modeling/owned-entities)hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="68953-187">Learn more about owned [entity support in EF Core](/ef/core/modeling/owned-entities).</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="68953-188">Dayanıklı bağlantılar</span><span class="sxs-lookup"><span data-stu-id="68953-188">Resilient connections</span></span>

<span data-ttu-id="68953-189">SQL veritabanları gibi dış kaynaklar zaman zaman kullanılabilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-189">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="68953-190">Geçici kullanım durumunda uygulamalar, bir özel durum oluşmasını önlemek için yeniden deneme mantığını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-190">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="68953-191">Bu teknik genellikle _bağlantı dayanıklılığı_ olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="68953-191">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="68953-192">En fazla yeniden deneme sayısına ulaşılana kadar, bir üstel bekleme süresi ile yeniden denemeye çalışırken, üstel geri alma tekniğinden [kendi yeniden denelerinizi](/azure/architecture/patterns/retry) uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-192">You can implement your [own retry with exponential backoff](/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="68953-193">Bu teknik, bulut kaynaklarının kısa süreler boyunca zaman zaman kullanılamamasına neden olabilir ve bu da bazı isteklerin başarısızlığından kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-193">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in the failure of some requests.</span></span>

<span data-ttu-id="68953-194">Azure SQL DB için Entity Framework Core, iç veritabanı bağlantı dayanıklılığı ve yeniden deneme mantığını zaten sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="68953-194">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="68953-195">Ancak dayanıklı EF Core bağlantılarına sahip olmak istiyorsanız her DbContext bağlantısı için Entity Framework yürütme stratejisini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="68953-195">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="68953-196">Örneğin, EF Core bağlantı düzeyindeki aşağıdaki kod, bağlantı başarısız olursa yeniden denenen dayanıklı SQL bağlantılarına izin verir.</span><span class="sxs-lookup"><span data-stu-id="68953-196">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30),
            errorNumbersToAdd: null);
        });
    });
}
//...
```

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="68953-197">BeginTransaction ve birden çok Dbbağlamlarını kullanarak yürütme stratejileri ve açık işlemler</span><span class="sxs-lookup"><span data-stu-id="68953-197">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="68953-198">EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden denenebilir işlemi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="68953-198">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="68953-199">Her bir sorgu ve her SaveChanges çağrısı, geçici bir hata oluşursa bir birim olarak yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="68953-199">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="68953-200">Ancak, kodunuz BeginTransaction kullanarak bir işlem başlatırsa, birim olarak değerlendirilmesi gereken kendi işlem grubunuzu tanımlamanız gerekir; bir hata oluşursa işlem içindeki her şeyin geri alınması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="68953-200">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="68953-201">Bir EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu işlemi yürütmeye çalışırsanız ve içinde birden fazla Dbbağlamdan birkaç SaveChanges eklerseniz, aşağıdaki gibi bir özel durum görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="68953-201">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="68953-202">System. InvalidOperationException: yapılandırılan ' Sqlserverretryingexecutionstrateji ' yürütme stratejisi, Kullanıcı tarafından başlatılan işlemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="68953-202">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="68953-203">İşlemdeki tüm işlemleri yeniden denenebilir bir birim olarak yürütmek için ' DbContext. Database. Createexecutionstrateji () ' tarafından döndürülen yürütme stratejisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="68953-203">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retryable unit.</span></span>

<span data-ttu-id="68953-204">Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68953-204">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="68953-205">Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="68953-205">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="68953-206">Aşağıdaki kod, bu yaklaşımın nasıl uygulanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="68953-206">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy();
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="68953-207">İlk DbContext, \_ catalogcontext ve Ikinci DbContext, \_ ıntegrationeventlogservice nesnesi içindedir.</span><span class="sxs-lookup"><span data-stu-id="68953-207">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="68953-208">Son olarak, yürütme eylemi birden fazla Dbbağlamı ve EF yürütme stratejisi kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="68953-208">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="68953-209">Başvurular – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="68953-209">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="68953-210">**EF Core docs**
>   <https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="68953-210">**EF Core Docs**
<https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="68953-211">**EF Core: Ilgili veriler**
>   <https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="68953-211">**EF Core: Related Data**
<https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="68953-212">**ASPNET uygulamalarında daha yavaş yükleme varlıklarını önleyin**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="68953-212">**Avoid Lazy Loading Entities in ASPNET Applications**
<https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="68953-213">EF Core veya Micro-ORM?</span><span class="sxs-lookup"><span data-stu-id="68953-213">EF Core or micro-ORM?</span></span>

<span data-ttu-id="68953-214">EF Core, kalıcılığı yönetmek için harika bir seçimdir ve çoğu bölüm uygulama geliştiricilerinden veritabanı ayrıntılarını kapsüller, tek seçim değildir.</span><span class="sxs-lookup"><span data-stu-id="68953-214">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn't the only choice.</span></span> <span data-ttu-id="68953-215">Diğer bir popüler açık kaynak alternatifi, mikro-ORM adlı [, yani olarak](https://github.com/StackExchange/Dapper)adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="68953-215">Another popular open-source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="68953-216">Mikro-ORM, nesneleri veri yapılarına eşlemek için hafif ve daha az bir tam özellikli araçtır.</span><span class="sxs-lookup"><span data-stu-id="68953-216">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="68953-217">Paber söz konusu olduğunda, tasarım hedefleri, verileri almak ve güncelleştirmek için kullandığı temeldeki sorguları tamamen kapsüllemek yerine performansa odaklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68953-217">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="68953-218">Geliştiriciden SQL soyut olmadığından, kaber "metal 'ya yakındır" ve geliştiricilerin belirli bir veri erişim işlemi için kullanmak istedikleri tam sorguları yazmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="68953-218">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="68953-219">EF Core, bu iki önemli özelliğe sahiptir ve bu, bunu bir yandan da kendi performans yüklerine ekler.</span><span class="sxs-lookup"><span data-stu-id="68953-219">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="68953-220">İlki LINQ ifadelerinden SQL 'e çevirmesidir.</span><span class="sxs-lookup"><span data-stu-id="68953-220">The first is the translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="68953-221">Bu çeviriler önbelleğe alınır, ancak bunu ilk kez gerçekleştirmede ek yük vardır.</span><span class="sxs-lookup"><span data-stu-id="68953-221">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="68953-222">İkincisi, varlıklarda değişiklik izleme (etkin güncelleştirme deyimlerinin üretilebilmesi için).</span><span class="sxs-lookup"><span data-stu-id="68953-222">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="68953-223">Bu davranış, uzantısı kullanılarak belirli sorgular için kapatılabilir <xref:System.Data.Entity.DbExtensions.AsNoTracking%2A> .</span><span class="sxs-lookup"><span data-stu-id="68953-223">This behavior can be turned off for specific queries by using the <xref:System.Data.Entity.DbExtensions.AsNoTracking%2A> extension.</span></span> <span data-ttu-id="68953-224">EF Core Ayrıca genellikle çok verimli olan ve performans açısından kusursuz bir şekilde kabul edilebilir olan SQL sorguları üretir, ancak yürütülecek kesin sorgu üzerinde iyi denetime ihtiyacınız varsa, EF Core kullanarak özel SQL (veya saklı yordam yürütme) geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-224">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="68953-225">Bu durumda, kaber hala EF Core, ancak biraz daha fazlasını gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="68953-225">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="68953-226">Julie Lerman, Mayıs 2016 MSDN makalesi [kaber, Entity Framework ve hibrit uygulamalarında](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps)bazı performans verileri sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68953-226">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span></span> <span data-ttu-id="68953-227">Çeşitli veri erişim yöntemlerine yönelik ek performans kıyaslama verileri [, kaber sitesinde](https://github.com/StackExchange/Dapper)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-227">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="68953-228">Kaber için sözdiziminin EF Core nasıl değiştiğini görmek için, öğelerin bir listesini almak için aynı yöntemin bu iki sürümünü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="68953-228">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="68953-229">Kaber ile daha karmaşık nesne grafikleri oluşturmanız gerekiyorsa, ilişkili sorguları kendiniz yazmanız gerekir (EF Core gibi bir Içerme eklemek yerine).</span><span class="sxs-lookup"><span data-stu-id="68953-229">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="68953-230">Bu işlevsellik, tek tek satırları birden çok eşlenmiş nesne ile eşlemenizi sağlayan çoklu eşleme adlı bir özellik dahil olmak üzere çeşitli sözdizimleri aracılığıyla desteklenir.</span><span class="sxs-lookup"><span data-stu-id="68953-230">This functionality is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="68953-231">Örneğin, Kullanıcı türünde bir özellik sahibi olan bir sınıf gönderisi verildiğinde, aşağıdaki SQL gerekli verilerin tümünü döndürür:</span><span class="sxs-lookup"><span data-stu-id="68953-231">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="68953-232">Döndürülen her satır hem Kullanıcı hem de veri Gönder ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="68953-232">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="68953-233">Kullanıcı verilerinin, sahibi özelliği aracılığıyla Post verilerine bağlanması gerektiğinden aşağıdaki işlev kullanılır:</span><span class="sxs-lookup"><span data-stu-id="68953-233">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="68953-234">İlişkili kullanıcı verileriyle doldurulmuş bir gönderilerin bir koleksiyonunu döndüren tam kod listesi şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="68953-234">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="68953-235">Paber, daha az kapsülleme sağladığından, geliştiricilerin verilerinin nasıl depolandığı, nasıl verimli bir şekilde sorgulanacağı ve bunu getirmek için daha fazla kod yazabileceği hakkında daha fazla bilgi sahibi olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="68953-235">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="68953-236">Model değiştiğinde, yalnızca yeni bir geçiş (başka bir EF Core özelliği) oluşturmak ve/veya eşleme bilgilerini bir DbContext içinde tek bir yerde güncelleştirmek yerine, etkilenen her sorgunun güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="68953-236">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="68953-237">Bu sorguların derleme zamanı garantisi yoktur, bu nedenle model veya veritabanındaki değişikliklere yanıt olarak çalışma zamanında kesintiye uğrarabilir ve hataları hızla algılamaya daha zor hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="68953-237">These queries have no compile-time guarantees, so they may break at run time in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="68953-238">Bu avantajları için Exchange 'de, kaber son derece hızlı performans sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68953-238">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="68953-239">Çoğu uygulama ve neredeyse tüm uygulamaların birçok bölümü için EF Core, kabul edilebilir performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="68953-239">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="68953-240">Bu nedenle, geliştirici üretkenlik avantajları büyük olasılıkla performans yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="68953-240">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="68953-241">Önbelleğe alma işleminden faydalanabilir sorgular için, gerçek sorgu yalnızca büyük bir yüzde oranında yürütülebilir ve görece küçük sorgu performansı farklılıklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="68953-241">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="68953-242">SQL veya NoSQL</span><span class="sxs-lookup"><span data-stu-id="68953-242">SQL or NoSQL</span></span>

<span data-ttu-id="68953-243">Geleneksel olarak, SQL Server gibi ilişkisel veritabanları kalıcı veri depolama alanı için Market 'e sahiptir, ancak bunlar kullanılabilir tek çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="68953-243">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="68953-244">[MongoDB](https://www.mongodb.com/what-is-mongodb) gibi NoSQL veritabanları, nesneleri depolamanın farklı bir yaklaşımını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68953-244">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="68953-245">Nesneleri tablo ve satırlara eşlemek yerine, diğer bir seçenek de nesne grafiğinin tamamını seri hale getirmek ve sonucu depolar.</span><span class="sxs-lookup"><span data-stu-id="68953-245">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="68953-246">En azından başlangıçta bu yaklaşımın avantajları basitlik ve performanslardır.</span><span class="sxs-lookup"><span data-stu-id="68953-246">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="68953-247">Tek bir seri hale getirilmiş bir nesneyi, bir anahtarla, nesne veritabanından en son alınmasından sonra değişmiş olabilecek ilişkiler ve güncelleştirme ve satırlar içeren çok sayıda tabloya parçalanmaya kıyasla bir anahtarla depolamak daha basittir.</span><span class="sxs-lookup"><span data-stu-id="68953-247">It's simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="68953-248">Benzer şekilde, anahtar tabanlı bir mağazadan tek bir nesneyi getirme ve serisini kaldırma genellikle karmaşık birleşimlerden çok daha hızlı ve daha kolay ve aynı nesneyi ilişkisel bir veritabanından tamamen oluşturmak için gereken birden çok veritabanı sorgusuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="68953-248">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="68953-249">Kilitleri veya işlemleri ya da sabit bir şemanın bulunmaması, NoSQL veritabanlarının çok büyük veri kümelerini destekleyen birçok makine genelinde ölçeklendirilmesine de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68953-249">The lack of locks or transactions or a fixed schema also makes NoSQL databases amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="68953-250">Diğer taraftan, NoSQL veritabanlarının (genellikle çağrıldığı gibi) dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="68953-250">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="68953-251">İlişkisel veritabanları, tutarlılığı zorlamak ve verilerin çoğaltılmasını önlemek için normalleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="68953-251">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="68953-252">Bu yaklaşım, veritabanının toplam boyutunu azaltır ve paylaşılan veriler için güncelleştirmelerin hemen veritabanının tamamında kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="68953-252">This approach reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="68953-253">İlişkisel bir veritabanında, bir ülke/bölge adı değiştirilirse adres kayıtları güncelleştirmeden önce güncelleştirilmesi gerekmeden, bir ülke tablosuna KIMLIĞE göre başvurabilir. bu şekilde,</span><span class="sxs-lookup"><span data-stu-id="68953-253">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="68953-254">Ancak, bir NoSQL veritabanında, adreste ve ilişkili ülkede birçok saklı nesnenin parçası olarak serileştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-254">However, in a NoSQL database, Address, and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="68953-255">Ülke/bölge adına yapılan bir güncelleştirme, bu gibi tüm nesnelerin tek bir satır yerine güncelleştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="68953-255">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="68953-256">İlişkisel veritabanları, yabancı anahtarlar gibi kuralları zorunlu tutarak ilişkisel bütünlüğünden de emin olabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-256">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="68953-257">NoSQL veritabanları genellikle verileri üzerinde böyle kısıtlamalar sunmaz.</span><span class="sxs-lookup"><span data-stu-id="68953-257">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="68953-258">Başka bir karmaşıklık NoSQL veritabanlarının sürümü oluşturma ile uğraşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68953-258">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="68953-259">Bir nesnenin özellikleri değiştiğinde, bu, depolanan eski sürümlerden seri durumdan çıkarılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-259">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="68953-260">Bu nedenle, nesnenin serileştirilmiş (önceki) sürümüne sahip tüm var olan nesnelerin yeni şemasına uymak için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="68953-260">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="68953-261">Bu yaklaşım, ilişkisel bir veritabanından kavramsal olarak farklılık içermez, burada şema değişiklikleri bazen güncelleştirme betikleri veya eşleme güncelleştirmeleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="68953-261">This approach is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="68953-262">Ancak, daha fazla veri yinelemesi olduğundan, değiştirilmesi gereken giriş sayısı NoSQL yaklaşımında genellikle çok daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="68953-262">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="68953-263">Nesnelerin birden çok sürümünü depolamak için NoSQL veritabanlarında, sabit bir şema ilişkisel veritabanları genellikle desteklemez.</span><span class="sxs-lookup"><span data-stu-id="68953-263">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="68953-264">Ancak, bu durumda, uygulama kodunuzun önceki nesne sürümlerinin varlığı için hesap yapması gerekir, ek karmaşıklık ekler.</span><span class="sxs-lookup"><span data-stu-id="68953-264">However, in this case, your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="68953-265">NoSQL veritabanları genellikle, ilişkisel veritabanları üzerinde performans ve ölçeklenebilirlik avantajları olan [ACID](https://en.wikipedia.org/wiki/ACID)'yi zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="68953-265">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="68953-266">Bunlara çok büyük veri kümeleri ve Normalleştirilmemiş tablo yapılarında depolamaya uygun olmayan nesneler için de idealdir.</span><span class="sxs-lookup"><span data-stu-id="68953-266">They're well suited to extremely large datasets and objects that are not well suited to storage in normalized table structures.</span></span> <span data-ttu-id="68953-267">Tek bir uygulamanın hem ilişkisel hem de NoSQL veritabanlarından yararlanması, her yerde en iyi şekilde yararlanamaması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="68953-267">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-cosmos-db"></a><span data-ttu-id="68953-268">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="68953-268">Azure Cosmos DB</span></span>

<span data-ttu-id="68953-269">Azure Cosmos DB, bulut tabanlı şemaya ücretsiz veri depolama sağlayan, tam olarak yönetilen bir NoSQL veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="68953-269">Azure Cosmos DB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="68953-270">Azure Cosmos DB, hızlı ve öngörülebilir performans, yüksek kullanılabilirlik, esnek ölçeklendirme ve küresel dağıtım için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="68953-270">Azure Cosmos DB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="68953-271">Geliştiriciler NoSQL veritabanı olmasına rağmen JSON verilerinde zengin ve tanıdık SQL sorgu yeteneklerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-271">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="68953-272">Azure Cosmos DB içindeki tüm kaynaklar JSON belgeleri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="68953-272">All resources in Azure Cosmos DB are stored as JSON documents.</span></span> <span data-ttu-id="68953-273">Kaynaklar, meta verileri içeren belgeler ve öğe koleksiyonları olan _akışlar_ olan _öğeler_ olarak yönetilir.</span><span class="sxs-lookup"><span data-stu-id="68953-273">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="68953-274">Şekil 8-2 farklı Azure Cosmos DB kaynakları arasındaki ilişkiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="68953-274">Figure 8-2 shows the relationship between different Azure Cosmos DB resources.</span></span>

![Bir NoSQL JSON veritabanı olan Azure Cosmos DB kaynaklar arasındaki hiyerarşik ilişki](./media/image8-2.png)

<span data-ttu-id="68953-276">**Şekil 8-2.**</span><span class="sxs-lookup"><span data-stu-id="68953-276">**Figure 8-2.**</span></span> <span data-ttu-id="68953-277">Kaynak organizasyonunu Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="68953-277">Azure Cosmos DB resource organization.</span></span>

<span data-ttu-id="68953-278">Azure Cosmos DB sorgu dili, JSON belgelerini sorgulamak için basit ancak güçlü bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="68953-278">The Azure Cosmos DB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="68953-279">Dil, ANSI SQL dil bilgisinin bir alt kümesini destekler ve JavaScript nesnesi, dizileri, nesne oluşturması ve işlev çağrısı için derin tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="68953-279">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="68953-280">**Başvurular – Azure Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="68953-280">**References – Azure Cosmos DB**</span></span>

- <span data-ttu-id="68953-281">Azure Cosmos DB giriş <https://docs.microsoft.com/azure/cosmos-db/introduction></span><span class="sxs-lookup"><span data-stu-id="68953-281">Azure Cosmos DB Introduction <https://docs.microsoft.com/azure/cosmos-db/introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="68953-282">Diğer kalıcılık seçenekleri</span><span class="sxs-lookup"><span data-stu-id="68953-282">Other persistence options</span></span>

<span data-ttu-id="68953-283">İlişkisel ve NoSQL depolama seçeneklerine ek olarak ASP.NET Core uygulamalar, çeşitli veri biçimlerini ve dosyalarını bulut tabanlı, ölçeklenebilir bir biçimde depolamak için Azure Storage 'ı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-283">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="68953-284">Azure Storage, büyük miktarlarda ölçeklenebilir hale gelir. bu nedenle, uygulamanız gerektiriyorsa yüzlerce veya terabayta varan miktarda veri depolamayı başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-284">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="68953-285">Azure Storage dört tür veriyi destekler:</span><span class="sxs-lookup"><span data-stu-id="68953-285">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="68953-286">Yapılandırılmamış metin veya ikili depolama için, nesne depolama olarak da adlandırılan BLOB depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="68953-286">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="68953-287">Yapılandırılmış veri kümeleri için satır anahtarları aracılığıyla erişilebilen tablo depolaması.</span><span class="sxs-lookup"><span data-stu-id="68953-287">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="68953-288">Sıradan sıra tabanlı mesajlaşma için kuyruk depolama.</span><span class="sxs-lookup"><span data-stu-id="68953-288">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="68953-289">Azure sanal makineler ve şirket içi uygulamalar arasında paylaşılan dosya erişimi için dosya depolama.</span><span class="sxs-lookup"><span data-stu-id="68953-289">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="68953-290">**Başvurular – Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="68953-290">**References – Azure Storage**</span></span>

- <span data-ttu-id="68953-291">Azure depolama giriş <https://docs.microsoft.com/azure/storage/common/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="68953-291">Azure Storage Introduction <https://docs.microsoft.com/azure/storage/common/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="68953-292">Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="68953-292">Caching</span></span>

<span data-ttu-id="68953-293">Web uygulamalarında, her Web isteği mümkün olan en kısa sürede tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68953-293">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="68953-294">Bu işlevi gerçekleştirmenin bir yolu, sunucunun isteği tamamlaması için yapması gereken dış çağrı sayısını sınırlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="68953-294">One way to achieve this functionality is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="68953-295">Önbelleğe alma işlemi, sunucuda verilerin bir kopyasının depolanmasını (veya verilerin kaynağından daha kolay sorgulanan başka bir veri deposu) içerir.</span><span class="sxs-lookup"><span data-stu-id="68953-295">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="68953-296">Web uygulamaları ve özellikle de non-SPA geleneksel olmayan Web uygulamaları, her istekle birlikte Kullanıcı arabiriminin tamamını oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="68953-296">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="68953-297">Bu yaklaşım sıklıkla, bir Kullanıcı isteğinden bir sonrakine kadar aynı veritabanı sorgularının birçok kez daha fazlasını yapmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="68953-297">This approach frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="68953-298">Çoğu durumda, bu veriler nadiren değişir, bu yüzden sürekli olarak veritabanından isteme nedenidir.</span><span class="sxs-lookup"><span data-stu-id="68953-298">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="68953-299">ASP.NET Core, tüm sayfaların önbelleğe alınması ve daha ayrıntılı önbelleğe alma davranışını destekleyen veri önbelleğe alma işlemleri için yanıt önbelleğe almayı destekler.</span><span class="sxs-lookup"><span data-stu-id="68953-299">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="68953-300">Önbelleğe alma uygularken, kaygıları göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="68953-300">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="68953-301">Veri erişim mantığınızdaki veya Kullanıcı arabiriminizdeki önbelleğe alma mantığını uygulamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="68953-301">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="68953-302">Bunun yerine, önbelleğe almayı kendi sınıflarında kapsülle ve davranışını yönetmek için yapılandırma kullanın.</span><span class="sxs-lookup"><span data-stu-id="68953-302">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="68953-303">Bu yaklaşım açık/kapalı ve tek sorumluluk ilkelerini izler ve uygulamanızda önbelleğe alma işlemini nasıl kullanacağınızı yönetmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="68953-303">This approach follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="68953-304">ASP.NET Core yanıtı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="68953-304">ASP.NET Core response caching</span></span>

<span data-ttu-id="68953-305">ASP.NET Core iki yanıt önbelleği düzeyini destekler.</span><span class="sxs-lookup"><span data-stu-id="68953-305">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="68953-306">İlk düzey sunucu üzerinde herhangi bir şeyi önbelleğe almaz, ancak istemcilerin ve proxy sunucularının yanıtları önbelleğe almasını sağlayan HTTP üstbilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="68953-306">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="68953-307">Bu işlevsellik, bireysel denetleyicilere veya eylemlere ResponseCache özniteliği eklenerek uygulanır:</span><span class="sxs-lookup"><span data-stu-id="68953-307">This functionality is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="68953-308">Önceki örnek, istemciye, sonucu 60 saniyeye kadar önbelleğe almak için, bu üst bilginin yanıta eklenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="68953-308">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="68953-309">Cache-Control: PUBLIC, max-age = 60</span><span class="sxs-lookup"><span data-stu-id="68953-309">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="68953-310">Uygulamaya sunucu tarafı bellek içi önbelleğe alma eklemek için Microsoft. AspNetCore. ResponseCaching NuGet paketine başvurmanız ve ardından yanıt önbelleğe alma ara yazılımını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="68953-310">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="68953-311">Bu ara yazılım hem ConfigureServices hem de başlangıçta yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="68953-311">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="68953-312">Yanıt önbelleğe alma ara yazılımı, özelleştirmeleri, özelleştirebileceğiniz bir dizi koşula göre otomatik olarak önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="68953-312">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="68953-313">Varsayılan olarak, GET veya HEAD yöntemleri aracılığıyla istenen yalnızca 200 (Tamam) yanıt önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="68953-313">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="68953-314">Ayrıca, isteklerin Cache-Control: public üst bilgisine sahip bir yanıtı olmalıdır ve yetkilendirme ya da set-Cookie üst bilgisini içeremez.</span><span class="sxs-lookup"><span data-stu-id="68953-314">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="68953-315">[Yanıt önbelleğe alma ara yazılımı tarafından kullanılan önbelleğe alma koşullarının tüm listesini](/aspnet/core/performance/caching/middleware#conditions-for-caching)görün.</span><span class="sxs-lookup"><span data-stu-id="68953-315">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="68953-316">Verileri önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="68953-316">Data caching</span></span>

<span data-ttu-id="68953-317">(Veya buna ek olarak) tam Web yanıtlarını önbelleğe alma yerine, bireysel veri sorgularının sonuçlarını önbelleğe alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-317">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="68953-318">Bu işlevsellik için, Web sunucusunda bellek önbelleğe alma veya [Dağıtılmış bir önbellek](/aspnet/core/performance/caching/distributed)kullanma ' yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-318">For this functionality, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="68953-319">Bu bölüm, bellek önbelleğe alma işleminde nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="68953-319">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="68953-320">ConfigureServices 'e bellek (veya dağıtılmış) önbelleği desteği eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="68953-320">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="68953-321">Microsoft. Extensions. Caching. Memory NuGet paketini de eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="68953-321">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="68953-322">Hizmeti ekledikten sonra, önbelleğe erişmeniz gereken her yerde, bağımlılık ekleme yoluyla ımemorycache istek duyarsınız.</span><span class="sxs-lookup"><span data-stu-id="68953-322">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="68953-323">Bu örnekte, CachedCatalogService, temel alınan CatalogService uygulamasına erişimi denetleyen (veya davranışı ekleyen) ıconalogservice 'in alternatif bir uygulamasını sağlayarak proxy (veya dekoratör) tasarım modelini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="68953-323">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }

    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }

    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = $"items-{pageIndex}-{itemsPage}-{brandID}-{typeId}";
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }

    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="68953-324">Uygulamayı, hizmetin önbelleğe alınmış sürümünü kullanacak şekilde yapılandırmak için, ancak hala hizmetin oluşturucuda ihtiyacı olan CatalogService örneğini almaya izin vermek için, ConfigureServices 'a aşağıdaki satırları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="68953-324">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following lines in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="68953-325">Bu kodla birlikte, katalog verilerini getirmek için veritabanı çağrıları her istek yerine yalnızca dakikada bir kez yapılır.</span><span class="sxs-lookup"><span data-stu-id="68953-325">With this code in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="68953-326">Site trafiğine bağlı olarak, bu, veritabanına yapılan sorgu sayısı üzerinde önemli bir etkiye ve ana sayfa için o anda bu hizmet tarafından kullanıma sunulan her bir sorguya bağlı olan ortalama sayfa yükleme süresine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-326">Depending on the traffic to the site, this can have a significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="68953-327">Önbelleğe alma işlemi uygulandığında ortaya çıkan bir sorun _eski veriler_ , yani kaynakta değiştirilen veriler, ancak güncel olmayan bir sürüm önbellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="68953-327">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out-of-date version remains in the cache.</span></span> <span data-ttu-id="68953-328">Bu sorunu azaltmanıza yönelik basit bir yol, yoğun bir uygulama için, verilerin uzatılması için sınırlı bir ek avantaj olduğu için küçük önbellek süreleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="68953-328">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is a limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="68953-329">Örneğin, tek bir veritabanı sorgusu oluşturan ve saniyede 10 kez istenen bir sayfa düşünün.</span><span class="sxs-lookup"><span data-stu-id="68953-329">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="68953-330">Bu sayfa bir dakika boyunca önbelleğe alınmışsa, 600 ' dan 1 ' e düşürülmesi için dakika başına yapılan Veritabanı sorgularının sayısına,% 99,8 oranında bir azalmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="68953-330">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="68953-331">Bunun yerine önbellek süresi bir saat yapılırsa, genel azaltma% 99,997 olur, ancak artık eski verilerin olasılığı ve potansiyel yaşı önemli ölçüde artar.</span><span class="sxs-lookup"><span data-stu-id="68953-331">If instead the cache duration was made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="68953-332">Diğer bir yaklaşım, içerdikleri veriler güncelleştirilirken önbellek girişlerini önceden kaldırmak olur.</span><span class="sxs-lookup"><span data-stu-id="68953-332">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="68953-333">Anahtarı biliniyorsa her bir giriş kaldırılabilir:</span><span class="sxs-lookup"><span data-stu-id="68953-333">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="68953-334">Uygulamanız, önbelleğe aldığı girdileri güncelleştirmek için işlevselliği kullanıma sunuyorsa, kodunuzda güncelleştirmeleri gerçekleştiren karşılık gelen önbellek girdilerini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-334">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="68953-335">Bazen belirli bir veri kümesine bağımlı birçok farklı giriş olabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-335">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="68953-336">Bu durumda, CancellationChangeToken kullanarak önbellek girişleri arasında bağımlılıklar oluşturmak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-336">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="68953-337">Bir CancellationChangeToken ile, belirteci iptal ederek birden çok önbellek girdisini bir kez sona erdirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-337">With a CancellationChangeToken, you can expire multiple cache entries at once by canceling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

<span data-ttu-id="68953-338">Önbelleğe alma, veritabanından aynı değerleri tekrar tekrar isteyen web sayfalarının performansını önemli ölçüde iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="68953-338">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="68953-339">Önbelleğe almayı uygulamadan önce veri erişimi ve sayfa performansını ölçdiğinizden emin olun ve yalnızca geliştirme gereksinimi olduğunu gördüğünüz önbelleğe alma işlemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="68953-339">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="68953-340">Önbelleğe alma, Web sunucusu bellek kaynaklarını tüketir ve uygulamanın karmaşıklığını artırır. bu sayede, bu tekniği kullanarak erken iyileştirmemenizi önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="68953-340">Caching consumes web server memory resources and increases the complexity of the application, so it's important you don't prematurely optimize using this technique.</span></span>

## <a name="getting-data-to-no-locblazor-no-locwebassembly-apps"></a><span data-ttu-id="68953-341">Uygulamalara veri alma Blazor WebAssembly</span><span class="sxs-lookup"><span data-stu-id="68953-341">Getting data to Blazor WebAssembly apps</span></span>

<span data-ttu-id="68953-342">Sunucu kullanan uygulamalar oluşturuyorsanız Blazor , bu bölümde şu ana kadar tartışıyoruz gibi Entity Framework ve diğer doğrudan veri erişim teknolojilerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-342">If you're building apps that use Blazor Server, you can use Entity Framework and other direct data access technologies as they've been discussed thus far in this chapter.</span></span> <span data-ttu-id="68953-343">Ancak, Blazor WebAssembly diğer Spa çerçeveleri gibi uygulamalar oluştururken veri erişimi için farklı bir stratejiye ihtiyacınız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="68953-343">However, when building Blazor WebAssembly apps, like other SPA frameworks, you will need a different strategy for data access.</span></span> <span data-ttu-id="68953-344">Genellikle, bu uygulamalar verilere erişir ve Web API uç noktaları aracılığıyla sunucuyla etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="68953-344">Typically, these applications access data and interact with the server through web API endpoints.</span></span>

<span data-ttu-id="68953-345">Gerçekleştirilen veriler ya da işlemler duyarlıysa, [önceki bölümde](develop-asp-net-core-mvc-apps.md) güvenlik bölümünde yer alan ve API 'lerinizi yetkisiz erişime karşı koruduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="68953-345">If the data or operations being performed are sensitive, be sure to review the section on security in the [previous chapter](develop-asp-net-core-mvc-apps.md) and protect your APIs against unauthorized access.</span></span>

<span data-ttu-id="68953-346">Blazor WebAssembly [Eshoponweb Reference uygulamasında](https://github.com/dotnet-architecture/eShopOnWeb), yönetici projesinde bir uygulama örneği bulacaksınız Blazor .</span><span class="sxs-lookup"><span data-stu-id="68953-346">You'll find an example of a Blazor WebAssembly app in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb), in the BlazorAdmin project.</span></span> <span data-ttu-id="68953-347">Bu proje eShopOnWeb Web projesi içinde barındırılır ve Yöneticiler grubundaki kullanıcıların depodaki öğeleri yönetmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="68953-347">This project is hosted within the eShopOnWeb Web project, and allows users in the Administrators group to manage the items in the store.</span></span> <span data-ttu-id="68953-348">Şekil 8-3 ' de uygulamanın ekran görüntüsünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-348">You can see a screenshot of the application in Figure 8-3.</span></span>

![eShopOnWeb Katalog Yöneticisi ekran görüntüsü](./media/image8-3.jpg)

<span data-ttu-id="68953-350">**Şekil 8-3.**</span><span class="sxs-lookup"><span data-stu-id="68953-350">**Figure 8-3.**</span></span> <span data-ttu-id="68953-351">eShopOnWeb Katalog Yöneticisi ekran görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="68953-351">eShopOnWeb Catalog Admin Screenshot.</span></span>

<span data-ttu-id="68953-352">Bir uygulama içindeki Web API 'Lerinden veri getirilirken Blazor WebAssembly , herhangi bir .NET uygulamasında olduğu gibi bir örneğini kullanmanız yeterlidir `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="68953-352">When fetching data from web APIs within a Blazor WebAssembly app, you just use an instance of `HttpClient` as you would in any .NET application.</span></span> <span data-ttu-id="68953-353">Söz konusu temel adımlar, gönderilecek isteği oluşturmaktır (gerekirse, genellikle POST veya PUT istekleri için), isteğin kendisini bekler, durum kodunu doğrular ve yanıtın serisini kaldıramıyor.</span><span class="sxs-lookup"><span data-stu-id="68953-353">The basic steps involved are to create the request to send (if necessary, usually for POST or PUT requests), await the request itself, verify the status code, and deserialize the response.</span></span> <span data-ttu-id="68953-354">Belirli bir API kümesine birçok istek oluşturacaksanız, API 'lerinizi kapsüllemek ve temel adresi merkezi olarak yapılandırmanız iyi bir fikirdir `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="68953-354">If you're going to make many requests to a given set of APIs, it's a good idea to encapsulate your APIs and configure the `HttpClient` base address centrally.</span></span> <span data-ttu-id="68953-355">Bu şekilde, ortamlar arasında bu ayarlardan herhangi birini ayarlamanız gerekirse, değişiklikleri yalnızca bir yerde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-355">This way, if you need to adjust any of these settings between environments, you can make the changes in just one place.</span></span> <span data-ttu-id="68953-356">Bu hizmet için destek eklemeniz gerekir `Program.Main` :</span><span class="sxs-lookup"><span data-stu-id="68953-356">You should add support for this service in your `Program.Main`:</span></span>

```csharp
builder.Services.AddScoped(sp =>
    new HttpClient
    {
        BaseAddress = new Uri(builder.HostEnvironment.BaseAddress)
    });
```

<span data-ttu-id="68953-357">Hizmetlere güvenli bir şekilde erişmeniz gerekiyorsa, güvenli bir belirtece erişmeniz ve `HttpClient` Bu belirteci her istekte bir kimlik doğrulama üst bilgisi olarak geçirmek üzere yapılandırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="68953-357">If you need to access services securely, you should access a secure token and configure the `HttpClient` to pass this token as an Authentication header with every request:</span></span>

```csharp
_httpClient.DefaultRequestHeaders.Authorization =
    new AuthenticationHeaderValue("Bearer", token);
```

<span data-ttu-id="68953-358">Bu etkinlik, uygulamaya eklenmiş olan herhangi bir bileşenden yapılabilir `HttpClient` ve bu, `HttpClient` bir yaşam süresi ile uygulamanın hizmetlerine eklenmemiş olabilir `Transient` .</span><span class="sxs-lookup"><span data-stu-id="68953-358">This activity can be done from any component that has the `HttpClient` injected into it, provided that `HttpClient` wasn't added to the application's services with a `Transient` lifetime.</span></span> <span data-ttu-id="68953-359">Uygulamadaki her başvuru `HttpClient` aynı örneğe başvurur, bu nedenle bir bileşen içindeki üzerinde yapılan her başvuru, uygulamanın tamamı boyunca akar.</span><span class="sxs-lookup"><span data-stu-id="68953-359">Every reference to `HttpClient` in the application references the same instance, so changes to it in one component flow through the entire application.</span></span> <span data-ttu-id="68953-360">Bu kimlik doğrulama denetimini gerçekleştirmek için iyi bir yer (arkasından belirteci belirterek), sitenin ana gezintisi gibi paylaşılan bir bileşende bulunur.</span><span class="sxs-lookup"><span data-stu-id="68953-360">A good place to perform this authentication check (followed by specifying the token) is in a shared component like the main navigation for the site.</span></span> <span data-ttu-id="68953-361">`BlazorAdmin` [Eshoponweb Reference uygulamasındaki](https://github.com/dotnet-architecture/eShopOnWeb)projede bu yaklaşım hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="68953-361">Learn more about this approach in the `BlazorAdmin` project in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

<span data-ttu-id="68953-362">Geleneksel JavaScript 'in avantajlarından birinin avantajlarından biri Blazor WebAssembly de, veri aktarım nesnelerinizin (DTOS) kopyaları eşitlenmiş halde tutmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="68953-362">One benefit of Blazor WebAssembly over traditional JavaScript SPAs is that you don't need to keep to copies of your data transfer objects(DTOs) synchronized.</span></span> <span data-ttu-id="68953-363">Blazor WebAssembly Projeniz ve Web API projeniz, ortak bir paylaşılan projede aynı DTOS 'ı paylaşabilir.</span><span class="sxs-lookup"><span data-stu-id="68953-363">Your Blazor WebAssembly project and your web API project can both share the same DTOs in a common shared project.</span></span> <span data-ttu-id="68953-364">Bu yaklaşım, maça 'Ları geliştirmeye yönelik bir kısmını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="68953-364">This approach eliminates some of the friction involved in developing SPAs.</span></span>

<span data-ttu-id="68953-365">Bir API uç noktasından hızlıca veri almak için yerleşik yardımcı yöntemini kullanabilirsiniz `GetFromJsonAsync` .</span><span class="sxs-lookup"><span data-stu-id="68953-365">To quickly get data from an API endpoint, you can use the built-in helper method, `GetFromJsonAsync`.</span></span> <span data-ttu-id="68953-366">GÖNDERI, PUT, vb. için benzer yöntemler vardır. Aşağıda, bir uygulamada yapılandırılmış bir API kullanarak bir API uç noktasından bir CatalogItem alma gösterilmektedir `HttpClient` Blazor WebAssembly :</span><span class="sxs-lookup"><span data-stu-id="68953-366">There are similar methods for POST, PUT, etc. The following shows how to get a CatalogItem from an API endpoint using a configured `HttpClient` in a Blazor WebAssembly app:</span></span>

```csharp
var item = await _httpClient.GetFromJsonAsync<CatalogItem>($"catalog-items/{id}");
```

<span data-ttu-id="68953-367">İhtiyaç duyduğunuz verilere sahipseniz, genellikle değişiklikleri yerel olarak izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68953-367">Once you have the data you need, you'll typically track changes locally.</span></span> <span data-ttu-id="68953-368">Arka uç veri deposunda güncelleştirmeler yapmak istediğinizde, bu amaçla ek Web API 'Leri çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="68953-368">When you want to make updates to the backend data store, you'll call additional web APIs for this purpose.</span></span>

<span data-ttu-id="68953-369">**Başvurular – Blazor veriler**</span><span class="sxs-lookup"><span data-stu-id="68953-369">**References – Blazor Data**</span></span>

- <span data-ttu-id="68953-370">ASP.NET Core bir Web API 'SI çağırma Blazor</span><span class="sxs-lookup"><span data-stu-id="68953-370">Call a web API from ASP.NET Core Blazor</span></span>
  <https://docs.microsoft.com/aspnet/core/blazor/call-web-api>

>[!div class="step-by-step"]
><span data-ttu-id="68953-371">[Önceki](develop-asp-net-core-mvc-apps.md) 
> [Sonraki](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="68953-371">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
