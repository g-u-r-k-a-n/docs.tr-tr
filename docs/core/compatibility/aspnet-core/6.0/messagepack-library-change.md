---
title: 'Son değişiklik: SignalR-Protocol-msgpack paketindeki MessagePack kitaplığı değiştirildi'
description: ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinmek için MessagePack kitaplığı 'nın değiştirildiği ve pakette iki seçenek kaldırılmış @microsoft/signalr-protocol-msgpack .
ms.date: 04/07/2021
ms.openlocfilehash: 62f853cbed0904e278e25f231528845baac9f71d
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107260047"
---
# <a name="changed-messagepack-library-in-microsoftsignalr-protocol-msgpack"></a>İçinde MessagePack kitaplığı değiştirildi @microsoft/signalr-protocol-msgpack

[@microsoft/signalr-protocol-msgpack](https://www.npmjs.com/package/@microsoft/signalr-protocol-msgpack)NPM paketi artık yerine başvuruyordur `@msgpack/msgpack` `msgpack5` . Ayrıca, isteğe bağlı olarak, isteğe bağlı olarak içine geçirilebilecek Seçenekler `MessagePackHubProtocol` değişmiştir. `MessagePackOptions.disableTimestampEncoding`Ve `MessagePackOptions.forceFloat64` özellikleri kaldırılmıştır ve bazı yeni seçenekler eklenmiştir.

Tartışma için bkz <https://github.com/dotnet/aspnetcore/issues/30471> ..

## <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 6,0

## <a name="old-behavior"></a>Eski davranış

Önceki sürümlerde, tarayıcıda [MessagePack hub protokolünü](/aspnet/core/signalr/messagepackhubprotocol) kullanmak için üç komut dosyası başvurusu eklemeniz gerekir:

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/msgpack5/msgpack5.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

## <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 6 ' dan başlayarak, tarayıcıda [MessagePack hub protokolünü](/aspnet/core/signalr/messagepackhubprotocol) kullanmak için yalnızca iki betik başvurusuna sahip olmanız gerekir:

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

Paket yerine `msgpack5` , `@msgpack/msgpack` uygulamayı doğrudan uygulamanızda kullanmak istiyorsanız, paketi *node_modules* dizinine indirilir.

Son olarak, `MessagePackOptions` Yeni, ek özelliklere sahiptir ve `disableTimestampEncoding` ve `forceFloat64` özellikleri kaldırılır.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik varlık boyutunu azaltmak, paketi daha kolay hale getirmek ve daha fazla özelleştirme eklemek için yapılmıştır.

## <a name="recommended-action"></a>Önerilen eylem

Uygulamanızda daha önce kullanıyorsanız `msgpack5` , dosyadaki *package.js* kitaplığa doğrudan bir başvuru eklemeniz gerekir.

## <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki API 'Ler kaldırılmıştır:

- `MessagePackOptions.disableTimestampEncoding`
- `MessagePackOptions.forceFloat64`

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis.

-->
