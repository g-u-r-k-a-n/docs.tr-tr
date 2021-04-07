---
title: 'Son değişiklik: yetkilendirme: uç nokta yönlendirmede kaynak HttpContext'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: Endpoint Routing Resource, HttpContext"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 90f15bcbc1fb05e67b1c6d7494938eebac7718fd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497897"
---
# <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="22f11-103">Yetkilendirme: uç nokta yönlendirmesinde kaynak HttpContext 'dir</span><span class="sxs-lookup"><span data-stu-id="22f11-103">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="22f11-104">ASP.NET Core 3,1 ' de Endpoint Routing kullanılırken, yetkilendirme için kullanılan kaynak uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="22f11-104">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="22f11-105">Bu yaklaşım, yol verilerine () erişim kazanmak için yeterli değildi <xref:Microsoft.AspNetCore.Routing.RouteData> .</span><span class="sxs-lookup"><span data-stu-id="22f11-105">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="22f11-106">Daha önce MVC 'de, <xref:Microsoft.AspNetCore.Http.HttpContext> hem uç nokta () hem de yol verilerine erişim sağlayan bir kaynak geçirildi <xref:Microsoft.AspNetCore.Http.Endpoint> .</span><span class="sxs-lookup"><span data-stu-id="22f11-106">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="22f11-107">Bu değişiklik, yetkilendirmeye geçirilen kaynağın her zaman ' i olmasını sağlar `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="22f11-107">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="22f11-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="22f11-108">Version introduced</span></span>

<span data-ttu-id="22f11-109">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="22f11-109">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="22f11-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="22f11-110">Old behavior</span></span>

<span data-ttu-id="22f11-111">Endpoint Routing ve yetkilendirme ara yazılımı ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) veya [[Yetkilendir]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) öznitelikleri kullanılırken, yetkilendirme öğesine geçirilen kaynak eşleşen uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="22f11-111">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="22f11-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="22f11-112">New behavior</span></span>

<span data-ttu-id="22f11-113">Endpoint Routing, ' i `HttpContext` Yetkilendirmeyi geçirir.</span><span class="sxs-lookup"><span data-stu-id="22f11-113">Endpoint routing passes the `HttpContext` to authorization.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="22f11-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="22f11-114">Reason for change</span></span>

<span data-ttu-id="22f11-115">Uç noktasına öğesinden ulaşabilirsiniz `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="22f11-115">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="22f11-116">Ancak, uç noktadan yol verileri gibi şeylere kadar bir yöntem yoktu.</span><span class="sxs-lookup"><span data-stu-id="22f11-116">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="22f11-117">Uç nokta olmayan yönlendirmenin işlevselliğinde bir kayıp vardı.</span><span class="sxs-lookup"><span data-stu-id="22f11-117">There was a loss in functionality from non-endpoint routing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="22f11-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="22f11-118">Recommended action</span></span>

<span data-ttu-id="22f11-119">Uygulamanız uç nokta kaynağını kullanıyorsa, <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> `HttpContext` uç noktaya erişmeye devam etmek için üzerinde öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="22f11-119">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="22f11-120">ASP.NET Core 5,0 Preview 8 ve üzeri sürümlerde, ile eski davranışa dönüştürebilirsiniz <xref:System.AppContext.SetSwitch%2A> .</span><span class="sxs-lookup"><span data-stu-id="22f11-120">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="22f11-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="22f11-121">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

## <a name="affected-apis"></a><span data-ttu-id="22f11-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="22f11-122">Affected APIs</span></span>

<span data-ttu-id="22f11-123">Yok</span><span class="sxs-lookup"><span data-stu-id="22f11-123">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
