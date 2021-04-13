---
title: 'Son değişiklik: Blazor : WebEventDescriptor. EventArgsType özelliği değişti'
description: WebEventDescriptor. EventArgsType özelliğinin, EventName özelliği ile değiştirildiği ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.author: scaddie
ms.date: 02/24/2021
no-loc:
- Blazor
ms.openlocfilehash: ed4bb3d19e6b78d751d24ae640f35c72bd15ed1f
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292307"
---
# <a name="blazor-no-loc-textwebeventdescriptoreventargstype-property-replaced"></a><span data-ttu-id="237e7-103">Blazor: :::no-loc text="WebEventDescriptor.EventArgsType"::: özellik değişti</span><span class="sxs-lookup"><span data-stu-id="237e7-103">Blazor: :::no-loc text="WebEventDescriptor.EventArgsType"::: property replaced</span></span>

<span data-ttu-id="237e7-104"><xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor>Sınıfı, Blazor olayları JavaScript 'ten .net 'e iletişim kurmak için iç protokolün bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="237e7-104">The <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor> class is part of Blazor's internal protocol for communicating events from JavaScript into .NET.</span></span> <span data-ttu-id="237e7-105">Bu sınıf genellikle uygulama kodu tarafından değil, platform yazarları tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="237e7-105">This class isn't typically used by app code, but rather by platform authors.</span></span>

<span data-ttu-id="237e7-106">ASP.NET Core 6,0 ' den başlayarak, <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A> üzerindeki özelliği `WebEventDescriptor` Yeni bir özellik ile değiştiriliyor `EventName` .</span><span class="sxs-lookup"><span data-stu-id="237e7-106">Starting in ASP.NET Core 6.0, the <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A> property on `WebEventDescriptor` is being replaced by a new `EventName` property.</span></span> <span data-ttu-id="237e7-107">Bu değişiklik, alt düzey platform uygulaması ayrıntısı olduğundan, herhangi bir uygulama kodunu etkilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="237e7-107">This change is unlikely to affect any app code, as it's a low-level platform implementation detail.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="237e7-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="237e7-108">Version introduced</span></span>

<span data-ttu-id="237e7-109">ASP.NET Core 6,0</span><span class="sxs-lookup"><span data-stu-id="237e7-109">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="237e7-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="237e7-110">Old behavior</span></span>

<span data-ttu-id="237e7-111">ASP.NET Core 5,0 ve önceki sürümlerde özelliği, `EventArgsType` Blazor DOM olay türleri grupları için standart olmayan,-özel kategori adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="237e7-111">In ASP.NET Core 5.0 and earlier, the property `EventArgsType` describes a nonstandard, Blazor-specific category name for groups of DOM event types.</span></span> <span data-ttu-id="237e7-112">Örneğin, `click` ve `mousedown` olaylarının her ikisi de bir değeriyle eşlenmiş `EventArgsType` `mouse` .</span><span class="sxs-lookup"><span data-stu-id="237e7-112">For example, the `click` and `mousedown` events were both mapped to an `EventArgsType` value of `mouse`.</span></span> <span data-ttu-id="237e7-113">Benzer şekilde,, `cut` `copy` , ve `paste` olayları `EventArgsType` değerine eşlenir `clipboard` .</span><span class="sxs-lookup"><span data-stu-id="237e7-113">Similarly, `cut`, `copy`, and `paste` events are mapped to an `EventArgsType` value of `clipboard`.</span></span> <span data-ttu-id="237e7-114">Bu kategori adları, gelen olay bağımsız değişkenleri verilerinin serisini kaldırmada kullanılacak .NET türünü belirlemekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="237e7-114">These category names are used to determine the .NET type to use for deserializing the incoming event arguments data.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="237e7-115">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="237e7-115">New behavior</span></span>

<span data-ttu-id="237e7-116">ASP.NET Core 6,0 ' den başlayarak, yeni özellik `EventName` yalnızca özgün etkinliğin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="237e7-116">Starting in ASP.NET Core 6.0, the new property `EventName` only specifies the original event's name.</span></span> <span data-ttu-id="237e7-117">Örneğin,,,, `click` `mousedown` `cut` `copy` veya `paste` .</span><span class="sxs-lookup"><span data-stu-id="237e7-117">For example, `click`, `mousedown`, `cut`, `copy`, or `paste`.</span></span> <span data-ttu-id="237e7-118">Artık Blazor belirli bir kategori adı sağlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="237e7-118">There's no longer a need to supply a Blazor-specific category name.</span></span> <span data-ttu-id="237e7-119">Bu nedenle, eski özellik `EventArgsType` kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="237e7-119">For that reason, the old property `EventArgsType` is removed.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="237e7-120">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="237e7-120">Reason for change</span></span>

<span data-ttu-id="237e7-121">Çekme isteği [DotNet/aspnetcore # 29993](https://github.com/dotnet/aspnetcore/pull/29993)içinde özel olay bağımsız değişkeni sınıfları için destek sunuldu.</span><span class="sxs-lookup"><span data-stu-id="237e7-121">In pull request [dotnet/aspnetcore#29993](https://github.com/dotnet/aspnetcore/pull/29993), support for custom event arguments classes was introduced.</span></span> <span data-ttu-id="237e7-122">Bu desteğin bir parçası olarak Framework artık önceden tanımlanmış bir kategori kümesine bağlı olan tüm olaylara dayanmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="237e7-122">As part of this support, the framework no longer relies on all events fitting into a predefined set of categories.</span></span> <span data-ttu-id="237e7-123">Artık çerçevenin yalnızca özgün olay adını bilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="237e7-123">The framework now only needs to know the original event name.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="237e7-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="237e7-124">Recommended action</span></span>

<span data-ttu-id="237e7-125">Uygulama kodu etkilenmemelidir ve değişikliğe gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="237e7-125">App code should be unaffected and doesn't need to change.</span></span>

<span data-ttu-id="237e7-126">Özel bir Blazor işleme platformu oluşturuyorsanız, içindeki olayları gönderme mekanizmasını güncelleştirmeniz gerekebilir `Renderer` .</span><span class="sxs-lookup"><span data-stu-id="237e7-126">If building a custom Blazor rendering platform, you may need to update the mechanism for dispatching events into the `Renderer`.</span></span> <span data-ttu-id="237e7-127">Olay kategorileri hakkındaki tüm sabit kodlanmış kuralları, özgün, Ham olay adını sağlayan daha basit bir mantık ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="237e7-127">Replace any hardcoded rules about event categories with simpler logic that supplies the original, raw event name.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="237e7-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="237e7-128">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`P:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType`

-->
