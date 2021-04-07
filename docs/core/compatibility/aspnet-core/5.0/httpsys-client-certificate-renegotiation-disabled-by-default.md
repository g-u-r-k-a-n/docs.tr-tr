---
title: 'Son değişiklik: HttpSys: Istemci sertifikası yeniden anlaşması varsayılan olarak devre dışıdır'
description: "HttpSys başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: Istemci sertifikası yeniden anlaşması varsayılan olarak devre dışıdır"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 41c421417125061fa9879f14a1307aa1463ca033
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498132"
---
# <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a>HttpSys: İstemci sertifikası yeniden anlaşması varsayılan olarak devre dışıdır

Bir bağlantıyı yeniden oluşturma ve istemci sertifikası isteme seçeneği varsayılan olarak devre dışı bırakılmıştır. Tartışma için bkz. sorun [DotNet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181).

## <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 5,0

## <a name="old-behavior"></a>Eski davranış

İstemci sertifikası istemek için bağlantıya yeniden anlaşma yapılabilir.

## <a name="new-behavior"></a>Yeni davranış

İstemci sertifikaları yalnızca ilk bağlantı el sıkışması sırasında istenebilir. Daha fazla bilgi için bkz. çekme isteği [DotNet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162).

## <a name="reason-for-change"></a>Değişiklik nedeni

Yeniden anlaşma, bir dizi performans ve kilitlenme sorununa neden oldu. HTTP/2 ' de de desteklenmez. Bu davranışı denetleme seçeneğinin ASP.NET Core 3,1 ' de tanıtılmasından daha fazla bağlam için, bkz. sorun [DotNet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806).

## <a name="recommended-action"></a>Önerilen eylem

İstemci sertifikaları gerektiren uygulamalar, seçeneğini olarak ayarlamak için *netsh.exe* kullanmalıdır `clientcertnegotiation` `enabled` . Daha fazla bilgi için bkz. [netsh http komutları](/windows-server/networking/technologies/netsh/netsh-http).

İstemci sertifikalarının yalnızca uygulamanızın bazı bölümleri için etkinleştirilmesini istiyorsanız, [Isteğe bağlı istemci sertifikalarındaki](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates)kılavuza bakın.

Eski yeniden anlaşmak davranışına ihtiyacınız varsa `HttpSysOptions.ClientCertificateMethod` eski değere ayarlayın `ClientCertificateMethod.AllowRenegotiate` . Bu, yukarıda ve bağlantılı kılavuzda özetlenen nedenlerle önerilmez.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
