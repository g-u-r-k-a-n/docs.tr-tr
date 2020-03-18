---
title: Esnek Entity Framework Core SQL bağlantılarını uygulama
description: Esnek Entity Framework Core SQL bağlantılarını nasıl uygulayacağınızı öğrenin. Bu teknik özellikle bulutta Azure SQL Veritabanı kullanırken önemlidir.
ms.date: 10/16/2018
ms.openlocfilehash: 7a047edca21d63a451e90f407b23f3358d461330
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78241071"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="c1a61-104">Esnek Entity Framework Core SQL bağlantılarını uygulama</span><span class="sxs-lookup"><span data-stu-id="c1a61-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="c1a61-105">Azure SQL DB için Entity Framework (EF) Core zaten dahili veritabanı bağlantısı esnekliği ve yeniden deneme mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1a61-105">For Azure SQL DB, Entity Framework (EF) Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="c1a61-106">Ancak [esnek EF Core bağlantılarına](/ef/core/miscellaneous/connection-resiliency)sahip <xref:Microsoft.EntityFrameworkCore.DbContext> olmak istiyorsanız, her bağlantı için Varlık Çerçevesi yürütme stratejisini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1a61-106">But you need to enable the Entity Framework execution strategy for each <xref:Microsoft.EntityFrameworkCore.DbContext> connection if you want to have [resilient EF Core connections](/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="c1a61-107">Örneğin, EF Core bağlantı düzeyindeki aşağıdaki kod, bağlantı başarısız olursa yeniden denenen esnek SQL bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1a61-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="c1a61-108">BeginTransaction ve birden çok DbContexts kullanarak yürütme stratejileri ve açık işlemler</span><span class="sxs-lookup"><span data-stu-id="c1a61-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="c1a61-109">EF Core bağlantılarında yeniden denemeler etkinleştirildiğinde, EF Core kullanarak gerçekleştirdiğiniz her işlem kendi yeniden çalışılabilir işlemi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="c1a61-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="c1a61-110">Geçici bir hata `SaveChanges` oluşursa, her sorgu ve her çağrı birim olarak yeniden denenecektir.</span><span class="sxs-lookup"><span data-stu-id="c1a61-110">Each query and each call to `SaveChanges` will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="c1a61-111">Ancak, kodunuz kullanarak `BeginTransaction`bir işlem başlatırsa, birim olarak kabul edilmesi gereken kendi işlem grubunuzu tanımlıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c1a61-111">However, if your code initiates a transaction using `BeginTransaction`, you're defining your own group of operations that need to be treated as a unit.</span></span> <span data-ttu-id="c1a61-112">Bir hata oluşursa, işlem içindeki her şeyin geri alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1a61-112">Everything inside the transaction has to be rolled back if a failure occurs.</span></span>

<span data-ttu-id="c1a61-113">Bir EF yürütme stratejisi (yeniden deneme ilkesi) kullanırken bu `SaveChanges` işlemi yürütmeye çalışırsanız ve birden çok DbContext'dan arama nız varsa, bunun gibi bir özel durum alırsınız:</span><span class="sxs-lookup"><span data-stu-id="c1a61-113">If you try to execute that transaction when using an EF execution strategy (retry policy) and you call `SaveChanges` from multiple DbContexts, you'll get an exception like this one:</span></span>

> <span data-ttu-id="c1a61-114">System.InvalidOperationException: Yapılandırılan yürütme stratejisi 'SqlServerRetryingExecutionStrategy' kullanıcı tarafından başlatılan hareketleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c1a61-114">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="c1a61-115">İşlemdeki tüm işlemleri geri alabilir birim olarak yürütmek için 'DbContext.Database.CreateExecutionStrategy()' tarafından döndürülen yürütme stratejisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1a61-115">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="c1a61-116">Çözüm, yürütülmesi gereken her şeyi temsil eden bir temsilciyle EF yürütme stratejisini el ile çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="c1a61-116">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="c1a61-117">Geçici bir hata oluşursa yürütme stratejisi temsilciyi yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="c1a61-117">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="c1a61-118">Örneğin, aşağıdaki kod, bir ürünü güncellerken ve farklı bir DbContext\_kullanması gereken ProductPriceChangedIntegrationEvent nesnesini kaydederken iki kez birden fazla DbContexts (catalogContext ve IntegrationEventLogContext) ile eShopOnContainers'da nasıl uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1a61-118">For example, the following code show how it's implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

```csharp
public async Task<IActionResult> UpdateProduct(
    [FromBody]CatalogItem productToUpdate)
{
    // Other code ...

    var oldPrice = catalogItem.Price;
    var raiseProductPriceChangedEvent = oldPrice != productToUpdate.Price;

    // Update current product
    catalogItem = productToUpdate;

    // Save product's data and publish integration event through the Event Bus
    // if price has changed
    if (raiseProductPriceChangedEvent)
    {
        //Create Integration Event to be published through the Event Bus
        var priceChangedEvent = new ProductPriceChangedIntegrationEvent(
          catalogItem.Id, productToUpdate.Price, oldPrice);

       // Achieving atomicity between original Catalog database operation and the
       // IntegrationEventLog thanks to a local transaction
       await _catalogIntegrationEventService.SaveEventAndCatalogContextChangesAsync(
           priceChangedEvent);

       // Publish through the Event Bus and mark the saved event as published
       await _catalogIntegrationEventService.PublishThroughEventBusAsync(
           priceChangedEvent);
    }
    // Just save the updated product because the Product's Price hasn't changed.
    else
    {
        await _catalogContext.SaveChangesAsync();
    }
}
```

<span data-ttu-id="c1a61-119">Birincisi, <xref:Microsoft.EntityFrameworkCore.DbContext> `_catalogContext` ikincisi `DbContext` nesnenin `_catalogIntegrationEventService` içindedir.</span><span class="sxs-lookup"><span data-stu-id="c1a61-119">The first <xref:Microsoft.EntityFrameworkCore.DbContext> is `_catalogContext` and the second `DbContext` is within the `_catalogIntegrationEventService` object.</span></span> <span data-ttu-id="c1a61-120">Commit eylemi, bir `DbContext` EF yürütme stratejisi kullanılarak tüm nesneler arasında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c1a61-120">The Commit action is performed across all `DbContext` objects using an EF execution strategy.</span></span>

<span data-ttu-id="c1a61-121">Bu birden `DbContext` çok işlemeyi `ResilientTransaction` gerçekleştirmek için, aşağıdaki kodda gösterildiği gibi bir sınıf `SaveEventAndCatalogContextChangesAsync` kullanır:</span><span class="sxs-lookup"><span data-stu-id="c1a61-121">To achieve this multiple `DbContext` commit, the `SaveEventAndCatalogContextChangesAsync` uses a `ResilientTransaction` class, as shown in the following code:</span></span>

```csharp
public class CatalogIntegrationEventService : ICatalogIntegrationEventService
{
    //…
    public async Task SaveEventAndCatalogContextChangesAsync(
        IntegrationEvent evt)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        await ResilientTransaction.New(_catalogContext).ExecuteAsync(async () =>
        {
            // Achieving atomicity between original catalog database
            // operation and the IntegrationEventLog thanks to a local transaction
            await _catalogContext.SaveChangesAsync();
            await _eventLogService.SaveEventAsync(evt,
                _catalogContext.Database.CurrentTransaction.GetDbTransaction());
        });
    }
}
```

<span data-ttu-id="c1a61-122">Yöntem `ResilientTransaction.ExecuteAsync` `DbContext` temelde geçirilen ()`_catalogContext`bir işlem başlar `EventLogService` ve sonra değişiklikleri kaydetmek `IntegrationEventLogContext` için bu hareketi kullanır ve sonra tüm işlem işler.</span><span class="sxs-lookup"><span data-stu-id="c1a61-122">The `ResilientTransaction.ExecuteAsync` method basically begins a transaction from the passed `DbContext` (`_catalogContext`) and then makes the `EventLogService` use that transaction to save changes from the `IntegrationEventLogContext` and then commits the whole transaction.</span></span>

```csharp
public class ResilientTransaction
{
    private DbContext _context;
    private ResilientTransaction(DbContext context) =>
        _context = context ?? throw new ArgumentNullException(nameof(context));

    public static ResilientTransaction New (DbContext context) =>
        new ResilientTransaction(context);

    public async Task ExecuteAsync(Func<Task> action)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        var strategy = _context.Database.CreateExecutionStrategy();
        await strategy.ExecuteAsync(async () =>
        {
            using (var transaction = _context.Database.BeginTransaction())
            {
                await action();
                transaction.Commit();
            }
        });
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="c1a61-123">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c1a61-123">Additional resources</span></span>

- <span data-ttu-id="c1a61-124">**ASP.NET MVC Uygulamasında EF ile Bağlantı Esnekliği ve Komut Durdurma** </span><span class="sxs-lookup"><span data-stu-id="c1a61-124">**Connection Resiliency and Command Interception with EF in an ASP.NET MVC Application** </span></span>\
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- <span data-ttu-id="c1a61-125">**Cesar de la Torre. Esnek Varlık Çerçeve Temel SQL Bağlantı ve Hareketlerini Kullanma** </span><span class="sxs-lookup"><span data-stu-id="c1a61-125">**Cesar de la Torre. Using Resilient Entity Framework Core SQL Connections and Transactions** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
><span data-ttu-id="c1a61-126">[Önceki](implement-retries-exponential-backoff.md)
>[Sonraki](use-httpclientfactory-to-implement-resilient-http-requests.md)</span><span class="sxs-lookup"><span data-stu-id="c1a61-126">[Previous](implement-retries-exponential-backoff.md)
[Next](use-httpclientfactory-to-implement-resilient-http-requests.md)</span></span>
