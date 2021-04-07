---
title: "Son değişiklik: Razor: RazorEngine API 'Leri kullanılmıyor olarak işaretlendi"
description: "ASP.NET Core 6,0 başlıklı Razor: RazorEngine API 'Lerini yok olarak işaretlenen Son değişiklik hakkında bilgi edinin"
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 08026cf32eec5ee391fab3d2ccdd9f22c4a3967b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497040"
---
# <a name="razor-razorengine-apis-marked-obsolete"></a><span data-ttu-id="379d2-103">Razor: RazorEngine API 'Leri kullanılmıyor olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="379d2-103">Razor: RazorEngine APIs marked obsolete</span></span>

<span data-ttu-id="379d2-104"><xref:Microsoft.AspNetCore.Razor.Language.RazorEngine>Blazor içindeki türle ilgili türler eski olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="379d2-104">Types related to the <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> type in Blazor have been marked as obsolete.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="379d2-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="379d2-105">Version introduced</span></span>

<span data-ttu-id="379d2-106">6,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="379d2-106">6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="379d2-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="379d2-107">Old behavior</span></span>

<span data-ttu-id="379d2-108">`RazorEngine`API 'ler artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="379d2-108">The `RazorEngine` APIs aren't obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="379d2-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="379d2-109">New behavior</span></span>

<span data-ttu-id="379d2-110">`RazorEngine`API 'ler artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="379d2-110">The `RazorEngine` APIs are obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="379d2-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="379d2-111">Reason for change</span></span>

<span data-ttu-id="379d2-112">Tür, `RazorEngine` türü yararına kullanım dışı bırakılmıştır <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .</span><span class="sxs-lookup"><span data-stu-id="379d2-112">The `RazorEngine` type has been deprecated in favor of the <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> type.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="379d2-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="379d2-113">Recommended action</span></span>

<span data-ttu-id="379d2-114">Kaynak kodunu türden türüne geçirin `RazorEngine` `RazorProjectEngine` .</span><span class="sxs-lookup"><span data-stu-id="379d2-114">Migrate source code from the `RazorEngine` type to the `RazorProjectEngine` type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="379d2-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="379d2-115">Affected APIs</span></span>

- `Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- [<span data-ttu-id="379d2-116">Microsoft. AspNetCore. Razor. Language. Extensions. FunctionsDirective. Register</span><span class="sxs-lookup"><span data-stu-id="379d2-116">Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.functionsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="379d2-117">Microsoft. AspNetCore. Razor. Language. Extensions. ınhersdirective. Register</span><span class="sxs-lookup"><span data-stu-id="379d2-117">Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.inheritsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="379d2-118">Microsoft. AspNetCore. Razor. Language. Extensions. SectionDirective. Register</span><span class="sxs-lookup"><span data-stu-id="379d2-118">Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.sectiondirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="379d2-119">Microsoft. AspNetCore. Razor. Language. IRazorEngineBuilder</span><span class="sxs-lookup"><span data-stu-id="379d2-119">Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.irazorenginebuilder?view=aspnetcore-3.0&preserve-view=true)

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
