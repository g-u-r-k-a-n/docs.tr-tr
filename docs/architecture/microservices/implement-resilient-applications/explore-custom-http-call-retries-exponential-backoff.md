---
title: Üstel geri alma ile özel HTTP çağrısı yeniden denemelerini keşfet
description: Kapalı HTTP hatası senaryolarını işlemek için sıfırdan üstel geri alma ile HTTP çağrı yeniden denemeleri uygulama hakkında bilgi edinin.
ms.date: 10/16/2018
ms.openlocfilehash: 2b40b73a014faa87d4eb42192c72b5a9b6c8d4fa
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296123"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a><span data-ttu-id="35881-103">Üstel geri alma ile özel HTTP çağrısı yeniden denemelerini keşfet</span><span class="sxs-lookup"><span data-stu-id="35881-103">Explore custom HTTP call retries with exponential backoff</span></span>

<span data-ttu-id="35881-104">Dayanıklı mikro hizmetler oluşturmak için olası HTTP hatası senaryolarını işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="35881-104">To create resilient microservices, you need to handle possible HTTP failure scenarios.</span></span> <span data-ttu-id="35881-105">Bu hataların yerine getirmenin bir yolu, önerilmez, ancak üstel geri alma ile kendi yeniden deneme uygulamanızı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="35881-105">One way of handling those failures, although not recommended, is to create your own implementation of retries with exponential backoff.</span></span>

<span data-ttu-id="35881-106">**Önemli bir dikkat:** Bu bölümde, HTTP çağrısı yeniden denemeleri uygulamak için kendi özel kodunuzu nasıl oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="35881-106">**Important note:** This section shows you how you could create your own custom code to implement HTTP call retries.</span></span> <span data-ttu-id="35881-107">Ancak, .NET Core 2,1 ' den beri sunulan, daha `HttpClientFactory` basit ve güvenilir bir şekilde kullanmak için, daha güçlü ve güvenilir bir şekilde kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="35881-107">However, it isn't recommended to do it on your own but to use more powerful and reliable while simpler to use mechanisms, such as `HttpClientFactory` with Polly, available since .NET Core 2.1.</span></span> <span data-ttu-id="35881-108">Bu önerilen yaklaşımlar sonraki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="35881-108">Those recommended approaches are explained in the next sections.</span></span>

<span data-ttu-id="35881-109">İlk araştırma olarak, [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260)' de olduğu gibi üstel geri alma için yardımcı program sınıfıyla kendi kodunuzu uygulayabilir ve aşağıdakine benzer bir kod ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35881-109">As an initial exploration, you could implement your own code with a utility class for exponential backoff as in [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus code like the following.</span></span>

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

<span data-ttu-id="35881-110">Bu kodu bir istemci C\# uygulamasında kullanmak (başka bir Web API istemcisi mikro hizmeti, ASP.NET MVC uygulaması, hatta C\# Xamarin uygulaması) basittir.</span><span class="sxs-lookup"><span data-stu-id="35881-110">Using this code in a client C\# application (another Web API client microservice, an ASP.NET MVC application, or even a C\# Xamarin application) is straightforward.</span></span> <span data-ttu-id="35881-111">Aşağıdaki örnekte, HttpClient sınıfının nasıl kullanıldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="35881-111">The following example shows how, using the HttpClient class.</span></span>

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

<span data-ttu-id="35881-112">Bu kodun yalnızca kavram kanıtı olarak uygun olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="35881-112">Remember that this code is suitable only as a proof of concept.</span></span> <span data-ttu-id="35881-113">Sonraki bölümlerde, HttpClientFactory kullanarak daha basit olan daha karmaşık yaklaşımların nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35881-113">The next sections explain how to use more sophisticated approaches while simpler, by using HttpClientFactory.</span></span> <span data-ttu-id="35881-114">HttpClientFactory, .NET Core 2,1 sürümünden itibaren Polly gibi kanıtlanmış dayanıklılık kitaplıklarıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-114">HttpClientFactory is available since .NET Core 2.1, with proven resiliency libraries like Polly.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="35881-115">[Önceki](implement-resilient-entity-framework-core-sql-connections.md)
>[İleri](use-httpclientfactory-to-implement-resilient-http-requests.md)</span><span class="sxs-lookup"><span data-stu-id="35881-115">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](use-httpclientfactory-to-implement-resilient-http-requests.md)</span></span>
