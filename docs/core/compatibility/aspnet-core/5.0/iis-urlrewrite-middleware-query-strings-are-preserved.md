---
title: 'Son değişiklik: IIS: URL yeniden yazma ara yazılımı sorgu dizeleri korunur'
description: "IIS başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: Urlyeniden yazma ara yazılımı sorgu dizeleri korunur"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3439844f04c89059a027c1264401efc46cd0d57e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497676"
---
# <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a>IIS: UrlRewrite ara yazılım sorgu dizeleri korunur

Bir IIS Urlyeniden yazma ara yazılım hatası sorgu dizesinin yeniden yazma kurallarında korunması engelledi. Bu hata, IIS Urlyeniden yazma modülünün davranışıyla tutarlılığı sağlamak için düzeltildi.

Tartışma için bkz. sorun [DotNet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).

## <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 5,0 Preview 7

## <a name="old-behavior"></a>Eski davranış

Aşağıdaki yeniden yazma kuralını göz önünde bulundurun:

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

Önceki kural sorgu dizesini eklememez. Yerine öğesine yeniden yönlendirme gibi bir URI `/about?id=1` `/contact` `/contact?id=1` . `appendQueryString`Özniteliği `true` de varsayılan olarak olur.

## <a name="new-behavior"></a>Yeni davranış

Sorgu dizesi korunur. [Eski davranıştaki](#old-behavior) örnekteki URI, olur `/contact?id=1` .

## <a name="reason-for-change"></a>Değişiklik nedeni

Eski davranış IIS Urlyeniden yazma modülünün davranışıyla eşleşmedi. Ara yazılım ve modülle modül arasında taşıma desteği sağlamak için, amaç tutarlı davranışları korumaktır.

## <a name="recommended-action"></a>Önerilen eylem

Sorgu dizesini kaldırma davranışı tercih edilirse, `action` öğesini olarak ayarlayın `appendQueryString="false"` .

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
