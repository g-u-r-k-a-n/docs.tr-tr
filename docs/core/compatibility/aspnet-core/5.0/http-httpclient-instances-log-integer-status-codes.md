---
title: 'Son değişiklik: HTTP: ıhttpclientfactory günlük tamsayı durum kodları tarafından oluşturulan HttpClient örnekleri'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin. ıhttpclientfactory günlük tamsayı durum kodları tarafından oluşturulan HTTP: HttpClient örnekleri"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 59e64c7127a97b1c11587d13803e4a085dbc090b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497690"
---
# <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a><span data-ttu-id="96a88-103">HTTP: ıhttpclientfactory günlük tamsayı durum kodları tarafından oluşturulan HttpClient örnekleri</span><span class="sxs-lookup"><span data-stu-id="96a88-103">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>

<span data-ttu-id="96a88-104"><xref:System.Net.Http.HttpClient><xref:System.Net.Http.IHttpClientFactory>günlük http durum kodları tarafından, durum kodu adları yerine tamsayılar olarak oluşturulan örnekler.</span><span class="sxs-lookup"><span data-stu-id="96a88-104"><xref:System.Net.Http.HttpClient> instances created by <xref:System.Net.Http.IHttpClientFactory> log HTTP status codes as integers instead of with status code names.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="96a88-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="96a88-105">Version introduced</span></span>

<span data-ttu-id="96a88-106">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="96a88-106">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="96a88-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="96a88-107">Old behavior</span></span>

<span data-ttu-id="96a88-108">Günlüğe kaydetme, HTTP durum kodlarının metinsel açıklamalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="96a88-108">Logging uses the textual descriptions of HTTP status codes.</span></span> <span data-ttu-id="96a88-109">Aşağıdaki günlük iletilerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="96a88-109">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

## <a name="new-behavior"></a><span data-ttu-id="96a88-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="96a88-110">New behavior</span></span>

<span data-ttu-id="96a88-111">Günlüğe kaydetme, HTTP durum kodlarının tamsayı değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="96a88-111">Logging uses the integer values of HTTP status codes.</span></span> <span data-ttu-id="96a88-112">Aşağıdaki günlük iletilerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="96a88-112">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

## <a name="reason-for-change"></a><span data-ttu-id="96a88-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="96a88-113">Reason for change</span></span>

<span data-ttu-id="96a88-114">Bu günlüğe kaydetmenin özgün davranışı, her zaman kullanılan tamsayı değerlerini içeren ASP.NET Core diğer bölümleri ile tutarsız.</span><span class="sxs-lookup"><span data-stu-id="96a88-114">The original behavior of this logging is inconsistent with other parts of ASP.NET Core that have always used integer values.</span></span> <span data-ttu-id="96a88-115">Tutarsızlık, oturum açma gibi yapılandırılmış günlük sistemleri aracılığıyla sorgu yapmayı [zorlaştırır.](https://www.elastic.co/elasticsearch/)</span><span class="sxs-lookup"><span data-stu-id="96a88-115">The inconsistency makes logs difficult to query via structured logging systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/).</span></span> <span data-ttu-id="96a88-116">Daha fazla bağlam için bkz. [DotNet/Extensions # 1549](https://github.com/dotnet/extensions/issues/1549).</span><span class="sxs-lookup"><span data-stu-id="96a88-116">For more context, see [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span></span>

<span data-ttu-id="96a88-117">Değer aralıklarında sorgulara izin verdiğinden tamsayı değerlerinin kullanılması metinden daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="96a88-117">Using integer values is more flexible than text because it allows queries on ranges of values.</span></span>

<span data-ttu-id="96a88-118">Tamsayı durum kodunu yakalamak için başka bir günlük değeri eklenmesi kabul edildi.</span><span class="sxs-lookup"><span data-stu-id="96a88-118">Adding another log value to capture the integer status code was considered.</span></span> <span data-ttu-id="96a88-119">Ne yazık ki, ASP.NET Core geri kalanı ile başka bir tutarsızlık ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="96a88-119">Unfortunately, doing so would introduce another inconsistency with the rest of ASP.NET Core.</span></span> <span data-ttu-id="96a88-120">HttpClient günlüğü ve HTTP sunucusu/barındırma günlüğü, zaten aynı `StatusCode` anahtar adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="96a88-120">HttpClient logging and HTTP server/hosting logging use the same `StatusCode` key name already.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="96a88-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="96a88-121">Recommended action</span></span>

<span data-ttu-id="96a88-122">En iyi seçenek, günlük sorgularını durum kodlarının tamsayı değerlerini kullanacak şekilde güncelleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="96a88-122">The best option is to update logging queries to use the integer values of status codes.</span></span> <span data-ttu-id="96a88-123">Bu seçenek, birden çok ASP.NET Core sürümünde sorgu yazarken zorluk gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="96a88-123">This option may cause some difficulty writing queries across multiple ASP.NET Core versions.</span></span> <span data-ttu-id="96a88-124">Ancak, bu amaçla tamsayıların kullanılması günlükleri sorgulamak için çok daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="96a88-124">However, using integers for this purpose is much more flexible for querying logs.</span></span>

<span data-ttu-id="96a88-125">Eski davranışla uyumluluğu zorlamak ve metin durum kodları kullanmak gerekirse, `IHttpClientFactory` günlük kaydını kendi ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="96a88-125">If you need to force compatibility with the old behavior and use textual status codes, replace the `IHttpClientFactory` logging with your own:</span></span>

1. <span data-ttu-id="96a88-126">Aşağıdaki sınıfların .NET Core 3,1 sürümlerini projenize kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="96a88-126">Copy the .NET Core 3.1 versions of the following classes into your project:</span></span>

    * [<span data-ttu-id="96a88-127">LoggingHttpMessageHandlerBuilderFilter</span><span class="sxs-lookup"><span data-stu-id="96a88-127">LoggingHttpMessageHandlerBuilderFilter</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [<span data-ttu-id="96a88-128">LoggingHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="96a88-128">LoggingHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [<span data-ttu-id="96a88-129">LoggingScopeHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="96a88-129">LoggingScopeHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [<span data-ttu-id="96a88-130">HttpHeadersLogValue</span><span class="sxs-lookup"><span data-stu-id="96a88-130">HttpHeadersLogValue</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. <span data-ttu-id="96a88-131">[Microsoft. Extensions. http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet paketindeki ortak türlerle çakışmaları önlemek için sınıfları yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="96a88-131">Rename the classes to avoid conflicts with public types in the [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet package.</span></span>

1. <span data-ttu-id="96a88-132">Uygulamasının yerleşik uygulamasını, `LoggingHttpMessageHandlerBuilderFilter` projenin yönteminde kendi ile değiştirin `Startup.ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="96a88-132">Replace the built-in implementation of `LoggingHttpMessageHandlerBuilderFilter` with your own in the project's `Startup.ConfigureServices` method.</span></span> <span data-ttu-id="96a88-133">Örnek:</span><span class="sxs-lookup"><span data-stu-id="96a88-133">For example:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        services.RemoveAll<IHttpMessageHandlerBuilderFilter>();

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

## <a name="affected-apis"></a><span data-ttu-id="96a88-134">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="96a88-134">Affected APIs</span></span>

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:System.Net.Http.HttpClient`

-->
