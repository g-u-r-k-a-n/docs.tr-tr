---
title: 'Son değişiklik: Blazor: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 36ba6c16ac970aa8acb0d0faab42b151addae888
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497846"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="be606-103">Blazor: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı</span><span class="sxs-lookup"><span data-stu-id="be606-103">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="be606-104">ASP.NET Core 5,0 RC2 sürümünün bir parçası olarak, `ProtectedBrowserStorage` özellik ASP.NET Core paylaşılan çerçeveye taşınır.</span><span class="sxs-lookup"><span data-stu-id="be606-104">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="be606-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="be606-105">Version introduced</span></span>

<span data-ttu-id="be606-106">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="be606-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="be606-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="be606-107">Old behavior</span></span>

<span data-ttu-id="be606-108">ASP.NET Core 5,0 Preview 8 ' de, özelliği [Microsoft. AspNetCore. components. Web. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) paketinin bir parçası olarak kullanılabilir ancak yalnızca Blazor WebAssembly ' de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be606-108">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="be606-109">ASP.NET Core 5,0 RC1 sürümünde, özelliği paylaşılan çerçeveye başvuran [Microsoft. AspNetCore. components. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) paketinin bir parçası olarak kullanılabilir `Microsoft.AspNetCore.App` .</span><span class="sxs-lookup"><span data-stu-id="be606-109">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="be606-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="be606-110">New behavior</span></span>

<span data-ttu-id="be606-111">ASP.NET Core 5,0 RC2 'de, artık bu özelliği kullanmak için bir NuGet paket başvurusuna gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="be606-111">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="be606-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="be606-112">Reason for change</span></span>

<span data-ttu-id="be606-113">Paylaşılan çerçeveye taşıma, müşterilerin beklediği Kullanıcı deneyimi için daha iyi bir uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="be606-113">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="be606-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="be606-114">Recommended action</span></span>

<span data-ttu-id="be606-115">ASP.NET Core 5,0 RC1 'den yükseltme yapıyorsanız, aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="be606-115">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="be606-116">`Microsoft.AspNetCore.Components.ProtectedBrowserStorage`Paket başvurusunu projeden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="be606-116">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="be606-117">`using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.</span><span class="sxs-lookup"><span data-stu-id="be606-117">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="be606-118">Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .</span><span class="sxs-lookup"><span data-stu-id="be606-118">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="be606-119">ASP.NET Core 5,0 Preview 8 ' den yükseltiyorsanız aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="be606-119">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="be606-120">`Microsoft.AspNetCore.Components.Web.Extensions`Paket başvurusunu projeden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="be606-120">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="be606-121">`using Microsoft.AspNetCore.Components.Web.Extensions;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.</span><span class="sxs-lookup"><span data-stu-id="be606-121">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="be606-122">Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .</span><span class="sxs-lookup"><span data-stu-id="be606-122">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="be606-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="be606-123">Affected APIs</span></span>

<span data-ttu-id="be606-124">Yok</span><span class="sxs-lookup"><span data-stu-id="be606-124">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
