---
title: 'Son değişiklik: güvenlik: tanımlama bilgisi adı kodlama kaldırıldı'
description: 'ASP.NET Core 5,0 güvenlik konusunda son değişiklik hakkında bilgi edinin: tanımlama bilgisi adı kodlama kaldırıldı'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: a50ef0ee34b7148d13b01f96e754d1cb47d40819
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497898"
---
# <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="3053b-103">Güvenlik: tanımlama bilgisi ad kodlaması kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="3053b-103">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="3053b-104">[Http tanımlama bilgisi standardı](https://tools.ietf.org/html/rfc6265#section-4.1.1) , tanımlama bilgisi adlarında ve değerlerinde yalnızca belirli karakterlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="3053b-104">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="3053b-105">İzin verilmeyen karakterleri desteklemek için ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="3053b-105">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="3053b-106">Yanıt tanımlama bilgisi oluştururken kodlama.</span><span class="sxs-lookup"><span data-stu-id="3053b-106">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="3053b-107">İstek tanımlama bilgisini okurken kodunu çözer.</span><span class="sxs-lookup"><span data-stu-id="3053b-107">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="3053b-108">ASP.NET Core 5,0 ' de, bu kodlama davranışı güvenlik kaygıına yanıt olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3053b-108">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="3053b-109">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).</span><span class="sxs-lookup"><span data-stu-id="3053b-109">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3053b-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3053b-110">Version introduced</span></span>

<span data-ttu-id="3053b-111">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="3053b-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="3053b-112">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="3053b-112">Old behavior</span></span>

<span data-ttu-id="3053b-113">Yanıt tanımlama bilgisi adları kodlanır.</span><span class="sxs-lookup"><span data-stu-id="3053b-113">Response cookie names are encoded.</span></span> <span data-ttu-id="3053b-114">İstek tanımlama bilgisi adlarının kodu çözüldü.</span><span class="sxs-lookup"><span data-stu-id="3053b-114">Request cookie names are decoded.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="3053b-115">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="3053b-115">New behavior</span></span>

<span data-ttu-id="3053b-116">Tanımlama bilgisi adlarının kodlama ve kod çözme işlemi kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3053b-116">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="3053b-117">ASP.NET Core önceki [desteklenen sürümleri](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) için, takım, kod çözme sorununu yerinde azaltmanızı planlıyor.</span><span class="sxs-lookup"><span data-stu-id="3053b-117">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="3053b-118">Ayrıca, <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> geçersiz bir tanımlama bilgisi adıyla çağırmak, türünde bir özel durum oluşturur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="3053b-118">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="3053b-119">Tanımlama bilgisi değerlerinin kodlama ve kod çözme değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="3053b-119">Encoding and decoding of cookie values remains unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3053b-120">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3053b-120">Reason for change</span></span>

<span data-ttu-id="3053b-121">[Birden çok Web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52)çerçevesi içinde bir sorun bulundu.</span><span class="sxs-lookup"><span data-stu-id="3053b-121">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="3053b-122">Kodlama ve kod çözme, bir saldırganın, gibi kodlanmış değerler ile gibi ayrılmış önekleri yanıltarak [tanımlama bilgisi önekleri](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) adlı bir güvenlik özelliğini atlamasına izin verebilir `__Host-` `__%48ost-` .</span><span class="sxs-lookup"><span data-stu-id="3053b-122">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="3053b-123">Saldırı, Web sitesinde siteler arası betik oluşturma (XSS) güvenlik açığı gibi sahte tanımlama bilgilerini eklemek için ikincil bir yararlanma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3053b-123">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="3053b-124">Bu ön ekler, ASP.NET Core veya `Microsoft.Owin` kitaplıklarda ya da şablonlarda varsayılan olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="3053b-124">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3053b-125">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3053b-125">Recommended action</span></span>

<span data-ttu-id="3053b-126">Projeleri ASP.NET Core 5,0 veya üzeri bir sürüme taşıyorsanız, tanımlama bilgisi adlarının [belirteç belirtim gereksinimlerine](https://tools.ietf.org/html/rfc2616#section-2.2)uygun olduğundan emin olun: denetimler ve ayırıcılar hariç ASCII karakterleri `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` .</span><span class="sxs-lookup"><span data-stu-id="3053b-126">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="3053b-127">Tanımlama bilgisi adlarında ASCII olmayan karakterlerin kullanılması veya diğer HTTP üstbilgileri, sunucudan bir özel duruma neden olabilir veya istemci tarafından doğru şekilde yuvarlak bir şekilde yuvarlamayabilir.</span><span class="sxs-lookup"><span data-stu-id="3053b-127">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3053b-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3053b-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- `Microsoft.Owin.IOwinRequest.Cookies`
- `Microsoft.Owin.IOwinResponse.Cookies`

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
