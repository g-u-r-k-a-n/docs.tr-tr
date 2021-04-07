---
title: 'Son değişiklik: Kestrel: HTTP/2 uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı'
description: "Kestrel başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: HTTP/2 uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b8bbe113b3357508b6af29fa9a4d1431f6a6acea
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498119"
---
# <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a><span data-ttu-id="864d7-103">Kestrel: HTTP/2, uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="864d7-103">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>

<span data-ttu-id="864d7-104">Windows üzerinde Aktarım Katmanı Güvenliği (TLS) üzerinden HTTP/2 ' yi etkinleştirmek için iki gereksinimin karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="864d7-104">To enable HTTP/2 over Transport Layer Security (TLS) on Windows, two requirements need to be met:</span></span>

- <span data-ttu-id="864d7-105">Windows 8.1 ve Windows Server 2012 R2 ile başlayarak kullanılabilen protokol anlaşması (ALPN) desteğini Application-Layer.</span><span class="sxs-lookup"><span data-stu-id="864d7-105">Application-Layer Protocol Negotiation (ALPN) support, which is available starting with Windows 8.1 and Windows Server 2012 R2.</span></span>
- <span data-ttu-id="864d7-106">Windows 10 ve Windows Server 2016 ile başlayarak kullanılabilen, HTTP/2 ile uyumlu olan bir şifre kümesi.</span><span class="sxs-lookup"><span data-stu-id="864d7-106">A set of ciphers compatible with HTTP/2, which is available starting with Windows 10 and Windows Server 2016.</span></span>

<span data-ttu-id="864d7-107">Bu nedenle, TLS üzerinden HTTP/2 yapılandırıldığında Kestrel davranışı şu şekilde değişir:</span><span class="sxs-lookup"><span data-stu-id="864d7-107">As such, Kestrel's behavior when HTTP/2 over TLS is configured has changed to:</span></span>

- <span data-ttu-id="864d7-108">`Http1` `Information` [Listenoptions. httpprotocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) olarak ayarlandığında bir iletiyi alçaltma ve bu düzeyde günlüğe kaydetme `Http1AndHttp2` .</span><span class="sxs-lookup"><span data-stu-id="864d7-108">Downgrade to `Http1` and log a message at the `Information` level when [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) is set to `Http1AndHttp2`.</span></span> <span data-ttu-id="864d7-109">`Http1AndHttp2` , için varsayılan değerdir `ListenOptions.HttpProtocols` .</span><span class="sxs-lookup"><span data-stu-id="864d7-109">`Http1AndHttp2` is the default value for `ListenOptions.HttpProtocols`.</span></span>
- <span data-ttu-id="864d7-110">`NotSupportedException` `ListenOptions.HttpProtocols` Olarak ayarlandığında bir oluşturun `Http2` .</span><span class="sxs-lookup"><span data-stu-id="864d7-110">Throw a `NotSupportedException` when `ListenOptions.HttpProtocols` is set to `Http2`.</span></span>

<span data-ttu-id="864d7-111">Tartışma için bkz. sorun [DotNet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068).</span><span class="sxs-lookup"><span data-stu-id="864d7-111">For discussion, see issue [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="864d7-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="864d7-112">Version introduced</span></span>

<span data-ttu-id="864d7-113">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="864d7-113">ASP.NET Core 5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="864d7-114">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="864d7-114">Old behavior</span></span>

<span data-ttu-id="864d7-115">Aşağıdaki tabloda, TLS üzerinden HTTP/2 yapılandırıldığında davranış özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="864d7-115">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="864d7-116">Protokoller</span><span class="sxs-lookup"><span data-stu-id="864d7-116">Protocols</span></span> | <span data-ttu-id="864d7-117">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="864d7-117">Windows 7,</span></span><br /><span data-ttu-id="864d7-118">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="864d7-118">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="864d7-119">veya daha önceki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="864d7-119">or earlier</span></span> | <span data-ttu-id="864d7-120">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="864d7-120">Windows 8,</span></span><br /><span data-ttu-id="864d7-121">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="864d7-121">Windows Server 2012</span></span> | <span data-ttu-id="864d7-122">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="864d7-122">Windows 8.1,</span></span><br /><span data-ttu-id="864d7-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="864d7-123">Windows Server 2012 R2</span></span> | <span data-ttu-id="864d7-124">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="864d7-124">Windows 10,</span></span><br /><span data-ttu-id="864d7-125">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="864d7-125">Windows Server 2016,</span></span><br /><span data-ttu-id="864d7-126">veya daha yeni</span><span class="sxs-lookup"><span data-stu-id="864d7-126">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="864d7-127">Yaratır `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="864d7-127">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="864d7-128">TLS el sıkışması sırasında hata</span><span class="sxs-lookup"><span data-stu-id="864d7-128">Error during TLS handshake</span></span>     | <span data-ttu-id="864d7-129">TLS el sıkışması sırasında hata &ast;</span><span class="sxs-lookup"><span data-stu-id="864d7-129">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="864d7-130">Hata yok</span><span class="sxs-lookup"><span data-stu-id="864d7-130">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="864d7-131">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="864d7-131">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="864d7-132">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="864d7-132">Downgrade to `Http1`</span></span>     | <span data-ttu-id="864d7-133">TLS el sıkışması sırasında hata &ast;</span><span class="sxs-lookup"><span data-stu-id="864d7-133">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="864d7-134">Hata yok</span><span class="sxs-lookup"><span data-stu-id="864d7-134">No error</span></span> |

<span data-ttu-id="864d7-135">&ast; Bu senaryoları etkinleştirmek için uyumlu şifre paketlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="864d7-135">&ast; Configure compatible cipher suites to enable these scenarios.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="864d7-136">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="864d7-136">New behavior</span></span>

<span data-ttu-id="864d7-137">Aşağıdaki tabloda, TLS üzerinden HTTP/2 yapılandırıldığında davranış özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="864d7-137">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="864d7-138">Protokoller</span><span class="sxs-lookup"><span data-stu-id="864d7-138">Protocols</span></span> | <span data-ttu-id="864d7-139">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="864d7-139">Windows 7,</span></span><br /><span data-ttu-id="864d7-140">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="864d7-140">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="864d7-141">veya daha önceki bir sürümü</span><span class="sxs-lookup"><span data-stu-id="864d7-141">or earlier</span></span> | <span data-ttu-id="864d7-142">Windows 8,</span><span class="sxs-lookup"><span data-stu-id="864d7-142">Windows 8,</span></span><br /><span data-ttu-id="864d7-143">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="864d7-143">Windows Server 2012</span></span> | <span data-ttu-id="864d7-144">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="864d7-144">Windows 8.1,</span></span><br /><span data-ttu-id="864d7-145">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="864d7-145">Windows Server 2012 R2</span></span> | <span data-ttu-id="864d7-146">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="864d7-146">Windows 10,</span></span><br /><span data-ttu-id="864d7-147">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="864d7-147">Windows Server 2016,</span></span><br /><span data-ttu-id="864d7-148">veya daha yeni</span><span class="sxs-lookup"><span data-stu-id="864d7-148">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="864d7-149">Yaratır `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="864d7-149">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="864d7-150">Yaratır `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="864d7-150">Throw `NotSupportedException`</span></span>     | <span data-ttu-id="864d7-151">Throw `NotSupportedException`&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="864d7-151">Throw `NotSupportedException` &ast;&ast;</span></span>     | <span data-ttu-id="864d7-152">Hata yok</span><span class="sxs-lookup"><span data-stu-id="864d7-152">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="864d7-153">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="864d7-153">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="864d7-154">Düşürme `Http1`</span><span class="sxs-lookup"><span data-stu-id="864d7-154">Downgrade to `Http1`</span></span>     | <span data-ttu-id="864d7-155">`Http1`Düşürme&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="864d7-155">Downgrade to `Http1` &ast;&ast;</span></span>     | <span data-ttu-id="864d7-156">Hata yok</span><span class="sxs-lookup"><span data-stu-id="864d7-156">No error</span></span> |

<span data-ttu-id="864d7-157">&ast;&ast; Uyumlu şifre paketlerini yapılandırın ve `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` `true` Bu senaryoları etkinleştirmek için uygulama bağlam anahtarını olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="864d7-157">&ast;&ast; Configure compatible cipher suites and set the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` to `true` to enable these scenarios.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="864d7-158">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="864d7-158">Reason for change</span></span>

<span data-ttu-id="864d7-159">Bu değişiklik, eski Windows sürümlerindeki TLS üzerinden HTTP/2 uyumluluk hatalarının erken ve mümkün olduğunca net bir şekilde ortaya geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="864d7-159">This change ensures compatibility errors for HTTP/2 over TLS on older Windows versions are surfaced as early and as clearly as possible.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="864d7-160">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="864d7-160">Recommended action</span></span>

<span data-ttu-id="864d7-161">Uyumsuz Windows sürümlerinde TLS üzerinden HTTP/2 devre dışı bırakıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="864d7-161">Ensure HTTP/2 over TLS is disabled on incompatible Windows versions.</span></span> <span data-ttu-id="864d7-162">Windows 8.1 ve Windows Server 2012 R2, varsayılan olarak gerekli şifrelemeleri olmadığından uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="864d7-162">Windows 8.1 and Windows Server 2012 R2 are incompatible since they lack the necessary ciphers by default.</span></span> <span data-ttu-id="864d7-163">Ancak, bilgisayar yapılandırma ayarlarını HTTP/2 ile uyumlu şifrelemeleri kullanacak şekilde güncelleştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="864d7-163">However, it's possible to update the Computer Configuration settings to use HTTP/2 compatible ciphers.</span></span> <span data-ttu-id="864d7-164">Daha fazla bilgi için bkz. [Windows 8.1 'de TLS şifre paketleri](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span><span class="sxs-lookup"><span data-stu-id="864d7-164">For more information, see [TLS cipher suites in Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span></span> <span data-ttu-id="864d7-165">Yapılandırıldıktan sonra Kestrel üzerinde TLS üzerinden HTTP/2, uygulama bağlamı anahtarı ayarlanarak etkinleştirilmelidir `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` .</span><span class="sxs-lookup"><span data-stu-id="864d7-165">Once configured, HTTP/2 over TLS on Kestrel must be enabled by setting the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span></span> <span data-ttu-id="864d7-166">Örnek:</span><span class="sxs-lookup"><span data-stu-id="864d7-166">For example:</span></span>

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

<span data-ttu-id="864d7-167">Temel alınan destek değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="864d7-167">No underlying support has changed.</span></span> <span data-ttu-id="864d7-168">Örneğin, TLS üzerinden HTTP/2, Windows 8 veya Windows Server 2012 ' de hiç çalışmadı.</span><span class="sxs-lookup"><span data-stu-id="864d7-168">For example, HTTP/2 over TLS has never worked on Windows 8 or Windows Server 2012.</span></span> <span data-ttu-id="864d7-169">Bu değişiklik, bu desteklenmeyen senaryolardaki hataların sunulma şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="864d7-169">This change modifies how errors in these unsupported scenarios are presented.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="864d7-170">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="864d7-170">Affected APIs</span></span>

<span data-ttu-id="864d7-171">Yok</span><span class="sxs-lookup"><span data-stu-id="864d7-171">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
