---
title: 'Son değişiklik: Blazor : güncelleştirilmiş tarayıcı desteği'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin Blazor : güncelleştirilmiş tarayıcı desteği"
ms.author: scaddie
ms.date: 10/01/2020
no-loc:
- Blazor
- Blazor WebAssembly
- Blazor Server
ms.openlocfilehash: 25566a4b30aaa8484ec4bcf26ab1e8fde6af1279
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497872"
---
# <a name="blazor-updated-browser-support"></a>Blazor: Tarayıcı desteği güncelleştirildi

ASP.NET Core 5,0, bazıları eski tarayıcılarla uyumsuz olan [Yeni Blazor Özellikler](https://github.com/dotnet/aspnetcore/issues/21514)sunar. ASP.NET Core 5,0 ' de tarafından desteklenen tarayıcıların listesi, Blazor buna göre güncelleştirilmiştir.

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="old-behavior"></a>Eski davranış

Blazor Server , yeterli polydolgular ile Microsoft Internet Explorer 11 ' i destekler. Blazor ServerBlazor WebAssemblyAyrıca, [Microsoft Edge eski](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)sürümünde de çalışır.

## <a name="new-behavior"></a>Yeni davranış

Blazor Server ASP.NET Core 5,0 ' de Microsoft Internet Explorer 11 desteklenmez. Blazor Server ve Blazor WebAssembly Microsoft Edge eski sürümünde tam olarak işlevsel değildir.

## <a name="reason-for-change"></a>Değişiklik nedeni

BlazorASP.NET Core 5,0 ' deki yeni özellikler bu eski tarayıcılarla uyumsuzdur ve bu eski tarayıcıların kullanımı, bu eski tarayıcıların kullanımına karşı azalmış olur. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

* [Microsoft Edge için Windows desteği, Ayrıca 9 Mart 2021 ' de sona eriyor](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [Microsoft 365 uygulamalar ve hizmetler, Microsoft Internet Explorer 11 için 17 Ağustos 2021 ' de destek sona acaktır.](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

## <a name="recommended-action"></a>Önerilen eylem

Bu eski tarayıcılardan [Yeni, Kmuum tabanlı Microsoft Edge](https://www.microsoft.com/edge)'e yükseltin. BlazorBu eski tarayıcıları desteklemesi gereken uygulamalar için ASP.NET Core 3,1 kullanın. BlazorASP.NET Core 3,1 ' de desteklenen tarayıcılar listesi değiştirilmedi ve [desteklenen platformlarda](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1)belgelenmiştir.

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
