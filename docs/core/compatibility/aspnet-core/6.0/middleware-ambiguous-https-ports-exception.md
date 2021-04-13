---
title: 'Son değişiklik: ara yazılım: HTTPS yeniden yönlendirme ara yazılımı belirsiz HTTPS bağlantı noktalarında özel durum oluşturur'
description: "ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin: HTTPS yeniden yönlendirme ara yazılımı, belirsiz HTTPS bağlantı noktalarında özel durum oluşturur"
ms.author: scaddie
ms.date: 02/04/2021
ms.openlocfilehash: e299fc7d2be295d723f5389a2b4cd6896078a752
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255083"
---
# <a name="middleware-https-redirection-middleware-throws-exception-on-ambiguous-https-ports"></a>Ara yazılım: HTTPS yeniden yönlendirme ara yazılımı belirsiz HTTPS bağlantı noktalarında özel durum oluşturur

ASP.NET Core 6,0 ' de, [https yeniden yönlendirme ara yazılımı](xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A) <xref:System.InvalidOperationException> sunucu YAPıLANDıRMASıNDA birden çok HTTPS bağlantı noktası bulduğunda türünde bir özel durum oluşturur. Özel durumun iletisi "ıvveraddressesözelliğinden HTTPS bağlantı noktası saptanamıyor, birden çok değer bulundu. İstenen bağlantı noktasını HttpsRedirectionOptions. HttpsPort üzerinde açık olarak ayarlayın. "

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 29222](https://github.com/dotnet/aspnetcore/issues/29222).

## <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 6,0

## <a name="old-behavior"></a>Eski davranış

HTTPS yeniden yönlendirme ara yazılımı bir bağlantı noktasıyla açıkça yapılandırılmamışsa, <xref:Microsoft.AspNetCore.Hosting.Server.Features.IServerAddressesFeature> ilk istek sırasında, yeniden yönlendirilmesi gereken HTTPS bağlantı noktasını belirleyen bir arama yapar.

HTTPS bağlantı noktası veya birden çok farklı bağlantı noktası yoksa, bu bağlantı noktasının kullanılması gerekir. Ara yazılım bir uyarı kaydeder ve kendisini devre dışı bırakır. HTTP istekleri normal şekilde işlenir.

## <a name="new-behavior"></a>Yeni davranış

HTTPS yeniden yönlendirme ara yazılımı bir bağlantı noktasıyla açıkça yapılandırılmamışsa, `IServerAddressesFeature` ilk istek sırasında, yeniden yönlendirilmesi gereken HTTPS bağlantı noktasını belirleyen bir arama yapar.

HTTPS bağlantı noktası yoksa, ara yazılım hala bir uyarı kaydeder ve kendisini devre dışı bırakır. HTTP istekleri normal şekilde işlenir. Bu davranış şunları destekler:

* HTTPS olmadan geliştirme senaryoları.
* Sunucuya ulaşmadan önce TLS 'nin sonlandırıldığı barındırılan senaryolar.

Birden çok farklı bağlantı noktası varsa, bu bağlantı noktasının kullanılması gerektiği anlaşılır değildir. Ara yazılım bir özel durum oluşturur ve HTTP isteği başarısız olur.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, HTTPS 'nin kullanılabilir olduğu bilindiğinde gizli verilerin şifrelenmemiş HTTP bağlantıları üzerinden sunulmasını önler.

## <a name="recommended-action"></a>Önerilen eylem

Sunucuda birden çok farklı HTTPS bağlantı noktası olduğunda HTTPS yeniden yönlendirmeyi etkinleştirmek için, yapılandırmada bir bağlantı noktası belirtmeniz gerekir. Daha fazla bilgi için bkz. [bağlantı noktası yapılandırması](/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&preserve-view=true#port-configuration).

Uygulamanızda HTTPS yeniden yönlendirme ara yazılımı gerekmiyorsa, `UseHttpsRedirection` *Başlangıç. cs*' den kaldırın.

Doğru HTTPS bağlantı noktasını dinamik olarak seçmeniz gerekiyorsa, GitHub sorunu [DotNet/aspnetcore # 21291](https://github.com/dotnet/aspnetcore/issues/21291)içinde geri bildirim sağlayın.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection`

-->
