---
title: 'Son değişiklik: Razor : derleyici artık tek bir derleme oluşturuyor'
description: ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin ve Razor derleyicinin artık iki ayrı derleme oluşturmak için iki adımlı derleme işlemi kullanmaz.
no-loc:
- Razor
ms.date: 04/08/2021
ms.openlocfilehash: 8b6817563c4670aebfe681d5f24c8e309d2500ad
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299296"
---
# <a name="razor-compiler-no-longer-produces-a-views-assembly"></a>Razor: Derleyici artık bir görünümler derlemesi üretmez

RazorDerleyici artık bir uygulamada tanımlanan cshtml görünümlerini içeren ayrı bir *Views.dll* dosyası üretmez.

## <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 6,0 Preview 3

## <a name="old-behavior"></a>Eski davranış

Önceki sürümlerde Razor derleyici, iki dosya üreten iki adımlı bir derleme işlemi kullanır:

- Uygulama türlerini içeren bir ana *AppName.dll* derlemesi.
- Uygulamada tanımlanan oluşturulmuş görünümleri içeren bir *AppName.Views.dll* derlemesi. Oluşturulan görünüm türleri `public` ve `AspNetCore` ad alanı altında.

## <a name="new-behavior"></a>Yeni davranış

Hem görünümler hem de uygulama türleri tek bir *AppName.dll* derlemesine dahil edilmiştir. Görünüm türleri erişilebilirlik değiştiricilerine sahiptir `internal` ve `sealed` Varsayılan olarak `AspNetCoreGeneratedDocument` ad alanı altında bulunur.

## <a name="reason-for-change"></a>Değişiklik nedeni

İki adımlı derleme işlemini kaldırma:

* Görünümleri kullanan uygulamalar için derleme performansını geliştirir Razor .
* RazorGörünümlerin Visual Studio için "sık yükleme" deneyimine katılmasına izin verir.

## <a name="recommended-action"></a>Önerilen eylem

Yok.

## <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
