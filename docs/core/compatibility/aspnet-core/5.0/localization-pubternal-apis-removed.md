---
title: "Son değişiklik: Pubternal API 'Ler kaldırıldı"
description: ASP.NET Core 5,0 ' deki, bazı pubternal yerelleştirme API 'Lerinin kaldırıldığı Son değişiklik hakkında bilgi edinin
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 35b6f80569945e54367117446ea96107d6c5199c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497677"
---
# <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="221a8-103">Yerelleştirme: "Pubternal" API 'Leri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="221a8-103">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="221a8-104">ASP.NET Core ortak API yüzeyini daha iyi korumak için bazı :::no-loc text="\"pubternal\""::: Yerelleştirme API 'leri kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="221a8-104">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="221a8-105">Bir :::no-loc text="\"pubternal\""::: API 'nin `public` erişim değiştiricisi vardır ve bir [iç](../../../../csharp/language-reference/keywords/internal.md) amacı gösteren bir ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="221a8-105">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="221a8-106">Tartışma için bkz. [DotNet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).</span><span class="sxs-lookup"><span data-stu-id="221a8-106">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="221a8-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="221a8-107">Version introduced</span></span>

<span data-ttu-id="221a8-108">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="221a8-108">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="221a8-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="221a8-109">Old behavior</span></span>

<span data-ttu-id="221a8-110">Aşağıdaki API 'Ler `public` :</span><span class="sxs-lookup"><span data-stu-id="221a8-110">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="221a8-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri:</span><span class="sxs-lookup"><span data-stu-id="221a8-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a><span data-ttu-id="221a8-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="221a8-112">New behavior</span></span>

<span data-ttu-id="221a8-113">Aşağıdaki listede değişiklikler özetlenmektedir:</span><span class="sxs-lookup"><span data-stu-id="221a8-113">The following list outlines the changes:</span></span>

- <span data-ttu-id="221a8-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`Şimdi geldi `internal` .</span><span class="sxs-lookup"><span data-stu-id="221a8-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="221a8-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`Şimdi geldi `internal` .</span><span class="sxs-lookup"><span data-stu-id="221a8-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="221a8-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri artık şunlardır `internal` :</span><span class="sxs-lookup"><span data-stu-id="221a8-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a><span data-ttu-id="221a8-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="221a8-117">Reason for change</span></span>

<span data-ttu-id="221a8-118">[ASPNET/Duyurular # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)'de daha kapsamlı bir şekilde açıklanmıştı, :::no-loc text="\"pubternal\""::: türler `public` API yüzeyinden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="221a8-118">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="221a8-119">Bu değişiklikler, bu tasarım kararına daha fazla sınıf uyarlar.</span><span class="sxs-lookup"><span data-stu-id="221a8-119">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="221a8-120">Söz konusu sınıflar, takımın iç testi için uzantı noktaları olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="221a8-120">The classes in question were intended as extension points for the team's internal testing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="221a8-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="221a8-121">Recommended action</span></span>

<span data-ttu-id="221a8-122">Büyük olasılıkla, bazı uygulamalar kasıtlı veya yanlışlıkla türlerine bağlı olabilir :::no-loc text="\"pubternal\""::: .</span><span class="sxs-lookup"><span data-stu-id="221a8-122">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="221a8-123">Türlerin dışında nasıl geçiş yapılacağını öğrenmek için [Yeni davranış](#new-behavior) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="221a8-123">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="221a8-124">Ortak API 'nin bu değişiklikten önce izin verilen ancak şimdi olmayan bir senaryo belirlediyseniz, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="221a8-124">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="221a8-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="221a8-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
