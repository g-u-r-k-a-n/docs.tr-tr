---
title: "Son değişiklik: Razor : Razor motor API 'leri kullanılmıyor olarak işaretlendi"
description: "ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin Razor : Razor kullanım dışı olarak Işaretlenen motor API 'leri"
no-loc:
- Razor
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 75ccc8e2640dda29749de40946e90c2b897a7245
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292255"
---
# <a name="razor-razorengine-apis-marked-obsolete"></a><span data-ttu-id="c4636-103">Razor: Razor Motor API 'leri kullanılmıyor olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="c4636-103">Razor: RazorEngine APIs marked obsolete</span></span>

<span data-ttu-id="c4636-104"><xref:Microsoft.AspNetCore.Razor.Language.RazorEngine>Blazor içindeki türle ilgili türler eski olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="c4636-104">Types related to the <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> type in Blazor have been marked as obsolete.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c4636-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c4636-105">Version introduced</span></span>

<span data-ttu-id="c4636-106">ASP.NET Core 6,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="c4636-106">ASP.NET Core 6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="c4636-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c4636-107">Old behavior</span></span>

<span data-ttu-id="c4636-108">`RazorEngine`API 'ler artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c4636-108">The `RazorEngine` APIs aren't obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="c4636-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c4636-109">New behavior</span></span>

<span data-ttu-id="c4636-110">`RazorEngine`API 'ler artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c4636-110">The `RazorEngine` APIs are obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c4636-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c4636-111">Reason for change</span></span>

<span data-ttu-id="c4636-112">Tür, `RazorEngine` türü yararına kullanım dışı bırakılmıştır <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .</span><span class="sxs-lookup"><span data-stu-id="c4636-112">The `RazorEngine` type has been deprecated in favor of the <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> type.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c4636-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c4636-113">Recommended action</span></span>

<span data-ttu-id="c4636-114">Kaynak kodunu türden türüne geçirin `RazorEngine` `RazorProjectEngine` .</span><span class="sxs-lookup"><span data-stu-id="c4636-114">Migrate source code from the `RazorEngine` type to the `RazorProjectEngine` type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c4636-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c4636-115">Affected APIs</span></span>

- `Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- [<span data-ttu-id="c4636-116">Microsoft. AspNetCore. Razor . Language. Extensions. FunctionsDirective. Register</span><span class="sxs-lookup"><span data-stu-id="c4636-116">Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.functionsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="c4636-117">Microsoft. AspNetCore. Razor . Language. Extensions. ınhersdirective. Register</span><span class="sxs-lookup"><span data-stu-id="c4636-117">Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.inheritsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="c4636-118">Microsoft. AspNetCore. Razor . Language. Extensions. SectionDirective. Register</span><span class="sxs-lookup"><span data-stu-id="c4636-118">Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.sectiondirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="c4636-119">Microsoft. AspNetCore. Razor . Language. I Razor enginebuilder</span><span class="sxs-lookup"><span data-stu-id="c4636-119">Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.irazorenginebuilder?view=aspnetcore-3.0&preserve-view=true)

<!--

## Category

ASP.NET Core

## Affected APIs

- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register`
- `T:Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder`

-->
