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
# <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="a1328-103">Kestrel: Varsayılan olarak desteklenen TLS protokol sürümleri değiştirildi</span><span class="sxs-lookup"><span data-stu-id="a1328-103">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="a1328-104">Kestrel artık, daha önce olduğu gibi TLS 1,1 ve TLS 1,2 protokollerinin bağlantılarını kısıtlamak yerine sistem varsayılan TLS protokolü sürümlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1328-104">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="a1328-105">Bu değişiklik şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="a1328-105">This change allows:</span></span>

* <span data-ttu-id="a1328-106">TLS 1,3, bunu destekleyen ortamlarda varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1328-106">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="a1328-107">TLS 1,0, bazı ortamlarda (varsayılan olarak Windows Server 2016 gibi) kullanılmak üzere genellikle [istenmez](/security/engineering/solving-tls1-problem).</span><span class="sxs-lookup"><span data-stu-id="a1328-107">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="a1328-108">Tartışma için bkz. sorun [DotNet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).</span><span class="sxs-lookup"><span data-stu-id="a1328-108">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a1328-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a1328-109">Version introduced</span></span>

<span data-ttu-id="a1328-110">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="a1328-110">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a1328-111">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a1328-111">Old behavior</span></span>

<span data-ttu-id="a1328-112">Kestrel, bağlantıların varsayılan olarak TLS 1,1 veya TLS 1,2 kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1328-112">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="a1328-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a1328-113">New behavior</span></span>

<span data-ttu-id="a1328-114">Kestrel, işletim sisteminin kullanılacak en iyi Protokolü seçmesini ve güvenli olmayan protokolleri engellemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1328-114">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="a1328-115"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> Artık yerine varsayılan olarak olur `SslProtocols.None` `SslProtocols.Tls12 | SslProtocols.Tls11` .</span><span class="sxs-lookup"><span data-stu-id="a1328-115"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a1328-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a1328-116">Reason for change</span></span>

<span data-ttu-id="a1328-117">Bu değişiklik, kullanılabilir hale geldiğinde TLS 1,3 ve gelecekteki TLS sürümlerini destekleyecek şekilde yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a1328-117">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a1328-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a1328-118">Recommended action</span></span>

<span data-ttu-id="a1328-119">Uygulamanıza özgü bir neden olmadığı takdirde, yeni varsayılan değerleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1328-119">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="a1328-120">Sisteminizin yalnızca güvenli protokollere izin verecek şekilde yapılandırıldığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="a1328-120">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="a1328-121">Eski protokolleri devre dışı bırakmak için aşağıdaki eylemlerden birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="a1328-121">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="a1328-122">[Windows yönergeleriyle](../../../../framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry)TLS 1,0, sistem genelinde gibi eski protokolleri devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="a1328-122">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](../../../../framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="a1328-123">Bu, şu anda tüm Windows sürümlerinde varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a1328-123">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="a1328-124">Kodda hangi protokolleri desteklemek istediğinizi el ile aşağıdaki gibi seçin:</span><span class="sxs-lookup"><span data-stu-id="a1328-124">Manually select which protocols you want to support in code as follows:</span></span>

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

<span data-ttu-id="a1328-125">Ne yazık ki belirli protokolleri dışlayacak bir API yok.</span><span class="sxs-lookup"><span data-stu-id="a1328-125">Unfortunately, there's no API to exclude specific protocols.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a1328-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a1328-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
