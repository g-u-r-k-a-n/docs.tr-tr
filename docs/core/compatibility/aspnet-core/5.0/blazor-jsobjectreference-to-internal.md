---
title: 'Son değişiklik: Blazor: JSObjectReference ve JSInProcessObjectReference türleri internal olarak değiştirildi'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: JSObjectReference ve JSInProcessObjectReference türleri internal olarak değiştirildi"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 44e4c902ff22e18fa9ab8b484952082e5b81be94
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497859"
---
# <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="08f56-103">Blazor: JSObjectReference ve JSInProcessObjectReference türleri internal olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="08f56-103">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="08f56-104">`Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` ASP.NET Core 5,0 RC1 'de tanıtılan yeni ve türler olarak işaretlendi `internal` .</span><span class="sxs-lookup"><span data-stu-id="08f56-104">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="08f56-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="08f56-105">Version introduced</span></span>

<span data-ttu-id="08f56-106">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="08f56-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="08f56-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="08f56-107">Old behavior</span></span>

<span data-ttu-id="08f56-108">`JSObjectReference`, İle bir JavaScript birlikte çalışma çağrısından elde edilebilir `IJSRuntime` .</span><span class="sxs-lookup"><span data-stu-id="08f56-108">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="08f56-109">Örnek:</span><span class="sxs-lookup"><span data-stu-id="08f56-109">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

## <a name="new-behavior"></a><span data-ttu-id="08f56-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="08f56-110">New behavior</span></span>

<span data-ttu-id="08f56-111">`JSObjectReference`[iç](../../../../csharp/language-reference/keywords/internal.md) erişim değiştiricisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="08f56-111">`JSObjectReference` uses the [internal](../../../../csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="08f56-112">`public` `IJSObjectReference` Bunun yerine arabirimin kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08f56-112">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="08f56-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="08f56-113">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="08f56-114">`JSInProcessObjectReference` aynı zamanda olarak işaretlendi `internal` ve tarafından değiştirildi `IJSInProcessObjectReference` .</span><span class="sxs-lookup"><span data-stu-id="08f56-114">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="08f56-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="08f56-115">Reason for change</span></span>

<span data-ttu-id="08f56-116">Değişiklik, JavaScript birlikte çalışma özelliğini Blazor içindeki diğer desenlerle daha tutarlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="08f56-116">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="08f56-117">`IJSObjectReference` , `IJSRuntime` benzer bir amaca hizmet veren ve benzer yöntemlere ve uzantılara sahip olacak şekilde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="08f56-117">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="08f56-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="08f56-118">Recommended action</span></span>

<span data-ttu-id="08f56-119">Ve gibi oluşumlarını `JSObjectReference` `JSInProcessObjectReference` `IJSObjectReference` sırasıyla ve ile değiştirin `IJSInProcessObjectReference` .</span><span class="sxs-lookup"><span data-stu-id="08f56-119">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="08f56-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="08f56-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
