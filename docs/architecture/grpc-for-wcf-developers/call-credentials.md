---
title: Arama kimlik bilgileri-WCF geliştiricileri için gRPC
description: ASP.NET Core 3,0 ' de gRPC çağrı kimlik bilgilerini uygulama ve kullanma.
ms.date: 12/15/2020
ms.openlocfilehash: 66394c75929bf068f83d631e022b467386e59ec5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938448"
---
# <a name="call-credentials"></a><span data-ttu-id="c8745-103">Çağrı kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="c8745-103">Call credentials</span></span>

<span data-ttu-id="c8745-104">Çağrı kimlik bilgileri, her istekle birlikte meta verilerde geçirilen bir belirteci temel alır.</span><span class="sxs-lookup"><span data-stu-id="c8745-104">Call credentials are all based on a token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="c8745-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="c8745-105">WS-Federation</span></span>

<span data-ttu-id="c8745-106">ASP.NET Core, [WSFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet paketini kullanarak WS-Federation destekler.</span><span class="sxs-lookup"><span data-stu-id="c8745-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="c8745-107">WS-Federation, Windows kimlik doğrulaması için HTTP/2 üzerinde desteklenmeyen en yakın seçenektir.</span><span class="sxs-lookup"><span data-stu-id="c8745-107">WS-Federation is the closest available alternative to Windows Authentication, which isn't supported over HTTP/2.</span></span> <span data-ttu-id="c8745-108">Kullanıcılar, ASP.NET Core kimlik doğrulaması için kullanılabilecek bir belirteç sağlayan Active Directory Federasyon Hizmetleri (AD FS) (AD FS) kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="c8745-108">Users are authenticated by using Active Directory Federation Services (AD FS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="c8745-109">Bu kimlik doğrulama yöntemiyle çalışmaya başlama hakkında daha fazla bilgi için bkz. [ASP.NET Core WS-Federation kullanıcılara kimlik doğrulama](/aspnet/core/security/authentication/ws-federation).</span><span class="sxs-lookup"><span data-stu-id="c8745-109">For more information on how to get started with this authentication method, see [Authenticate users with WS-Federation in ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="c8745-110">JWT taşıyıcı belirteçleri</span><span class="sxs-lookup"><span data-stu-id="c8745-110">JWT Bearer tokens</span></span>

<span data-ttu-id="c8745-111">[JSON Web Token](https://jwt.io) (JWT) standardı, kodlanmış bir dizedeki bir Kullanıcı ve talepleri hakkında bilgi kodlamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8745-111">The [JSON Web Token](https://jwt.io) (JWT) standard provides a way to encode information about a user and their claims in an encoded string.</span></span> <span data-ttu-id="c8745-112">Ayrıca, tüketicinin ortak anahtar şifrelemesi kullanarak belirtecin bütünlüğünü doğrulayabilmesi için bu belirteci imzalamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8745-112">It also provides a way to sign that token, so that the consumer can verify the integrity of the token by using public key cryptography.</span></span> <span data-ttu-id="c8745-113">Kullanıcıların kimliğini doğrulamak ve gRPC ve HTTP API 'Leri ile kullanılacak OpenID Connect (OıDC) belirteçlerini oluşturmak için ıdentityserver4 gibi çeşitli hizmetleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8745-113">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="c8745-114">5,0 ASP.NET Core, JWT taşıyıcı paketini kullanarak JWTs 'yi işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c8745-114">ASP.NET Core 5.0 can handle JWTs by using the JWT Bearer package.</span></span> <span data-ttu-id="c8745-115">Yapılandırma, ASP.NET Core MVC uygulaması için olduğu gibi bir gRPC uygulaması için tam olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c8745-115">The configuration is exactly the same for a gRPC application as it is for an ASP.NET Core MVC application.</span></span> <span data-ttu-id="c8745-116">Burada, WS-Federation ' den daha kolay geliştirileceği için JWT taşıyıcı belirteçlerine odaklanacağız.</span><span class="sxs-lookup"><span data-stu-id="c8745-116">Here, we'll focus on JWT Bearer tokens, because they're easier to develop with than WS-Federation.</span></span>

## <a name="add-authentication-and-authorization-to-the-server"></a><span data-ttu-id="c8745-117">Sunucuya kimlik doğrulaması ve yetkilendirme ekleme</span><span class="sxs-lookup"><span data-stu-id="c8745-117">Add authentication and authorization to the server</span></span>

<span data-ttu-id="c8745-118">JWT taşıyıcı paketi, varsayılan olarak ASP.NET Core 5,0 ' ye dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="c8745-118">The JWT Bearer package isn't included in ASP.NET Core 5.0 by default.</span></span> <span data-ttu-id="c8745-119">Uygulamanıza [Microsoft. AspNetCore. Authentication. Jwttaşıyıcı](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="c8745-119">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="c8745-120">Başlangıç sınıfına kimlik doğrulama hizmetini ekleyin ve JWT taşıyıcı işleyicisini yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="c8745-120">Add the Authentication service in the Startup class, and configure the JWT Bearer handler:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

<span data-ttu-id="c8745-121">`IssuerSigningKey`Özelliği, `Microsoft.IdentityModels.Tokens.SecurityKey` imzalı belirteçleri doğrulamak için gerekli olan şifreleme verileriyle bir uygulamasının uygulanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8745-121">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="c8745-122">Bu belirteci, Azure Key Vault gibi bir *gizli dizi sunucusunda* güvenli bir şekilde depolayın.</span><span class="sxs-lookup"><span data-stu-id="c8745-122">Store this token securely in a *secrets server*, like Azure Key Vault.</span></span>

<span data-ttu-id="c8745-123">Ardından, sisteme erişimi denetleyen yetkilendirme hizmetini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c8745-123">Next, add the Authorization service, which controls access to the system:</span></span>

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> <span data-ttu-id="c8745-124">Kimlik doğrulama ve yetkilendirme iki ayrı adımdan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c8745-124">Authentication and authorization are two separate steps.</span></span> <span data-ttu-id="c8745-125">Kullanıcının kimliğini öğrenmek için kimlik doğrulaması kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8745-125">You use authentication to determine the user's identity.</span></span> <span data-ttu-id="c8745-126">Kullanıcının sistemin çeşitli bölümlerine erişmesine izin verilip verilmeyeceğini belirlemek için Yetkilendirmeyi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c8745-126">You use authorization to decide whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="c8745-127">Şimdi kimlik doğrulama ve yetkilendirme ara yazılımını yöntemdeki ASP.NET Core işlem hattına ekleyin `Configure` :</span><span class="sxs-lookup"><span data-stu-id="c8745-127">Now add the authentication and authorization middleware to the ASP.NET Core pipeline in the `Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="c8745-128">Son olarak, `[Authorize]` özniteliğini güvenli hale getirilmesi için herhangi bir hizmete veya yönteme uygulayın ve `User` izinleri doğrulamak için temel alınan özelliğini kullanın `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="c8745-128">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="provide-call-credentials-in-the-client-application"></a><span data-ttu-id="c8745-129">İstemci uygulamasında çağrı kimlik bilgilerini sağlayın</span><span class="sxs-lookup"><span data-stu-id="c8745-129">Provide call credentials in the client application</span></span>

<span data-ttu-id="c8745-130">Bir kimlik sunucusundan JWT belirteci aldıktan sonra, bunu, çağrı üzerine bir meta veri üst bilgisi olarak ekleyerek istemciden gRPC çağrılarının kimliğini doğrulamak için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c8745-130">After you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

<span data-ttu-id="c8745-131">Artık gRPC hizmetinizi, JWT taşıyıcı belirteçlerini çağrı kimlik bilgileri olarak kullanarak güvenli hale getirdi.</span><span class="sxs-lookup"><span data-stu-id="c8745-131">Now you've secured your gRPC service by using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="c8745-132">, [Kimlik doğrulaması ve yetkilendirme eklenmiş bir portföyleri örnek gRPC uygulamasının](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) sürümü GitHub ' dır.</span><span class="sxs-lookup"><span data-stu-id="c8745-132">A version of the [portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c8745-133">[Önceki](security.md) 
> [Sonraki](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="c8745-133">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
