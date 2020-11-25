---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032700"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="12359-101">Kimlik doğrulaması: Google + kullanım dışı ve değiştirilmiş</span><span class="sxs-lookup"><span data-stu-id="12359-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="12359-102">Google, ilk olarak 28 Ocak 2019 tarihinden itibaren, uygulamalar için Google + oturum açmayı [kapatmaya](https://developers.google.com/+/api-shutdown) başlıyor.</span><span class="sxs-lookup"><span data-stu-id="12359-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="12359-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="12359-103">Change description</span></span>

<span data-ttu-id="12359-104">ASP.NET 4. x ve ASP.NET Core, Web Apps 'te Google hesabı kullanıcılarının kimliğini doğrulamak için Google + oturum açma API 'Lerini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="12359-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="12359-105">Etkilenen NuGet paketleri, ASP.NET Web Forms ve MVC ile için [Microsoft. AspNetCore. Authentication. Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core ve [Microsoft. Owin. Security. Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) ' dir `Microsoft.Owin` .</span><span class="sxs-lookup"><span data-stu-id="12359-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="12359-106">Google 'ın değiştirme API 'Leri farklı bir veri kaynağı ve biçimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="12359-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="12359-107">Yapısal değişiklikler için aşağıda belirtilen Azaltıcı Etkenler ve çözümler.</span><span class="sxs-lookup"><span data-stu-id="12359-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="12359-108">Uygulamalar, verilerin hala gereksinimlerini karşıladığından emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="12359-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="12359-109">Örneğin adlar, e-posta adresleri, profil bağlantıları ve profil fotoğrafları, daha önce daha çok farklı değerler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="12359-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12359-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="12359-110">Version introduced</span></span>

<span data-ttu-id="12359-111">Tüm sürümler.</span><span class="sxs-lookup"><span data-stu-id="12359-111">All versions.</span></span> <span data-ttu-id="12359-112">Bu değişiklik ASP.NET Core dış.</span><span class="sxs-lookup"><span data-stu-id="12359-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12359-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="12359-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="12359-114">ASP.NET Web Forms ve MVC ile Owin</span><span class="sxs-lookup"><span data-stu-id="12359-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="12359-115">`Microsoft.Owin`3.1.0 ve üzeri için geçici bir risk azaltma [burada](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="12359-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="12359-116">Uygulamalar, veri biçimindeki değişiklikleri denetlemek için azaltma ile testi tamamlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="12359-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="12359-117">4.0.1 'i bir düzeltmeyle yayınlama planları vardır `Microsoft.Owin` .</span><span class="sxs-lookup"><span data-stu-id="12359-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="12359-118">Önceki sürümleri kullanan uygulamalar 4.0.1 sürümüne güncellemelidir.</span><span class="sxs-lookup"><span data-stu-id="12359-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="12359-119">ASP.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="12359-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="12359-120">[Owin ASP.NET Web Forms ve MVC ile olan](#owin-with-aspnet-web-forms-and-mvc) azaltıcı etken, 1. x ASP.NET Core uyarlanabilirler.</span><span class="sxs-lookup"><span data-stu-id="12359-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="12359-121">1. x, [yaşam durumunun sonuna](https://dotnet.microsoft.com/platform/support-policy) ulaştığı için NuGet paket yamaları planlanmadı.</span><span class="sxs-lookup"><span data-stu-id="12359-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="12359-122">ASP.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="12359-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="12359-123">`Microsoft.AspNetCore.Authentication.Google`Sürüm 2. x için, mevcut çağrlarınızı `AddGoogle` `Startup.ConfigureServices` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="12359-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

<span data-ttu-id="12359-124">Şubat 2,1 ve 2,2 yamaları önceki yeniden yapılandırma yeni varsayılan olarak eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="12359-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="12359-125">ASP.NET Core 2,0 için bir düzeltme eki planlanmıyor çünkü [yaşam sonuna](https://dotnet.microsoft.com/platform/support-policy)ulaştı.</span><span class="sxs-lookup"><span data-stu-id="12359-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="12359-126">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="12359-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="12359-127">ASP.NET Core 2. x için verilen risk azaltma, ASP.NET Core 3,0 için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12359-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="12359-128">Gelecekteki 3,0 önizlemelerde `Microsoft.AspNetCore.Authentication.Google` paket kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="12359-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="12359-129">Kullanıcılar, `Microsoft.AspNetCore.Authentication.OpenIdConnect` bunun yerine öğesine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="12359-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="12359-130">Aşağıdaki kod, içindeki ile nasıl değiştirileceğini `AddGoogle` gösterir `AddOpenIdConnect` `Startup.ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="12359-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="12359-131">Bu değişiklik, ASP.NET Core 2,0 ve üzeri sürümlerle kullanılabilir ve gerektiğinde ASP.NET Core 1. x için uyarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="12359-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="12359-132">Kategori</span><span class="sxs-lookup"><span data-stu-id="12359-132">Category</span></span>

<span data-ttu-id="12359-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="12359-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12359-134">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="12359-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
