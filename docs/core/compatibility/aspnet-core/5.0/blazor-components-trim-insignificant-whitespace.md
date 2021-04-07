---
title: 'Son değişiklik: Blazor: derleme sırasında bileşenlerden çok önemli olan boşluk'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: derleme zamanında bileşenden kırpılan önemli boşluk"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: d29171c43e587eba648de3f877e1cbb1c7156499
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498210"
---
# <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="b6f4c-103">Blazor: derleme zamanında bileşenlerden çok önemli olan boşluk</span><span class="sxs-lookup"><span data-stu-id="b6f4c-103">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="b6f4c-104">ASP.NET Core 5,0 Preview 7 ' den başlayarak, Razor derleyicisi derleme zamanında Blazor Components (*. Razor* dosyaları) içinde önemli olmayan boşluğu atlar.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-104">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="b6f4c-105">Tartışma için bkz. sorun [DotNet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).</span><span class="sxs-lookup"><span data-stu-id="b6f4c-105">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b6f4c-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b6f4c-106">Version introduced</span></span>

<span data-ttu-id="b6f4c-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="b6f4c-107">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b6f4c-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b6f4c-108">Old behavior</span></span>

<span data-ttu-id="b6f4c-109">Blazor Server ve Blazor WebAssembly 'in 3. x sürümlerinde, bir bileşenin kaynak kodunda boşluk kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-109">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="b6f4c-110">Görsel efekt olmasa bile yalnızca boşluk metin düğümleri tarayıcının Belge Nesne Modeli (DOM) içinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-110">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="b6f4c-111">Aşağıdaki Blazor bileşen kodunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b6f4c-111">Consider the following Blazor component code:</span></span>

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

<span data-ttu-id="b6f4c-112">Yukarıdaki örnek iki boşluk düğümü oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b6f4c-112">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="b6f4c-113">`@foreach`Kod bloğunun dışında.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-113">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="b6f4c-114">Öğesinin etrafında `<li>` .</span><span class="sxs-lookup"><span data-stu-id="b6f4c-114">Around the `<li>` element.</span></span>
* <span data-ttu-id="b6f4c-115">Çıktı etrafında `@item.Text` .</span><span class="sxs-lookup"><span data-stu-id="b6f4c-115">Around the `@item.Text` output.</span></span>

<span data-ttu-id="b6f4c-116">100 öğe içeren bir liste 402 boşluk düğümlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-116">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="b6f4c-117">Diğer bir deyişle, bir boşluk düğümlerinin hiçbiri işlenmiş çıktıyı görsel olarak etkilemese de, işlenen tüm düğümlerin yarısı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-117">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="b6f4c-118">Bileşenler için statik HTML işlenirken, bir etiket içindeki boşluk korunmaz.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-118">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="b6f4c-119">Örneğin, aşağıdaki bileşenin kaynağını görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="b6f4c-119">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="b6f4c-120">Boşluk korunmaz.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-120">Whitespace isn't preserved.</span></span> <span data-ttu-id="b6f4c-121">Önceden işlenmiş çıkış:</span><span class="sxs-lookup"><span data-stu-id="b6f4c-121">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

## <a name="new-behavior"></a><span data-ttu-id="b6f4c-122">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b6f4c-122">New behavior</span></span>

<span data-ttu-id="b6f4c-123">`@preservewhitespace`Yönergesi değerle kullanılmadığı takdirde, şu `true` durumlarda boşluk düğümleri kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="b6f4c-123">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="b6f4c-124">Bir öğe içinde başında veya sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-124">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="b6f4c-125">Bir parametre içinde başında veya sonunda görüntülenir `RenderFragment` .</span><span class="sxs-lookup"><span data-stu-id="b6f4c-125">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="b6f4c-126">Örneğin, alt içerik başka bir bileşene geçirilmekte.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-126">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="b6f4c-127">Ve gibi bir C# kod bloğunun önüne veya uygulayın `@if` `@foreach` .</span><span class="sxs-lookup"><span data-stu-id="b6f4c-127">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b6f4c-128">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b6f4c-128">Reason for change</span></span>

<span data-ttu-id="b6f4c-129">ASP.NET Core 5,0 ' deki Blazor için bir hedef, oluşturma ve dağıtma performansını artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-129">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="b6f4c-130">Kıyaslamalar halinde işleme süresinin yüzde 40 ' una kadar tüketilen çok önemli boşluk ağacı düğümleri.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-130">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b6f4c-131">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b6f4c-131">Recommended action</span></span>

<span data-ttu-id="b6f4c-132">Çoğu durumda, işlenmiş bileşenin görsel düzeni etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-132">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="b6f4c-133">Ancak, boşluk kaldırma, gibi bir CSS kuralı kullanırken işlenen çıktıyı etkileyebilir `white-space: pre` .</span><span class="sxs-lookup"><span data-stu-id="b6f4c-133">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="b6f4c-134">Bu performans iyileştirmesini devre dışı bırakmak ve boşluğu korumak için aşağıdaki eylemlerden birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="b6f4c-134">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="b6f4c-135">`@preservewhitespace true`Tercihi belirli bir bileşene uygulamak için *. Razor* dosyasının en üstündeki yönergeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-135">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="b6f4c-136">`@preservewhitespace true`Tercihi bir alt dizinin tamamına veya tüm projeye uygulamak için bir *_Imports. Razor* dosyası içinde yönergesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-136">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="b6f4c-137">Çoğu durumda, uygulamalar genellikle normal şekilde davranmaya devam edecek şekilde hiçbir eylem gerekmez (ancak daha hızlı).</span><span class="sxs-lookup"><span data-stu-id="b6f4c-137">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="b6f4c-138">Ortaya çıkan boşluk belirli bir bileşen için herhangi bir soruna neden oluyorsa, `@preservewhitespace true` Bu iyileştirmeyi devre dışı bırakmak için o bileşende kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6f4c-138">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b6f4c-139">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b6f4c-139">Affected APIs</span></span>

<span data-ttu-id="b6f4c-140">Yok</span><span class="sxs-lookup"><span data-stu-id="b6f4c-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
