---
title: 'Son değişiklik: Blazor: Blazor uygulamalarında yönlendirme mantığındaki değişiklikler'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: Blazor uygulamalarında yönlendirme mantığındaki değişiklikler"
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: cec05b26319fc8302261e41cc868dd73b46c8af0
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497833"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a>Blazor: Blazor uygulamalarında rota önceliği mantığı değişti

Blazor yönlendirme uygulamasındaki bir hata, yolların önceliğin nasıl belirlendiğine göre etkilendi. Bu hata, Blazor uygulamanızda isteğe bağlı parametrelerle tüm yolları veya yolları etkiler.

## <a name="version-introduced"></a>Sunulan sürüm

5.0.1

## <a name="old-behavior"></a>Eski davranış

Hatalı davranışla, daha düşük önceliğe sahip yollar, daha yüksek önceliğe sahip yollar üzerinden değerlendirilir ve eşleştirilir. Örneğin, yol daha `{*slug}` önce eşleştirilir `/customer/{id}` .

## <a name="new-behavior"></a>Yeni davranış

Geçerli davranış ASP.NET Core uygulamalarda tanımlanan yönlendirme davranışıyla daha yakından eşleşir. Framework, ilk olarak her bir segmentin yol önceliğini belirler. Yolun uzunluğu, yalnızca kesme özellikleri için ikinci bir ölçüt olarak kullanılır.

## <a name="reason-for-change"></a>Değişiklik nedeni

Özgün davranış uygulamadaki bir hata olarak kabul edilir. Hedef olarak, Blazor Apps 'teki yönlendirme sistemi, ASP.NET Core geri kalanında yönlendirme sistemiyle aynı şekilde davranmalıdır.

## <a name="recommended-action"></a>Önerilen eylem

Önceki Blazor sürümlerinden 5. x sürümüne yükseltiyorsanız, `PreferExactMatches` bileşendeki özniteliğini kullanın `Router` . Bu öznitelik doğru davranışı kabul etmek için kullanılabilir. Örnek:

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

`PreferExactMatches`Olarak ayarlandığında `true` , rota eşleştirme joker karakterlerle tam eşleşmeler tercih eder.

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
