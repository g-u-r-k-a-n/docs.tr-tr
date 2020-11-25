---
title: "Son değişiklik: kimlik doğrulaması: AzureAD. UI ve AzureADB2C. UI API 'Leri ve kullanım dışı olarak işaretlenen paketler"
description: "Kimlik doğrulaması ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: AzureAD. UI ve AzureADB2C. UI API 'Leri ve kullanım dışı olarak işaretlenen paketler"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c977ba4d6e34fc5f11133bdd1446a94d54efcb63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761666"
---
# <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a><span data-ttu-id="e7d76-103">Kimlik doğrulaması: AzureAD. UI ve AzureADB2C. UI API 'Leri ve kullanım dışı olarak işaretlenen paketler</span><span class="sxs-lookup"><span data-stu-id="e7d76-103">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>

<span data-ttu-id="e7d76-104">ASP.NET Core 2,1 ' de, Azure Active Directory (Azure AD) ve Azure Active Directory B2C (Azure AD B2C) kimlik doğrulaması ile tümleştirme [Microsoft. aspnetcore. Authentication. AzureAD. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) ve [Microsoft. Aspnetcore. Authentication. AzureADB2C. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) paketleri tarafından sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7d76-104">In ASP.NET Core 2.1, integration with Azure Active Directory (Azure AD) and Azure Active Directory B2C (Azure AD B2C) authentication is provided by the [Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) and [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) packages.</span></span> <span data-ttu-id="e7d76-105">Bu paketler tarafından sunulan işlevsellik, Azure AD v 1.0 uç noktasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="e7d76-105">The functionality provided by these packages is based on the Azure AD v1.0 endpoint.</span></span>

<span data-ttu-id="e7d76-106">ASP.NET Core 5,0 ve üzeri sürümlerde, Azure AD ve Azure AD B2C kimlik doğrulamasıyla tümleştirme [Microsoft. Identity. Web](https://www.nuget.org/packages/Microsoft.Identity.Web) paketi tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e7d76-106">In ASP.NET Core 5.0 and later, integration with Azure AD and Azure AD B2C authentication is provided by the [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) package.</span></span> <span data-ttu-id="e7d76-107">Bu paket, daha önce Azure AD v 2.0 uç noktası olarak bilinen Microsoft Identity platformunu temel alır.</span><span class="sxs-lookup"><span data-stu-id="e7d76-107">This package is based on the Microsoft Identity Platform, which is formerly known as the Azure AD v2.0 endpoint.</span></span> <span data-ttu-id="e7d76-108">Sonuç olarak, `Microsoft.AspNetCore.Authentication.AzureAD.UI` ve paketlerdeki eski API 'ler `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e7d76-108">Consequently, the old APIs in the `Microsoft.AspNetCore.Authentication.AzureAD.UI` and `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages were deprecated.</span></span>

<span data-ttu-id="e7d76-109">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807).</span><span class="sxs-lookup"><span data-stu-id="e7d76-109">For discussion, see GitHub issue [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e7d76-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e7d76-110">Version introduced</span></span>

<span data-ttu-id="e7d76-111">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="e7d76-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="e7d76-112">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e7d76-112">Old behavior</span></span>

<span data-ttu-id="e7d76-113">API 'Ler eski olarak işaretlenmedi.</span><span class="sxs-lookup"><span data-stu-id="e7d76-113">The APIs weren't marked as obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="e7d76-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e7d76-114">New behavior</span></span>

<span data-ttu-id="e7d76-115">API 'Ler eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="e7d76-115">The APIs are marked as obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e7d76-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e7d76-116">Reason for change</span></span>

<span data-ttu-id="e7d76-117">Azure AD ve Azure AD B2C kimlik doğrulaması işlevselliği tarafından sağlanmış olan Microsoft kimlik doğrulama kitaplığı (MSAL) API 'Lerine geçirildi `Microsoft.Identity.Web` .</span><span class="sxs-lookup"><span data-stu-id="e7d76-117">The Azure AD and Azure AD B2C authentication functionality was migrated to Microsoft Authentication Library (MSAL) APIs that are provided by `Microsoft.Identity.Web`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e7d76-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e7d76-118">Recommended action</span></span>

<span data-ttu-id="e7d76-119">`Microsoft.Identity.Web` [Web uygulamaları](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) ve [Web API 'leri](https://github.com/azuread/microsoft-identity-web/wiki/web-apis)için API kılavuzunu izleyin.</span><span class="sxs-lookup"><span data-stu-id="e7d76-119">Follow the `Microsoft.Identity.Web` API guidance for [web apps](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) and [web APIs](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e7d76-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e7d76-120">Affected APIs</span></span>

* [<span data-ttu-id="e7d76-121">Microsoft. AspNetCore. Authentication. AzureADAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="e7d76-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="e7d76-122">Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADDefaults</span><span class="sxs-lookup"><span data-stu-id="e7d76-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="e7d76-123">Microsoft. aspnetcore. Authentication. azuread. UI. azureadoçen</span><span class="sxs-lookup"><span data-stu-id="e7d76-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [<span data-ttu-id="e7d76-124">Microsoft. AspNetCore. Authentication. AzureADB2CAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="e7d76-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="e7d76-125">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2CDefaults</span><span class="sxs-lookup"><span data-stu-id="e7d76-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="e7d76-126">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2COptions</span><span class="sxs-lookup"><span data-stu-id="e7d76-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
