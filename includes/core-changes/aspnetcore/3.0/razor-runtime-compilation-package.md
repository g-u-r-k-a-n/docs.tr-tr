---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032852"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="c6621-101">Razor: çalışma zamanı derlemesi bir pakete taşındı</span><span class="sxs-lookup"><span data-stu-id="c6621-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="c6621-102">Razor görünümlerinin ve Razor Pages çalışma zamanı derlenmesi desteği ayrı bir pakete taşındı.</span><span class="sxs-lookup"><span data-stu-id="c6621-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c6621-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c6621-103">Version introduced</span></span>

<span data-ttu-id="c6621-104">3,0</span><span class="sxs-lookup"><span data-stu-id="c6621-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c6621-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c6621-105">Old behavior</span></span>

<span data-ttu-id="c6621-106">Çalışma zamanı derlemesi ek paketlere gerek olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6621-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c6621-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c6621-107">New behavior</span></span>

<span data-ttu-id="c6621-108">İşlevsellik, [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) paketine taşınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6621-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="c6621-109">Aşağıdaki API 'Ler, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` çalışma zamanı derlemesini desteklemek için daha önce ' de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6621-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="c6621-110">API 'Ler ile artık kullanılabilir `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions` .</span><span class="sxs-lookup"><span data-stu-id="c6621-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="c6621-111">`RazorViewEngineOptions.FileProviders` Artık `MvcRazorRuntimeCompilationOptions.FileProviders`</span><span class="sxs-lookup"><span data-stu-id="c6621-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="c6621-112">`RazorViewEngineOptions.AdditionalCompilationReferences` Artık `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span><span class="sxs-lookup"><span data-stu-id="c6621-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="c6621-113">Ayrıca, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6621-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="c6621-114">Dosya değişikliklerinde yeniden derleme, pakete başvurarak varsayılan olarak etkindir `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` .</span><span class="sxs-lookup"><span data-stu-id="c6621-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c6621-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c6621-115">Reason for change</span></span>

<span data-ttu-id="c6621-116">Bu değişiklik, Roslyn 'de ASP.NET Core paylaşılan çerçeve bağımlılığını kaldırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c6621-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c6621-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c6621-117">Recommended action</span></span>

<span data-ttu-id="c6621-118">Razor dosyalarının çalışma zamanı derlemesini veya yeniden derlemesini gerektiren uygulamalar aşağıdaki adımları almalıdır:</span><span class="sxs-lookup"><span data-stu-id="c6621-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="c6621-119">Pakete bir başvuru ekleyin `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` .</span><span class="sxs-lookup"><span data-stu-id="c6621-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="c6621-120">`Startup.ConfigureServices`İçin bir çağrı içerecek şekilde projenin metodunu güncelleştirin `AddRazorRuntimeCompilation` .</span><span class="sxs-lookup"><span data-stu-id="c6621-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="c6621-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c6621-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="c6621-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="c6621-122">Category</span></span>

<span data-ttu-id="c6621-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6621-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c6621-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c6621-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
