---
title: 'Son değişiklik: Uzantılar: bazı NuGet paketlerini etkileyen paket başvuru değişiklikleri'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: bazı NuGet paketlerini etkileyen paket başvuru değişiklikleri"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 82ee5129d6422d0a5ea4a0f14632a42e779f6ded
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497742"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a>Uzantılar: bazı NuGet paketlerini etkileyen paket başvuru değişiklikleri

Bazı `Microsoft.Extensions.*` NuGet paketlerinin [DotNet/Extensions](https://github.com/dotnet/extensions) deposundan [DotNet/çalışma zamanına](https://github.com/dotnet/runtime), [ASPNET/Duyurular # 411](https://github.com/aspnet/Announcements/issues/411)' de açıklandığı gibi geçirilirken, paket değişiklikleri geçirilmiş paketlerden bazılarına uygulanıyor. Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 4

## <a name="old-behavior"></a>Eski davranış

Bazı `Microsoft.Extensions.*` paketler, uygulamanızın güvenolduğu API 'ler için paket başvuruları içerir.

## <a name="new-behavior"></a>Yeni davranış

Uygulamanızın `Microsoft.Extensions.*` paket bağımlılıklarını eklemesi gerekebilir.

## <a name="reason-for-change"></a>Değişiklik nedeni

Paketleme ilkeleri *DotNet/Runtime* deposuna daha iyi uyum sağlamak için güncelleştirildi. Yeni ilke altında kullanılmayan paket başvuruları paketleme sırasında *. nupkg* dosyalarından kaldırılır.

## <a name="recommended-action"></a>Önerilen eylem

Etkilenen paketlerin tüketicileri, kaldırılan paket bağımlılığıyla API 'Ler kullanılırsa, bu projedeki kaldırılan paket bağımlılığına doğrudan bağımlılık eklememelidir. Aşağıdaki tabloda etkilenen paketler ve ilgili değişiklikler listelenmiştir.

|Paket adı|Açıklamayı Değiştir|
|------------|------------------|
|[Microsoft.Extensions.Configurlama. Bağlayıcısı](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|Başvurusu kaldırıldı `Microsoft.Extensions.Configuration`|
|[ ÜzerindeMicrosoft.Extensions.Configuration.Js](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |Başvurusu kaldırıldı `System.Threading.Tasks.Extensions`|
|[Microsoft. Extensions. Hosting. soyutlamalar](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|Başvurusu kaldırıldı `Microsoft.Extensions.Logging.Abstractions`|
|[Microsoft.Extensions.Logging](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |Başvurusu kaldırıldı `Microsoft.Extensions.Configuration.Binder`|
|[Microsoft. Extensions. Logging. Console](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |Başvurusu kaldırıldı `Microsoft.Extensions.Configuration.Abstractions`|
|[Microsoft. Extensions. Logging. EventLog](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |`System.Diagnostics.EventLog`.NET Framework 4.6.1 hedef Framework bilinen adı için başvuru kaldırıldı|
|[Microsoft. Extensions. Logging. EventSource](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |Başvurusu kaldırıldı `System.Threading.Tasks.Extensions`|
|[Microsoft. Extensions. Options](https://nuget.org/packages/Microsoft.Extensions.Options)                          |Başvurusu kaldırıldı `System.ComponentModel.Annotations`|

Örneğin, öğesine paket başvurusu `Microsoft.Extensions.Configuration` öğesinden kaldırılmıştır `Microsoft.Extensions.Configuration.Binder` . Pakette, bağımlılıktan API kullanılmadı. `Microsoft.Extensions.Configuration.Binder`API 'lerine bağlı olan kullanıcıların `Microsoft.Extensions.Configuration` , projesinde kendisine bir doğrudan başvuru eklemesi gerekir.

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
