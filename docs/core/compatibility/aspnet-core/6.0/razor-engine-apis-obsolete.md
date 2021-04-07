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
# <a name="razor-razorengine-apis-marked-obsolete"></a>Razor: RazorEngine API 'Leri kullanılmıyor olarak işaretlendi

<xref:Microsoft.AspNetCore.Razor.Language.RazorEngine>Blazor içindeki türle ilgili türler eski olarak işaretlendi.

## <a name="version-introduced"></a>Sunulan sürüm

6,0 Preview 1

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
- [Microsoft. AspNetCore. Razor. Language. Extensions. FunctionsDirective. Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.functionsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft. AspNetCore. Razor. Language. Extensions. ınhersdirective. Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.inheritsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft. AspNetCore. Razor. Language. Extensions. SectionDirective. Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.sectiondirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft. AspNetCore. Razor. Language. IRazorEngineBuilder](/dotnet/api/microsoft.aspnetcore.razor.language.irazorenginebuilder?view=aspnetcore-3.0&preserve-view=true)

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
