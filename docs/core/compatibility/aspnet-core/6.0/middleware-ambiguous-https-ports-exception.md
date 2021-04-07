---
title: 'Son değişiklik: ara yazılım: HTTPS yeniden yönlendirme ara yazılımı belirsiz HTTPS bağlantı noktalarında özel durum oluşturur'
description: "ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin: HTTPS yeniden yönlendirme ara yazılımı, belirsiz HTTPS bağlantı noktalarında özel durum oluşturur"
ms.author: scaddie
ms.date: 02/04/2021
ms.openlocfilehash: 5c41251fac29f7c2dc2bdc3eb5610bb571f438c9
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497027"
---
# <a name="middleware-https-redirection-middleware-throws-exception-on-ambiguous-https-ports"></a><span data-ttu-id="f93dc-103">Ara yazılım: HTTPS yeniden yönlendirme ara yazılımı belirsiz HTTPS bağlantı noktalarında özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="f93dc-103">Middleware: HTTPS Redirection Middleware throws exception on ambiguous HTTPS ports</span></span>

<span data-ttu-id="f93dc-104">ASP.NET Core 6,0 ' de, [https yeniden yönlendirme ara yazılımı](xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A) <xref:System.InvalidOperationException> sunucu YAPıLANDıRMASıNDA birden çok HTTPS bağlantı noktası bulduğunda türünde bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f93dc-104">In ASP.NET Core 6.0, the [HTTPS Redirection Middleware](xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A) throws an exception of type <xref:System.InvalidOperationException> when it finds multiple HTTPS ports in the server configuration.</span></span> <span data-ttu-id="f93dc-105">Özel durumun iletisi "ıvveraddressesözelliğinden HTTPS bağlantı noktası saptanamıyor, birden çok değer bulundu.</span><span class="sxs-lookup"><span data-stu-id="f93dc-105">The exception's message contains the text "Cannot determine the https port from IServerAddressesFeature, multiple values were found.</span></span> <span data-ttu-id="f93dc-106">İstenen bağlantı noktasını HttpsRedirectionOptions. HttpsPort üzerinde açık olarak ayarlayın. "</span><span class="sxs-lookup"><span data-stu-id="f93dc-106">Set the desired port explicitly on HttpsRedirectionOptions.HttpsPort."</span></span>

<span data-ttu-id="f93dc-107">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 29222](https://github.com/dotnet/aspnetcore/issues/29222).</span><span class="sxs-lookup"><span data-stu-id="f93dc-107">For discussion, see GitHub issue [dotnet/aspnetcore#29222](https://github.com/dotnet/aspnetcore/issues/29222).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f93dc-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f93dc-108">Version introduced</span></span>

<span data-ttu-id="f93dc-109">6.0</span><span class="sxs-lookup"><span data-stu-id="f93dc-109">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="f93dc-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="f93dc-110">Old behavior</span></span>

<span data-ttu-id="f93dc-111">HTTPS yeniden yönlendirme ara yazılımı bir bağlantı noktasıyla açıkça yapılandırılmamışsa, <xref:Microsoft.AspNetCore.Hosting.Server.Features.IServerAddressesFeature> ilk istek sırasında, yeniden yönlendirilmesi gereken HTTPS bağlantı noktasını belirleyen bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="f93dc-111">When the HTTPS Redirection Middleware isn't explicitly configured with a port, it searches <xref:Microsoft.AspNetCore.Hosting.Server.Features.IServerAddressesFeature> during the first request to determine the HTTPS port to which it should redirect.</span></span>

<span data-ttu-id="f93dc-112">HTTPS bağlantı noktası veya birden çok farklı bağlantı noktası yoksa, bu bağlantı noktasının kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f93dc-112">If there are no HTTPS ports or multiple distinct ports, it's unclear which port should be used.</span></span> <span data-ttu-id="f93dc-113">Ara yazılım bir uyarı kaydeder ve kendisini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f93dc-113">The middleware logs a warning and disables itself.</span></span> <span data-ttu-id="f93dc-114">HTTP istekleri normal şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="f93dc-114">HTTP requests are processed normally.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="f93dc-115">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="f93dc-115">New behavior</span></span>

<span data-ttu-id="f93dc-116">HTTPS yeniden yönlendirme ara yazılımı bir bağlantı noktasıyla açıkça yapılandırılmamışsa, `IServerAddressesFeature` ilk istek sırasında, yeniden yönlendirilmesi gereken HTTPS bağlantı noktasını belirleyen bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="f93dc-116">When the HTTPS Redirection Middleware isn't explicitly configured with a port, it searches `IServerAddressesFeature` during the first request to determine the HTTPS port to which it should redirect.</span></span>

<span data-ttu-id="f93dc-117">HTTPS bağlantı noktası yoksa, ara yazılım hala bir uyarı kaydeder ve kendisini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f93dc-117">If there are no HTTPS ports, the middleware still logs a warning and disables itself.</span></span> <span data-ttu-id="f93dc-118">HTTP istekleri normal şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="f93dc-118">HTTP requests are processed normally.</span></span> <span data-ttu-id="f93dc-119">Bu davranış şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="f93dc-119">This behavior supports:</span></span>

* <span data-ttu-id="f93dc-120">HTTPS olmadan geliştirme senaryoları.</span><span class="sxs-lookup"><span data-stu-id="f93dc-120">Development scenarios without HTTPS.</span></span>
* <span data-ttu-id="f93dc-121">Sunucuya ulaşmadan önce TLS 'nin sonlandırıldığı barındırılan senaryolar.</span><span class="sxs-lookup"><span data-stu-id="f93dc-121">Hosted scenarios in which TLS is terminated before reaching the server.</span></span>

<span data-ttu-id="f93dc-122">Birden çok farklı bağlantı noktası varsa, bu bağlantı noktasının kullanılması gerektiği anlaşılır değildir.</span><span class="sxs-lookup"><span data-stu-id="f93dc-122">If there are multiple distinct ports, it's unclear which port should be used.</span></span> <span data-ttu-id="f93dc-123">Ara yazılım bir özel durum oluşturur ve HTTP isteği başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f93dc-123">The middleware throws an exception and fails the HTTP request.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f93dc-124">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="f93dc-124">Reason for change</span></span>

<span data-ttu-id="f93dc-125">Bu değişiklik, HTTPS 'nin kullanılabilir olduğu bilindiğinde gizli verilerin şifrelenmemiş HTTP bağlantıları üzerinden sunulmasını önler.</span><span class="sxs-lookup"><span data-stu-id="f93dc-125">This change prevents potentially sensitive data from being served over unencrypted HTTP connections when HTTPS is known to be available.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f93dc-126">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f93dc-126">Recommended action</span></span>

<span data-ttu-id="f93dc-127">Sunucuda birden çok farklı HTTPS bağlantı noktası olduğunda HTTPS yeniden yönlendirmeyi etkinleştirmek için, yapılandırmada bir bağlantı noktası belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f93dc-127">To enable HTTPS redirection when the server has multiple distinct HTTPS ports, you must specify one port in the configuration.</span></span> <span data-ttu-id="f93dc-128">Daha fazla bilgi için bkz. [bağlantı noktası yapılandırması](/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&preserve-view=true#port-configuration).</span><span class="sxs-lookup"><span data-stu-id="f93dc-128">For more information, see [Port configuration](/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&preserve-view=true#port-configuration).</span></span>

<span data-ttu-id="f93dc-129">Uygulamanızda HTTPS yeniden yönlendirme ara yazılımı gerekmiyorsa, `UseHttpsRedirection` *Başlangıç. cs*' den kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f93dc-129">If you don't need the HTTPS Redirection Middleware in your app, remove `UseHttpsRedirection` from *Startup.cs*.</span></span>

<span data-ttu-id="f93dc-130">Doğru HTTPS bağlantı noktasını dinamik olarak seçmeniz gerekiyorsa, GitHub sorunu [DotNet/aspnetcore # 21291](https://github.com/dotnet/aspnetcore/issues/21291)içinde geri bildirim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f93dc-130">If you need to select the correct HTTPS port dynamically, provide feedback in GitHub issue [dotnet/aspnetcore#21291](https://github.com/dotnet/aspnetcore/issues/21291).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f93dc-131">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f93dc-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection`

-->
