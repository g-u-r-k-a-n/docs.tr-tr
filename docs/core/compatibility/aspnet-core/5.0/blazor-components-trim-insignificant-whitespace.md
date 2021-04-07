---
title: 'Son değişiklik: Blazor: derleme sırasında bileşenlerden çok önemli olan boşluk'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: derleme zamanında bileşenden kırpılan önemli boşluk"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: d29171c43e587eba648de3f877e1cbb1c7156499
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498210"
---
# <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a>Blazor: derleme zamanında bileşenlerden çok önemli olan boşluk

ASP.NET Core 5,0 Preview 7 ' den başlayarak, Razor derleyicisi derleme zamanında Blazor Components (*. Razor* dosyaları) içinde önemli olmayan boşluğu atlar. Tartışma için bkz. sorun [DotNet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 7

## <a name="old-behavior"></a>Eski davranış

Blazor Server ve Blazor WebAssembly 'in 3. x sürümlerinde, bir bileşenin kaynak kodunda boşluk kabul edilir. Görsel efekt olmasa bile yalnızca boşluk metin düğümleri tarayıcının Belge Nesne Modeli (DOM) içinde işlenir.

Aşağıdaki Blazor bileşen kodunu göz önünde bulundurun:

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

Yukarıdaki örnek iki boşluk düğümü oluşturur:

* `@foreach`Kod bloğunun dışında.
* Öğesinin etrafında `<li>` .
* Çıktı etrafında `@item.Text` .

100 öğe içeren bir liste 402 boşluk düğümlerine neden olur. Diğer bir deyişle, bir boşluk düğümlerinin hiçbiri işlenmiş çıktıyı görsel olarak etkilemese de, işlenen tüm düğümlerin yarısı üzerinde.

Bileşenler için statik HTML işlenirken, bir etiket içindeki boşluk korunmaz. Örneğin, aşağıdaki bileşenin kaynağını görüntüleyin:

```razor
<foo        bar="baz"     />
```

Boşluk korunmaz. Önceden işlenmiş çıkış:

```razor
<foo bar="baz" />
```

## <a name="new-behavior"></a>Yeni davranış

`@preservewhitespace`Yönergesi değerle kullanılmadığı takdirde, şu `true` durumlarda boşluk düğümleri kaldırılır:

* Bir öğe içinde başında veya sonunda bulunur.
* Bir parametre içinde başında veya sonunda görüntülenir `RenderFragment` . Örneğin, alt içerik başka bir bileşene geçirilmekte.
* Ve gibi bir C# kod bloğunun önüne veya uygulayın `@if` `@foreach` .

## <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 5,0 ' deki Blazor için bir hedef, oluşturma ve dağıtma performansını artırmaktır. Kıyaslamalar halinde işleme süresinin yüzde 40 ' una kadar tüketilen çok önemli boşluk ağacı düğümleri.

## <a name="recommended-action"></a>Önerilen eylem

Çoğu durumda, işlenmiş bileşenin görsel düzeni etkilenmez. Ancak, boşluk kaldırma, gibi bir CSS kuralı kullanırken işlenen çıktıyı etkileyebilir `white-space: pre` . Bu performans iyileştirmesini devre dışı bırakmak ve boşluğu korumak için aşağıdaki eylemlerden birini gerçekleştirin:

* `@preservewhitespace true`Tercihi belirli bir bileşene uygulamak için *. Razor* dosyasının en üstündeki yönergeyi ekleyin.
* `@preservewhitespace true`Tercihi bir alt dizinin tamamına veya tüm projeye uygulamak için bir *_Imports. Razor* dosyası içinde yönergesini ekleyin.

Çoğu durumda, uygulamalar genellikle normal şekilde davranmaya devam edecek şekilde hiçbir eylem gerekmez (ancak daha hızlı). Ortaya çıkan boşluk belirli bir bileşen için herhangi bir soruna neden oluyorsa, `@preservewhitespace true` Bu iyileştirmeyi devre dışı bırakmak için o bileşende kullanın.

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
