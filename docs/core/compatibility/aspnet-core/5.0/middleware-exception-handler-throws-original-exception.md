---
title: 'Son değişiklik: ara yazılım: özel durum Işleyici ara yazılımı, işleyici bulunmazsa özgün özel durum oluşturur'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: özel durum Işleyici ara yazılımı, işleyici bulunmazsa özgün özel durum oluşturur"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c28e09e544ac01c04a23fb7d2e73f3fdc242e9cd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497950"
---
# <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a>Ara yazılım: özel durum Işleyicisi ara yazılımı, işleyici bulunmazsa özgün özel durum oluşturur

5,0 ASP.NET Core önce, [özel durum Işleyici ara yazılımı](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) yapılandırılmış özel durum işleyicisini bir özel durum oluştuğunda yürütür. Aracılığıyla yapılandırılan özel durum işleyicisi bulunamazsa, <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> BIR HTTP 404 yanıtı üretilir. Yanıt şu şekilde yanıltıcıdır:

* Kullanıcı hatası gibi görünüyor.
* Sunucu üzerinde bir özel durumun gerçekleştiği gerçeğini gizler.

ASP.NET Core 5,0 ' deki yanıltıcı hatayı gidermek için, `ExceptionHandlerMiddleware` özel durum işleyicisi bulunamazsa özgün özel durumu oluşturur. Sonuç olarak, sunucu tarafından bir HTTP 500 yanıtı üretilir. Yanıt, oluşan hata ayıklanırken sunucu günlüklerinde İncelenme daha kolay olacaktır.

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 RC 1

## <a name="old-behavior"></a>Eski davranış

Yapılandırılmış özel durum işleyicisi bulunamazsa, özel durum Işleyicisi ara yazılımı bir HTTP 404 yanıtı üretir.

## <a name="new-behavior"></a>Yeni davranış

Özel durum Işleyici ara yazılımı, yapılandırılmış özel durum işleyicisi bulunamazsa özgün özel durumu oluşturur.

## <a name="reason-for-change"></a>Değişiklik nedeni

HTTP 404 hatası, sunucuda bir özel durumun gerçekleşmediğini açık hale getirir. Bu değişiklik şunları açık hale getirmek için bir HTTP 500 hatası üretir:

* Sorun bir kullanıcı hatasından kaynaklanmıyor.
* Sunucuda bir özel durumla karşılaşıldı.

## <a name="recommended-action"></a>Önerilen eylem

API değişikliği yok. Tüm mevcut uygulamalar derlenmeye ve çalıştırmaya devam edecektir. Oluşturulan özel durum sunucu tarafından işlenir. Örneğin, özel durum [Kestrel](/aspnet/core/fundamentals/servers/kestrel) veya [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys)tarafından http 500 hata yanıtına dönüştürülür.

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
