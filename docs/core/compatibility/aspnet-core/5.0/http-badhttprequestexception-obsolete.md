---
title: 'Son değişiklik: HTTP: Kestrel ve IIS BadHttpRequestException türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi'
description: "ASP.NET Core 5,0 ' de, HTTP: Kestrel ve IIS Rozhttprequestexception türlerini Kullanımdan kaldırılmış ve değiştirilmiş olarak işaretlenen Son değişiklik hakkında bilgi edinin"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5837018def634b732b4f273f1a794267f4d17972
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498145"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="99c53-103">HTTP: Kestrel ve IIS BadHttpRequestException türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="99c53-103">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="99c53-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` artık kullanılmıyor olarak işaretlendi ve öğesinden türetilme değiştirildi `Microsoft.AspNetCore.Http.BadHttpRequestException` .</span><span class="sxs-lookup"><span data-stu-id="99c53-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="99c53-105">Kestrel ve IIS sunucuları geriye dönük uyumluluk için eski özel durum türlerini hala oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99c53-105">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="99c53-106">Eski türler gelecek sürümde kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="99c53-106">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="99c53-107">Tartışma için bkz. [DotNet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).</span><span class="sxs-lookup"><span data-stu-id="99c53-107">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="99c53-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="99c53-108">Version introduced</span></span>

<span data-ttu-id="99c53-109">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="99c53-109">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="99c53-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="99c53-110">Old behavior</span></span>

<span data-ttu-id="99c53-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` öğesinden türetilir <xref:System.IO.IOException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="99c53-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="99c53-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="99c53-112">New behavior</span></span>

<span data-ttu-id="99c53-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="99c53-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="99c53-114">Türler Ayrıca öğesinden türetilir `Microsoft.AspNetCore.Http.BadHttpRequestException` `System.IO.IOException` .</span><span class="sxs-lookup"><span data-stu-id="99c53-114">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="99c53-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="99c53-115">Reason for change</span></span>

<span data-ttu-id="99c53-116">Değişikliğin yapıldığı yer:</span><span class="sxs-lookup"><span data-stu-id="99c53-116">The change was made to:</span></span>

* <span data-ttu-id="99c53-117">Yinelenen türleri birleştirin.</span><span class="sxs-lookup"><span data-stu-id="99c53-117">Consolidate duplicate types.</span></span>
* <span data-ttu-id="99c53-118">Sunucu uygulamalarında davranışı bütünleştirme.</span><span class="sxs-lookup"><span data-stu-id="99c53-118">Unify behavior across server implementations.</span></span>

<span data-ttu-id="99c53-119">Uygulama artık `Microsoft.AspNetCore.Http.BadHttpRequestException` Kestrel veya IIS kullanırken temel özel durumu yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="99c53-119">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="99c53-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="99c53-120">Recommended action</span></span>

<span data-ttu-id="99c53-121">Ve kullanımlarının `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` kullanımlarını `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` ile değiştirin `Microsoft.AspNetCore.Http.BadHttpRequestException` .</span><span class="sxs-lookup"><span data-stu-id="99c53-121">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="99c53-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="99c53-122">Affected APIs</span></span>

- [<span data-ttu-id="99c53-123">Microsoft. AspNetCore. Server. IIS. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="99c53-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="99c53-124">Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="99c53-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
