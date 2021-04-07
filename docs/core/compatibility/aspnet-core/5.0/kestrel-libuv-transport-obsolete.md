---
title: 'Son değişiklik: Kestrel: libuv taşıması eski olarak işaretlendi'
description: "Kestrel adlı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: libuv taşıması eski olarak işaretlendi"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7edec666df729edbffe60b6017a2b8ee5f46ae67
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497638"
---
# <a name="kestrel-libuv-transport-marked-as-obsolete"></a><span data-ttu-id="c860e-103">Kestrel: Libuv taşıması kullanımdan kaldırıldı olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="c860e-103">Kestrel: Libuv transport marked as obsolete</span></span>

<span data-ttu-id="c860e-104">Önceki ASP.NET Core sürümleri, zaman uyumsuz giriş ve çıktının nasıl gerçekleştirildiği hakkında bir uygulama ayrıntısı olarak libuv kullandı.</span><span class="sxs-lookup"><span data-stu-id="c860e-104">Earlier versions of ASP.NET Core used Libuv as an implementation detail of how asynchronous input and output was performed.</span></span> <span data-ttu-id="c860e-105">ASP.NET Core 2,0 ' de, alternatif bir <xref:System.Net.Sockets.Socket> tabanlı Aktarım geliştirdik.</span><span class="sxs-lookup"><span data-stu-id="c860e-105">In ASP.NET Core 2.0, an alternative, <xref:System.Net.Sockets.Socket>-based transport was developed.</span></span> <span data-ttu-id="c860e-106">ASP.NET Core 2,1 ' de, Kestrel `Socket` Varsayılan olarak tabanlı aktarımı kullanmaya geçti.</span><span class="sxs-lookup"><span data-stu-id="c860e-106">In ASP.NET Core 2.1, Kestrel switched to using the `Socket`-based transport by default.</span></span> <span data-ttu-id="c860e-107">Uyumluluk nedenleriyle libuv desteği korunmıştı.</span><span class="sxs-lookup"><span data-stu-id="c860e-107">Libuv support was maintained for compatibility reasons.</span></span>

<span data-ttu-id="c860e-108">Bu noktada, tabanlı `Socket` taşımanın kullanımı libuv aktarımından çok daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="c860e-108">At this point, use of the `Socket`-based transport is far more common than the Libuv transport.</span></span> <span data-ttu-id="c860e-109">Bu nedenle, libuv desteği .NET 5,0 ' de kullanılmıyor olarak işaretlenir ve tamamen .NET 6,0 ' de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c860e-109">Consequently, Libuv support is marked as obsolete in .NET 5.0 and will be removed entirely in .NET 6.0.</span></span>

<span data-ttu-id="c860e-110">Bu değişikliğin bir parçası olarak, .NET 5,0 zaman diliminde yeni işletim sistemi platformları (Windows ARM64 gibi) için libuv desteği eklenmez.</span><span class="sxs-lookup"><span data-stu-id="c860e-110">As part of this change, Libuv support for new operating system platforms (like Windows ARM64) won't be added in the .NET 5.0 timeframe.</span></span>

<span data-ttu-id="c860e-111">Libuv aktarımının kullanılması gereken sorunları engelleme hakkında tartışmak için, [DotNet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409)adresindeki GitHub sorununa bakın.</span><span class="sxs-lookup"><span data-stu-id="c860e-111">For discussion on blocking issues that require the use of the Libuv transport, see the GitHub issue at [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c860e-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c860e-112">Version introduced</span></span>

<span data-ttu-id="c860e-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="c860e-113">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="c860e-114">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c860e-114">Old behavior</span></span>

<span data-ttu-id="c860e-115">Libuv API 'Leri eski olarak işaretlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="c860e-115">The Libuv APIs aren't marked as obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="c860e-116">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c860e-116">New behavior</span></span>

<span data-ttu-id="c860e-117">Libuv API 'Leri eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="c860e-117">The Libuv APIs are marked as obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c860e-118">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c860e-118">Reason for change</span></span>

<span data-ttu-id="c860e-119">`Socket`-Tabanlı Aktarım varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c860e-119">The `Socket`-based transport is the default.</span></span> <span data-ttu-id="c860e-120">Libuv taşımasını kullanmaya devam etmek için etkileyici bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="c860e-120">There aren't any compelling reasons to continue using the Libuv transport.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c860e-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c860e-121">Recommended action</span></span>

<span data-ttu-id="c860e-122">[Libuv paketi](https://www.nuget.org/packages/Libuv) ve genişletme yöntemlerinin kullanımını durdur.</span><span class="sxs-lookup"><span data-stu-id="c860e-122">Discontinue use of the [Libuv package](https://www.nuget.org/packages/Libuv) and extension methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c860e-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c860e-123">Affected APIs</span></span>

- [<span data-ttu-id="c860e-124">WebHostBuilderLibuvExtensions</span><span class="sxs-lookup"><span data-stu-id="c860e-124">WebHostBuilderLibuvExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [<span data-ttu-id="c860e-125">WebHostBuilderLibuvExtensions. UseLibuv</span><span class="sxs-lookup"><span data-stu-id="c860e-125">WebHostBuilderLibuvExtensions.UseLibuv</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [<span data-ttu-id="c860e-126">Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions</span><span class="sxs-lookup"><span data-stu-id="c860e-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [<span data-ttu-id="c860e-127">Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions. ThreadCount</span><span class="sxs-lookup"><span data-stu-id="c860e-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [<span data-ttu-id="c860e-128">Microsoft. AspNetCore. Server. Kestrel. Transport. Lıbuv. LibuvTransportOptions. NoDelay</span><span class="sxs-lookup"><span data-stu-id="c860e-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [<span data-ttu-id="c860e-129">Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions. MaxWriteBufferSize</span><span class="sxs-lookup"><span data-stu-id="c860e-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [<span data-ttu-id="c860e-130">Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions. MaxReadBufferSize</span><span class="sxs-lookup"><span data-stu-id="c860e-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
