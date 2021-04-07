---
title: 'Son değişiklik: SignalR: MessagePack hub Protokolü MessagePack 2. x paketine taşındı'
description: "ASP.NET Core 5,0 ' deki, SignalR: MessagePack hub protokolünü MessagePack 2. x paketine taşınan Son değişiklik hakkında bilgi edinin"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 6851c4fdbaab61e7655dd71ba3c21b8835b2b855
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497118"
---
# <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="78627-103">SignalR: MessagePack 2. x paketine taşınan MessagePack hub Protokolü</span><span class="sxs-lookup"><span data-stu-id="78627-103">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="78627-104">ASP.NET Core SignalR [MessagePack hub Protokolü](/aspnet/core/signalr/messagepackhubprotocol) MessagePack serileştirme Için [MessagePack NuGet paketini](https://www.nuget.org/packages/MessagePack) kullanır.</span><span class="sxs-lookup"><span data-stu-id="78627-104">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="78627-105">ASP.NET Core 5,0 paketi 1. x sürümünden en son 2. x paketi sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="78627-105">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="78627-106">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692).</span><span class="sxs-lookup"><span data-stu-id="78627-106">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="78627-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="78627-107">Version introduced</span></span>

<span data-ttu-id="78627-108">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="78627-108">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="78627-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="78627-109">Old behavior</span></span>

<span data-ttu-id="78627-110">ASP.NET Core SignalR, MessagePack iletilerini seri hale getirmek ve seri durumdan çıkarmak için MessagePack 1. x paketini kullandı.</span><span class="sxs-lookup"><span data-stu-id="78627-110">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="78627-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="78627-111">New behavior</span></span>

<span data-ttu-id="78627-112">ASP.NET Core SignalR, MessagePack iletilerinin serileştirilmek ve serisini kaldırmak için MessagePack 2. x paketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="78627-112">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="78627-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="78627-113">Reason for change</span></span>

<span data-ttu-id="78627-114">MessagePack 2. x paketindeki en son geliştirmeler yararlı işlevsellik ekler.</span><span class="sxs-lookup"><span data-stu-id="78627-114">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="78627-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="78627-115">Recommended action</span></span>

<span data-ttu-id="78627-116">Bu son değişiklik şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="78627-116">This breaking change applies when:</span></span>

* <span data-ttu-id="78627-117">Değerleri ayarlama veya yapılandırma <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .</span><span class="sxs-lookup"><span data-stu-id="78627-117">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="78627-118">MessagePack API 'Lerini doğrudan kullanarak ve aynı projede ASP.NET Core SignalR MessagePack hub protokolünü kullanarak.</span><span class="sxs-lookup"><span data-stu-id="78627-118">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="78627-119">Önceki sürüm yerine daha yeni bir sürüm yüklenecektir.</span><span class="sxs-lookup"><span data-stu-id="78627-119">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="78627-120">Paket yazarlarından geçiş kılavuzu için bkz. [MessagePack v1. x 'Ten MessagePack v2. x 'e](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)geçiş.</span><span class="sxs-lookup"><span data-stu-id="78627-120">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="78627-121">İleti serileştirme ve seri durumdan çıkarma özelliklerinin bazı yönleri etkilenir.</span><span class="sxs-lookup"><span data-stu-id="78627-121">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="78627-122">Özellikle, [DateTime değerlerinin serileştirilme şekli için davranış değişiklikleri](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)vardır.</span><span class="sxs-lookup"><span data-stu-id="78627-122">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="78627-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="78627-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
