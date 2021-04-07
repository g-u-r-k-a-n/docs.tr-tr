---
title: 'Son değişiklik: yerelleştirme: ResourceManagerWithCultureStringLocalizer Class ve WithCulture arabirim üyesi kaldırıldı'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: ResourceManagerWithCultureStringLocalizer Class ve WithCulture arabirim üyesi kaldırıldı"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 0c02a0e0cc78e4bfbf6f4a1ba5951cd13b56fe0c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498093"
---
# <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a>Yerelleştirme: ResourceManagerWithCultureStringLocalizer Class ve WithCulture arabirim üyesi kaldırıldı

.NET 5,0 Preview 1 ' de [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) Class ve [withculture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) yöntemi kaldırılmıştır.

Bağlam için bkz. [ASPNET/Duyurular # 346](https://github.com/aspnet/Announcements/issues/346) ve [DotNet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Bu değişiklik hakkında tartışma için bkz. [DotNet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 1

## <a name="old-behavior"></a>Eski davranış

`ResourceManagerWithCultureStringLocalizer`Sınıfı ve `ResourceManagerStringLocalizer.WithCulture` yöntemi [.NET Core 3,0 Preview 3 ve sonraki sürümlerde kullanılmıyor](../../3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).

## <a name="new-behavior"></a>Yeni davranış

`ResourceManagerWithCultureStringLocalizer`Sınıfı ve `ResourceManagerStringLocalizer.WithCulture` yöntemi .NET 5,0 Preview 1 ' de kaldırılmıştır. Yapılan değişikliklerin envanterini görmek için [DotNet/Extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files)konumundaki çekme isteğine bakın.

## <a name="reason-for-change"></a>Değişiklik nedeni

[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) sınıfı ve [Resourcemanagerstringlocalizer. withculture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) yöntemi genellikle yerelleştirme kullanıcıları için karışıklık kaynaklarıdır. Özel bir uygulama oluşturulurken karışıklık özellikle yüksek <xref:Microsoft.Extensions.Localization.IStringLocalizer> . Bu sınıf ve yöntem, tüketicilere bir `IStringLocalizer` Örneğin "dil başına, kaynak başına" olması beklenme izlenimi verir. Gerçekte, örnek yalnızca "kaynak başına" olmalıdır. Çalışma zamanında, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özelliği kullanılacak dili belirler.

## <a name="recommended-action"></a>Önerilen eylem

`ResourceManagerWithCultureStringLocalizer`Sınıfını ve yöntemini kullanmayı durdurun `ResourceManagerStringLocalizer.WithCulture` .

## <a name="affected-apis"></a>Etkilenen API’ler

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
