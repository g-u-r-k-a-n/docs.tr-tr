---
title: 'Son değişiklik: ara yazılım: veritabanı hatası sayfası eski olarak işaretlendi'
description: "ASP.NET Core 5,0 ' daki Son değişiklik hakkında bilgi edinin ara yazılım: eski olarak işaretlenen veritabanı hatası sayfası"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 8bc8852d7fb54b0d558342ee3c69085117512a1a
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497625"
---
# <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="3eafe-103">Ara yazılım: Veritabanı hatası sayfası kullanımdan kaldırıldı olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="3eafe-103">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="3eafe-104">[Databaseerrorpageara yazılımı](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) ve ilişkili uzantı yöntemleri ASP.NET Core 5,0 ' de kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="3eafe-104">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="3eafe-105">Ara yazılım ve uzantı yöntemleri ASP.NET Core 6,0 ' de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3eafe-105">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="3eafe-106">Bu işlevsellik, `DatabaseDeveloperPageExceptionFilter` ve uzantı yöntemleri tarafından sağlanacak.</span><span class="sxs-lookup"><span data-stu-id="3eafe-106">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="3eafe-107">Tartışma için, [DotNet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987)konumundaki GitHub sorununa bakın.</span><span class="sxs-lookup"><span data-stu-id="3eafe-107">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3eafe-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3eafe-108">Version introduced</span></span>

<span data-ttu-id="3eafe-109">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="3eafe-109">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="3eafe-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="3eafe-110">Old behavior</span></span>

<span data-ttu-id="3eafe-111">`DatabaseErrorPageMiddleware` ve ilişkili uzantı yöntemleri artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3eafe-111">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="3eafe-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="3eafe-112">New behavior</span></span>

<span data-ttu-id="3eafe-113">`DatabaseErrorPageMiddleware` ve ilişkili genişletme yöntemleri artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3eafe-113">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3eafe-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3eafe-114">Reason for change</span></span>

<span data-ttu-id="3eafe-115">`DatabaseErrorPageMiddleware`[Geliştirici özel durum sayfası](/aspnet/core/fundamentals/error-handling#developer-exception-page)için GENIŞLETILEBILIR bir API 'ye geçirildi.</span><span class="sxs-lookup"><span data-stu-id="3eafe-115">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="3eafe-116">Genişletilebilir API hakkında daha fazla bilgi için bkz. GitHub sorunu [DotNet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).</span><span class="sxs-lookup"><span data-stu-id="3eafe-116">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3eafe-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3eafe-117">Recommended action</span></span>

<span data-ttu-id="3eafe-118">Aşağıdaki adımları tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="3eafe-118">Complete the following steps:</span></span>

1. <span data-ttu-id="3eafe-119">Projenizde kullanmayı durdurun `DatabaseErrorPageMiddleware` .</span><span class="sxs-lookup"><span data-stu-id="3eafe-119">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="3eafe-120">Örneğin, `UseDatabaseErrorPage` öğesinden yöntem çağrısını kaldırın `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="3eafe-120">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="3eafe-121">Geliştirici özel durum sayfasını projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3eafe-121">Add the developer exception page to your project.</span></span> <span data-ttu-id="3eafe-122">Örneğin, <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> içinde yöntemini çağırın `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="3eafe-122">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="3eafe-123">Proje dosyasına [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet paketini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3eafe-123">Add the [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet package to the project file.</span></span>

1. <span data-ttu-id="3eafe-124">Veritabanı Geliştirici sayfası özel durum filtresini hizmetler koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3eafe-124">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="3eafe-125">Örneğin, `AddDatabaseDeveloperPageExceptionFilter` içinde yöntemini çağırın `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="3eafe-125">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

## <a name="affected-apis"></a><span data-ttu-id="3eafe-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3eafe-126">Affected APIs</span></span>

- [<span data-ttu-id="3eafe-127">Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="3eafe-127">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="3eafe-128">Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. Databaseerrorpageara yazılımı</span><span class="sxs-lookup"><span data-stu-id="3eafe-128">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
