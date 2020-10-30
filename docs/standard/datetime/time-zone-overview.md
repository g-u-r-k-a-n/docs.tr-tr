---
title: Saat dilimine genel bakış
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET], about time zones
- transition time [.NET]
- TimeZoneInfo class, about TimeZoneInfo class
- time zones [.NET], creating
- invalid time [.NET]
- fixed rule [.NET]
- ambiguous time [.NET]
- floating rule [.NET]
- daylight saving time [.NET]
- adjustment rule [.NET]
- time zones [.NET], terminology
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
ms.openlocfilehash: 0f0fdbe4b63ddc9d55f7397fa71198d72e60e669
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064112"
---
# <a name="time-zone-overview"></a>Saat dilimine genel bakış

<xref:System.TimeZoneInfo>Sınıfı, saat dilimi kullanan uygulamaların oluşturulmasını basitleştirir. <xref:System.TimeZone>Sınıfı, yerel saat dilimi ve Eşgüdümlü Evrensel Saat (UTC) ile çalışmayı destekler. <xref:System.TimeZoneInfo>Sınıfı bu bölgelerin her ikisini de ve kayıt defterinde önceden tanımlanmış bilgilerin bulunduğu herhangi bir saat dilimini destekler. Ayrıca <xref:System.TimeZoneInfo> , sistemin hakkında bilgi içermeyen özel saat dilimlerini tanımlamak için öğesini kullanabilirsiniz.

## <a name="time-zone-essentials"></a>Saat dilimi temelleri

Saat dilimi, aynı saatin kullanıldığı coğrafi bir bölgedir. Genellikle, bitişik saat dilimleri her zaman bir saattir. Dünyanın saat dilimlerinde bulunan zaman, Eşgüdümlü Evrensel Saat (UTC) arasında bir fark olarak ifade edilebilir.

Dünyanın çoğu saat dilimi gün ışığından yararlanma süresini destekler. Gün ışığından yararlanma saati, bahar veya erken yaz 'daki bir saat boyunca ilerleyerek ve geç yaz veya Fall içindeki normal (veya standart) zamana geri dönerek yaz saati süresini en üst düzeye çıkarmaya çalışır. Standart zamandan gelen ve bu değişiklikler ayarlama kuralları olarak bilinir.

Belirli bir saat diliminde gün ışığından yararlanma saatine geçiş yaparak, sabit veya kayan bir ayarlama kuralıyla tanımlanabilir. Sabit ayarlama kuralı, her yıl gün ışığından yararlanma saatine geçiş veya sunucudan geçen belirli bir tarihi ayarlar. Örneğin, gün ışığından yararlanma saatinden her yıl 25 Ekim, bir sabit ayarlama kuralıyla oluşan standart saate geçiş yapılır. Çok daha yaygın olarak, belirli bir haftanın belirli bir gününü gün ışığından yararlanma saatine geçiş için belirli bir ayda belirleyen kayan ayar kuralları vardır. Örneğin, Mart ayının üçüncü Pazar günü gerçekleşen standart zamandan günışığından yararlanma saatine geçiş bir kayan ayarlama kuralına uyar.

Ayarlama kurallarını destekleyen saat dilimleri için, gün ışığından yararlanma saatine yapılan ve bu saate geçiş iki tür anormal kez oluşturulur: geçersiz süreler ve belirsiz zamanlar. Geçersiz bir saat, standart zamandan günışığından yararlanma saatine geçiş tarafından oluşturulan varolmayan bir süredir. Örneğin, bu geçiş belirli bir gün 2:00:00 ' da gerçekleşirse ve saat 3:00, her zaman aralığı 2:00 ile arasında değişir. ve 2:59:99  geçersizdir. Belirsiz bir saat, tek bir saat diliminde iki farklı kez eşlenemeyen bir süredir. Günışığından yararlanma saatinden standart saate geçiş tarafından oluşturulur. Örneğin, bu geçiş belirli bir gün 2:00:00 ' da gerçekleşirse ve saat 1:00, her zaman aralığı 1:00 ile arasında değişir. ve 1:59:99 , standart bir saat veya yaz saati olarak yorumlanamaz.

## <a name="time-zone-terminology"></a>Saat dilimi terminolojisi

Aşağıdaki tabloda, Saat dilimleriyle çalışırken ve saat dilimi kullanan uygulamalar geliştirilirken yaygın olarak kullanılan terimler tanımlanmaktadır.

| Terim            | Tanım |
| --------------- | ---------- |
| Ayarlama kuralı | Standart saatten gün ışığından yararlanma saatine ve gün ışığından yararlanma zamanından standart saate geçişin ne zaman gerçekleşeceğini tanımlayan bir kural. Her ayarlama kuralında, kuralın yerinde olduğu zaman tanımlayan bir başlangıç ve bitiş tarihi bulunur (örneğin, ayarlama kuralı 1 Ocak 1986 ' den 31 Aralık 2006 ' e, bir Delta (Standart saatin ayarlama kuralı uygulamasının bir sonucu olarak değiştiği süre) ve ayarlama dönemi boyunca geçişlerin gerçekleştiği belirli tarih ve saat hakkındaki bilgilere sahip olur. Geçişler, sabit bir kural ya da kayan bir kural izleyebilir. |
| Belirsiz saat  | Tek bir saat diliminde iki farklı kez eşlenebilir bir zaman. Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir. Örneğin, bu geçiş belirli bir gün 2:00:00 ' da gerçekleşirse ve saat 1:00, her zaman aralığı 1:00 ile arasında değişir. ve 1:59:99 , standart bir saat veya yaz saati olarak yorumlanamaz. |
| Sabit kural      | Gün ışığından yararlanma saatine geçiş için belirli bir tarihi ayarlayan bir ayarlama kuralı. Örneğin, gün ışığından yararlanma saatinden her yıl 25 Ekim, bir sabit ayarlama kuralıyla oluşan standart saate geçiş yapılır. |
| Kayan kural   | Belirli bir haftanın belirli bir gününü gün ışığından yararlanma saatine geçiş yapmak için belirli bir ay ayarlayan bir ayarlama kuralı. Örneğin, Mart ayının üçüncü Pazar günü gerçekleşen standart zamandan günışığından yararlanma saatine geçiş bir kayan ayarlama kuralına uyar. |
| Geçersiz zaman    | Standart zamandan gün ışığından yararlanma saatine geçişin yapıtı olan varolmayan bir zaman. Saat dilimi standart saatinden gün ışığından yararlanma saatine geçiş sırasında olduğu gibi saat içinde ileri doğru ayarlandığında meydana gelir. Örneğin, bu geçiş belirli bir gün 2:00:00 ' da gerçekleşirse ve saat 3:00, her zaman aralığı 2:00 ile arasında değişir. ve 2:59:99  geçersizdir. |
| Geçiş süresi | Belirli bir saat diliminde gün ışığından yararlanma saatinden standart saate veya bunun tersini değiştirme gibi belirli bir zaman değişikliği hakkında bilgiler. |

## <a name="time-zones-and-the-timezoneinfo-class"></a>Saat dilimleri ve TimeZoneInfo sınıfı

.NET sürümünde bir <xref:System.TimeZoneInfo> nesne bir saat dilimini temsil eder. <xref:System.TimeZoneInfo>Sınıfı, <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> nesne dizisi döndüren bir yöntemi içerir <xref:System.TimeZoneInfo.AdjustmentRule> . Bu dizinin her bir öğesi, belirli bir zaman aralığı için gün ışığından yararlanma saatine geçiş hakkında bilgi sağlar. (Yaz saati kaydetme süresini desteklemeyen saat dilimleri için, yöntem boş bir dizi döndürür.) Her <xref:System.TimeZoneInfo.AdjustmentRule> nesne bir <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> ve, <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> gün ışığından yararlanma saatine yapılan geçişin belirli tarih ve saatini tanımlayan bir özelliğine sahiptir. <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A>Özelliği, geçişin sabit veya kayan olduğunu gösterir.

.NET, Windows işletim sistemi tarafından sunulan ve kayıt defterinde depolanan saat dilimi bilgilerini kullanır. Dünya saat dilimlerinin sayısı nedeniyle, mevcut saat dilimlerinin hepsi kayıt defterinde gösterilmeyecektir. Ayrıca, kayıt defteri dinamik bir yapı olduğundan, önceden tanımlanmış saat dilimleri buna eklenebilir veya gruptan kaldırılabilir. Son olarak, kayıt defteri geçmiş saat dilimi verilerini içermez. Örneğin, Windows XP 'de kayıt defteri yalnızca tek bir saat dilimi ayarlamaları kümesiyle ilgili veriler içerir. Windows Vista dinamik saat dilimi verilerini destekler, bu da tek bir saat diliminin belirli yıl aralıklarında uygulanan birden çok ayarlama kuralına sahip olabileceği anlamına gelir. Ancak, Windows Vista kayıt defterinde tanımlanan ve gün ışığından yararlanma saatinin desteklediği çoğu bölge yalnızca bir veya iki öntanımlı ayarlama kuralına sahiptir.

<xref:System.TimeZoneInfo>Kayıt defterindeki sınıfının bağımlılığı, saat dilimi kullanan bir uygulamanın, kayıt defterinde belirli bir saat diliminin tanımlandığından emin olabileceği anlamına gelir. Sonuç olarak, belirli bir saat dilimini (yerel saat dilimi veya UTC 'yi temsil eden saat dilimi dışında) örneğini oluşturma girişimi özel durum işlemeyi kullanmalıdır. Ayrıca, gerekli bir <xref:System.TimeZoneInfo> nesne kayıt defterinden oluşturulamadıysanız uygulamanın devam etmesine izin vermek için bazı yöntemler sağlamalıdır.

Gerekli bir saat diliminin yokluğunu işlemek için, sınıfı, <xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> kayıt defterinde bulunmayan özel saat dilimlerini oluşturmak için kullanabileceğiniz bir yöntemini içerir. Özel saat dilimi oluşturma hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları Ile saat dilimleri oluşturma](create-time-zones-with-adjustment-rules.md). Ayrıca, <xref:System.TimeZoneInfo.ToSerializedString%2A> Yeni oluşturulan bir saat dilimini bir dizeye dönüştürmek ve bir veri deposuna (örneğin, bir veritabanı, bir metin dosyası, kayıt defteri veya uygulama kaynağı) kaydetmek için yöntemini kullanabilirsiniz. Daha sonra <xref:System.TimeZoneInfo.FromSerializedString%2A> Bu dizeyi bir nesneye geri dönüştürmek için yöntemini kullanabilirsiniz <xref:System.TimeZoneInfo> . Ayrıntılar için bkz. [nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme](save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: bir katıştırılmış kaynaktan saat dilimlerini geri yükleme](restore-time-zones-from-an-embedded-resource.md).

Her saat dilimi UTC 'den temel bir uzaklığa göre ve mevcut ayarlama kurallarını yansıtan UTC 'den bir uzaklığa göre, bir saat dilimindeki bir zaman, başka bir saat dilimindeki zamana kolayca dönüştürülebilir. Bu amaçla, <xref:System.TimeZoneInfo> nesnesi aşağıdakiler dahil olmak üzere çeşitli dönüştürme yöntemleri içerir:

- <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>, UTC 'yi belirlenen saat dilimindeki zamana dönüştürür.

- <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, belirlenen saat dilimindeki saati UTC 'ye dönüştürür.

- <xref:System.TimeZoneInfo.ConvertTime%2A>, belirli bir saat dilimindeki saati, başka bir belirlenen saat dilimindeki zamana dönüştürür.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, <xref:System.TimeZoneInfo> belirli bir saat dilimindeki saati başka bir belirlenen saat diliminde saate dönüştürmek için parametre olarak saat dilimi tanımlayıcıları (nesneler yerine) kullanır.

Saatleri saat dilimleri arasında dönüştürme hakkında daha fazla bilgi için bkz. [saat dilimleri arasında süreleri dönüştürme](converting-between-time-zones.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
