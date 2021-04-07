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
# <a name="signalr-messagepack-hub-protocol-options-type-changed"></a>SignalR: MessagePack Hub Protokolü seçenekleri türü değiştirildi

ASP.NET Core SignalR MessagePack hub protokol seçenekleri türü, öğesinden `IList<MessagePack.IFormatterResolver>` [MessagePack](https://www.nuget.org/packages/MessagePack) kitaplığının `MessagePackSerializerOptions` türüne değişmiştir.

Bu değişiklik hakkında tartışma için bkz. [DotNet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 4

## <a name="old-behavior"></a>Eski davranış

Seçeneklere aşağıdaki örnekte gösterildiği gibi ekleyebilirsiniz:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

Ve seçenekleri aşağıdaki gibi değiştirin:

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

## <a name="new-behavior"></a>Yeni davranış

Seçeneklere aşağıdaki örnekte gösterildiği gibi ekleyebilirsiniz:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

Ve seçenekleri aşağıdaki gibi değiştirin:

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

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, [ASPNET/Duyurular # 404](https://github.com/aspnet/Announcements/issues/404)' de duyurulan ileti paketi v2. x ' e taşınmasına yönelik bir parçasıdır. V2. x kitaplığı, kullanımı daha kolay olan bir seçenekler API 'SI ekledi ve daha önce sunulan listesinden daha fazla özellik sağlar `MessagePack.IFormatterResolver` .

## <a name="recommended-action"></a>Önerilen eylem

Bu son değişiklik, üzerinde değer yapılandıran herkesi etkiler <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> . ASP.NET Core SignalR MessagePack hub protokolünü kullanıyorsanız ve seçenekleri değiştiriyorsanız, kullanımınızı yukarıda gösterildiği gibi yeni seçenekler API 'sini kullanacak şekilde güncelleştirin.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
