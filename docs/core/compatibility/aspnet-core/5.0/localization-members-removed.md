---
title: 'Son değişiklik: yerelleştirme: ResourceManagerWithCultureStringLocalizer Class ve WithCulture arabirim üyesi kaldırıldı'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: ResourceManagerWithCultureStringLocalizer Class ve WithCulture arabirim üyesi kaldırıldı"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 0c02a0e0cc78e4bfbf6f4a1ba5951cd13b56fe0c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498093"
---
# <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="123b3-103">Yerelleştirme: ResourceManagerWithCultureStringLocalizer Class ve WithCulture arabirim üyesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="123b3-103">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="123b3-104">.NET 5,0 Preview 1 ' de [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) Class ve [withculture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) yöntemi kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="123b3-104">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="123b3-105">Bağlam için bkz. [ASPNET/Duyurular # 346](https://github.com/aspnet/Announcements/issues/346) ve [DotNet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="123b3-105">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="123b3-106">Bu değişiklik hakkında tartışma için bkz. [DotNet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="123b3-106">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="123b3-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="123b3-107">Version introduced</span></span>

<span data-ttu-id="123b3-108">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="123b3-108">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="123b3-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="123b3-109">Old behavior</span></span>

<span data-ttu-id="123b3-110">`ResourceManagerWithCultureStringLocalizer`Sınıfı ve `ResourceManagerStringLocalizer.WithCulture` yöntemi [.NET Core 3,0 Preview 3 ve sonraki sürümlerde kullanılmıyor](../../3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span><span class="sxs-lookup"><span data-stu-id="123b3-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](../../3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

## <a name="new-behavior"></a><span data-ttu-id="123b3-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="123b3-111">New behavior</span></span>

<span data-ttu-id="123b3-112">`ResourceManagerWithCultureStringLocalizer`Sınıfı ve `ResourceManagerStringLocalizer.WithCulture` yöntemi .NET 5,0 Preview 1 ' de kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="123b3-112">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="123b3-113">Yapılan değişikliklerin envanterini görmek için [DotNet/Extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files)konumundaki çekme isteğine bakın.</span><span class="sxs-lookup"><span data-stu-id="123b3-113">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="123b3-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="123b3-114">Reason for change</span></span>

<span data-ttu-id="123b3-115">[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) sınıfı ve [Resourcemanagerstringlocalizer. withculture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) yöntemi genellikle yerelleştirme kullanıcıları için karışıklık kaynaklarıdır.</span><span class="sxs-lookup"><span data-stu-id="123b3-115">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="123b3-116">Özel bir uygulama oluşturulurken karışıklık özellikle yüksek <xref:Microsoft.Extensions.Localization.IStringLocalizer> .</span><span class="sxs-lookup"><span data-stu-id="123b3-116">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="123b3-117">Bu sınıf ve yöntem, tüketicilere bir `IStringLocalizer` Örneğin "dil başına, kaynak başına" olması beklenme izlenimi verir.</span><span class="sxs-lookup"><span data-stu-id="123b3-117">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="123b3-118">Gerçekte, örnek yalnızca "kaynak başına" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="123b3-118">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="123b3-119">Çalışma zamanında, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özelliği kullanılacak dili belirler.</span><span class="sxs-lookup"><span data-stu-id="123b3-119">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="123b3-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="123b3-120">Recommended action</span></span>

<span data-ttu-id="123b3-121">`ResourceManagerWithCultureStringLocalizer`Sınıfını ve yöntemini kullanmayı durdurun `ResourceManagerStringLocalizer.WithCulture` .</span><span class="sxs-lookup"><span data-stu-id="123b3-121">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="123b3-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="123b3-122">Affected APIs</span></span>

- [<span data-ttu-id="123b3-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="123b3-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="123b3-124">ResourceManagerStringLocalizer. WithCulture</span><span class="sxs-lookup"><span data-stu-id="123b3-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
