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
# <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a><span data-ttu-id="a2123-103">HttpSys: İstemci sertifikası yeniden anlaşması varsayılan olarak devre dışıdır</span><span class="sxs-lookup"><span data-stu-id="a2123-103">HttpSys: Client certificate renegotiation disabled by default</span></span>

<span data-ttu-id="a2123-104">Bir bağlantıyı yeniden oluşturma ve istemci sertifikası isteme seçeneği varsayılan olarak devre dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2123-104">The option to renegotiate a connection and request a client certificate has been disabled by default.</span></span> <span data-ttu-id="a2123-105">Tartışma için bkz. sorun [DotNet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181).</span><span class="sxs-lookup"><span data-stu-id="a2123-105">For discussion, see issue [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a2123-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a2123-106">Version introduced</span></span>

<span data-ttu-id="a2123-107">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="a2123-107">ASP.NET Core 5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a2123-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a2123-108">Old behavior</span></span>

<span data-ttu-id="a2123-109">İstemci sertifikası istemek için bağlantıya yeniden anlaşma yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2123-109">The connection can be renegotiated to request a client certificate.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="a2123-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a2123-110">New behavior</span></span>

<span data-ttu-id="a2123-111">İstemci sertifikaları yalnızca ilk bağlantı el sıkışması sırasında istenebilir.</span><span class="sxs-lookup"><span data-stu-id="a2123-111">Client certificates can only be requested during the initial connection handshake.</span></span> <span data-ttu-id="a2123-112">Daha fazla bilgi için bkz. çekme isteği [DotNet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162).</span><span class="sxs-lookup"><span data-stu-id="a2123-112">For more information, see pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a2123-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a2123-113">Reason for change</span></span>

<span data-ttu-id="a2123-114">Yeniden anlaşma, bir dizi performans ve kilitlenme sorununa neden oldu.</span><span class="sxs-lookup"><span data-stu-id="a2123-114">Renegotiation caused a number of performance and deadlock issues.</span></span> <span data-ttu-id="a2123-115">HTTP/2 ' de de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a2123-115">It's also not supported in HTTP/2.</span></span> <span data-ttu-id="a2123-116">Bu davranışı denetleme seçeneğinin ASP.NET Core 3,1 ' de tanıtılmasından daha fazla bağlam için, bkz. sorun [DotNet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806).</span><span class="sxs-lookup"><span data-stu-id="a2123-116">For additional context from when the option to control this behavior was introduced in ASP.NET Core 3.1, see issue [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a2123-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a2123-117">Recommended action</span></span>

<span data-ttu-id="a2123-118">İstemci sertifikaları gerektiren uygulamalar, seçeneğini olarak ayarlamak için *netsh.exe* kullanmalıdır `clientcertnegotiation` `enabled` .</span><span class="sxs-lookup"><span data-stu-id="a2123-118">Apps that require client certificates should use *netsh.exe* to set the `clientcertnegotiation` option to `enabled`.</span></span> <span data-ttu-id="a2123-119">Daha fazla bilgi için bkz. [netsh http komutları](/windows-server/networking/technologies/netsh/netsh-http).</span><span class="sxs-lookup"><span data-stu-id="a2123-119">For more information, see [netsh http commands](/windows-server/networking/technologies/netsh/netsh-http).</span></span>

<span data-ttu-id="a2123-120">İstemci sertifikalarının yalnızca uygulamanızın bazı bölümleri için etkinleştirilmesini istiyorsanız, [Isteğe bağlı istemci sertifikalarındaki](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates)kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="a2123-120">If you want client certificates enabled for only some parts of your app, see the guidance at [Optional client certificates](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span></span>

<span data-ttu-id="a2123-121">Eski yeniden anlaşmak davranışına ihtiyacınız varsa `HttpSysOptions.ClientCertificateMethod` eski değere ayarlayın `ClientCertificateMethod.AllowRenegotiate` .</span><span class="sxs-lookup"><span data-stu-id="a2123-121">If you need the old renegotiate behavior, set `HttpSysOptions.ClientCertificateMethod` to the old value `ClientCertificateMethod.AllowRenegotiate`.</span></span> <span data-ttu-id="a2123-122">Bu, yukarıda ve bağlantılı kılavuzda özetlenen nedenlerle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="a2123-122">This isn't recommended for the reasons outlined above and in the linked guidance.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a2123-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a2123-123">Affected APIs</span></span>

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
