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
# <a name="razor-razorengine-apis-marked-obsolete"></a>Razor: Razor Motor API 'leri kullanılmıyor olarak işaretlendi

<xref:Microsoft.AspNetCore.Razor.Language.RazorEngine>Blazor içindeki türle ilgili türler eski olarak işaretlendi.

## <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 6,0 Preview 1

## <a name="old-behavior"></a>Eski davranış

`RazorEngine`API 'ler artık kullanılmıyor.

## <a name="new-behavior"></a>Yeni davranış

`RazorEngine`API 'ler artık kullanılmıyor.

## <a name="reason-for-change"></a>Değişiklik nedeni

Tür, `RazorEngine` türü yararına kullanım dışı bırakılmıştır <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .

## <a name="recommended-action"></a>Önerilen eylem

Kaynak kodunu türden türüne geçirin `RazorEngine` `RazorProjectEngine` .

## <a name="affected-apis"></a>Etkilenen API’ler

- `Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- [Microsoft. AspNetCore. Razor . Language. Extensions. FunctionsDirective. Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.functionsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft. AspNetCore. Razor . Language. Extensions. ınhersdirective. Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.inheritsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft. AspNetCore. Razor . Language. Extensions. SectionDirective. Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.sectiondirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft. AspNetCore. Razor . Language. I Razor enginebuilder](/dotnet/api/microsoft.aspnetcore.razor.language.irazorenginebuilder?view=aspnetcore-3.0&preserve-view=true)

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
