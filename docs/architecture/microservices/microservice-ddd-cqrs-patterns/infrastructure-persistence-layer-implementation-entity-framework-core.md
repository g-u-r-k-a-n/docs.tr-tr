---
title: Entity Framework Core ile altyapı kalıcılık katmanını uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Entity Framework Core kullanarak altyapı kalıcılığı katmanının uygulama ayrıntılarını bulun.
ms.date: 01/13/2021
ms.openlocfilehash: 2c7b6dbe2f59a26d33a4842e74aed2b7588bd14d
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188900"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="749f4-103">Altyapı kalıcılığı katmanını Entity Framework Core ile uygulama</span><span class="sxs-lookup"><span data-stu-id="749f4-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="749f4-104">SQL Server, Oracle veya PostgreSQL gibi ilişkisel veritabanları kullandığınızda önerilen bir yaklaşım, Entity Framework (EF) temelinde Kalıcılık katmanını uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="749f4-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="749f4-105">EF, LINQ 'i destekler ve modelinize yönelik kesin olarak belirlenmiş nesneler sağlar ve veritabanınıza basit kalıcı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="749f4-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="749f4-106">Entity Framework .NET Framework bir parçası olarak uzun bir geçmişi vardır.</span><span class="sxs-lookup"><span data-stu-id="749f4-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="749f4-107">.NET kullandığınızda, .NET ile aynı şekilde Windows veya Linux üzerinde çalışan Entity Framework Core de kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="749f4-107">When you use .NET, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET.</span></span> <span data-ttu-id="749f4-108">EF Core, performansa göre çok daha küçük bir kaplama ve önemli iyileştirmeler ile uygulanan Entity Framework tamamen yeniden yazma işlemi olur.</span><span class="sxs-lookup"><span data-stu-id="749f4-108">EF Core is a complete rewrite of Entity Framework that's implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="749f4-109">Entity Framework Core giriş</span><span class="sxs-lookup"><span data-stu-id="749f4-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="749f4-110">Entity Framework (EF) Core, popüler Entity Framework veri erişim teknolojisinin basit, genişletilebilir ve platformlar arası bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="749f4-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="749f4-111">Bu, m2016 ' de .NET Core ile tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="749f4-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="749f4-112">EF Core giriş Microsoft belgelerinde zaten mevcut olduğundan, bu bilgilere yönelik bağlantılar sağlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="749f4-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="749f4-113">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="749f4-113">Additional resources</span></span>

- <span data-ttu-id="749f4-114">**Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="749f4-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="749f4-115">**Visual Studio 'Yu kullanarak ASP.NET Core ve Entity Framework Core kullanmaya başlama** </span><span class="sxs-lookup"><span data-stu-id="749f4-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="749f4-116">**DbContext sınıfı** </span><span class="sxs-lookup"><span data-stu-id="749f4-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="749f4-117">**Compare EF Core & EF6. x** </span><span class="sxs-lookup"><span data-stu-id="749f4-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="749f4-118">Bir DDD perspektifinden Entity Framework Core altyapısı</span><span class="sxs-lookup"><span data-stu-id="749f4-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="749f4-119">DDD türünde, önemli bir özellik olan POCO etki alanı varlıklarını, POCO *kodu-ilk varlıkları* olarak EF terimlerinde de bilinen bir şekilde kullanma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="749f4-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="749f4-120">POCO etki alanı varlıklarını kullanıyorsanız, etki alanı model sınıflarınız Kalıcılık [Ignorance](https://deviq.com/persistence-ignorance/) ve [altyapı Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) ilkelerine göre Kalıcılık-Ignorant ' dir.</span><span class="sxs-lookup"><span data-stu-id="749f4-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="749f4-121">DDD desenleri başına, varlık sınıfı içinde etki alanı davranışını ve kurallarını kapsüllemek gerekir, bu sayede herhangi bir koleksiyona erişirken ınvaryantlar, doğrulamaları ve kuralları kontrol edebilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="749f4-122">Bu nedenle, alt varlıkların veya değer nesnelerinin koleksiyonlarına genel erişime izin vermek için DDD 'da iyi bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="749f4-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="749f4-123">Bunun yerine, alanlar ve özellik koleksiyonlarınızın nasıl ve ne zaman güncelleştirileceğini ve ne zaman meydana gelir ve eylemlerin ne zaman gerçekleşeceğini denetleyen yöntemleri göstermek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="749f4-124">EF Core 1,1 ' den itibaren bu DDD gereksinimlerini karşılayacak şekilde, varlıklarınızda ortak özellikler yerine düz alanlara sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="749f4-125">Bir varlık alanının dışarıdan erişilebilir olmasını istemiyorsanız, bir özellik yerine yalnızca özniteliği veya alanı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="749f4-126">Özel özellik ayarlayıcıları da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-126">You can also use private property setters.</span></span>

<span data-ttu-id="749f4-127">Benzer bir şekilde, artık olarak yazılmış bir ortak özelliği kullanarak koleksiyonlara salt okuma erişimine sahip olabilirsiniz. Bu bir  `IReadOnlyCollection<T>` özel alan üyesi tarafından (örneğin `List<T>` ,), KALıCıLıĞı için EF 'e bağlı olan varlıktaki bir özel alan üyesi tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="749f4-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="749f4-128">' Nin, `ICollection<T>` üst varlık sınıfını kullanan herhangi bir geliştiricinin özellik koleksiyonları aracılığıyla öğe eklemesine veya kaldırabileceği anlamına gelen, gerekli koleksiyon özelliklerinin Entity Framework önceki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="749f4-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="749f4-129">Bu olasılık, DDD 'daki önerilen desenlere karşı bir yaklaşımlar.</span><span class="sxs-lookup"><span data-stu-id="749f4-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="749f4-130">`IReadOnlyCollection<T>`Aşağıdaki kod örneğinde gösterildiği gibi, salt okunurdur bir nesne ortaya çıkarmak için özel bir koleksiyon kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="749f4-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
                             decimal unitPrice, decimal discount,
                             string pictureUrl, int units = 1)
    {
        // Validation logic...

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="749f4-131">`OrderItems`Özelliğe yalnızca, kullanılarak salt okunurdur `IReadOnlyCollection<OrderItem>` .</span><span class="sxs-lookup"><span data-stu-id="749f4-131">The `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="749f4-132">Bu tür salt okunurdur, bu nedenle normal dış güncelleştirmelere karşı korunur.</span><span class="sxs-lookup"><span data-stu-id="749f4-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="749f4-133">EF Core, etki alanı modelini "kirmadan", etki alanı modelini fiziksel veritabanıyla eşlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="749f4-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="749f4-134">Bu saf .NET POCO kodudur çünkü eşleme eylemi Kalıcılık katmanında uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="749f4-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="749f4-135">Bu eşleme eyleminde, alanları veritabanına eşlemeyi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="749f4-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="749f4-136">İçindeki `OnModelCreating` yönteminin `OrderingContext` ve sınıfından aşağıdaki örnekte `OrderEntityTypeConfiguration` , ' ın çağrısı, ' ın `SetPropertyAccessMode` `OrderItems` alanı aracılığıyla özelliğine erişmesini söyler EF Core.</span><span class="sxs-lookup"><span data-stu-id="749f4-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="749f4-137">Özellikler yerine alanları kullandığınızda `OrderItem` varlık bir özelliğe sahip gibi kalıcıdır `List<OrderItem>` .</span><span class="sxs-lookup"><span data-stu-id="749f4-137">When you use fields instead of properties, the `OrderItem` entity is persisted as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="749f4-138">Ancak, `AddOrderItem` sırayla yeni öğeler eklemek için tek bir erişimci ve yöntemi sunar.</span><span class="sxs-lookup"><span data-stu-id="749f4-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="749f4-139">Sonuç olarak, davranış ve veriler birlikte birbirlerine bağlanır ve etki alanı modelini kullanan tüm uygulama kodları boyunca tutarlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="749f4-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="749f4-140">Entity Framework Core ile özel depolar uygulama</span><span class="sxs-lookup"><span data-stu-id="749f4-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="749f4-141">Uygulama düzeyinde, bir depo, aşağıdaki sınıfta gösterildiği gibi, güncelleştirmeleri gerçekleştirirken bir iş birimi (EF Core 'de DBContext) tarafından koordine edilen veri Kalıcılık koduna sahip bir sınıftır:</span><span class="sxs-lookup"><span data-stu-id="749f4-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using directives...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;
        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string buyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == buyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="749f4-142">`IBuyerRepository`Arabirim, etki alanı modeli katmanından sözleşme olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="749f4-142">The `IBuyerRepository` interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="749f4-143">Ancak, depo uygulama kalıcı ve altyapı katmanında yapılır.</span><span class="sxs-lookup"><span data-stu-id="749f4-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="749f4-144">EF DbContext, Oluşturucu aracılığıyla bağımlılık ekleme yoluyla gelir.</span><span class="sxs-lookup"><span data-stu-id="749f4-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="749f4-145">Aynı HTTP istek kapsamındaki birden çok depo arasında paylaşılır ve IOC kapsayıcısında () varsayılan yaşam süresi ( `ServiceLifetime.Scoped` ) ile (ile açıkça ayarlanabilir `services.AddDbContext<>` ).</span><span class="sxs-lookup"><span data-stu-id="749f4-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="749f4-146">Bir depoda uygulanacak Yöntemler (güncelleştirmeler veya işlemler ve sorgular)</span><span class="sxs-lookup"><span data-stu-id="749f4-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="749f4-147">Her bir depo sınıfı içinde, ilgili toplamanın içerdiği varlıkların durumunu güncelleştiren Kalıcılık yöntemlerini koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="749f4-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="749f4-148">Bir toplama ve ilgili depo arasında bire bir ilişki olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="749f4-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="749f4-149">Bir toplama kök varlık nesnesinin EF grafiğinde gömülü alt varlıkların olabileceğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="749f4-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="749f4-150">Örneğin, bir alıcı ilgili alt varlıklar olarak birden fazla ödeme yöntemine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="749f4-151">EShopOnContainers 'da, mikro hizmet sıralaması için yaklaşım ayrıca CQS/CQRS 'yi temel aldığı için sorguların çoğu özel depolarda uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="749f4-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="749f4-152">Geliştiriciler, toplamalar tarafından uygulanan kısıtlamalar, toplama başına özel depolar ve genel olarak DDD, sunum katmanı için gereken sorguları ve birleştirmeleri oluşturma özgürlüğü sunar.</span><span class="sxs-lookup"><span data-stu-id="749f4-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="749f4-153">Bu kılavuzda önerilen özel depoların çoğu, birkaç güncelleştirme ya da işlem yöntemine sahiptir ancak yalnızca güncelleştirilecek verileri almak için gereken sorgu yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="749f4-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="749f4-154">Örneğin, BuyerRepository deposu bir Findadsync yöntemi uygular, çünkü uygulamanın siparişle ilgili yeni bir alıcı oluşturmadan önce belirli bir alıcının mevcut olup olmadığını bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="749f4-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="749f4-155">Ancak, sunum katmanına veya istemci uygulamalarına gönderilmek üzere verileri almak için gerçek sorgu yöntemleri,, kaber kullanılarak esnek sorgulara dayanan CQRS sorgularında belirtilen şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="749f4-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="749f4-156">Özel bir depoyu kullanarak doğrudan EF DbContext kullanma</span><span class="sxs-lookup"><span data-stu-id="749f4-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="749f4-157">Entity Framework DbContext sınıfı Iş ve depo desenlerini temel alır ve doğrudan kodunuzdan (örneğin, bir ASP.NET Core MVC denetleyicisinden) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="749f4-158">Iş ve depo desenlerinin birimi, eShopOnContainers içindeki CRUD Katalog mikro hizmetindeki gibi en basit kodla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="749f4-158">The Unit of Work and Repository patterns result in the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="749f4-159">En basit kodun mümkün olmasını istediğiniz durumlarda, çoğu geliştirici olduğu için DbContext sınıfını doğrudan kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="749f4-160">Ancak, özel depoları uygulamak, daha karmaşık mikro hizmetler veya uygulamalar uygularken çeşitli avantajlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="749f4-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="749f4-161">Çalışma birimi ve depo desenlerinin, uygulama ve etki alanı modeli katmanlarından ayrılması için altyapı Kalıcılık katmanını kapsüllemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="749f4-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain-model layers.</span></span> <span data-ttu-id="749f4-162">Bu desenleri uygulamak, veritabanına erişimi taklit eden sahte depoların kullanımını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="749f4-163">Şekil 7-18 ' de, depoları kullanmanın yanı da bu depoları daha kolay hale getiren depoların (doğrudan EF DbContext kullanarak) kullanılmasıyla ilgili farkları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-163">In Figure 7-18, you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories, which makes it easier to mock those repositories.</span></span>

![İki depodaki bileşenlerin ve veri akışının gösterildiği diyagram.](./media/infrastructure-persistence-layer-implementation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="749f4-165">**Şekil 7-18**.</span><span class="sxs-lookup"><span data-stu-id="749f4-165">**Figure 7-18**.</span></span> <span data-ttu-id="749f4-166">Özel depoları kullanma, düz bir DbContext</span><span class="sxs-lookup"><span data-stu-id="749f4-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="749f4-167">Şekil 7-18, özel bir depoyu kullanmanın, depoyu test ederek testi kolaylaştırmak için kullanılabilecek bir soyutlama katmanı ekler.</span><span class="sxs-lookup"><span data-stu-id="749f4-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="749f4-168">Mocking için birden çok alternatif vardır.</span><span class="sxs-lookup"><span data-stu-id="749f4-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="749f4-169">Yalnızca depoların tamamını veya bir bütün çalışma birimini sahte bir şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="749f4-170">Genellikle depolarda bulunan depolar yeterlidir ve tüm iş birimi için soyut ve anlamlı olan karmaşıklık genellikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="749f4-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="749f4-171">Daha sonra uygulama katmanına odaklandığımızda, bağımlılık ekleme 'nın ASP.NET Core içinde nasıl çalıştığını ve depoları kullanırken nasıl uygulandığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="749f4-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="749f4-172">Kısacası, özel depolar, veri katmanı durumundan etkilenmeyenler olan birim testleri ile kodu daha kolay test edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="749f4-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="749f4-173">Gerçek veritabanına aynı zamanda Entity Framework aracılığıyla erişen testler çalıştırırsanız, bunlar birim testleri, ancak çok daha yavaş olan tümleştirme sınamalarından değildir.</span><span class="sxs-lookup"><span data-stu-id="749f4-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="749f4-174">DbContext 'i doğrudan kullanıyorsanız, birim testleri için öngörülebilir verilerle bellek içi SQL Server kullanarak birim testlerini bir veya daha fazla şekilde çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="749f4-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="749f4-175">Ancak DbContext 'e göz at veya sahte verilerin denetlenmesi, depo düzeyinde sahte işlem 'ten daha fazla çalışma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="749f4-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="749f4-176">Kuşkusuz, her zaman MVC denetleyicilerini test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="749f4-177">IFC kapsayıcıda EF DbContext ve IUnitOfWork örnek ömrü</span><span class="sxs-lookup"><span data-stu-id="749f4-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="749f4-178">`DbContext`Nesne (bir nesne olarak gösterilir `IUnitOfWork` ), aynı http istek kapsamı içinde birden çok depo arasında paylaşılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="749f4-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="749f4-179">Örneğin, yürütülmekte olan işlem birden çok toplama ile uğraşmak veya birden çok depo örneği kullandığınız için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="749f4-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="749f4-180">`IUnitOfWork`Arabirimin, EF Core türü değil, etki alanı katmanının bir parçası olması da önemlidir.</span><span class="sxs-lookup"><span data-stu-id="749f4-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="749f4-181">Bunu yapmak için `DbContext` nesnenin örneğinin hizmet ömrü servicelifetime. kapsamlıdır olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="749f4-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="749f4-182">Bu, `DbContext` `services.AddDbContext` `Startup.cs` ASP.NET Core Web API projenizdeki dosyanın ConfigureServices yönteminden IOC kapsayıcıınızda bir ile kayıt yapılırken varsayılan yaşam süresidir.</span><span class="sxs-lookup"><span data-stu-id="749f4-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="749f4-183">Aşağıdaki kodda bu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-183">The following code illustrates this.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
      .AddDbContext<OrderingContext>(options =>
      {
          options.UseSqlServer(Configuration["ConnectionString"],
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="749f4-184">DbContext örnek oluşturma modu ServiceLifetime. geçici veya ServiceLifetime. Singleton olarak yapılandırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="749f4-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="749f4-185">IoC kapsayıcıınızda depo örneği ömrü</span><span class="sxs-lookup"><span data-stu-id="749f4-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="749f4-186">Benzer şekilde, deponun ömrü genellikle kapsam olarak ayarlanmalıdır (Autofac içinde InstancePerLifetimeScope).</span><span class="sxs-lookup"><span data-stu-id="749f4-186">In a similar way, repository's lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="749f4-187">Ayrıca geçici (Autofac ' de ınstanceperdependency) olabilir, ancak ağınız kapsamlı ömür kullanılırken belleği dikkate alarak daha verimli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="749f4-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="749f4-188">Depo için tek yaşam süresinin kullanılması, DbContext kapsam (InstancePerLifetimeScope) yaşam süresi (bir DBContext için varsayılan yaşam süreleri) olarak ayarlandığında ciddi eşzamanlılık sorunları oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-188">Using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="749f4-189">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="749f4-189">Additional resources</span></span>

- <span data-ttu-id="749f4-190">**Bir ASP.NET MVC uygulamasında depo ve Iş düzeni birimi uygulama** </span><span class="sxs-lookup"><span data-stu-id="749f4-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="749f4-191">**Jonathan Allen. Entity Framework, kaber ve zincirle depo deseninin uygulama stratejileri** </span><span class="sxs-lookup"><span data-stu-id="749f4-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="749f4-192">**Cesar de La Torre. Autofac IoC kapsayıcı örneği kapsamları ile ASP.NET Core IOC kapsayıcı hizmeti yaşam sürelerini karşılaştırma** </span><span class="sxs-lookup"><span data-stu-id="749f4-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="749f4-193">Tablo eşleme</span><span class="sxs-lookup"><span data-stu-id="749f4-193">Table mapping</span></span>

<span data-ttu-id="749f4-194">Tablo eşleme, sorgulanacak tablo verilerini tanımlar ve veritabanına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="749f4-195">Daha önce etki alanı varlıklarının (örneğin, bir ürün veya sipariş etki alanı) ilgili veritabanı şeması oluşturmak için nasıl kullanılabileceğini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="749f4-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="749f4-196">EF, *kural* kavramı etrafında kesin olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="749f4-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="749f4-197">Kurallar, "bir tablonun adı ne olacak?" gibi soruları ele alacak.</span><span class="sxs-lookup"><span data-stu-id="749f4-197">Conventions address questions like "What will the name of a table be?"</span></span> <span data-ttu-id="749f4-198">or "birincil anahtar nedir?"</span><span class="sxs-lookup"><span data-stu-id="749f4-198">or "What property is the primary key?"</span></span> <span data-ttu-id="749f4-199">Kurallar genellikle geleneksel adlara dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="749f4-199">Conventions are typically based on conventional names.</span></span> <span data-ttu-id="749f4-200">Örneğin, birincil anahtarın ile biten bir özellik olması normaldir `Id` .</span><span class="sxs-lookup"><span data-stu-id="749f4-200">For example, it is typical for the primary key to be a property that ends with `Id`.</span></span>

<span data-ttu-id="749f4-201">Kural gereği, her varlık `DbSet<TEntity>` türetilmiş bağlamda varlığı sunan özelliği ile aynı ada sahip bir tabloya eşlenecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="749f4-201">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="749f4-202">`DbSet<TEntity>`Verilen varlık için hiçbir değer sağlanmazsa, sınıf adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="749f4-202">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="749f4-203">Veri ek açıklamaları ve akıcı API</span><span class="sxs-lookup"><span data-stu-id="749f4-203">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="749f4-204">Birçok ek EF Core kuralı vardır ve bunların çoğu, Onmodeloluþturma yöntemi içinde uygulanan veri ek açıklamaları veya Floent API kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-204">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="749f4-205">Veri ek açıklamaları, bir DDD bir görünüm noktasından daha kolay bir şekilde olan varlık modeli sınıflarının kendileri üzerinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="749f4-205">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="749f4-206">Bunun nedeni, modelinizi altyapı veritabanıyla ilgili veri ek açıklamalarıyla kirmaktan kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="749f4-206">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="749f4-207">Öte yandan, akıcı API, veri Kalıcılık altyapısı katmanınızdaki birçok kuralı ve eşlemeyi değiştirmek için kullanışlı bir yoldur. bu nedenle, varlık modeli temiz ve kalıcılık altyapısından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="749f4-207">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="749f4-208">Akıcı API ve Onmodeloluþturma yöntemi</span><span class="sxs-lookup"><span data-stu-id="749f4-208">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="749f4-209">Belirtildiği gibi, kuralları ve eşlemeleri değiştirmek için DbContext sınıfında Onmodeloluþturma yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-209">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="749f4-210">EShopOnContainers 'daki sıralama mikro hizmeti, gerektiğinde aşağıdaki kodda gösterildiği gibi açık eşleme ve yapılandırma uygular.</span><span class="sxs-lookup"><span data-stu-id="749f4-210">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

        orderConfiguration.HasKey(o => o.Id);

        orderConfiguration.Ignore(b => b.DomainEvents);

        orderConfiguration.Property(o => o.Id)
            .UseHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

        //Address value object persisted as owned entity type supported since EF Core 2.0
        orderConfiguration
            .OwnsOne(o => o.Address, a =>
            {
                a.WithOwner();
            });

        orderConfiguration
            .Property<int?>("_buyerId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("BuyerId")
            .IsRequired(false);

        orderConfiguration
            .Property<DateTime>("_orderDate")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderDate")
            .IsRequired();

        orderConfiguration
            .Property<int>("_orderStatusId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderStatusId")
            .IsRequired();

        orderConfiguration
            .Property<int?>("_paymentMethodId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("PaymentMethodId")
            .IsRequired(false);

        orderConfiguration.Property<string>("Description").IsRequired(false);

        var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        // DDD Patterns comment:
        //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        orderConfiguration.HasOne<PaymentMethod>()
            .WithMany()
            .HasForeignKey("_paymentMethodId")
            .IsRequired(false)
            .OnDelete(DeleteBehavior.Restrict);

        orderConfiguration.HasOne<Buyer>()
            .WithMany()
            .IsRequired(false)
            .HasForeignKey("_buyerId");

        orderConfiguration.HasOne(o => o.OrderStatus)
            .WithMany()
            .HasForeignKey("_orderStatusId");
    }
}
```

<span data-ttu-id="749f4-211">Tüm akıcı API eşlemelerini aynı yöntem içinde ayarlayabilirsiniz `OnModelCreating` , ancak örnekte gösterildiği gibi bu kodu bölümlemek ve varlık başına bir tane olmak üzere birden çok yapılandırma sınıfı olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-211">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="749f4-212">Özellikle büyük modellerde, farklı varlık türlerini yapılandırmak için ayrı yapılandırma sınıfları olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-212">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="749f4-213">Örnekteki kodda birkaç açık bildirim ve eşleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="749f4-213">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="749f4-214">Ancak, EF Core kuralları bu eşlemelerin çoğunu otomatik olarak bir şekilde yapın, bu nedenle, büyük/küçük harfli ihtiyacınız olan gerçek kod daha küçük olabilir.</span><span class="sxs-lookup"><span data-stu-id="749f4-214">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="749f4-215">EF Core 'daki Hi/Lo algoritması</span><span class="sxs-lookup"><span data-stu-id="749f4-215">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="749f4-216">Önceki örnekteki kodun ilginç bir yönü, anahtar oluşturma stratejisi olarak [Hi/Lo algoritmasını](https://vladmihalcea.com/the-hilo-algorithm/) kullanmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="749f4-216">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="749f4-217">Merhaba/Lo algoritması, değişiklikleri uygulamadan önce benzersiz anahtarlara ihtiyacınız olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="749f4-217">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="749f4-218">Özet olarak, Hi-Lo algoritması, satırı veritabanında depolamaya bağlı olarak tablo satırlarına benzersiz tanımlayıcılar atar.</span><span class="sxs-lookup"><span data-stu-id="749f4-218">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="749f4-219">Bu, normal sıralı veritabanı kimlikleri gibi olduğu gibi, tanımlayıcıları hemen kullanmaya başlayabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="749f4-219">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="749f4-220">Merhaba/Lo algoritması, ilgili bir veritabanı sırasından benzersiz kimlik toplu kimliklerini alma mekanizmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="749f4-220">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="749f4-221">Veritabanı benzersizlik sağladığından, bu kimlikler kullanım açısından güvenlidir, bu nedenle kullanıcılar arasında çakışma olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="749f4-221">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="749f4-222">Bu algoritma şu nedenlerle ilginç olur:</span><span class="sxs-lookup"><span data-stu-id="749f4-222">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="749f4-223">Iş deseninin birimini bozmaz.</span><span class="sxs-lookup"><span data-stu-id="749f4-223">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="749f4-224">Veritabanına gidiş dönüşleri en aza indirmek için dizi kimliklerini toplu olarak alır.</span><span class="sxs-lookup"><span data-stu-id="749f4-224">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="749f4-225">GUID kullanan tekniklerin aksine, okunabilir bir tanımlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="749f4-225">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="749f4-226">EF Core [](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) `UseHiLo` , yukarıdaki örnekte gösterildiği gibi, yöntemiyle Tepo 'u destekler.</span><span class="sxs-lookup"><span data-stu-id="749f4-226">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="749f4-227">Özellikler yerine harita alanları</span><span class="sxs-lookup"><span data-stu-id="749f4-227">Map fields instead of properties</span></span>

<span data-ttu-id="749f4-228">Bu özellik ile EF Core 1,1 ' den bu yana, sütunları doğrudan alanlarla eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-228">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="749f4-229">Varlık sınıfında özellikler kullanılamaz ve yalnızca tablodaki sütunları alanlarla eşlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="749f4-229">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="749f4-230">İçin ortak bir kullanım, varlığın dışından erişilmesi gerekmeyen herhangi bir iç durum için özel alanlar olacaktır.</span><span class="sxs-lookup"><span data-stu-id="749f4-230">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="749f4-231">Bunu tek alanlarla veya bir alan gibi koleksiyonlarla yapabilirsiniz `List<>` .</span><span class="sxs-lookup"><span data-stu-id="749f4-231">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="749f4-232">Bu nokta, etki alanı model sınıflarını modelleyen daha önce bahsedildiği halde, bu eşlemenin `PropertyAccessMode.Field` Önceki kodda vurgulanan yapılandırmayla nasıl gerçekleştirileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-232">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="749f4-233">Altyapı düzeyinde gizlenen EF Core gölge özelliklerini kullanın</span><span class="sxs-lookup"><span data-stu-id="749f4-233">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="749f4-234">EF Core 'daki gölge özellikler, varlık sınıfı modelinizde bulunmayan özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="749f4-234">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="749f4-235">Bu özelliklerin değerleri ve durumları, yalnızca altyapı düzeyindeki [Changetracker](/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) sınıfında saklanır.</span><span class="sxs-lookup"><span data-stu-id="749f4-235">The values and states of these properties are maintained purely in the [ChangeTracker](/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="749f4-236">Sorgu belirtim modelini uygulama</span><span class="sxs-lookup"><span data-stu-id="749f4-236">Implement the Query Specification pattern</span></span>

<span data-ttu-id="749f4-237">Daha önce tasarım bölümünde sunulan sorgu belirtim deseninin, isteğe bağlı sıralama ve sayfalama mantığı ile bir sorgunun tanımını koyabileceğiniz yer olarak tasarlanan Domain-Driven tasarım deseninin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="749f4-237">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="749f4-238">Sorgu belirtim stili bir nesne içindeki bir sorguyu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="749f4-238">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="749f4-239">Örneğin, bazı ürünleri arayan bir disk belleğine alınmış sorguyu kapsüllemek için gerekli giriş parametrelerini (pageNumber, pageSize, filtre, vb.) alan bir PagedProduct belirtimi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-239">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="749f4-240">Ardından, herhangi bir depo yönteminde (genellikle bir liste () aşırı yüklemesi) bir ıqueryspecification kabul eder ve beklenen sorguyu bu belirtiye göre çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="749f4-240">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="749f4-241">Genel belirtim arabirimine bir örnek, [Eshoponweb](https://github.com/dotnet-architecture/eShopOnWeb)'den aşağıdaki koddur.</span><span class="sxs-lookup"><span data-stu-id="749f4-241">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="749f4-242">Daha sonra, Genel belirtim temel sınıfının uygulanması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="749f4-242">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="749f4-243">Aşağıdaki belirtim, sepetin KIMLIĞI veya sepetinin ait olduğu alıcının KIMLIĞI verildiğinde tek bir sepet varlığı yükler.</span><span class="sxs-lookup"><span data-stu-id="749f4-243">The following specification loads a single basket entity given either the basket's ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="749f4-244">Sepetin koleksiyonunu [yükleyecek](/ef/core/querying/related-data) `Items` .</span><span class="sxs-lookup"><span data-stu-id="749f4-244">It will [eagerly load](/ef/core/querying/related-data) the basket's `Items` collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }

    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="749f4-245">Son olarak, bir genel EF deposunun belirli bir varlık türü T ile ilgili verileri filtrelemek ve bunlara göre yüklemek için bu belirtimi nasıl kullanabileceği hakkında daha fazla bilgi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="749f4-245">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

<span data-ttu-id="749f4-246">Filtre mantığını kapsüllemenin yanı sıra belirtim, doldurulacak verilerin şeklini belirtebilir ve bu da doldurulacak özellikler de dahil olmak üzere döndürülür.</span><span class="sxs-lookup"><span data-stu-id="749f4-246">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="749f4-247">Bir depodan döndürmemenizi önermeyiz olsa da `IQueryable` , bir dizi sonuç oluşturmak için bunların depoda kullanılması çok güzel.</span><span class="sxs-lookup"><span data-stu-id="749f4-247">Although we don't recommend returning `IQueryable` from a repository, it's perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="749f4-248">Bu yaklaşımı Yukarıdaki liste yönteminde görebilirsiniz. Bu yaklaşım, sorguyu `IQueryable` , son satırdaki belirtim ölçütlerine göre yürütmeden önce sorgunun dahil olduğu bir sorgu listesini oluşturmak için ara ifadeler kullanır.</span><span class="sxs-lookup"><span data-stu-id="749f4-248">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query's list of includes before executing the query with the specification's criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="749f4-249">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="749f4-249">Additional resources</span></span>

- <span data-ttu-id="749f4-250">**Tablo eşleme** </span><span class="sxs-lookup"><span data-stu-id="749f4-250">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="749f4-251">**Entity Framework Core ile anahtar oluşturmak için Tepo kullanın** </span><span class="sxs-lookup"><span data-stu-id="749f4-251">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="749f4-252">**Alanları yedekleme** </span><span class="sxs-lookup"><span data-stu-id="749f4-252">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="749f4-253">**Steve Smith. Entity Framework Core içinde kapsüllenmiş Koleksiyonlar** </span><span class="sxs-lookup"><span data-stu-id="749f4-253">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="749f4-254">**Gölge özellikleri** </span><span class="sxs-lookup"><span data-stu-id="749f4-254">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="749f4-255">**Belirtim deseninin** </span><span class="sxs-lookup"><span data-stu-id="749f4-255">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="749f4-256">[Önceki](infrastructure-persistence-layer-design.md) 
>  [Sonraki](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="749f4-256">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
