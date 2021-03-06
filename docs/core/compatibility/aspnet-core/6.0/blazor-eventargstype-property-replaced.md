---
title: 'Son değişiklik: Blazor : WebEventDescriptor. EventArgsType özelliği değişti'
description: WebEventDescriptor. EventArgsType özelliğinin, EventName özelliği ile değiştirildiği ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin.
author: scottaddie
ms.author: scaddie
ms.date: 02/24/2021
no-loc:
- Blazor
ms.openlocfilehash: 6df086ed234c0071ede83e9fe9d1710f011a2039
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102260070"
---
# <a name="blazor-no-loc-textwebeventdescriptoreventargstype-property-replaced"></a>Blazor: :::no-loc text="WebEventDescriptor.EventArgsType"::: özellik değişti

<xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor>Sınıfı, Blazor olayları JavaScript 'ten .net 'e iletişim kurmak için iç protokolün bir parçasıdır. Bu sınıf genellikle uygulama kodu tarafından değil, platform yazarları tarafından kullanılmaz.

ASP.NET Core 6,0 ' den başlayarak, <xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A> üzerindeki özelliği `WebEventDescriptor` Yeni bir özellik ile değiştiriliyor `EventName` . Bu değişiklik, alt düzey platform uygulaması ayrıntısı olduğundan, herhangi bir uygulama kodunu etkilemeyebilir.

## <a name="version-introduced"></a>Sunulan sürüm

6.0

## <a name="old-behavior"></a>Eski davranış

ASP.NET Core 5,0 ve önceki sürümlerde özelliği, `EventArgsType` Blazor DOM olay türleri grupları için standart olmayan,-özel kategori adını tanımlar. Örneğin, `click` ve `mousedown` olaylarının her ikisi de bir değeriyle eşlenmiş `EventArgsType` `mouse` . Benzer şekilde,, `cut` `copy` , ve `paste` olayları `EventArgsType` değerine eşlenir `clipboard` . Bu kategori adları, gelen olay bağımsız değişkenleri verilerinin serisini kaldırmada kullanılacak .NET türünü belirlemekte kullanılır.

## <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 6,0 ' den başlayarak, yeni özellik `EventName` yalnızca özgün etkinliğin adını belirtir. Örneğin,,,, `click` `mousedown` `cut` `copy` veya `paste` . Artık Blazor belirli bir kategori adı sağlamanız gerekmez. Bu nedenle, eski özellik `EventArgsType` kaldırılır.

## <a name="reason-for-change"></a>Değişiklik nedeni

Çekme isteği [DotNet/aspnetcore # 29993](https://github.com/dotnet/aspnetcore/pull/29993)içinde özel olay bağımsız değişkeni sınıfları için destek sunuldu. Bu desteğin bir parçası olarak Framework artık önceden tanımlanmış bir kategori kümesine bağlı olan tüm olaylara dayanmayacaktır. Artık çerçevenin yalnızca özgün olay adını bilmeleri gerekir.

## <a name="recommended-action"></a>Önerilen eylem

Uygulama kodu etkilenmemelidir ve değişikliğe gerek kalmaz.

Özel bir Blazor işleme platformu oluşturuyorsanız, içindeki olayları gönderme mekanizmasını güncelleştirmeniz gerekebilir `Renderer` . Olay kategorileri hakkındaki tüm sabit kodlanmış kuralları, özgün, Ham olay adını sağlayan daha basit bir mantık ile değiştirin.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`P:Microsoft.AspNetCore.Components.RenderTree.WebEventDescriptor.EventArgsType`

-->
