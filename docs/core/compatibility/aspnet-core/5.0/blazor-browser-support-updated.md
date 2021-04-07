---
title: 'Son değişiklik: Blazor : güncelleştirilmiş tarayıcı desteği'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin Blazor : güncelleştirilmiş tarayıcı desteği"
ms.author: scaddie
ms.date: 10/01/2020
no-loc:
- Blazor
- Blazor WebAssembly
- Blazor Server
ms.openlocfilehash: 25566a4b30aaa8484ec4bcf26ab1e8fde6af1279
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497872"
---
# <a name="blazor-updated-browser-support"></a><span data-ttu-id="b6e00-103">Blazor: Tarayıcı desteği güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="b6e00-103">Blazor: Updated browser support</span></span>

<span data-ttu-id="b6e00-104">ASP.NET Core 5,0, bazıları eski tarayıcılarla uyumsuz olan [Yeni Blazor Özellikler](https://github.com/dotnet/aspnetcore/issues/21514)sunar.</span><span class="sxs-lookup"><span data-stu-id="b6e00-104">ASP.NET Core 5.0 introduces [new Blazor features](https://github.com/dotnet/aspnetcore/issues/21514), some of which are incompatible with older browsers.</span></span> <span data-ttu-id="b6e00-105">ASP.NET Core 5,0 ' de tarafından desteklenen tarayıcıların listesi, Blazor buna göre güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b6e00-105">The list of browsers supported by Blazor in ASP.NET Core 5.0 has been updated accordingly.</span></span>

<span data-ttu-id="b6e00-106">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).</span><span class="sxs-lookup"><span data-stu-id="b6e00-106">For discussion, see GitHub issue [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b6e00-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b6e00-107">Version introduced</span></span>

<span data-ttu-id="b6e00-108">5.0</span><span class="sxs-lookup"><span data-stu-id="b6e00-108">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b6e00-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b6e00-109">Old behavior</span></span>

<span data-ttu-id="b6e00-110">Blazor Server , yeterli polydolgular ile Microsoft Internet Explorer 11 ' i destekler.</span><span class="sxs-lookup"><span data-stu-id="b6e00-110">Blazor Server supports Microsoft Internet Explorer 11 with sufficient polyfills.</span></span> <span data-ttu-id="b6e00-111">Blazor ServerBlazor WebAssemblyAyrıca, [Microsoft Edge eski](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)sürümünde de çalışır.</span><span class="sxs-lookup"><span data-stu-id="b6e00-111">Blazor Server and Blazor WebAssembly are also functional in [Microsoft Edge Legacy](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span></span>

## <a name="new-behavior"></a><span data-ttu-id="b6e00-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b6e00-112">New behavior</span></span>

<span data-ttu-id="b6e00-113">Blazor Server ASP.NET Core 5,0 ' de Microsoft Internet Explorer 11 desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b6e00-113">Blazor Server in ASP.NET Core 5.0 isn't supported with Microsoft Internet Explorer 11.</span></span> <span data-ttu-id="b6e00-114">Blazor Server ve Blazor WebAssembly Microsoft Edge eski sürümünde tam olarak işlevsel değildir.</span><span class="sxs-lookup"><span data-stu-id="b6e00-114">Blazor Server and Blazor WebAssembly aren't fully functional in Microsoft Edge Legacy.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b6e00-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b6e00-115">Reason for change</span></span>

<span data-ttu-id="b6e00-116">BlazorASP.NET Core 5,0 ' deki yeni özellikler bu eski tarayıcılarla uyumsuzdur ve bu eski tarayıcıların kullanımı, bu eski tarayıcıların kullanımına karşı azalmış olur.</span><span class="sxs-lookup"><span data-stu-id="b6e00-116">New Blazor features in ASP.NET Core 5.0 are incompatible with these older browsers, and use of these older browsers is diminishing.</span></span> <span data-ttu-id="b6e00-117">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="b6e00-117">For more information, see the following resources:</span></span>

* [<span data-ttu-id="b6e00-118">Microsoft Edge için Windows desteği, Ayrıca 9 Mart 2021 ' de sona eriyor</span><span class="sxs-lookup"><span data-stu-id="b6e00-118">Windows support for Microsoft Edge Legacy is also ending on March 9, 2021</span></span>](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [<span data-ttu-id="b6e00-119">Microsoft 365 uygulamalar ve hizmetler, Microsoft Internet Explorer 11 için 17 Ağustos 2021 ' de destek sona acaktır.</span><span class="sxs-lookup"><span data-stu-id="b6e00-119">Microsoft 365 apps and services will end support for Microsoft Internet Explorer 11 by August 17, 2021</span></span>](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

## <a name="recommended-action"></a><span data-ttu-id="b6e00-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b6e00-120">Recommended action</span></span>

<span data-ttu-id="b6e00-121">Bu eski tarayıcılardan [Yeni, Kmuum tabanlı Microsoft Edge](https://www.microsoft.com/edge)'e yükseltin.</span><span class="sxs-lookup"><span data-stu-id="b6e00-121">Upgrade from these older browsers to the [new, Chromium-based Microsoft Edge](https://www.microsoft.com/edge).</span></span> <span data-ttu-id="b6e00-122">BlazorBu eski tarayıcıları desteklemesi gereken uygulamalar için ASP.NET Core 3,1 kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6e00-122">For Blazor apps that need to support these older browsers, use ASP.NET Core 3.1.</span></span> <span data-ttu-id="b6e00-123">BlazorASP.NET Core 3,1 ' de desteklenen tarayıcılar listesi değiştirilmedi ve [desteklenen platformlarda](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1)belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b6e00-123">The supported browsers list for Blazor in ASP.NET Core 3.1 hasn't changed and is documented at [Supported platforms](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b6e00-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b6e00-124">Affected APIs</span></span>

<span data-ttu-id="b6e00-125">Yok</span><span class="sxs-lookup"><span data-stu-id="b6e00-125">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
