---
title: 'Son değişiklik: Blazor: NuGet paketlerinin hedef çerçevesi değiştirildi'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: NuGet paketlerinin hedef çerçevesi değişti"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 02945c223410860c9336b6046afe54cacce878dd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498197"
---
# <a name="blazor-target-framework-of-nuget-packages-changed"></a><span data-ttu-id="306b3-103">Blazor: NuGet paketlerinin hedef çerçevesi değiştirildi</span><span class="sxs-lookup"><span data-stu-id="306b3-103">Blazor: Target framework of NuGet packages changed</span></span>

<span data-ttu-id="306b3-104">Blazor 3,2 WebAssembly projeleri .NET Standard 2,1 () hedefine derlendi `<TargetFramework>netstandard2.1</TargetFramework>` .</span><span class="sxs-lookup"><span data-stu-id="306b3-104">Blazor 3.2 WebAssembly projects were compiled to target .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`).</span></span> <span data-ttu-id="306b3-105">ASP.NET Core 5,0 ' de, hem Blazor Server hem de Blazor WebAssembly projeleri .NET 5,0 () öğesini hedefleyin `<TargetFramework>net5.0</TargetFramework>` .</span><span class="sxs-lookup"><span data-stu-id="306b3-105">In ASP.NET Core 5.0, both Blazor Server and Blazor WebAssembly projects target .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`).</span></span> <span data-ttu-id="306b3-106">Hedef Framework değişikliğine daha iyi uyum sağlamak için aşağıdaki Blazor paketleri artık .NET Standard 2,1 ' i hedeflemiyor:</span><span class="sxs-lookup"><span data-stu-id="306b3-106">To better align with the target framework change, the following Blazor packages no longer target .NET Standard 2.1:</span></span>

* [<span data-ttu-id="306b3-107">Microsoft. AspNetCore. Components</span><span class="sxs-lookup"><span data-stu-id="306b3-107">Microsoft.AspNetCore.Components</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [<span data-ttu-id="306b3-108">Microsoft. AspNetCore. components. Authorization</span><span class="sxs-lookup"><span data-stu-id="306b3-108">Microsoft.AspNetCore.Components.Authorization</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [<span data-ttu-id="306b3-109">Microsoft. AspNetCore. components. Forms</span><span class="sxs-lookup"><span data-stu-id="306b3-109">Microsoft.AspNetCore.Components.Forms</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [<span data-ttu-id="306b3-110">Microsoft. AspNetCore. components. Web</span><span class="sxs-lookup"><span data-stu-id="306b3-110">Microsoft.AspNetCore.Components.Web</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [<span data-ttu-id="306b3-111">Microsoft. AspNetCore. components. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="306b3-111">Microsoft.AspNetCore.Components.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [<span data-ttu-id="306b3-112">Microsoft. AspNetCore. components. WebAssembly. Authentication</span><span class="sxs-lookup"><span data-stu-id="306b3-112">Microsoft.AspNetCore.Components.WebAssembly.Authentication</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [<span data-ttu-id="306b3-113">Microsoft.JSbirlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="306b3-113">Microsoft.JSInterop</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop)
* [<span data-ttu-id="306b3-114">Microsoft.JSInterop. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="306b3-114">Microsoft.JSInterop.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [<span data-ttu-id="306b3-115">Microsoft. Authentication. WebAssembly. msal</span><span class="sxs-lookup"><span data-stu-id="306b3-115">Microsoft.Authentication.WebAssembly.Msal</span></span>](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

<span data-ttu-id="306b3-116">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424).</span><span class="sxs-lookup"><span data-stu-id="306b3-116">For discussion, see GitHub issue [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="306b3-117">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="306b3-117">Version introduced</span></span>

<span data-ttu-id="306b3-118">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="306b3-118">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="306b3-119">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="306b3-119">Old behavior</span></span>

<span data-ttu-id="306b3-120">Blazor 3,1 ve 3,2 ' de, paketler .NET Standard 2,1 ve .NET Core 3,1 ' i hedefler.</span><span class="sxs-lookup"><span data-stu-id="306b3-120">In Blazor 3.1 and 3.2, packages target .NET Standard 2.1 and .NET Core 3.1.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="306b3-121">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="306b3-121">New behavior</span></span>

<span data-ttu-id="306b3-122">ASP.NET Core 5,0 ' de, paketler .NET 5,0 ' i hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="306b3-122">In ASP.NET Core 5.0, packages target .NET 5.0.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="306b3-123">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="306b3-123">Reason for change</span></span>

<span data-ttu-id="306b3-124">.NET hedef Framework gereksinimleriyle daha iyi uyum sağlamak için değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="306b3-124">The change was made to better align with .NET target framework requirements.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="306b3-125">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="306b3-125">Recommended action</span></span>

<span data-ttu-id="306b3-126">Blazor 3,2 WebAssembly projeleri, paket başvurularını 5. x.x. güncelleştirme kapsamında .NET 5,0 ' i hedeflemelidir.</span><span class="sxs-lookup"><span data-stu-id="306b3-126">Blazor 3.2 WebAssembly projects should target .NET 5.0 as part of updating their package references to 5.x.x.</span></span> <span data-ttu-id="306b3-127">Bu paketlerin birine başvuran kitaplıklar, gereksinimlerine bağlı olarak .NET 5,0 veya birden çok hedef hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="306b3-127">Libraries that reference one of these packages can either target .NET 5.0 or multi-target depending on their requirements.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="306b3-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="306b3-128">Affected APIs</span></span>

<span data-ttu-id="306b3-129">Yok</span><span class="sxs-lookup"><span data-stu-id="306b3-129">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
