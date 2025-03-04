---
title: CLR ETW Olayları
description: 'Windows için ortak dil çalışma zamanı (CLR) olay izleme (ETW) olayları makalesine bakın. İki olay sağlayıcısı vardır: çalışma zamanı sağlayıcısı ve runaşağı sağlayıcı.'
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
ms.openlocfilehash: 8acc792b5217519e2a73c0cdf30c20161373c678
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283919"
---
# <a name="clr-etw-events"></a>CLR ETW Olayları

Bu bölümdeki konular, Windows için olay izleme (ETW) olaylarını anlatmaktadır. Her olayın ilişkili bir anahtar sözcüğü ve düzeyi vardır ve bu, [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md) konusunda açıklanmıştır. CLR, olaylar için iki sağlayıcıya sahiptir:  
  
- Hangi anahtar kelimelerle (olay kategorileri) etkin olarak olay başlatan çalışma zamanı sağlayıcısı. CLR çalışma zamanı sağlayıcısı GUID 'SI e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.  
  
- Özel amaçlı kullanımları olan özet sağlayıcısı. CLR özeti sağlayıcısı GUID 'SI A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Sağlayıcılar hakkında daha fazla bilgi için bkz. [CLR ETW sağlayıcıları](clr-etw-providers.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Çalışma Zamanı Bilgileri Olayları](runtime-information-etw-events.md)  
 Çalışma zamanı hakkında SKU, sürüm numarası, çalışma zamanının etkinleştirildiği yol, ile başlatıldığı komut satırı parametreleri, GUID (varsa) ve diğer ilgili bilgiler dahil olmak üzere çalışma zamanı hakkındaki bilgileri yakalar.  
  
 [Özel Durum Thrown_V1 Olayı](exception-thrown-v1-etw-event.md)  
 Oluşturulan özel durumlarla ilgili bilgileri yakalar.  
  
 [Çekişme Olayları](contention-etw-events.md)  
 İzleme kilitleri veya çalışma zamanının kullandığı yerel kilitler hakkında çekişme hakkında bilgi yakalar.  
  
 [İş Parçacığı Havuzu Olayları](thread-pool-etw-events.md)  
 Çalışan iş parçacığı havuzları ve g/ç iş parçacığı havuzları hakkında bilgi yakalar.  
  
 [Yükleyici Olayları](loader-etw-events.md)  
 Uygulama etki alanlarını, derlemeleri ve modülleri yükleme ve kaldırma hakkında bilgi yakalar.  
  
 [Yöntem Olayları](method-etw-events.md)  
 Sembol çözümleme için CLR yöntemleriyle ilgili bilgileri yakalar.  
  
 [Atık Toplama Olayları](garbage-collection-etw-events.md)  
 Tanılama ve hata ayıklama konusunda yardımcı olmak için çöp koleksiyonuyla ilgili bilgileri yakalar.  
  
 [Olayları Tam Zamanında İzleme](jit-tracing-etw-events.md)  
 Tam zamanında (JıT) giriş ve kuyruk çağrıları hakkındaki bilgileri yakalar.  
  
 [Birlikte Çalışma Olayları](interop-etw-events.md)  
 Microsoft ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.  
  
 [ARM Olayları](application-domain-resource-monitoring-arm-etw-events.md)  
 Bir uygulama etki alanının durumu hakkında ayrıntılı tanılama bilgilerini yakalar.  
  
 [Güvenlik Olayları](security-etw-events.md)  
 Tanımlayıcı ad ve Authenticode doğrulama hakkındaki bilgileri yakalar.  
  
 [Yığın Olayı](stack-etw-event.md)  
 Bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılan bilgileri yakalar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ETW Ile hata ayıklama ve performans ayarlamayı geliştirme](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [.NET Framework Günlük Kaydını Denetleme](controlling-logging.md)
- [CLR ETW Sağlayıcılar](clr-etw-providers.md)
- [CLR ETW Anahtar Sözcükleri ve Düzeyler](clr-etw-keywords-and-levels.md)
- [Ortak Dil Çalışma Zamanında ETW Olayları](etw-events-in-the-common-language-runtime.md)
