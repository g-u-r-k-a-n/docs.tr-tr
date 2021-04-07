---
title: ASP.NET Core son değişiklikler
titleSuffix: ''
description: ASP.NET Core 3,0 ve 3,1 ' deki son değişiklikleri listeler.
ms.date: 11/03/2020
ms.author: scaddie
ms.openlocfilehash: 080cd3c34617e932b64806a6aa1268b4e397e410
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497222"
---
# <a name="aspnet-core-breaking-changes-for-versions-30-and-31"></a>3,0 ve 3,1 sürümleri için ASP.NET Core son değişiklikler

ASP.NET Core .NET Core tarafından kullanılan Web uygulaması geliştirme özelliklerini sağlar.

Belirli bir sürümdeki son değişiklikler için aşağıdaki bağlantılardan birini seçin:

* [ASP.NET Core 3,1](#aspnet-core-31)
* [ASP.NET Core 3,0](#aspnet-core-30)

ASP.NET Core 3,0 ve 3,1 ' deki aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

- [Kullanılmayan Antiforgery, CORS, tanılama, MVC ve yönlendirme API 'Leri kaldırıldı](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Kimlik doğrulaması: Google + kullanımdan kaldırma](#authentication-google-deprecated-and-replaced)
- [Kimlik doğrulaması: HttpContext. Authentication özelliği kaldırıldı](#authentication-httpcontextauthentication-property-removed)
- [Kimlik doğrulaması: değiştirilmekte olan türler üzerinde Newtonsoft.Js](#authentication-newtonsoftjson-types-replaced)
- [Kimlik doğrulaması: OAuthHandler ExchangeCodeAsync imzası değişti](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Yetkilendirme: Addaduthorleştirme aşırı yüklemesi farklı bir derlemeye taşındı](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Yetkilendirme: ıallowanonymous, AuthorizationFilterContext. Filters öğesinden kaldırıldı](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı](#caching-compactonmemorypressure-property-removed)
- [Önbelleğe alma: Microsoft. Extensions. Caching. SqlServer yeni SqlClient paketini kullanır](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Veri koruma: DataProtection. blob 'lar yeni Azure depolama API 'Lerini kullanır](#data-protection-dataprotectionblobs-uses-new-azure-storage-apis)
- [Barındırma: AspNetCoreModule v1 Windows barındırma paketinden kaldırıldı](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Barındırma: genel ana bilgisayar, başlangıç Oluşturucu ekleme işlemini kısıtlar](#hosting-generic-host-restricts-startup-constructor-injection)
- [Barındırma: IIS işlem dışı uygulamalar için HTTPS yönlendirmesi etkinleştirildi](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Barındırma: ıhostingenvironment ve ıapplicationlifetime türleri değişti](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıklarından kaldırıldı](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP: Browser SameSite değişikliklerinin etkisi kimlik doğrulaması](#http-browser-samesite-changes-impact-authentication)
- [HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı](#http-defaulthttpcontext-extensibility-removed)
- [HTTP: HeaderNames alanları statik ReadOnly olarak değiştirildi](#http-headernames-constants-changed-to-static-readonly)
- [HTTP: yanıt gövdesi altyapı değişiklikleri](#http-response-body-infrastructure-changes)
- [HTTP: bazı tanımlama bilgisi SameSite varsayılan değerleri değiştirildi](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP: zaman uyumlu GÇ varsayılan olarak devre dışıdır](#http-synchronous-io-disabled-in-all-servers)
- [Kimlik: Adddefaultuı yöntemi aşırı yüklemesi kaldırıldı](#identity-adddefaultui-method-overload-removed)
- [Kimlik: UI önyükleme sürümü değişikliği](#identity-default-bootstrap-version-of-ui-changed)
- [Kimlik: Signınasync kimliği doğrulanmamış kimlik için özel durum oluşturur](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Kimlik: SignInManager Oluşturucusu yeni parametreyi kabul ediyor](#identity-signinmanager-constructor-accepts-new-parameter)
- [Kimlik: UI statik Web varlıkları özelliğini kullanır](#identity-ui-uses-static-web-assets-feature)
- [Kestrel: bağlantı bağdaştırıcıları kaldırıldı](#kestrel-connection-adapters-removed)
- [Kestrel: boş HTTPS derlemesi kaldırıldı](#kestrel-empty-https-assembly-removed)
- [Kestrel: yeni koleksiyona taşınan artbilgisi üstbilgileri ıste](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel: aktarım soyutlama katmanı değişiklikleri](#kestrel-transport-abstractions-removed-and-made-public)
- [Yerelleştirme: kullanım dışı olarak işaretlenen API 'Ler](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Günlüğe kaydetme: Debuggünlükçü sınıfı iç oluşturulmuş](#logging-debuglogger-class-made-internal)
- [MVC: denetleyici eylemi zaman uyumsuz son ek kaldırıldı](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC: JsonResult, Microsoft. AspNetCore. Mvc. Core 'a taşındı](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC: ön derleme aracı kullanım dışı](#mvc-precompilation-tool-deprecated)
- [MVC: türler internal olarak değiştirildi](#mvc-pubternal-types-changed-to-internal)
- [MVC: Web API 'SI uyumluluk dolgusu kaldırıldı](#mvc-web-api-compatibility-shim-removed)
- [Razor: RazorTemplateEngine API 'SI kaldırıldı](#razor-razortemplateengine-api-removed)
- [Razor: çalışma zamanı derlemesi bir pakete taşındı](#razor-runtime-compilation-moved-to-a-package)
- [Oturum durumu: kullanılmayan API 'Ler kaldırıldı](#session-state-obsolete-apis-removed)
- [Paylaşılan çerçeve: Microsoft.AspNetCore.App 'den derleme kaldırma](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Paylaşılan çerçeve: Microsoft. AspNetCore. All kaldırıldı](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR: HandshakeProtocol. Başarıkıandshakedata değişti](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR: HubConnection yöntemleri kaldırıldı](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR: HubConnectionContext oluşturucuları değişti](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR: JavaScript istemci paketi adı değişikliği](#signalr-javascript-client-package-name-changed)
- [SignalR: kullanılmayan API 'Ler](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [Maça 'Lar: SpaServices ve NodeServices konsol günlükçü geri dönüş varsayılan değişikliği](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [Maça 'Lar: gereksiz olarak işaretlenen SpaServices ve NodeServices](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Hedef Framework: .NET Framework desteklenmiyor](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a>ASP.NET Core 3,1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Core 3,0

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
