---
title: 'Son değişiklik: Uzantılar: bazı NuGet paketlerini etkileyen paket başvuru değişiklikleri'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: bazı NuGet paketlerini etkileyen paket başvuru değişiklikleri"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 4a525d9f7aad4409fd507fcf80c00968ff4b63d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761474"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="46945-103">Uzantılar: bazı NuGet paketlerini etkileyen paket başvuru değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="46945-103">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="46945-104">Bazı `Microsoft.Extensions.*` NuGet paketlerinin [DotNet/Extensions](https://github.com/dotnet/extensions) deposundan [DotNet/çalışma zamanına](https://github.com/dotnet/runtime), [ASPNET/Duyurular # 411](https://github.com/aspnet/Announcements/issues/411)' de açıklandığı gibi geçirilirken, paket değişiklikleri geçirilmiş paketlerden bazılarına uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="46945-104">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="46945-105">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).</span><span class="sxs-lookup"><span data-stu-id="46945-105">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="46945-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="46945-106">Version introduced</span></span>

<span data-ttu-id="46945-107">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="46945-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="46945-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="46945-108">Old behavior</span></span>

<span data-ttu-id="46945-109">Bazı `Microsoft.Extensions.*` paketler, uygulamanızın güvenolduğu API 'ler için paket başvuruları içerir.</span><span class="sxs-lookup"><span data-stu-id="46945-109">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="46945-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="46945-110">New behavior</span></span>

<span data-ttu-id="46945-111">Uygulamanızın `Microsoft.Extensions.*` paket bağımlılıklarını eklemesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="46945-111">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="46945-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="46945-112">Reason for change</span></span>

<span data-ttu-id="46945-113">Paketleme ilkeleri *DotNet/Runtime* deposuna daha iyi uyum sağlamak için güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="46945-113">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="46945-114">Yeni ilke altında kullanılmayan paket başvuruları paketleme sırasında *. nupkg* dosyalarından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="46945-114">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="46945-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="46945-115">Recommended action</span></span>

<span data-ttu-id="46945-116">Etkilenen paketlerin tüketicileri, kaldırılan paket bağımlılığıyla API 'Ler kullanılırsa, bu projedeki kaldırılan paket bağımlılığına doğrudan bağımlılık eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="46945-116">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="46945-117">Aşağıdaki tabloda etkilenen paketler ve ilgili değişiklikler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="46945-117">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="46945-118">Paket adı</span><span class="sxs-lookup"><span data-stu-id="46945-118">Package name</span></span>|<span data-ttu-id="46945-119">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="46945-119">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="46945-120">Microsoft.Extensions.Configurlama. Bağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="46945-120">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="46945-121">Başvurusu kaldırıldı `Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="46945-121">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="46945-122"> ÜzerindeMicrosoft.Extensions.Configuration.Js</span><span class="sxs-lookup"><span data-stu-id="46945-122">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="46945-123">Başvurusu kaldırıldı `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="46945-123">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="46945-124">Microsoft. Extensions. Hosting. soyutlamalar</span><span class="sxs-lookup"><span data-stu-id="46945-124">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="46945-125">Başvurusu kaldırıldı `Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="46945-125">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="46945-126">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="46945-126">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="46945-127">Başvurusu kaldırıldı `Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="46945-127">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="46945-128">Microsoft. Extensions. Logging. Console</span><span class="sxs-lookup"><span data-stu-id="46945-128">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="46945-129">Başvurusu kaldırıldı `Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="46945-129">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="46945-130">Microsoft. Extensions. Logging. EventLog</span><span class="sxs-lookup"><span data-stu-id="46945-130">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="46945-131">`System.Diagnostics.EventLog`.NET Framework 4.6.1 hedef Framework bilinen adı için başvuru kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="46945-131">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="46945-132">Microsoft. Extensions. Logging. EventSource</span><span class="sxs-lookup"><span data-stu-id="46945-132">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="46945-133">Başvurusu kaldırıldı `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="46945-133">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="46945-134">Microsoft. Extensions. Options</span><span class="sxs-lookup"><span data-stu-id="46945-134">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="46945-135">Başvurusu kaldırıldı `System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="46945-135">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="46945-136">Örneğin, öğesine paket başvurusu `Microsoft.Extensions.Configuration` öğesinden kaldırılmıştır `Microsoft.Extensions.Configuration.Binder` .</span><span class="sxs-lookup"><span data-stu-id="46945-136">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="46945-137">Pakette, bağımlılıktan API kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="46945-137">No API from the dependency was used in the package.</span></span> <span data-ttu-id="46945-138">`Microsoft.Extensions.Configuration.Binder`API 'lerine bağlı olan kullanıcıların `Microsoft.Extensions.Configuration` , projesinde kendisine bir doğrudan başvuru eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="46945-138">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="46945-139">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="46945-139">Affected APIs</span></span>

<span data-ttu-id="46945-140">Yok</span><span class="sxs-lookup"><span data-stu-id="46945-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
