---
title: 'Son değişiklik: Kestrel: çalışma zamanında varsayılan olarak algılanan yapılandırma değişiklikleri'
description: "Kestrel başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: varsayılan olarak algılanan çalışma sırasında yapılandırma değişiklikleri"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 35b733cd872b9d6d944896349921c54f672b31b0
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498106"
---
# <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a>Kestrel: çalışma zamanında varsayılan olarak algılanan yapılandırma değişiklikleri

Kestrel şimdi `Kestrel` `IConfiguration` , çalışma zamanında projenin örneğinin bölümünde yapılan değişikliklere (örneğin, *appsettings.jsaçık*) yeniden davranır. *Üzerindeappsettings.js* kullanarak Kestrel yapılandırma hakkında daha fazla bilgi edinmek Için [uç nokta yapılandırması](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration)'nda *appsettings.jshakkında* bölümüne bakın.

Kestrel, bu yapılandırma değişikliklerine tepki vermek için uç noktaları gerektiği şekilde bağlar, çözer ve yeniden bağlayın.

Tartışma için bkz. sorun [DotNet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 7

## <a name="old-behavior"></a>Eski davranış

ASP.NET Core 5,0 Preview 6 ' dan önce Kestrel, çalışma zamanında yapılandırmanın değiştirilmesini desteklememektedir.

ASP.NET Core 5,0 Preview 6 ' da, çalışma zamanında yapılandırma değişikliklerine yeniden davranma özelliğinin varsayılan davranışını kabul edebilirsiniz. Gerekli bağlama Kestrel yapılandırması el ile:

```csharp
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
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

## <a name="new-behavior"></a>Yeni davranış

Kestrel, varsayılan olarak çalışma zamanında yapılandırma değişikliklerine tepki verir. Bu değişikliği desteklemek için, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> `KestrelServerOptions.Configure(IConfiguration, bool)` `reloadOnChange: true` Varsayılan olarak ile çağırır.

## <a name="reason-for-change"></a>Değişiklik nedeni

Sunucu tamamen yeniden başlatılmadan çalışma zamanında bitiş noktası yeniden yapılandırması desteklemek için değişiklik yapıldı. Tam sunucu yeniden başlatmasından farklı olarak, değiştirilmemiş uç noktalar geçici olarak geçici olarak ilişkisiz olmaz.

## <a name="recommended-action"></a>Önerilen eylem

* Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değişmediğinden çoğu senaryo için, bu değişikliğin etkisi yoktur ve hiçbir eylem gerekmez.
* Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değişme ve Kestrel 'e yanıt vermesini gerektiren senaryolar için, bu artık varsayılan davranıştır.
* Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değiştiği ve Kestrel 'e yanıt vermeme senaryolarında, aşağıdaki gibi devre dışı bırakabilirsiniz:

    ```csharp
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
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

**Notlar:**

Bu değişiklik aşırı yükleme davranışını değiştirmez, bu da `KestrelServerOptions.Configure(IConfiguration)` davranışa varsayılan olarak devam eder `reloadOnChange: false` .

Yapılandırma kaynağının yeniden yüklemeyi desteklediğinden emin olmak da önemlidir. JSON kaynakları için, yeniden yükleme çağırarak yapılandırılır `AddJsonFile(path, reloadOnChange: true)` . Yeniden yükleme, *appsettings.json* ve appSettings için varsayılan olarak zaten yapılandırılmıştır *. { Environment}. JSON*.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
