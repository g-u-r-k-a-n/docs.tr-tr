---
title: 'Son değişiklik: SignalR: MessagePack hub protokol seçenekleri türü değişti'
description: "ASP.NET Core 5,0 ' deki, SignalR: MessagePack hub protokol seçenekleri türü değiştirilen Son değişiklik hakkında bilgi edinin"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5a1a3728e4f842074c80f5063dcfe47ad8858674
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497924"
---
# <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="c4c43-103">SignalR: MessagePack Hub Protokolü seçenekleri türü değiştirildi</span><span class="sxs-lookup"><span data-stu-id="c4c43-103">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="c4c43-104">ASP.NET Core SignalR MessagePack hub protokol seçenekleri türü, öğesinden `IList<MessagePack.IFormatterResolver>` [MessagePack](https://www.nuget.org/packages/MessagePack) kitaplığının `MessagePackSerializerOptions` türüne değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="c4c43-104">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="c4c43-105">Bu değişiklik hakkında tartışma için bkz. [DotNet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).</span><span class="sxs-lookup"><span data-stu-id="c4c43-105">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c4c43-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c4c43-106">Version introduced</span></span>

<span data-ttu-id="c4c43-107">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="c4c43-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="c4c43-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c4c43-108">Old behavior</span></span>

<span data-ttu-id="c4c43-109">Seçeneklere aşağıdaki örnekte gösterildiği gibi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4c43-109">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="c4c43-110">Ve seçenekleri aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c4c43-110">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

## <a name="new-behavior"></a><span data-ttu-id="c4c43-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c4c43-111">New behavior</span></span>

<span data-ttu-id="c4c43-112">Seçeneklere aşağıdaki örnekte gösterildiği gibi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c4c43-112">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="c4c43-113">Ve seçenekleri aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c4c43-113">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

## <a name="reason-for-change"></a><span data-ttu-id="c4c43-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c4c43-114">Reason for change</span></span>

<span data-ttu-id="c4c43-115">Bu değişiklik, [ASPNET/Duyurular # 404](https://github.com/aspnet/Announcements/issues/404)' de duyurulan ileti paketi v2. x ' e taşınmasına yönelik bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="c4c43-115">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="c4c43-116">V2. x kitaplığı, kullanımı daha kolay olan bir seçenekler API 'SI ekledi ve daha önce sunulan listesinden daha fazla özellik sağlar `MessagePack.IFormatterResolver` .</span><span class="sxs-lookup"><span data-stu-id="c4c43-116">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c4c43-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c4c43-117">Recommended action</span></span>

<span data-ttu-id="c4c43-118">Bu son değişiklik, üzerinde değer yapılandıran herkesi etkiler <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .</span><span class="sxs-lookup"><span data-stu-id="c4c43-118">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="c4c43-119">ASP.NET Core SignalR MessagePack hub protokolünü kullanıyorsanız ve seçenekleri değiştiriyorsanız, kullanımınızı yukarıda gösterildiği gibi yeni seçenekler API 'sini kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c4c43-119">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c4c43-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c4c43-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
