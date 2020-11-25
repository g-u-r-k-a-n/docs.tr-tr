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
# <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a>Kimlik doğrulaması: AzureAD. UI ve AzureADB2C. UI API 'Leri ve kullanım dışı olarak işaretlenen paketler

ASP.NET Core 2,1 ' de, Azure Active Directory (Azure AD) ve Azure Active Directory B2C (Azure AD B2C) kimlik doğrulaması ile tümleştirme [Microsoft. aspnetcore. Authentication. AzureAD. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) ve [Microsoft. Aspnetcore. Authentication. AzureADB2C. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) paketleri tarafından sağlanmaktadır. Bu paketler tarafından sunulan işlevsellik, Azure AD v 1.0 uç noktasını temel alır.

ASP.NET Core 5,0 ve üzeri sürümlerde, Azure AD ve Azure AD B2C kimlik doğrulamasıyla tümleştirme [Microsoft. Identity. Web](https://www.nuget.org/packages/Microsoft.Identity.Web) paketi tarafından sağlanır. Bu paket, daha önce Azure AD v 2.0 uç noktası olarak bilinen Microsoft Identity platformunu temel alır. Sonuç olarak, `Microsoft.AspNetCore.Authentication.AzureAD.UI` ve paketlerdeki eski API 'ler `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` kullanımdan kaldırılmıştır.

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

## <a name="old-behavior"></a>Eski davranış

API 'Ler eski olarak işaretlenmedi.

## <a name="new-behavior"></a>Yeni davranış

API 'Ler eski olarak işaretlenir.

## <a name="reason-for-change"></a>Değişiklik nedeni

Azure AD ve Azure AD B2C kimlik doğrulaması işlevselliği tarafından sağlanmış olan Microsoft kimlik doğrulama kitaplığı (MSAL) API 'Lerine geçirildi `Microsoft.Identity.Web` .

## <a name="recommended-action"></a>Önerilen eylem

`Microsoft.Identity.Web` [Web uygulamaları](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) ve [Web API 'leri](https://github.com/azuread/microsoft-identity-web/wiki/web-apis)için API kılavuzunu izleyin.

## <a name="affected-apis"></a>Etkilenen API’ler

* [Microsoft. AspNetCore. Authentication. AzureADAuthenticationBuilderExtensions](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADDefaults](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [Microsoft. aspnetcore. Authentication. azuread. UI. azureadoçen](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureADB2CAuthenticationBuilderExtensions](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2CDefaults](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2COptions](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

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
