---
description: 'Daha fazla bilgi edinin: Time-Based önbellek Ilkeleri'
title: Saat Temelli Önbellek İlkeleri
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
ms.openlocfilehash: 42a76be0da664899295a583d72477de0698cc39e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712304"
---
# <a name="time-based-cache-policies"></a>Saat Temelli Önbellek İlkeleri

Zaman tabanlı önbellek ilkesi, kaynağın alındığı zamanı, kaynakla döndürülen üstbilgileri ve geçerli saati kullanarak önbelleğe alınmış girişlerin yeniliği tanımlar. Zaman tabanlı bir önbellek ilkesi ayarlarken, <xref:System.Net.Cache.HttpRequestCacheLevel.Default> zaman tabanlı ilkeyi kullanabilir veya özelleştirilmiş zaman tabanlı bir ilke oluşturabilirsiniz. Köprü Metni Aktarım Protokolü (HTTP) kullanılarak elde edilen kaynaklar için varsayılan zaman tabanlı ilkeyi kullanırken, tam önbellek davranışı, önbelleğe alınan yanıtta yer alan üst bilgiler ve [Internet Mühendisliği görev zorlaması (IETF)](https://www.ietf.org/) Web sitesinde bulunabilir 2616 ve 13. bölümde belirtilen davranışlar tarafından belirlenir. HTTP kaynakları için varsayılan zaman tabanlı ilkeyi ayarlamayı gösteren bir kod örneği için, bkz. [nasıl yapılır: bir uygulama Için varsayılan Time-Based önbellek Ilkesini ayarlama](how-to-set-the-default-time-based-cache-policy-for-an-application.md). Önbellek ilkeleri oluşturmayı ve kullanmayı gösteren kod örnekleri için bkz. [Ağ uygulamalarında önbelleğe alma yapılandırma](configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Önbelleğe alınmış girişlerin yeniliği belirleme ölçütleri  

 Zaman tabanlı bir önbellek ilkesini özelleştirmek için, aşağıdaki ölçütlerden birini veya daha fazlasını, önbelleğe alınmış girişlerin yeniliği belirlemek için kullanabilirsiniz:  
  
- Maksimum yaş  
  
- Maksimum Eskime durumu  
  
- En düşük yenilik  
  
- Önbellek eşitleme tarihi  
  
> [!NOTE]
> Varsayılan süre tabanlı önbellek ilkesinin kullanılması, uygulamanız için varsayılan önbellek ilkesi ayarlanarak karıştırılmamalıdır. Varsayılan zaman tabanlı ilke, istek veya uygulama düzeyinde kullanılabilen belirli bir ilkedir. Uygulamanız için varsayılan önbellek ilkesi, bir istekte hiçbir ilke ayarlanmamışsa geçerli olan bir ilkedir (konum tabanlı veya zaman tabanlı). Uygulamanız için varsayılan önbellek ilkesi ayarlama hakkında daha fazla bilgi için bkz <xref:System.Net.WebRequest.DefaultCachePolicy%2A> ..  
  
### <a name="maximum-age"></a>Maksimum yaş  

 Maksimum yaş ilkesi ölçütü, bir kaynağın önbelleğe alınmış kopyasının kullanılabileceği süreyi belirtir. Kaynağın önbelleğe alınmış kopyası belirtilen süreden daha eskiyse, kaynak sunucu üzerindeki içeriğe karşı denetlenerek yeniden doğrulanması gerekir. En fazla yaş kaynağın süresi dolduktan sonra kullanılmasına izin veracaksa, en yüksek bir stalet değeri de belirtilmediği takdirde bu ölçüt kabul edilmez.  
  
### <a name="maximum-staleness"></a>Maksimum Eskime durumu  

 En yüksek stalet ilkesi ölçütü, kaynağın önbelleğe alınmış kopyasının kullanılabileceği içerik süresi dolduktan sonraki sürenin uzunluğunu belirtir. Bu, kaynakların süre dolduktan sonra kullanılmasına izin veren tek önbellek ilkesi ölçütünüz.  
  
### <a name="minimum-freshness"></a>En düşük yenilik  

 Minimum yeniliği ilke ölçütü, kaynağın önbelleğe alınmış kopyasının kullanılabileceği içerik süresinin dolması için geçen sürenin uzunluğunu belirtir. Bu ilke, bir önbellek girişinin süre sonu tarihinden önce sona ermesine neden olan etkileri sağlar; Bu nedenle, en düşük yenilik ve en yüksek stalet ayarları birbirini dışlıyor.  
  
## <a name="cache-synchronization-date"></a>Önbellek eşitleme tarihi  

 Önbellek eşitleme tarihi ilke ölçütü, bir kaynağın önbelleğe alınmış kopyasının, sunucudaki içeriğe karşı denetlenerek yeniden doğrulanması gerektiğini belirler. İçerik, öğe önbelleğe alındıktan sonra değiştirildiyse, sunucudan alınır, önbellekte depolanır ve uygulamaya döndürülür. İçerik değiştirilmediyse, zaman damgası güncellenir ve uygulama önbelleğe alınmış içeriği alır.  
  
 Önbellek eşitleme tarihi, önbelleğe alınmış içeriklerin yeniden doğrulanması gerektiğinde mutlak bir tarih belirtmenize olanak tanır. Önbellek eşitleme tarihinden önce yeni bir önbellek girişinin yeniden doğrulanması durumunda sunucu ile yeniden doğrulama işlemi devam eder. Önbellek girişi önbellek eşitleme tarihinden sonra yeniden doğrulandıysa ve önbellekteki girişi geçersiz kılan ek bir yenilik veya sunucu yeniden doğrulama gereksinimi yoksa, önbellekten gelen giriş kullanılır. Önbellek eşitleme tarihi gelecek bir tarih olarak ayarlandıysa, önbellek eşitleme tarihi geçirilmeden, giriş her istendiğinde yeniden onaylanır.  
  
 Aşağıdaki konular, zaman tabanlı önbellek ilkesi ölçütlerini birleştirmenin etkileri hakkında bilgi sağlar:  
  
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
- [\<requestCaching> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
