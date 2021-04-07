---
title: 'Son değişiklik: statik dosyalar: CSV içerik türü, standartlara uyumlu olarak değiştirildi'
description: "Statik dosyaları başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: CSV içerik türü, standartlara uyumlu olarak değiştirildi"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3a7a1b2fc94f5cc956d85fc93ae72362e2e89b0e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497092"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Statik dosyalar: CSV içerik türü, standartlara uyumlu olarak değiştirildi

ASP.NET Core 5,0 ' de, `Content-Type` [statik dosya ara yazılım](/aspnet/core/fundamentals/static-files) 'nin *. csv* dosyaları için kullandığı varsayılan yanıt üst bilgisi değeri, standartlara uyumlu değere değiştirilmiştir `text/csv` .

Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 1

## <a name="old-behavior"></a>Eski davranış

`Content-Type`Üst bilgi değeri `application/octet-stream` kullanıldı.

## <a name="new-behavior"></a>Yeni davranış

`Content-Type`Üst bilgi değeri `text/csv` kullanılır.

## <a name="reason-for-change"></a>Değişiklik nedeni

[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standardına uyum.

## <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik uygulamanızı etkile etkileirse, dosya uzantısı-MIME tür eşlemesini özelleştirebilirsiniz. MIME türüne dönmek için `application/octet-stream` <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> içindeki yöntem çağrısını değiştirin `Startup.Configure` . Örnek:

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Eşlemeyi özelleştirme hakkında daha fazla bilgi için bkz. [Fileextensioncontenttypeprovider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
