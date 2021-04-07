---
title: 'Son değişiklik: SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı'
description: ASP.NET Core 5,0 ' deki ve SignalR başlıklı UseSignalR ve UseConnections yöntemlerinin kaldırıldığı Son değişiklik hakkında bilgi edinin
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3b6e301ee8414a503f7b3697d3b1a01174a1cefb
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497106"
---
# <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="7e5cf-103">SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="7e5cf-103">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="7e5cf-104">ASP.NET Core 3,0 ' de, SignalR bir uç nokta yönlendirme benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="7e5cf-104">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="7e5cf-105">Bu değişikliğin bir parçası olarak,, <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> ve bazı ilgili yöntemler artık kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="7e5cf-105">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="7e5cf-106">ASP.NET Core 5,0 ' de, eski yöntemler kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7e5cf-106">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="7e5cf-107">Yöntemlerin tam listesi için bkz. [etkilenen API 'ler](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="7e5cf-107">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="7e5cf-108">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="7e5cf-108">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7e5cf-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7e5cf-109">Version introduced</span></span>

<span data-ttu-id="7e5cf-110">5,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="7e5cf-110">5.0 Preview 3</span></span>

## <a name="old-behavior"></a><span data-ttu-id="7e5cf-111">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="7e5cf-111">Old behavior</span></span>

<span data-ttu-id="7e5cf-112">SignalR hub 'ları ve bağlantı işleyicileri, veya yöntemlerini kullanarak ara yazılım ardışık düzenine `UseSignalR` kaydedilebilir `UseConnections` .</span><span class="sxs-lookup"><span data-stu-id="7e5cf-112">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="7e5cf-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="7e5cf-113">New behavior</span></span>

<span data-ttu-id="7e5cf-114">SignalR hub 'ları ve bağlantı işleyicileri <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> , <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> üzerinde ve genişletme yöntemleri kullanılarak kaydedilmelidir <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .</span><span class="sxs-lookup"><span data-stu-id="7e5cf-114">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7e5cf-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7e5cf-115">Reason for change</span></span>

<span data-ttu-id="7e5cf-116">Eski yöntemlerde, ASP.NET Core diğer yönlendirme bileşenleriyle etkileşime girmediğiniz özel yönlendirme mantığı vardı.</span><span class="sxs-lookup"><span data-stu-id="7e5cf-116">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="7e5cf-117">ASP.NET Core 3,0 ' de, uç nokta yönlendirme olarak adlandırılan yeni bir genel amaçlı yönlendirme sistemi tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="7e5cf-117">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="7e5cf-118">Uç nokta yönlendirme özelliği, diğer yönlendirme bileşenleriyle etkileşim kurmak için SignalR.</span><span class="sxs-lookup"><span data-stu-id="7e5cf-118">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="7e5cf-119">Bu modele geçiş yapmak, kullanıcıların Endpoint Routing 'in tüm avantajlarını belirlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e5cf-119">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="7e5cf-120">Sonuç olarak, eski yöntemler kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7e5cf-120">Consequently, the old methods have been removed.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7e5cf-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7e5cf-121">Recommended action</span></span>

<span data-ttu-id="7e5cf-122">`UseSignalR`Projenizin yönteminden veya öğesini çağıran kodu kaldırın `UseConnections` `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="7e5cf-122">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="7e5cf-123">Bunu `MapHub` `MapConnectionHandler` , bir çağrısının gövdesinde, sırasıyla veya olan çağrılarıyla değiştirin `UseEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="7e5cf-123">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="7e5cf-124">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7e5cf-124">For example:</span></span>

<span data-ttu-id="7e5cf-125">**Eski kod:**</span><span class="sxs-lookup"><span data-stu-id="7e5cf-125">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="7e5cf-126">**Yeni kod:**</span><span class="sxs-lookup"><span data-stu-id="7e5cf-126">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="7e5cf-127">Genel olarak, önceki `MapHub` ve `MapConnectionHandler` çağrılarınız, ' ın gövdesinden `UseSignalR` ve en az bir `UseConnections` değişikliğe gerek kalmadan doğrudan aktarılabilir `UseEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="7e5cf-127">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7e5cf-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7e5cf-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
