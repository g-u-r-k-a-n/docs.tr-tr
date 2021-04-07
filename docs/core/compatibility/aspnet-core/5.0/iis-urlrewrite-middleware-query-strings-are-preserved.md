---
title: 'Son değişiklik: IIS: URL yeniden yazma ara yazılımı sorgu dizeleri korunur'
description: "IIS başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: Urlyeniden yazma ara yazılımı sorgu dizeleri korunur"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3439844f04c89059a027c1264401efc46cd0d57e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497676"
---
# <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="4da68-103">IIS: UrlRewrite ara yazılım sorgu dizeleri korunur</span><span class="sxs-lookup"><span data-stu-id="4da68-103">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="4da68-104">Bir IIS Urlyeniden yazma ara yazılım hatası sorgu dizesinin yeniden yazma kurallarında korunması engelledi.</span><span class="sxs-lookup"><span data-stu-id="4da68-104">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="4da68-105">Bu hata, IIS Urlyeniden yazma modülünün davranışıyla tutarlılığı sağlamak için düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="4da68-105">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="4da68-106">Tartışma için bkz. sorun [DotNet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).</span><span class="sxs-lookup"><span data-stu-id="4da68-106">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4da68-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4da68-107">Version introduced</span></span>

<span data-ttu-id="4da68-108">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="4da68-108">ASP.NET Core 5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="4da68-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="4da68-109">Old behavior</span></span>

<span data-ttu-id="4da68-110">Aşağıdaki yeniden yazma kuralını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4da68-110">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="4da68-111">Önceki kural sorgu dizesini eklememez.</span><span class="sxs-lookup"><span data-stu-id="4da68-111">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="4da68-112">Yerine öğesine yeniden yönlendirme gibi bir URI `/about?id=1` `/contact` `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="4da68-112">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="4da68-113">`appendQueryString`Özniteliği `true` de varsayılan olarak olur.</span><span class="sxs-lookup"><span data-stu-id="4da68-113">The `appendQueryString` attribute defaults to `true` as well.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="4da68-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="4da68-114">New behavior</span></span>

<span data-ttu-id="4da68-115">Sorgu dizesi korunur.</span><span class="sxs-lookup"><span data-stu-id="4da68-115">The query string is preserved.</span></span> <span data-ttu-id="4da68-116">[Eski davranıştaki](#old-behavior) örnekteki URI, olur `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="4da68-116">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4da68-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="4da68-117">Reason for change</span></span>

<span data-ttu-id="4da68-118">Eski davranış IIS Urlyeniden yazma modülünün davranışıyla eşleşmedi.</span><span class="sxs-lookup"><span data-stu-id="4da68-118">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="4da68-119">Ara yazılım ve modülle modül arasında taşıma desteği sağlamak için, amaç tutarlı davranışları korumaktır.</span><span class="sxs-lookup"><span data-stu-id="4da68-119">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4da68-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4da68-120">Recommended action</span></span>

<span data-ttu-id="4da68-121">Sorgu dizesini kaldırma davranışı tercih edilirse, `action` öğesini olarak ayarlayın `appendQueryString="false"` .</span><span class="sxs-lookup"><span data-stu-id="4da68-121">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4da68-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4da68-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
