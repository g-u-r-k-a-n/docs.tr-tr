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
# <a name="changed-messagepack-library-in-microsoftsignalr-protocol-msgpack"></a><span data-ttu-id="d3ed1-103">İçinde MessagePack kitaplığı değiştirildi @microsoft/signalr-protocol-msgpack</span><span class="sxs-lookup"><span data-stu-id="d3ed1-103">Changed MessagePack library in @microsoft/signalr-protocol-msgpack</span></span>

<span data-ttu-id="d3ed1-104">[@microsoft/signalr-protocol-msgpack](https://www.npmjs.com/package/@microsoft/signalr-protocol-msgpack)NPM paketi artık yerine başvuruyordur `@msgpack/msgpack` `msgpack5` .</span><span class="sxs-lookup"><span data-stu-id="d3ed1-104">The [@microsoft/signalr-protocol-msgpack](https://www.npmjs.com/package/@microsoft/signalr-protocol-msgpack) npm package now references `@msgpack/msgpack` instead of `msgpack5`.</span></span> <span data-ttu-id="d3ed1-105">Ayrıca, isteğe bağlı olarak, isteğe bağlı olarak içine geçirilebilecek Seçenekler `MessagePackHubProtocol` değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-105">Additionally, the available options that can optionally be passed into the `MessagePackHubProtocol` have changed.</span></span> <span data-ttu-id="d3ed1-106">`MessagePackOptions.disableTimestampEncoding`Ve `MessagePackOptions.forceFloat64` özellikleri kaldırılmıştır ve bazı yeni seçenekler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-106">The `MessagePackOptions.disableTimestampEncoding` and `MessagePackOptions.forceFloat64` properties were removed, and some new options were added.</span></span>

<span data-ttu-id="d3ed1-107">Tartışma için bkz <https://github.com/dotnet/aspnetcore/issues/30471> ..</span><span class="sxs-lookup"><span data-stu-id="d3ed1-107">For discussion, see <https://github.com/dotnet/aspnetcore/issues/30471>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d3ed1-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d3ed1-108">Version introduced</span></span>

<span data-ttu-id="d3ed1-109">ASP.NET Core 6,0</span><span class="sxs-lookup"><span data-stu-id="d3ed1-109">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d3ed1-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="d3ed1-110">Old behavior</span></span>

<span data-ttu-id="d3ed1-111">Önceki sürümlerde, tarayıcıda [MessagePack hub protokolünü](/aspnet/core/signalr/messagepackhubprotocol) kullanmak için üç komut dosyası başvurusu eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="d3ed1-111">In previous versions, you must include three script references to use the [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) in the browser:</span></span>

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/msgpack5/msgpack5.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

## <a name="new-behavior"></a><span data-ttu-id="d3ed1-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="d3ed1-112">New behavior</span></span>

<span data-ttu-id="d3ed1-113">ASP.NET Core 6 ' dan başlayarak, tarayıcıda [MessagePack hub protokolünü](/aspnet/core/signalr/messagepackhubprotocol) kullanmak için yalnızca iki betik başvurusuna sahip olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="d3ed1-113">Starting in ASP.NET Core 6, you only need two script references to use the [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) in the browser:</span></span>

```html
<script src="~/lib/signalr/signalr.js"></script>
<script src="~/lib/signalr/signalr-protocol-msgpack.js"></script>
```

<span data-ttu-id="d3ed1-114">Paket yerine `msgpack5` , `@msgpack/msgpack` uygulamayı doğrudan uygulamanızda kullanmak istiyorsanız, paketi *node_modules* dizinine indirilir.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-114">Instead of the `msgpack5` package, the `@msgpack/msgpack` package is downloaded to your *node_modules* directory if you want to use it directly in your app.</span></span>

<span data-ttu-id="d3ed1-115">Son olarak, `MessagePackOptions` Yeni, ek özelliklere sahiptir ve `disableTimestampEncoding` ve `forceFloat64` özellikleri kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-115">Finally, `MessagePackOptions` has new, additional properties, and the `disableTimestampEncoding` and `forceFloat64` properties are removed.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d3ed1-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d3ed1-116">Reason for change</span></span>

<span data-ttu-id="d3ed1-117">Bu değişiklik varlık boyutunu azaltmak, paketi daha kolay hale getirmek ve daha fazla özelleştirme eklemek için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-117">This change was made to reduce asset size, make it simpler to consume the package, and add more customizability.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d3ed1-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d3ed1-118">Recommended action</span></span>

<span data-ttu-id="d3ed1-119">Uygulamanızda daha önce kullanıyorsanız `msgpack5` , dosyadaki *package.js* kitaplığa doğrudan bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3ed1-119">If you were previously using `msgpack5` in your app, you'll need to add a direct reference to the library in your *package.json* file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d3ed1-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d3ed1-120">Affected APIs</span></span>

<span data-ttu-id="d3ed1-121">Aşağıdaki API 'Ler kaldırılmıştır:</span><span class="sxs-lookup"><span data-stu-id="d3ed1-121">The following APIs were removed:</span></span>

- `MessagePackOptions.disableTimestampEncoding`
- `MessagePackOptions.forceFloat64`

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis.

-->
