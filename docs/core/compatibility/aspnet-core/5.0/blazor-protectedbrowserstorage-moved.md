---
title: 'Son değişiklik: Blazor: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 36ba6c16ac970aa8acb0d0faab42b151addae888
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497846"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a>Blazor: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı

ASP.NET Core 5,0 RC2 sürümünün bir parçası olarak, `ProtectedBrowserStorage` özellik ASP.NET Core paylaşılan çerçeveye taşınır.

## <a name="version-introduced"></a>Sunulan sürüm

5,0 RC2

## <a name="old-behavior"></a>Eski davranış

ASP.NET Core 5,0 Preview 8 ' de, özelliği [Microsoft. AspNetCore. components. Web. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) paketinin bir parçası olarak kullanılabilir ancak yalnızca Blazor WebAssembly ' de kullanılabilir.

ASP.NET Core 5,0 RC1 sürümünde, özelliği paylaşılan çerçeveye başvuran [Microsoft. AspNetCore. components. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) paketinin bir parçası olarak kullanılabilir `Microsoft.AspNetCore.App` .

## <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 5,0 RC2 'de, artık bu özelliği kullanmak için bir NuGet paket başvurusuna gerek yoktur.

## <a name="reason-for-change"></a>Değişiklik nedeni

Paylaşılan çerçeveye taşıma, müşterilerin beklediği Kullanıcı deneyimi için daha iyi bir uyum sağlar.

## <a name="recommended-action"></a>Önerilen eylem

ASP.NET Core 5,0 RC1 'den yükseltme yapıyorsanız, aşağıdaki adımları izleyin:

1. `Microsoft.AspNetCore.Components.ProtectedBrowserStorage`Paket başvurusunu projeden kaldırın.
1. `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.
1. Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .

ASP.NET Core 5,0 Preview 8 ' den yükseltiyorsanız aşağıdaki adımları uygulayın:

1. `Microsoft.AspNetCore.Components.Web.Extensions`Paket başvurusunu projeden kaldırın.
1. `using Microsoft.AspNetCore.Components.Web.Extensions;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.
1. Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
