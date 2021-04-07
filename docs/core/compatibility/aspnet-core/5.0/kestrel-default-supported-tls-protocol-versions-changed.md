---
title: 'Son değişiklik: Kestrel: desteklenen varsayılan TLS protokol sürümleri değiştirildi'
description: "Kestrel başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: varsayılan desteklenen TLS protokol sürümleri değişti"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1e3ebd700e5bb603f95a8b20ebdbd61379f1e508
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497651"
---
# <a name="kestrel-default-supported-tls-protocol-versions-changed"></a>Kestrel: Varsayılan olarak desteklenen TLS protokol sürümleri değiştirildi

Kestrel artık, daha önce olduğu gibi TLS 1,1 ve TLS 1,2 protokollerinin bağlantılarını kısıtlamak yerine sistem varsayılan TLS protokolü sürümlerini kullanır.

Bu değişiklik şunları sağlar:

* TLS 1,3, bunu destekleyen ortamlarda varsayılan olarak kullanılır.
* TLS 1,0, bazı ortamlarda (varsayılan olarak Windows Server 2016 gibi) kullanılmak üzere genellikle [istenmez](/security/engineering/solving-tls1-problem).

Tartışma için bkz. sorun [DotNet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 6

## <a name="old-behavior"></a>Eski davranış

Kestrel, bağlantıların varsayılan olarak TLS 1,1 veya TLS 1,2 kullanması gerekir.

## <a name="new-behavior"></a>Yeni davranış

Kestrel, işletim sisteminin kullanılacak en iyi Protokolü seçmesini ve güvenli olmayan protokolleri engellemesini sağlar. <xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> Artık yerine varsayılan olarak olur `SslProtocols.None` `SslProtocols.Tls12 | SslProtocols.Tls11` .

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, kullanılabilir hale geldiğinde TLS 1,3 ve gelecekteki TLS sürümlerini destekleyecek şekilde yapılmıştır.

## <a name="recommended-action"></a>Önerilen eylem

Uygulamanıza özgü bir neden olmadığı takdirde, yeni varsayılan değerleri kullanmanız gerekir. Sisteminizin yalnızca güvenli protokollere izin verecek şekilde yapılandırıldığını doğrulayın.

Eski protokolleri devre dışı bırakmak için aşağıdaki eylemlerden birini gerçekleştirin:

* [Windows yönergeleriyle](../../../../framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry)TLS 1,0, sistem genelinde gibi eski protokolleri devre dışı bırakın. Bu, şu anda tüm Windows sürümlerinde varsayılan olarak etkinleştirilmiştir.
* Kodda hangi protokolleri desteklemek istediğinizi el ile aşağıdaki gibi seçin:

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

Ne yazık ki belirli protokolleri dışlayacak bir API yok.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
