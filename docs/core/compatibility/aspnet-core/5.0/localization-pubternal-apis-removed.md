---
title: "Son değişiklik: Pubternal API 'Ler kaldırıldı"
description: ASP.NET Core 5,0 ' deki, bazı pubternal yerelleştirme API 'Lerinin kaldırıldığı Son değişiklik hakkında bilgi edinin
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 35b6f80569945e54367117446ea96107d6c5199c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497677"
---
# <a name="localization-pubternal-apis-removed"></a>Yerelleştirme: "Pubternal" API 'Leri kaldırıldı

ASP.NET Core ortak API yüzeyini daha iyi korumak için bazı :::no-loc text="\"pubternal\""::: Yerelleştirme API 'leri kaldırılmıştır. Bir :::no-loc text="\"pubternal\""::: API 'nin `public` erişim değiştiricisi vardır ve bir [iç](../../../../csharp/language-reference/keywords/internal.md) amacı gösteren bir ad alanında tanımlanır.

Tartışma için bkz. [DotNet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 6

## <a name="old-behavior"></a>Eski davranış

Aşağıdaki API 'Ler `public` :

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri:
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a>Yeni davranış

Aşağıdaki listede değişiklikler özetlenmektedir:

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`Şimdi geldi `internal` .
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`Şimdi geldi `internal` .
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri artık şunlardır `internal` :
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a>Değişiklik nedeni

[ASPNET/Duyurular # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)'de daha kapsamlı bir şekilde açıklanmıştı, :::no-loc text="\"pubternal\""::: türler `public` API yüzeyinden kaldırılmıştır. Bu değişiklikler, bu tasarım kararına daha fazla sınıf uyarlar. Söz konusu sınıflar, takımın iç testi için uzantı noktaları olarak tasarlanmıştır.

## <a name="recommended-action"></a>Önerilen eylem

Büyük olasılıkla, bazı uygulamalar kasıtlı veya yanlışlıkla türlerine bağlı olabilir :::no-loc text="\"pubternal\""::: . Türlerin dışında nasıl geçiş yapılacağını öğrenmek için [Yeni davranış](#new-behavior) bölümlerine bakın.

Ortak API 'nin bu değişiklikten önce izin verilen ancak şimdi olmayan bir senaryo belirlediyseniz, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun oluştu.

## <a name="affected-apis"></a>Etkilenen API’ler

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
