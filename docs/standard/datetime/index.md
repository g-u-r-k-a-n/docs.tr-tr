---
title: Tarihler, saatler ve saat dilimleri
ms.date: 04/10/2017
helpviewer_keywords:
- time zone objects [.NET]
- date and time data [.NET]
- time zones [.NET]
- times [.NET], time zones
- time [.NET], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
ms.openlocfilehash: b9dbbfa30c3398a984432fb0ecb8d0052c425f51
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817906"
---
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="00fd3-102">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="00fd3-102">Dates, times, and time zones</span></span>

<span data-ttu-id="00fd3-103"><xref:System.DateTime>.Net, temel yapıya ek olarak, Saat dilimleriyle çalışmayı destekleyen aşağıdaki sınıfları sağlar:</span><span class="sxs-lookup"><span data-stu-id="00fd3-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="00fd3-104">Sistemin yerel saat dilimi ve Eşgüdümlü Evrensel Saat (UTC) bölgesi ile çalışmak için bu sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="00fd3-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="00fd3-105"><xref:System.TimeZone>Sınıfın işlevselliği büyük ölçüde sınıfının yerini almıştır <xref:System.TimeZoneInfo> .</span><span class="sxs-lookup"><span data-stu-id="00fd3-105">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="00fd3-106">Bu sınıfı, bir sistemde önceden tanımlanmış tüm Saat dilimleriyle çalışmak, yeni saat dilimleri oluşturmak ve Tarih ve saatleri bir saat diliminden diğerine kolayca dönüştürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="00fd3-106">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="00fd3-107">Yeni geliştirme için <xref:System.TimeZoneInfo> sınıfı yerine sınıfını kullanın <xref:System.TimeZone> .</span><span class="sxs-lookup"><span data-stu-id="00fd3-107">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="00fd3-108">UTC 'den gelen fark (veya farkı) bilindiğinde tarih ve saatlerle çalışmak için bu yapıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="00fd3-108">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="00fd3-109"><xref:System.DateTimeOffset>Yapı, tarih ve saat DEĞERINI UTC 'den bu saatin bir değeriyle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="00fd3-109">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="00fd3-110">UTC ile ilişkisi nedeniyle, bağımsız bir tarih ve saat değeri kesin bir zamanda tek bir noktayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-110">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="00fd3-111">Bu, bir <xref:System.DateTimeOffset> değeri bir bilgisayardan diğerine daha taşınabilir hale getirir <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="00fd3-111">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="00fd3-112">Belgelerinin bu bölümü, Saat dilimleriyle çalışmanız ve Tarih ve saatleri bir saat diliminden diğerine dönüştürebileceğiniz saat dilimi kullanan uygulamalar oluşturmak için gereken bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-112">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="00fd3-113">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="00fd3-113">In this section</span></span>

<span data-ttu-id="00fd3-114">[Saat dilimine genel bakış](time-zone-overview.md) Saat dilimi kullanan uygulamalar oluşturma ile ilgili terminolojiyi, kavramları ve sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-114">[Time zone overview](time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="00fd3-115">[DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](choosing-between-datetime.md) <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.TimeZoneInfo> Tarih ve saat verileriyle çalışırken,, ve türlerinin ne zaman kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-115">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="00fd3-116">[Yerel bir sistemde tanımlanan saat dilimlerini bulma](finding-the-time-zones-on-local-system.md) Yerel bir sistemde bulunan saat dilimlerinin nasıl numaralandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-116">[Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="00fd3-117">[Nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](enumerate-time-zones.md) Bir bilgisayarın kayıt defterinde tanımlanan saat dilimlerinin numaralandırılacağı ve kullanıcıların bir listeden önceden tanımlanmış bir saat dilimi seçmesini sağlayan örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-117">[How to: Enumerate time zones present on a computer](enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="00fd3-118">[Nasıl yapılır: önceden TANıMLANMıŞ UTC ve yerel saat dilimi nesnelerine erişme](access-utc-and-local.md) Eşgüdümlü Evrensel Saat ve yerel saat dilimine nasıl erişebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-118">[How to: Access the predefined UTC and local time zone objects](access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="00fd3-119">[Nasıl yapılır: TimeZoneInfo nesnesinin örneğini oluşturma](instantiate-time-zone-info.md) <xref:System.TimeZoneInfo> Yerel sistem kayıt defterinden bir nesnenin örneğini oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-119">[How to: Instantiate a TimeZoneInfo object](instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="00fd3-120">[DateTimeOffset nesnesini örnekleme](instantiating-a-datetimeoffset-object.md) Bir <xref:System.DateTimeOffset> nesnenin örneklendiği ve bir <xref:System.DateTime> değerin bir değere dönüştürülebileceği yollar açıklanmaktadır <xref:System.DateTimeOffset> .</span><span class="sxs-lookup"><span data-stu-id="00fd3-120">[Instantiating a DateTimeOffset object](instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="00fd3-121">[Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](create-time-zones-without-adjustment-rules.md) Gün ışığından yararlanma saatine geçişi desteklemeyen bir özel saat dilimi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-121">[How to: Create time zones without adjustment rules](create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="00fd3-122">[Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](create-time-zones-with-adjustment-rules.md) Gün ışığından yararlanma saatine bir veya daha fazla geçişi destekleyen bir özel saat dilimi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-122">[How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="00fd3-123">[Saat dilimlerini kaydetme ve geri yükleme](saving-and-restoring-time-zones.md) <xref:System.TimeZoneInfo> Saat dilimi verilerinin serileştirilmesi ve serisini kaldırma desteğini açıklar ve bu özelliklerin kullanılabileceği bazı senaryoları gösterir.</span><span class="sxs-lookup"><span data-stu-id="00fd3-123">[Saving and restoring time zones](saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="00fd3-124">[Nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme](save-time-zones-to-an-embedded-resource.md) Özel saat dilimini oluşturmayı ve bu bilgilerin bir kaynak dosyasına nasıl kaydedileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-124">[How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="00fd3-125">[Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](restore-time-zones-from-an-embedded-resource.md) Katıştırılmış bir kaynak dosyasına kaydedilmiş özel saat dilimlerinin örneğini oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-125">[How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="00fd3-126">[Tarih ve saatlerle aritmetik Işlemler gerçekleştirme](performing-arithmetic-operations.md) Ekleme, çıkarma ve karşılaştırma ve değer ile ilgili sorunları ele <xref:System.DateTime> alır <xref:System.DateTimeOffset> .</span><span class="sxs-lookup"><span data-stu-id="00fd3-126">[Performing arithmetic operations with dates and times](performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="00fd3-127">[Nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma](use-time-zones-in-arithmetic.md) Saat diliminin ayarlama kurallarını yansıtan tarih ve saat aritmetiği yapmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-127">[How to: Use time zones in date and time arithmetic](use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="00fd3-128">[DateTime ve DateTimeOffset arasında dönüştürme](converting-between-datetime-and-offset.md) Ve değerlerini arasında dönüştürme işlemini <xref:System.DateTime> açıklar <xref:System.DateTimeOffset> .</span><span class="sxs-lookup"><span data-stu-id="00fd3-128">[Converting between DateTime and DateTimeOffset](converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="00fd3-129">[Saatleri saat dilimleri arasında dönüştürme](converting-between-time-zones.md) Saatlerin bir saat diliminden diğerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-129">[Converting times between time zones](converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="00fd3-130">[Nasıl yapılır: belirsiz zamanları çözme](resolve-ambiguous-times.md) Saat diliminin standart saatine eşleyerek belirsiz bir sürenin nasıl çözümleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-130">[How to: Resolve ambiguous times](resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="00fd3-131">[Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver](let-users-resolve-ambiguous-times.md) Kullanıcının belirsiz bir yerel saat ve eşgüdümlü evrensel saat arasındaki eşlemeyi belirlemesine nasıl izin verbileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="00fd3-131">[How to: Let users resolve ambiguous times](let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="00fd3-132">Başvuru</span><span class="sxs-lookup"><span data-stu-id="00fd3-132">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
