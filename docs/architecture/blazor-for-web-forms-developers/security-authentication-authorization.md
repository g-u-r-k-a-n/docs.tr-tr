---
title: 'Güvenlik: ASP.NET Web Forms ve üzerinde kimlik doğrulaması ve yetkilendirme Blazor'
description: ASP.NET Web Forms ve ' de kimlik doğrulama ve yetkilendirmeyi nasıl işleyeceğinizi öğrenin Blazor .
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 0344960237a5d9da61eb0d85987c44e136f1be48
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509851"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-blazor"></a><span data-ttu-id="ef9db-103">Güvenlik: ASP.NET Web Forms ve üzerinde kimlik doğrulaması ve yetkilendirme Blazor</span><span class="sxs-lookup"><span data-stu-id="ef9db-103">Security: Authentication and Authorization in ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="ef9db-104">Bir ASP.NET Web Forms uygulamasından ' ye geçiş yapmak Blazor , uygulamanın kimlik doğrulaması ile yapılandırıldığını varsayarak kimlik doğrulamanın ve yetkilendirmenin nasıl gerçekleştirileceğini neredeyse tamamen gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-104">Migrating from an ASP.NET Web Forms application to Blazor will almost certainly require updating how authentication and authorization are performed, assuming the application had authentication configured.</span></span> <span data-ttu-id="ef9db-105">Bu bölümde, ASP.NET Web Forms evrensel sağlayıcı modelinden (üyelik, roller ve Kullanıcı profilleri için) ve uygulamalardan ASP.NET Core kimlik ile nasıl çalışabileceğiniz ele alınacaktır Blazor .</span><span class="sxs-lookup"><span data-stu-id="ef9db-105">This chapter will cover how to migrate from the ASP.NET Web Forms universal provider model (for membership, roles, and user profiles) and how to work with ASP.NET Core Identity from Blazor apps.</span></span> <span data-ttu-id="ef9db-106">Bu bölümde üst düzey adımlar ve önemli noktalar ele alınırken, ayrıntılı adımlar ve betikler başvurulan belgelerde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-106">While this chapter will cover the high-level steps and considerations, the detailed steps and scripts may be found in the referenced documentation.</span></span>

## <a name="aspnet-universal-providers"></a><span data-ttu-id="ef9db-107">ASP.NET evrensel sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="ef9db-107">ASP.NET universal providers</span></span>

<span data-ttu-id="ef9db-108">ASP.NET 2,0 ' den itibaren, ASP.NET Web Forms platformu üyelik dahil olmak üzere çeşitli özellikler için bir sağlayıcı modeli destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="ef9db-108">Since ASP.NET 2.0, the ASP.NET Web Forms platform has supported a provider model for a variety of features, including membership.</span></span> <span data-ttu-id="ef9db-109">Evrensel üyelik sağlayıcısı, isteğe bağlı rol sağlayıcısıyla birlikte, genellikle ASP.NET Web Forms uygulamalarıyla dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-109">The universal membership provider, along with the optional role provider, is commonly deployed with ASP.NET Web Forms applications.</span></span> <span data-ttu-id="ef9db-110">Bugün çalışmaya devam eden kimlik doğrulama ve yetkilendirmeyi yönetmenin sağlam ve güvenli bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="ef9db-110">It offers a robust and secure way to manage authentication and authorization that continues to work well today.</span></span> <span data-ttu-id="ef9db-111">Bu evrensel sağlayıcıların en son sunumu, [Microsoft. Aspnet. Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers)bir NuGet paketi olarak sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-111">The most recent offering of these universal providers is available as a NuGet package, [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span></span>

<span data-ttu-id="ef9db-112">Evrensel sağlayıcılar,, ve gibi tabloları içeren bir SQL veritabanı şeması ile `aspnet_Applications` çalışır `aspnet_Membership` `aspnet_Roles` `aspnet_Users` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-112">The Universal Providers work with a SQL database schema that includes tables like `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles`, and `aspnet_Users`.</span></span> <span data-ttu-id="ef9db-113">[aspnet_regsql.exe komutu](/previous-versions/ms229862(v=vs.140))çalıştırılarak yapılandırıldığında, sağlayıcılar, temel alınan verilerle çalışacak tüm gerekli sorguları ve komutları sağlayan tabloları ve saklı yordamları yükler.</span><span class="sxs-lookup"><span data-stu-id="ef9db-113">When configured by running the [aspnet_regsql.exe command](/previous-versions/ms229862(v=vs.140)), the providers install tables and stored procedures that provide all of the necessary queries and commands to work with the underlying data.</span></span> <span data-ttu-id="ef9db-114">Veritabanı şeması ve bu saklı yordamlar, daha yeni ASP.NET Identity ve ASP.NET Core kimlik sistemleriyle uyumlu değildir, bu nedenle mevcut verilerin yeni sisteme geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-114">The database schema and these stored procedures are not compatible with newer ASP.NET Identity and ASP.NET Core Identity systems, so existing data must be migrated into the new system.</span></span> <span data-ttu-id="ef9db-115">Şekil 1 ' de, evrensel sağlayıcılar için yapılandırılmış örnek bir tablo şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-115">Figure 1 shows an example table schema configured for universal providers.</span></span>

![Evrensel sağlayıcılar şeması](./media/security/membership-tables.png)

<span data-ttu-id="ef9db-117">Evrensel sağlayıcı kullanıcıları, üyeliği, rolleri ve profilleri işler.</span><span class="sxs-lookup"><span data-stu-id="ef9db-117">The universal provider handles users, membership, roles, and profiles.</span></span> <span data-ttu-id="ef9db-118">Kullanıcılara genel benzersiz tanımlayıcılar atanır ve Kullanıcı kimliği, Kullanıcı adı vb. gibi temel bilgiler `aspnet_Users` tabloda depolanır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-118">Users are assigned globally unique identifiers and basic information like userId, userName etc. are stored in the `aspnet_Users` table.</span></span> <span data-ttu-id="ef9db-119">Parola, parola biçimi, parola güvenlik, kilitleme sayaçları ve ayrıntılar gibi kimlik doğrulama bilgileri `aspnet_Membership` tabloda depolanır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-119">Authentication information, such as password, password format, password salt, lockout counters and details, etc. are stored in the `aspnet_Membership` table.</span></span> <span data-ttu-id="ef9db-120">Roller, yalnızca ilişkilendirme tablosu aracılığıyla kullanıcılara atanan adları ve benzersiz tanımlayıcılardan oluşur ve `aspnet_UsersInRoles` çoktan çoğa bir ilişki sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef9db-120">Roles consist simply of names and unique identifiers, which are assigned to users via the `aspnet_UsersInRoles` association table, providing a many-to-many relationship.</span></span>

<span data-ttu-id="ef9db-121">Mevcut sisteminiz üyeliğe ek olarak roller kullanıyorsa, Kullanıcı hesaplarını, ilişkili parolaları, rolleri ve rol üyeliğini ASP.NET Core kimliğe geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-121">If your existing system is using roles in addition to membership, you will need to migrate the user accounts, the associated passwords, the roles, and the role membership into ASP.NET Core Identity.</span></span> <span data-ttu-id="ef9db-122">Ayrıca, şu anda, ' nin bildirim temelli filtrelerin, özniteliklerin ve/veya etiket yardımcılarını kullanmasını sağlamak için If deyimlerini kullanarak şu anda rol denetimleri gerçekleştirmekte olduğunuz kodunuzu güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-122">You will also most likely need to update your code where you're currently performing role checks using if statements to instead leverage declarative filters, attributes, and/or tag helpers.</span></span> <span data-ttu-id="ef9db-123">Bu bölümün sonunda, geçiş konularını daha ayrıntılı olarak gözden geçitireceğiz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-123">We will review migration considerations in greater detail at the end of this chapter.</span></span>

### <a name="authorization-configuration-in-web-forms"></a><span data-ttu-id="ef9db-124">Web Forms 'de yetkilendirme yapılandırması</span><span class="sxs-lookup"><span data-stu-id="ef9db-124">Authorization configuration in Web Forms</span></span>

<span data-ttu-id="ef9db-125">Bir ASP.NET Web Forms uygulamasındaki belirli sayfalara yetkili erişimi yapılandırmak için, genellikle belirli sayfaların veya klasörlerin anonim kullanıcılara erişilmez olduğunu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-125">To configure authorized access to certain pages in an ASP.NET Web Forms application, typically you specify that certain pages or folders are inaccessible to anonymous users.</span></span> <span data-ttu-id="ef9db-126">Bu yapılandırma web.config dosyasında yapılır:</span><span class="sxs-lookup"><span data-stu-id="ef9db-126">This configuration is done in the web.config file:</span></span>

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

<span data-ttu-id="ef9db-127">`authentication`Yapılandırma bölümü, uygulama için form kimlik doğrulamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ef9db-127">The `authentication` configuration section sets up the forms authentication for the application.</span></span> <span data-ttu-id="ef9db-128">Bu `authorization` bölüm, tüm uygulama için anonim kullanıcılara izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-128">The `authorization` section is used to disallow anonymous users for the entire application.</span></span> <span data-ttu-id="ef9db-129">Ancak, her konum için daha ayrıntılı yetkilendirme kuralları sağlayabilir ve rol tabanlı yetkilendirme denetimleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-129">However, you can provide more granular authorization rules on a per-location basis as well as apply role-based authorization checks.</span></span>

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="ef9db-130">Yukarıdaki yapılandırma, ilki ile birleştirildiğinde, anonim kullanıcıların oturum açma sayfasına erişmesine izin verir ve bu, kimliği doğrulanmamış kullanıcılar için site genelinde kısıtlamayı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ef9db-130">The above configuration, when combined with the first one, would allow anonymous users to access the login page, overriding the site-wide restriction on non-authenticated users.</span></span>

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="ef9db-131">Yukarıdaki yapılandırma, diğerleri ile birleştirildiğinde, `/admin` klasöre ve içindeki tüm kaynaklara erişimi "Administrators" rolünün üyeleriyle kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="ef9db-131">The above configuration, when combined with the others, restricts access to the `/admin` folder and all resources within it to members of the "Administrators" role.</span></span> <span data-ttu-id="ef9db-132">Bu kısıtlama ayrıca klasör köküne ayrı bir dosya yerleştirilerek de uygulanabilir `web.config` `/admin` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-132">This restriction could also be applied by placing a separate `web.config` file within the `/admin` folder root.</span></span>

### <a name="authorization-code-in-web-forms"></a><span data-ttu-id="ef9db-133">Web Forms 'de yetkilendirme kodu</span><span class="sxs-lookup"><span data-stu-id="ef9db-133">Authorization code in Web Forms</span></span>

<span data-ttu-id="ef9db-134">' Yi kullanarak erişimi yapılandırmanın yanı sıra `web.config` , Web Forms uygulamanızda erişimi ve davranışı programlı bir şekilde de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-134">In addition to configuring access using `web.config`, you can also programmatically configure access and behavior in your Web Forms application.</span></span> <span data-ttu-id="ef9db-135">Örneğin, belirli işlemleri gerçekleştirme veya kullanıcının rolüne bağlı olarak belirli verileri görüntüleme özelliğini kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-135">For instance, you can restrict the ability to perform certain operations or view certain data based on the user's role.</span></span>

<span data-ttu-id="ef9db-136">Bu kod, hem arka plan kod mantığındaki hem de sayfanın kendisi üzerinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ef9db-136">This code can be used both in code-behind logic as well as in the page itself:</span></span>

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

<span data-ttu-id="ef9db-137">Kullanıcı rolü üyeliğini denetlemeye ek olarak, kimlik doğrulamasının yapılıp yapılmadığını da belirleyebilirsiniz (genellikle bu, yukarıda bahsedilen konum tabanlı yapılandırma kullanılarak daha iyi yapılır).</span><span class="sxs-lookup"><span data-stu-id="ef9db-137">In addition to checking user role membership, you can also determine if they are authenticated (though often this is better done using the location-based configuration covered above).</span></span> <span data-ttu-id="ef9db-138">Aşağıda bu yaklaşımın bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-138">Below is an example of this approach.</span></span>

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

<span data-ttu-id="ef9db-139">Yukarıdaki kodda rol tabanlı erişim denetimi (RBAC), sayfanın belirli öğelerinin (örneğin `SecretPanel` ,) geçerli kullanıcının rolüne göre görünür olup olmadığını belirlemekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-139">In the code above, role-based access control (RBAC) is used to determine whether certain elements of the page, such as a `SecretPanel`, are visible based on the current user's role.</span></span>

<span data-ttu-id="ef9db-140">Genellikle, ASP.NET Web Forms uygulamalar dosya içinde güvenliği yapılandırır `web.config` ve ardından sayfada gereken yere `.aspx` ve ilgili `.aspx.cs` arka plan kod dosyalarına daha fazla denetim ekler.</span><span class="sxs-lookup"><span data-stu-id="ef9db-140">Typically, ASP.NET Web Forms applications configure security within the `web.config` file and then add additional checks where needed in `.aspx` pages and their related `.aspx.cs` code-behind files.</span></span> <span data-ttu-id="ef9db-141">Çoğu uygulama, genellikle ek rol sağlayıcısıyla birlikte evrensel üyelik sağlayıcısından faydalanır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-141">Most applications leverage the universal membership provider, frequently with the additional role provider.</span></span>

## <a name="aspnet-core-identity"></a><span data-ttu-id="ef9db-142">ASP.NET Core kimliği</span><span class="sxs-lookup"><span data-stu-id="ef9db-142">ASP.NET Core Identity</span></span>

<span data-ttu-id="ef9db-143">Kimlik doğrulama ve yetkilendirme ile hala çalışmaya devam etse de ASP.NET Core kimliği, evrensel sağlayıcılardan karşılaştırıldığında farklı bir soyutlama ve varsayımlar kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-143">Although still tasked with authentication and authorization, ASP.NET Core Identity uses a different set of abstractions and assumptions when compared to the universal providers.</span></span> <span data-ttu-id="ef9db-144">Örneğin, yeni kimlik modeli üçüncü taraf kimlik doğrulamasını destekler, böylece kullanıcılar sosyal medya hesabı veya diğer güvenilir kimlik doğrulama sağlayıcısı kullanarak kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-144">For example, the new Identity model supports third party authentication, allowing users to authenticate using a social media account or other trusted authentication provider.</span></span> <span data-ttu-id="ef9db-145">ASP.NET Core kimlik, oturum açma, oturum kapatma ve kayıt gibi yaygın olarak gereken sayfaların Kullanıcı arabirimini destekler.</span><span class="sxs-lookup"><span data-stu-id="ef9db-145">ASP.NET Core Identity supports UI for commonly needed pages like login, logout, and register.</span></span> <span data-ttu-id="ef9db-146">Veri erişimi için EF Core yararlanır ve veri modelini desteklemek için gerekli şemayı oluşturmak üzere EF Core geçişleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-146">It leverages EF Core for its data access, and uses EF Core migrations to generate the necessary schema required to support its data model.</span></span> <span data-ttu-id="ef9db-147">Bu [ASP.NET Core kimliğe giriş](/aspnet/core/security/authentication/identity) , ASP.NET Core kimliği ile nelerin dahil olduğu ve onunla çalışmaya başlama hakkında iyi bir genel bakış sunar.</span><span class="sxs-lookup"><span data-stu-id="ef9db-147">This [introduction to Identity on ASP.NET Core](/aspnet/core/security/authentication/identity) provides a good overview of what is included with ASP.NET Core Identity and how to get started working with it.</span></span> <span data-ttu-id="ef9db-148">Uygulamanızda ve veritabanında ASP.NET Core kimlik ayarlamadıysanız, başlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ef9db-148">If you haven't already set up ASP.NET Core Identity in your application and its database, it will help you get started.</span></span>

### <a name="roles-claims-and-policies"></a><span data-ttu-id="ef9db-149">Roller, talepler ve ilkeler</span><span class="sxs-lookup"><span data-stu-id="ef9db-149">Roles, claims, and policies</span></span>

<span data-ttu-id="ef9db-150">Hem Evrensel sağlayıcılar hem de ASP.NET Core kimlik, rol kavramını destekler.</span><span class="sxs-lookup"><span data-stu-id="ef9db-150">Both the universal providers and ASP.NET Core Identity support the concept of roles.</span></span> <span data-ttu-id="ef9db-151">Kullanıcılar için roller oluşturabilir ve kullanıcılara roller atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-151">You can create roles for users and assign users to roles.</span></span> <span data-ttu-id="ef9db-152">Kullanıcılar herhangi bir sayıda role ait olabilir ve yetkilendirme uygulamanızın bir parçası olarak rol üyeliğini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-152">Users can belong to any number of roles, and you can verify role membership as part of your authorization implementation.</span></span>

<span data-ttu-id="ef9db-153">Rollere ek olarak, ASP.NET Core kimlik, talepler ve ilkelerin kavramlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="ef9db-153">In addition to roles, ASP.NET Core identity supports the concepts of claims and policies.</span></span> <span data-ttu-id="ef9db-154">Bir rol özellikle bu roldeki bir kullanıcının erişim sağlayabilmesi gereken bir kaynak kümesine karşılık gelmelidir, bir talep yalnızca kullanıcının kimliğinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-154">While a role should specifically correspond to a set of resources a user in that role should be able to access, a claim is simply part of a user's identity.</span></span> <span data-ttu-id="ef9db-155">Talep, konunun ne yapabileceğini temsil eden bir ad değer çiftidir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-155">A claim is a name value pair that represents what the subject is, not what the subject can do.</span></span>

<span data-ttu-id="ef9db-156">Bir kullanıcının taleplerini doğrudan incelemek ve bir kullanıcıya bir kaynağa erişim verilmesi gerekip gerekmediğini bu değerlere göre tespit etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ef9db-156">It is possible to directly inspect a user's claims and determine based on these values whether a user should be given access to a resource.</span></span> <span data-ttu-id="ef9db-157">Ancak, bu tür denetimler genellikle sistem genelinde tekrarlanır ve dağılmış olur.</span><span class="sxs-lookup"><span data-stu-id="ef9db-157">However, such checks are often repetitive and scattered throughout the system.</span></span> <span data-ttu-id="ef9db-158">Bir *ilke* tanımlamak daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-158">A better approach is to define a *policy*.</span></span>

<span data-ttu-id="ef9db-159">Yetkilendirme ilkesi bir veya daha fazla gereksinimden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ef9db-159">An authorization policy consists of one or more requirements.</span></span> <span data-ttu-id="ef9db-160">İlkeler, yetkilendirme hizmeti yapılandırmasının bir parçası olarak ' `ConfigureServices` ın yönteminde kaydedilir `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-160">Policies are registered as part of the authorization service configuration in the `ConfigureServices` method of `Startup.cs`.</span></span> <span data-ttu-id="ef9db-161">Örneğin, aşağıdaki kod parçacığı, "CanadiansOnly" adlı bir ilke yapılandırır, bu, kullanıcının "Kanada" değeriyle ülke talebine sahip olması gereksinimini içerir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-161">For example, the following code snippet configures a policy called "CanadiansOnly", which has the requirement that the user has the Country claim with the value of "Canada".</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

<span data-ttu-id="ef9db-162">[Belgelerde özel ilkeler oluşturma hakkında daha fazla bilgi](/aspnet/core/security/authorization/policies)edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-162">You can [learn more about how to create custom policies in the documentation](/aspnet/core/security/authorization/policies).</span></span>

<span data-ttu-id="ef9db-163">İlkeleri veya rolleri kullanıp kullansanız, uygulamanızdaki belirli bir sayfanın, Blazor `[Authorize]` yönergeyle uygulanan özniteliği olan rolün veya ilkenin gerekli olduğunu belirtebilirsiniz `@attribute` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-163">Whether you're using policies or roles, you can specify that a particular page in your Blazor application requires that role or policy with the `[Authorize]` attribute, applied with the `@attribute` directive.</span></span>

<span data-ttu-id="ef9db-164">Rol gerektirme:</span><span class="sxs-lookup"><span data-stu-id="ef9db-164">Requiring a role:</span></span>

```csharp
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="ef9db-165">Bir ilkenin karşılanmasını gerektirme:</span><span class="sxs-lookup"><span data-stu-id="ef9db-165">Requiring a policy be satisfied:</span></span>

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

<span data-ttu-id="ef9db-166">Kodunuzda bir kullanıcının kimlik doğrulama durumuna, rollerine veya taleplerine erişmeniz gerekiyorsa, bu işlevselliğe ulaşmak için iki temel yol vardır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-166">If you need access to a user's authentication state, roles, or claims in your code, there are two primary ways to achieve this functionality.</span></span> <span data-ttu-id="ef9db-167">Birincisi, kimlik doğrulama durumunu basamaklı bir parametre olarak almadır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-167">The first is to receive the authentication state as a cascading parameter.</span></span> <span data-ttu-id="ef9db-168">İkincisi, eklenen ' i kullanarak duruma erişdir `AuthenticationStateProvider` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-168">The second is to access the state using an injected `AuthenticationStateProvider`.</span></span> <span data-ttu-id="ef9db-169">Bu yaklaşımların her birinin ayrıntıları [ Blazor güvenlik belgelerinde](/aspnet/core/blazor/security/)açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-169">The details of each of these approaches are described in the [Blazor Security documentation](/aspnet/core/blazor/security/).</span></span>

<span data-ttu-id="ef9db-170">Aşağıdaki kod, nasıl `AuthenticationState` bir geçişli parametre olarak alınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ef9db-170">The following code shows how to receive the `AuthenticationState` as a cascading parameter:</span></span>

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

<span data-ttu-id="ef9db-171">Bu parametre yerine, kullanıcıyı şu kodu kullanarak edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ef9db-171">With this parameter in place, you can get the user using this code:</span></span>

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

<span data-ttu-id="ef9db-172">Aşağıdaki kod, aşağıdakilerin nasıl ekleneceğini göstermektedir `AuthenticationStateProvider` :</span><span class="sxs-lookup"><span data-stu-id="ef9db-172">The following code shows how to inject the `AuthenticationStateProvider`:</span></span>

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

<span data-ttu-id="ef9db-173">Sağlayıcı ile, aşağıdaki kodla kullanıcıya erişim sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ef9db-173">With the provider in place, you can gain access to the user with the following code:</span></span>

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

<span data-ttu-id="ef9db-174">**Note:** `AuthorizeView` Bu bölümün ilerleyen kısımlarında yer alan bileşen, kullanıcının bir sayfada veya bileşende ne göreceğini denetlemek için bildirim temelli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef9db-174">**Note:** The `AuthorizeView` component, covered later in this chapter, provides a declarative way to control what a user sees on a page or component.</span></span>

<span data-ttu-id="ef9db-175">Kullanıcılar ve talepler (sunucu uygulamalarında) ile çalışmak için, bir Blazor `UserManager<T>` `IdentityUser` kullanıcının taleplerini numaralandırmak ve değiştirmek üzere kullanabileceğiniz bir (varsayılan için kullanın) eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-175">To work with users and claims (in Blazor Server applications) you may also need to inject a `UserManager<T>` (use `IdentityUser` for default) which you can use to enumerate and modify claims for a user.</span></span> <span data-ttu-id="ef9db-176">Önce türü ekleme ve bir özelliğe atama:</span><span class="sxs-lookup"><span data-stu-id="ef9db-176">First inject the type and assign it to a property:</span></span>

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

<span data-ttu-id="ef9db-177">Daha sonra kullanıcının taleplerine göre çalışmak için bu uygulamayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef9db-177">Then use it to work with the user's claims.</span></span> <span data-ttu-id="ef9db-178">Aşağıdaki örnek, bir kullanıcıya bir talebin nasıl ekleneceğini ve kalıcı hale alınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ef9db-178">The following sample shows how to add and persist a claim on a user:</span></span>

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

<span data-ttu-id="ef9db-179">Rollerle çalışmanız gerekiyorsa, aynı yaklaşımı izleyin.</span><span class="sxs-lookup"><span data-stu-id="ef9db-179">If you need to work with roles, follow the same approach.</span></span> <span data-ttu-id="ef9db-180">`RoleManager<T>` `IdentityRole` Rolleri listelemek ve yönetmek için bir (varsayılan tür için kullanın) eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-180">You may need to inject a `RoleManager<T>` (use `IdentityRole` for default type) to list and manage the roles themselves.</span></span>

<span data-ttu-id="ef9db-181">**Note:** Blazor Webassembly projelerinde, bu işlemleri gerçekleştirmek için sunucu API 'leri sağlamanız gerekir ( `UserManager<T>` veya doğrudan kullanmak yerine `RoleManager<T>` ).</span><span class="sxs-lookup"><span data-stu-id="ef9db-181">**Note:** In Blazor WebAssembly projects, you will need to provide server APIs to perform these operations (instead of using `UserManager<T>` or `RoleManager<T>` directly).</span></span> <span data-ttu-id="ef9db-182">BlazorWebassembly istemci uygulaması, bu amaçla sunulan API uç noktalarını güvenli bir şekilde çağırarak talepleri ve/veya rolleri yönetebilir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-182">A Blazor WebAssembly client application would manage claims and/or roles by securely calling API endpoints exposed for this purpose.</span></span>

### <a name="migration-guide"></a><span data-ttu-id="ef9db-183">Geçiş kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ef9db-183">Migration guide</span></span>

<span data-ttu-id="ef9db-184">ASP.NET Web Forms ve evrensel sağlayıcılardan ASP.NET Core kimliğe geçiş için birkaç adım gerekir:</span><span class="sxs-lookup"><span data-stu-id="ef9db-184">Migrating from ASP.NET Web Forms and universal providers to ASP.NET Core Identity requires several steps:</span></span>

1. <span data-ttu-id="ef9db-185">Hedef veritabanında ASP.NET Core Identity Database şeması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef9db-185">Create ASP.NET Core Identity database schema in the destination database</span></span>
2. <span data-ttu-id="ef9db-186">Verileri evrensel sağlayıcı şemasından ASP.NET Core Identity şemasına geçirme</span><span class="sxs-lookup"><span data-stu-id="ef9db-186">Migrate data from universal provider schema to ASP.NET Core Identity schema</span></span>
3. <span data-ttu-id="ef9db-187">Yapılandırma `web.config` ' dan ara yazılım ve hizmetlere, genellikle içinde `Startup.cs`</span><span class="sxs-lookup"><span data-stu-id="ef9db-187">Migrate configuration from the `web.config` to middleware and services, typically in `Startup.cs`</span></span>
4. <span data-ttu-id="ef9db-188">Etiket Yardımcıları ve yeni kimlik API 'Lerini kullanmak için denetimleri ve koşulları kullanarak sayfaları tek tek güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ef9db-188">Update individual pages using controls and conditionals to use tag helpers and new identity APIs.</span></span>

<span data-ttu-id="ef9db-189">Bu adımların her biri, aşağıdaki bölümlerde ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-189">Each of these steps is described in detail in the following sections.</span></span>

### <a name="creating-the-aspnet-core-identity-schema"></a><span data-ttu-id="ef9db-190">ASP.NET Core Identity şeması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef9db-190">Creating the ASP.NET Core Identity schema</span></span>

<span data-ttu-id="ef9db-191">ASP.NET Core kimliği için kullanılan gerekli tablo yapısını oluşturmanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-191">There are several ways to create the necessary table structure used for ASP.NET Core Identity.</span></span> <span data-ttu-id="ef9db-192">En basit, yeni bir ASP.NET Core Web uygulaması oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-192">The simplest is to create a new ASP.NET Core Web application.</span></span> <span data-ttu-id="ef9db-193">Web uygulaması ' nı seçin ve kimlik doğrulamasını bireysel kullanıcı hesapları kullanacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ef9db-193">Choose Web Application and then change Authentication to use Individual User Accounts.</span></span>

![bireysel kullanıcı hesaplarıyla Yeni proje](./media/security/individual-user-accounts.png)

<span data-ttu-id="ef9db-195">Komut satırından, komutunu çalıştırarak aynı şeyi yapabilirsiniz `dotnet new webapp -au Individual` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-195">From the command line, you can do the same thing by running `dotnet new webapp -au Individual`.</span></span> <span data-ttu-id="ef9db-196">Uygulama oluşturulduktan sonra çalıştırın ve siteye kaydolun.</span><span class="sxs-lookup"><span data-stu-id="ef9db-196">Once the app has been created, run it and register on the site.</span></span> <span data-ttu-id="ef9db-197">Bir sayfayı aşağıda gösterildiği gibi tetiklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="ef9db-197">You should trigger a page like the one shown below:</span></span>

![geçişleri uygula sayfası](./media/security/apply-migrations-page.png)

<span data-ttu-id="ef9db-199">"Geçişleri Uygula" düğmesine tıklayın ve gerekli veritabanı tablolarının sizin için oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-199">Click on the "Apply Migrations" button and the necessary database tables should be created for you.</span></span> <span data-ttu-id="ef9db-200">Ayrıca, geçiş dosyaları projenizde gösterildiği gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ef9db-200">In addition, the migration files should appear in your project, as shown:</span></span>

![geçiş dosyaları](./media/security/migration-files.png)

<span data-ttu-id="ef9db-202">Bu komut satırı aracını kullanarak, Web uygulamasını çalıştırmadan geçişi kendiniz çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ef9db-202">You can run the migration yourself, without running the web application, using this command-line tool:</span></span>

```powershell
dotnet ef database update
```

<span data-ttu-id="ef9db-203">Yeni şemayı mevcut bir veritabanına uygulamak için bir komut dosyası çalıştırırsanız, komut satırından bu geçişlere komut dosyası ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-203">If you would rather run a script to apply the new schema to an existing database, you can script these migrations from the command-line.</span></span> <span data-ttu-id="ef9db-204">Betiği oluşturmak için şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ef9db-204">Run this command to generate the script:</span></span>

```powershell
dotnet ef migrations script -o auth.sql
```

<span data-ttu-id="ef9db-205">Yukarıdaki komut, çıkış dosyasında `auth.sql` istediğiniz veritabanına göre çalıştırılabilecek BIR SQL betiği oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="ef9db-205">The above command will produce a SQL script in the output file `auth.sql`, which can then be run against whatever database you like.</span></span> <span data-ttu-id="ef9db-206">Komutları çalıştırırken sorun yaşarsanız `dotnet ef` [sisteminizde EF Core araçlarının yüklü olduğundan emin olun](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="ef9db-206">If you have any trouble running `dotnet ef` commands, [make sure you have the EF Core tools installed on your system](/ef/core/miscellaneous/cli/dotnet).</span></span>

<span data-ttu-id="ef9db-207">Kaynak tablolarınızda ek sütunlarınız varsa, bu sütunlar için yeni şemada en iyi konumu belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-207">In the event you have additional columns on your source tables, you will need to identify the best location for these columns in the new schema.</span></span> <span data-ttu-id="ef9db-208">Genellikle tabloda bulunan sütunların `aspnet_Membership` tabloya eşlenmesi gerekir `AspNetUsers` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-208">Generally, columns found on the `aspnet_Membership` table should be mapped to the `AspNetUsers` table.</span></span> <span data-ttu-id="ef9db-209">Üzerindeki sütunlar `aspnet_Roles` ile eşlenmelidir `AspNetRoles` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-209">Columns on `aspnet_Roles` should be mapped to `AspNetRoles`.</span></span> <span data-ttu-id="ef9db-210">Tablodaki ek sütunlar `aspnet_UsersInRoles` `AspNetUserRoles` tabloya eklenir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-210">Any additional columns on the `aspnet_UsersInRoles` table would be added to the `AspNetUserRoles` table.</span></span>

<span data-ttu-id="ef9db-211">Ayrıca, ek sütunları ayrı tablolara yerleştirmeyi de göz önünde bulundurmaktır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-211">It's also worth considering putting any additional columns on separate tables.</span></span> <span data-ttu-id="ef9db-212">Bu nedenle, gelecekteki geçişlerin varsayılan kimlik şemasının özelleştirmeleri gibi bir hesaba sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ef9db-212">So that future migrations won't need to take into account such customizations of the default identity schema.</span></span>

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a><span data-ttu-id="ef9db-213">Verileri evrensel sağlayıcılardan ASP.NET Core kimliğe geçirme</span><span class="sxs-lookup"><span data-stu-id="ef9db-213">Migrating data from universal providers to ASP.NET Core Identity</span></span>

<span data-ttu-id="ef9db-214">Hedef tablo şemasını oluşturduktan sonra, bir sonraki adım, Kullanıcı ve rol kayıtlarınızı yeni şemaya geçirmadır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-214">Once you have the destination table schema in place, the next step is to migrate your user and role records to the new schema.</span></span> <span data-ttu-id="ef9db-215">Hangi sütunların yeni sütunlara eşlenebileceği de dahil olmak üzere, şema farklarının kapsamlı bir listesi [burada](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-215">A complete list of the schema differences, including which columns map to which new columns, can be found [here](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span>

<span data-ttu-id="ef9db-216">Kullanıcılarınıza yeni kimlik tablolarına geçiş yapmak için [belgelerde açıklanan adımları izlemeniz](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-216">To migrate your users from membership to the new identity tables, you should [follow the steps described in the documentation](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="ef9db-217">Bu adımlar ve komut dosyası sağlandıktan sonra kullanıcılarınızın bir sonraki oturum açışlarında parolasını değiştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-217">After following these steps and the script provided, your users will need to change their password the next time they log in.</span></span>

<span data-ttu-id="ef9db-218">Kullanıcı parolalarının geçirilmesi mümkündür ancak işlem çok daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-218">It is possible to migrate user passwords but the process is much more involved.</span></span> <span data-ttu-id="ef9db-219">Kullanıcıların, geçiş işleminin bir parçası olarak parolalarını güncelleştirmeleri gerekliliği ve bunları yeni, benzersiz parolalar kullanacak şekilde teşvik, uygulamanın genel güvenliğini artırmaları olasıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-219">Requiring users to update their passwords as part of the migration process, and encouraging them to use new, unique passwords, is likely to enhance the overall security of the application.</span></span>

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a><span data-ttu-id="ef9db-220">web.config güvenlik ayarlarını başlangıç. cs 'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="ef9db-220">Migrating security settings from web.config to Startup.cs</span></span>

<span data-ttu-id="ef9db-221">Yukarıda belirtildiği gibi, ASP.NET üyeliği ve rol sağlayıcıları uygulamanın `web.config` dosyasında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-221">As noted above, ASP.NET membership and role providers are configured in the application's `web.config` file.</span></span> <span data-ttu-id="ef9db-222">ASP.NET Core uygulamalar IIS 'ye bağlı olmadığından ve yapılandırma için ayrı bir sistem kullandıklarından, bu ayarların başka bir yerde yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-222">Since ASP.NET Core apps are not tied to IIS and use a separate system for configuration, these settings must be configured elsewhere.</span></span> <span data-ttu-id="ef9db-223">Çoğu bölüm için, ASP.NET Core kimlik `Startup.cs` dosyada yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-223">For the most part, ASP.NET Core Identity is configured in the `Startup.cs` file.</span></span> <span data-ttu-id="ef9db-224">Daha önce oluşturulmuş olan Web projesini açın (kimlik tablosu şeması oluşturmak için) ve dosyasını gözden geçirin `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-224">Open the web project that was created earlier (to generate the identity table schema) and review its `Startup.cs` file.</span></span>

<span data-ttu-id="ef9db-225">Varsayılan ConfigureServices yöntemi EF Core ve kimlik için destek ekler:</span><span class="sxs-lookup"><span data-stu-id="ef9db-225">The default ConfigureServices method adds support for EF Core and Identity:</span></span>

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

<span data-ttu-id="ef9db-226">`AddDefaultIdentity`Genişletme yöntemi, kimliği varsayılan `ApplicationDbContext` ve çerçevesinin türünü kullanacak şekilde yapılandırmak için kullanılır `IdentityUser` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-226">The `AddDefaultIdentity` extension method is used to configure Identity to use the default `ApplicationDbContext` and the framework's `IdentityUser` type.</span></span> <span data-ttu-id="ef9db-227">Özel bir kullanıyorsanız `IdentityUser` , türünü burada belirttiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ef9db-227">If you're using a custom `IdentityUser`, be sure to specify its type here.</span></span> <span data-ttu-id="ef9db-228">Bu uzantı yöntemleri uygulamanızda çalışmıyorsa, uygun bir using deyimlerinin olduğunu ve gerekli NuGet paket başvurularına sahip olup olmadığınızı kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="ef9db-228">If these extension methods aren't working in your application, check that you have the appropriate using statements and that you have the necessary NuGet package references.</span></span> <span data-ttu-id="ef9db-229">Örneğin, projeniz `Microsoft.AspNetCore.Identity.EntityFrameworkCore` başvurulan ve paketlerinin bazı sürümlerine sahip olmalıdır `Microsoft.AspNetCore.Identity.UI` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-229">For example, your project should have some version of the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` and `Microsoft.AspNetCore.Identity.UI` packages referenced.</span></span>

<span data-ttu-id="ef9db-230">Ayrıca, `Startup.cs` site için yapılandırılmış gerekli ara yazılımı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-230">Also in `Startup.cs` you should see the necessary middleware configured for the site.</span></span> <span data-ttu-id="ef9db-231">Özellikle, `UseAuthentication` ve `UseAuthorization` doğru konumda ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-231">Specifically, `UseAuthentication` and `UseAuthorization` should be set up, and in the proper location.</span></span>

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

<span data-ttu-id="ef9db-232">ASP.NET Identity, içindeki konumlara anonim veya rol tabanlı erişimi yapılandırmaz `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-232">ASP.NET Identity does not configure anonymous or role-based access to locations from `Startup.cs`.</span></span> <span data-ttu-id="ef9db-233">Konuma özgü herhangi bir Yetkilendirme yapılandırma verilerini ASP.NET Core filtrelerine geçirmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-233">You will need to migrate any location-specific authorization configuration data to filters in ASP.NET Core.</span></span> <span data-ttu-id="ef9db-234">Hangi klasör ve sayfaların bu güncelleştirme için gerekli olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ef9db-234">Make note of which folders and pages will require such updates.</span></span> <span data-ttu-id="ef9db-235">Sonraki bölümde bu değişiklikleri yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="ef9db-235">You will make these changes in the next section.</span></span>

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a><span data-ttu-id="ef9db-236">Bağımsız sayfaları ASP.NET Core kimlik soyutlamalarını kullanacak şekilde güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="ef9db-236">Updating individual pages to use ASP.NET Core Identity abstractions</span></span>

<span data-ttu-id="ef9db-237">ASP.NET Web Forms uygulamanızda, `web.config` anonim kullanıcılara belirli sayfalara veya klasörlere erişimi reddetme ayarlarına sahipseniz, bu değişiklikleri bu `[Authorize]` tür sayfalara ekleyerek geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ef9db-237">In your ASP.NET Web Forms application, if you had `web.config` settings to deny access to certain pages or folders to anonymous users, you would migrate these changes by adding the `[Authorize]` attribute to such pages:</span></span>

```razor
@attribute [Authorize]
```

<span data-ttu-id="ef9db-238">Belirli bir role ait olan kullanıcılar hariç erişimi daha fazla reddetseyiyorsa, bu davranışı bir rol belirten bir öznitelik ekleyerek de geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ef9db-238">If you further had denied access except to those users belonging to a certain role, you would likewise migrate this behavior by adding an attribute specifying a role:</span></span>

```razor
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="ef9db-239">`[Authorize]`Özniteliği yalnızca `@page` yönlendirici üzerinden ulaşılan bileşenlerde kullanılabilir Blazor .</span><span class="sxs-lookup"><span data-stu-id="ef9db-239">The `[Authorize]` attribute only works on `@page` components that are reached via the Blazor Router.</span></span> <span data-ttu-id="ef9db-240">Özniteliği, bunun yerine kullanılması gereken alt bileşenleriyle birlikte çalışmaz `AuthorizeView` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-240">The attribute does not work with child components, which should instead use `AuthorizeView`.</span></span>

<span data-ttu-id="ef9db-241">Belirli bir kullanıcıya bazı kodların görüntülenip görüntülenmeyeceğini belirlemek için sayfa biçimlendirmesinde mantığa sahipseniz, bunu `AuthorizeView` bileşeniyle değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9db-241">If you have logic within page markup for determining whether to display some code to a certain user, you can replace this with the `AuthorizeView` component.</span></span> <span data-ttu-id="ef9db-242">[Authorizeview bileşeni](/aspnet/core/blazor/security#authorizeview-component) , kullanıcının onu görme yetkisine sahip olup olmadığına bağlı olarak Kullanıcı arabirimini seçmeli olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ef9db-242">The [AuthorizeView component](/aspnet/core/blazor/security#authorizeview-component) selectively displays UI depending on whether the user is authorized to see it.</span></span> <span data-ttu-id="ef9db-243">Ayrıca `context` , Kullanıcı bilgilerine erişmek için kullanılabilecek bir değişken gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-243">It also exposes a `context` variable that can be used to access user information.</span></span>

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

<span data-ttu-id="ef9db-244">Kullanıcıya özniteliğiyle yapılandırılmış bir öğesinden erişerek, yordamsal mantığdaki kimlik doğrulama durumuna erişebilirsiniz `Task<AuthenticationState` `[CascadingParameter]` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-244">You can access the authentication state within procedural logic by accessing the user from a `Task<AuthenticationState` configured with the `[CascadingParameter]` attribute.</span></span> <span data-ttu-id="ef9db-245">Bu yapılandırma kullanıcıya erişim sağlar. Bu, kimlik doğrulamasının yapılıp kalmadığını ve belirli bir role ait olup olmadığını belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef9db-245">This configuration will get you access to the user, which can let you determine if they are authenticated and if they belong to a particular role.</span></span> <span data-ttu-id="ef9db-246">Bir ilke procedurally değerlendirmeniz gerekiyorsa, bir örneğini ekleyebilir `IAuthorizationService` ve `AuthorizeAsync` üzerinde yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-246">If you need to evaluate a policy procedurally, you can inject an instance of the `IAuthorizationService` and calls the `AuthorizeAsync` method on it.</span></span> <span data-ttu-id="ef9db-247">Aşağıdaki örnek kod, Kullanıcı bilgilerinin nasıl alınacağını ve yetkili bir kullanıcının ilke tarafından kısıtlanan bir görevi gerçekleştirmesine nasıl izin verildiğini gösterir `content-editor` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-247">The following sample code demonstrates how to get user information and allow an authorized user to perform a task restricted by the `content-editor` policy.</span></span>

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

<span data-ttu-id="ef9db-248">`AuthenticationState`Birincisi bunun gibi bir geçişli parametreye bağlanmadan önce, bir geçişli değer olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-248">The `AuthenticationState` first need to be set up as a cascading value before it can be bound to a cascading parameter like this.</span></span> <span data-ttu-id="ef9db-249">Bu genellikle bileşeni kullanılarak yapılır `CascadingAuthenticationState` .</span><span class="sxs-lookup"><span data-stu-id="ef9db-249">That's typically done using the `CascadingAuthenticationState` component.</span></span> <span data-ttu-id="ef9db-250">Bu yapılandırma genellikle ' de yapılır `App.razor` :</span><span class="sxs-lookup"><span data-stu-id="ef9db-250">This configuration is typically done in `App.razor`:</span></span>

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a><span data-ttu-id="ef9db-251">Özet</span><span class="sxs-lookup"><span data-stu-id="ef9db-251">Summary</span></span>

<span data-ttu-id="ef9db-252">Blazor , ASP.NET Core kimlik olan ASP.NET Core ile aynı güvenlik modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef9db-252">Blazor uses the same security model as ASP.NET Core, which is ASP.NET Core Identity.</span></span> <span data-ttu-id="ef9db-253">Evrensel sağlayıcılardan ASP.NET Core kimlik 'e geçiş oldukça basittir, ancak özgün veri şemasına çok fazla özelleştirme uygulandığını varsayarsak.</span><span class="sxs-lookup"><span data-stu-id="ef9db-253">Migrating from universal providers to ASP.NET Core Identity is relatively straightforward, assuming not too much customization was applied to the original data schema.</span></span> <span data-ttu-id="ef9db-254">Veriler geçirildikten sonra, uygulamalarda kimlik doğrulama ve yetkilendirme ile çalışmak iyi bir şekilde Blazor belgelenmiştir ve güvenlik gereksinimlerinin çoğu için programlı destek içerir.</span><span class="sxs-lookup"><span data-stu-id="ef9db-254">Once the data has been migrated, working with authentication and authorization in Blazor apps is well documented, with configurable as well as programmatic support for most security requirements.</span></span>

## <a name="references"></a><span data-ttu-id="ef9db-255">Başvurular</span><span class="sxs-lookup"><span data-stu-id="ef9db-255">References</span></span>

- [<span data-ttu-id="ef9db-256">ASP.NET Core kimliğe giriş</span><span class="sxs-lookup"><span data-stu-id="ef9db-256">Introduction to Identity on ASP.NET Core</span></span>](/aspnet/core/security/authentication/identity)
- [<span data-ttu-id="ef9db-257">ASP.NET üyelik kimlik doğrulamasından ASP.NET Core 2,0 kimliği 'ne geçiş</span><span class="sxs-lookup"><span data-stu-id="ef9db-257">Migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity</span></span>](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [<span data-ttu-id="ef9db-258">Kimlik doğrulaması ve kimliği ASP.NET Core geçir</span><span class="sxs-lookup"><span data-stu-id="ef9db-258">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/core/migration/identity)
- [<span data-ttu-id="ef9db-259">ASP.NET Core Blazor kimlik doğrulaması ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="ef9db-259">ASP.NET Core Blazor authentication and authorization</span></span>](/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
><span data-ttu-id="ef9db-260">[Önceki](config.md) 
> [Sonraki](migration.md)</span><span class="sxs-lookup"><span data-stu-id="ef9db-260">[Previous](config.md)
[Next](migration.md)</span></span>
