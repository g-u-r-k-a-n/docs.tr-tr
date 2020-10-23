---
ms.openlocfilehash: d9526055041f036958699aa935aa6cfef494b520
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434952"
---
### <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="ac4df-101">PrincipalPermissionAttribute hata olarak kullanımdan kalktı</span><span class="sxs-lookup"><span data-stu-id="ac4df-101">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="ac4df-102"><xref:System.Security.Permissions.PrincipalPermissionAttribute>Oluşturucu kullanımdan kalkmıştır ve derleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac4df-102">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="ac4df-103">Bu özniteliği örnekleyemezsiniz veya bir yönteme uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ac4df-103">You cannot instantiate this attribute or apply it to a method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ac4df-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="ac4df-104">Change description</span></span>

<span data-ttu-id="ac4df-105">.NET Framework ve .NET Core 'da, özniteliğiyle yöntemlere not ekleyebilirsiniz <xref:System.Security.Permissions.PrincipalPermissionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ac4df-105">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="ac4df-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ac4df-106">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="ac4df-107">.NET 5,0 ' den başlayarak <xref:System.Security.Permissions.PrincipalPermissionAttribute> özniteliği bir yönteme uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ac4df-107">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="ac4df-108">Özniteliği için Oluşturucu artık kullanılmıyor ve derleme zamanı hatası veriyor.</span><span class="sxs-lookup"><span data-stu-id="ac4df-108">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="ac4df-109">Kullanımdan çıkarma uyarılarının aksine, hatayı bastırılamaz.</span><span class="sxs-lookup"><span data-stu-id="ac4df-109">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ac4df-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="ac4df-110">Reason for change</span></span>

<span data-ttu-id="ac4df-111"><xref:System.Security.Permissions.PrincipalPermissionAttribute>Türü, alt sınıfını oluşturan diğer türler gibi <xref:System.Security.Permissions.SecurityAttribute> bir parçasıdır. NET 'in kod erişim güvenliği (CAS) altyapısı.</span><span class="sxs-lookup"><span data-stu-id="ac4df-111">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="ac4df-112">.NET Framework 2. x-4. x içinde, çalışma zamanı, <xref:System.Security.Permissions.PrincipalPermissionAttribute> uygulama tam güven senaryosunda çalışıyor olsa bile Yöntem girişinde ek açıklamaları zorlar.</span><span class="sxs-lookup"><span data-stu-id="ac4df-112">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="ac4df-113">.NET Core ve .NET 5,0 ve üzeri CAS özniteliklerini desteklemez ve çalışma zamanı bunları yoksayar.</span><span class="sxs-lookup"><span data-stu-id="ac4df-113">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="ac4df-114">.NET Framework .NET Core ve .NET 5,0 davranışlarındaki bu fark, erişimin engellenmesi gereken ancak bunun yerine izin verilen bir "başarısız açma" senaryosu oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac4df-114">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="ac4df-115">"Başarısız açma" senaryosunu engellemek için artık .NET 5,0 veya üstünü hedefleyen kodda özniteliği uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ac4df-115">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ac4df-116">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ac4df-116">Version introduced</span></span>

<span data-ttu-id="ac4df-117">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="ac4df-117">5.0 Preview 7</span></span>

#### <a name=""></a><span data-ttu-id="ac4df-118"><a id="permission-action">Önerilen eylem</a></span><span class="sxs-lookup"><span data-stu-id="ac4df-118"><a id="permission-action">Recommended action</a></span></span>

<span data-ttu-id="ac4df-119">Kullanımdan çıkarma hatasıyla karşılaşırsanız, işlem yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac4df-119">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="ac4df-120">**Özniteliği bir ASP.NET MVC eylem yöntemine uyguluyorsanız:**</span><span class="sxs-lookup"><span data-stu-id="ac4df-120">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="ac4df-121">ASP kullanmayı düşünün. NET 'in yerleşik yetkilendirme altyapısı.</span><span class="sxs-lookup"><span data-stu-id="ac4df-121">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="ac4df-122">Aşağıdaki kod, bir denetleyiciye bir özniteliğe nasıl not ekleneceğini gösterir <xref:System.Web.Mvc.AuthorizeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ac4df-122">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="ac4df-123">ASP.NET çalışma zamanı, eylemi gerçekleştirmeden önce kullanıcıyı yetkilendirecektir.</span><span class="sxs-lookup"><span data-stu-id="ac4df-123">The ASP.NET runtime will authorize the user before performing the action.</span></span>

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  <span data-ttu-id="ac4df-124">Daha fazla bilgi için, [ASP.NET Core rol tabanlı yetkilendirme](/aspnet/core/security/authorization/roles) ve [ASP.NET Core yetkilendirme bölümüne giriş](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="ac4df-124">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="ac4df-125">**Özniteliği, bir Web uygulaması bağlamı dışında kitaplık koduna uyguluyorsanız:**</span><span class="sxs-lookup"><span data-stu-id="ac4df-125">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="ac4df-126">Yönteminizin başlangıcında denetimleri el ile gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="ac4df-126">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="ac4df-127">Bu, yöntemi kullanılarak yapılabilir <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ac4df-127">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

#### <a name="category"></a><span data-ttu-id="ac4df-128">Kategori</span><span class="sxs-lookup"><span data-stu-id="ac4df-128">Category</span></span>

- <span data-ttu-id="ac4df-129">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="ac4df-129">Core .NET libraries</span></span>
- <span data-ttu-id="ac4df-130">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="ac4df-130">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ac4df-131">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ac4df-131">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
