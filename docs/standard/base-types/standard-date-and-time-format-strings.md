---
title: Standart tarih ve saat biçim dizeleri
description: .NET 'teki bir tarih ve saat değerinin metin temsilini tanımlamak için standart tarih ve saat biçimi dizesi kullanmayı öğrenin.
ms.date: 12/07/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET], dates
- custom DateTime format string
- format specifiers, custom date and time
- format strings
- custom date and time format strings
- formatting [.NET], time
- date and time strings
ms.topic: reference
ms.custom: contperfq2
ms.openlocfilehash: 688aaf7a1814e132f3bffa48394873653bf314e8
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851138"
---
# <a name="standard-date-and-time-format-strings"></a>Standart tarih ve saat biçim dizeleri

Standart Tarih ve saat biçimi dizesi, bir veya değerinin metin temsilini tanımlamak için Biçim belirleyicisi olarak tek bir karakter kullanır <xref:System.DateTime> <xref:System.DateTimeOffset> . Boşluk da dahil olmak üzere birden fazla karakter içeren herhangi bir tarih ve saat biçim dizesi, [özel bir tarih ve saat biçim dizesi](custom-date-and-time-format-strings.md)olarak yorumlanır. Standart veya özel bir biçim dizesi iki şekilde kullanılabilir:

- Bir biçimlendirme işleminin sonucunda ortaya çıkan dizeyi tanımlamak için.

- Bir tarih ve saat değerinin <xref:System.DateTime> ayrıştırma işlemi tarafından bir veya değere dönüştürülebileceği metin temsilini tanımlamak için <xref:System.DateTimeOffset> .

> [!TIP]
> Biçim dizelerini sayısal veya tarih ve saat değerlerine uygulamanızı ve sonuç dizeyi görüntülemenizi sağlayan bir .NET Windows Forms uygulaması olan **biçimlendirme yardımcı programını** indirebilirsiniz. Kaynak kodu [C#](/samples/dotnet/samples/windowsforms-formatting-utility-cs) ve [Visual Basic](/samples/dotnet/samples/windowsforms-formatting-utility-vb)için kullanılabilir.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

## <a name="table-of-format-specifiers"></a>Biçim belirticileri tablosu

<a name="table"></a> Aşağıdaki tabloda standart tarih ve saat biçimi belirticileri açıklanmaktadır. Aksi belirtilmedikçe, belirli bir standart tarih ve saat biçim belirticisi, bir veya değeriyle kullanılıp kullanılmadığına bakılmaksızın özdeş bir dize temsili üretir <xref:System.DateTime> <xref:System.DateTimeOffset> . Standart Tarih ve saat biçimi dizelerini kullanma hakkında daha fazla bilgi için bkz. [Denetim Masası ayarları](#control-panel-settings) ve [DateTimeFormatInfo özellikleri](#datetimeformatinfo-properties) .

|Biçim belirteci|Açıklama|Örnekler|
|----------------------|-----------------|--------------|
|"d"|Kısa Tarih Modeli<br /><br /> Daha fazla bilgi:[kısa tarih ("d") Biçim belirleyicisi](#ShortDate).|2009-06-15T13:45:30-> 6/15/2009 (en-US)<br /><br /> 2009-06-15T13:45:30-> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30-> 2009/06/15 (ja-JP)|
|"D"|Uzun tarih deseni.<br /><br /> Daha fazla bilgi:[uzun tarih ("D") Biçim belirleyicisi](#LongDate).|2009-06-15T13:45:30-> Pazartesi, 15 Haziran 2009 (en-US)<br /><br /> 2009-06-15T13:45:30-> 15 июня 2009 г. (ru-RU)<br /><br /> 2009-06-15T13:45:30-> Montag, 15. Juni 2009 (de-DE)|
|"f"|Tam tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [tam tarih kısa saat ("f") Biçim belirleyicisi](#FullDateShortTime).|2009-06-15T13:45:30-> Pazartesi, 15 Haziran 2009 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> den 15 junı 2009 13:45 (ZF-o)<br /><br /> 2009-06-15T13:45:30-> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|
|"F"|Tam tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [tam tarih uzun saat ("F") Biçim belirleyicisi](#FullDateLongTime).|2009-06-15T13:45:30-> Pazartesi, 15 Haziran 2009 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> den 15 junı 2009 13:45:30 (ZF-o)<br /><br /> 2009-06-15T13:45:30-> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|
|"g"|Genel tarih veya saat deseni (süre).<br /><br /> Daha fazla bilgi: [Genel Tarih kısa saat ("g") Biçim belirleyicisi](#GeneralDateShortTime).|2009-06-15T13:45:30-> 6/15/2009 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> 15/06/2009 13:45 (ES-ES)<br /><br /> 2009-06-15T13:45:30-> 2009/6/15 13:45 (zh-CN)|
|"G"|Genel tarih veya saat deseni (uzun süre).<br /><br /> Daha fazla bilgi: [Genel Tarih uzun saat ("G") Biçim belirleyicisi](#GeneralDateLongTime).|2009-06-15T13:45:30-> 6/15/2009 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> 15/06/2009 13:45:30 (ES-ES)<br /><br /> 2009-06-15T13:45:30-> 2009/6/15 13:45:30 (zh-CN)|
|"M", "m"|Ay/gün deseni.<br /><br /> Daha fazla bilgi: [ay ("ı", "d") Biçim belirleyicisi](#MonthDay).|2009-06-15T13:45:30-> 15 Haziran (en-US)<br /><br /> 2009-06-15T13:45:30-> 15. junı (da-DK)<br /><br /> 2009-06-15T13:45:30-> 15 Junı (kimlik KIMLIĞI)|
|"O", "o"|gidiş dönüş Tarih/saat biçimi.<br /><br /> Daha fazla bilgi: [gidiş dönüş ("o", "o") Biçim belirleyicisi](#Roundtrip).|<xref:System.DateTime> deðerler<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. Local)--> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. UTC)--> 2009-06-15T13:45:30.0000000 Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. Unspecified)--> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset> deðerler<br /><br /> 2009-06-15T13:45:30-07:00--> 2009-06-15T13:45:30.0000000-07:00|
|"R", "r"|Desen: RFC1123<br /><br /> Daha fazla bilgi: [RFC1123 ("r", "r") Biçim belirleyicisi](#RFC1123).|2009-06-15T13:45:30-> Mon, 15 Haz 2009 20:45:30 GMT|
|"s"|Sıralanabilir tarih veya saat deseni.<br /><br /> Daha fazla bilgi: [sıralanabilir ("s") Biçim belirleyicisi](#Sortable).|2009-06-15T13:45:30 (DateTimeKind. Local)-> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. UTC)-> 2009-06-15T13:45:30|
|"t"|Kısa bir süre deseni.<br /><br /> Daha fazla bilgi: [kısa saat ("t") Biçim belirleyicisi](#ShortTime).|2009-06-15T13:45:30-> 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> 13:45 (HR-HR)<br /><br /> 2009-06-15T13:45:30-> 01:45 م (ar-EG)|
|"T"|Uzun süre deseni.<br /><br /> Daha fazla bilgi: [uzun saat ("T") Biçim belirleyicisi](#LongTime).|2009-06-15T13:45:30-> 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> 13:45:30 (HR-HR)<br /><br /> 2009-06-15T13:45:30-> 01:45:30 م (ar-EG)|
|"u"|Evrensel sıralanabilir tarih/saat deseni.<br /><br /> Daha fazla bilgi: [evrensel sıralanabilir ("u") Biçim belirleyicisi](#UniversalSortable).|Değer ile <xref:System.DateTime> : 2009-06-15T13:45:30-> 2009-06-15 13:45:30Z<br /><br /> Değer ile <xref:System.DateTimeOffset> : 2009-06-15T13:45:30-> 2009-06-15 20:45:30Z|
|"U"|Evrensel tam tarih/saat deseni.<br /><br /> Daha fazla bilgi: [Evrensel tam ("U") Biçim belirleyicisi](#UniversalFull).|2009-06-15T13:45:30-> Pazartesi, 15 Haziran 2009 8:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30-> den 15 junı 2009 20:45:30 (ZF-o)<br /><br /> 2009-06-15T13:45:30-> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|
|"Y", "y"|Yıl ay deseni.<br /><br /> Daha fazla bilgi: [yıl ay ("Y") Biçim belirleyicisi](#YearMonth).|2009-06-15T13:45:30-> Haziran 2009 (en-US)<br /><br /> 2009-06-15T13:45:30-> junı 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30-> Junı 2009 (kimlik KIMLIĞI)|
|Başka bir tek karakter|Bilinmeyen tanımlayıcı.|Çalışma zamanı oluşturur <xref:System.FormatException> .|

## <a name="how-standard-format-strings-work"></a>Standart biçim dizeleri nasıl çalışır?

Bir biçimlendirme işleminde, standart biçim dizesi aslında bir özel biçim dizesi için diğer addır. Bir özel biçim dizesine başvururken diğer ad kullanmanın yararı, diğer ad değişmez iken özel biçim dizesinin kendisinin değişebilmesidir. Bu, tarih ve saat değerleri genellikle kültüre göre değiştiği için önemlidir. Örneğin, "d" standart biçim dizesi bir tarih ve saat değerinin kısa tarih deseni kullanılarak görüntüleneceğini belirtir. Sabit kültür için bu desen "MM/dd/yyyy" şeklindedir. fr-FR kültürü için "dd/MM/yyyy" şeklindedir. ja-JP kültürü için "yyyy/MM/dd" şeklindedir.

Eğer bir biçimlendirme işleminde standart format dizesi belirli bir kültürün özel biçim dizesiyle eşleniyorsa, uygulamanız özel biçim dizeleri aşağıdaki şekillerden birinde kullanılan belirli kültürü tanımlayabilir:

- Varsayılan (veya geçerli( kültürü kullanabilirsiniz. Aşağıdaki örnek geçerli kültürün kısa tarih biçimini kullanarak bir tarih görüntüler. Bu durumda geçerli kültür en-US değeridir.

  [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
  [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]

- Bir parametre içeren bir <xref:System.Globalization.CultureInfo> yöntemde biçimlendirme kullanılacak olan kültürü temsil eden bir nesneyi geçirebilirsiniz <xref:System.IFormatProvider> . Aşağıdaki örnek pt-BR kültürünün kısa tarih biçimini kullanarak bir tarih görüntüler.

  [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
  [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]

- Bir parametre içeren bir <xref:System.Globalization.DateTimeFormatInfo> yönteme biçimlendirme bilgileri sağlayan bir nesneyi geçirebilirsiniz <xref:System.IFormatProvider> . Aşağıdaki örnek, <xref:System.Globalization.DateTimeFormatInfo> hr-hr kültürü için bir nesnesinden kısa tarih biçimini kullanarak bir tarih görüntüler.

  [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
  [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]

> [!NOTE]
> Tarih ve saat değerlerinde kullanılan desenleri veya dizeleri özelleştirme hakkında bilgi için, bkz <xref:System.Globalization.NumberFormatInfo> . sınıf konusu.

Bazı durumlarda, standart biçim dizesi sabit olan daha uzun bir özel biçim dizesi için uygun bir kısaltma görevi görür. Dört standart biçim dizesi bu kategoriye girer: "O" (veya "o"), "R" (veya "r"), "s" ve "u". Bu dizeler sabit kültür tarafından tanımlanan özel biçim dizelerine karşılık gelir. Kültürler arası aynı olan tarih ve saat değerlerinin dize temsillerini oluştururlar. Aşağıdaki tablo bu dört standart tarih ve saat biçim dizesi hakkında bilgi verir.

|Standart biçim dizeleri|DateTimeFormatInfo.InvariantInfo özelliği tarafından tanımı|Özel biçim dizesi|
|----------------------------|----------------------------------------------------------|--------------------------|
|"O" veya "o"|Hiçbiri|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|
|"R" ya da "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|

Standart biçim dizeleri, <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> ya da <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> bir giriş dizesinin başarılı olması için belirli bir modele tam olarak uyması gereken ya da yöntemleriyle aynı zamanda işlem yapmak için kullanılabilir. Birçok standart biçim dizesi birden çok özel biçim dizesine eşlenir, yani bir tarih ve saat değeri çeşitli biçimlerde temsil edilebilir ve ayrıştırma işlemi yine de başarılı olur. Yöntemi çağırarak standart biçim dizesine karşılık gelen özel biçim dizesini veya dizeleri belirleyebilirsiniz <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> . Aşağıdaki örnek "d" (kısa tarih deseni) standart biçim dizesiyle eşlenen özel biçim dizelerini görüntüler.

[!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
[!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]

Aşağıdaki bölümlerde, ve değerleri için standart biçim belirticileri <xref:System.DateTime> açıklanır <xref:System.DateTimeOffset> .

## <a name="date-formats"></a>Tarih biçimleri

Bu grup aşağıdaki biçimleri içerir:

- [Kısa tarih ("d") Biçim belirleyicisi](#the-short-date-d-format-specifier)
- [Uzun Tarih ("D") Biçim belirleyicisi](#the-long-date-d-format-specifier)

<a name="ShortDate"></a>

### <a name="the-short-date-d-format-specifier"></a>Kısa tarih ("d") Biçim belirleyicisi

"D" standart biçim Belirleyicisi, belirli bir kültürün özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> . Örneğin, sabit kültürün özelliği tarafından döndürülen özel biçim dizesi <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> "aa/gg/yyyy" şeklindedir.

Aşağıdaki tablo <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyen nesne özelliklerini listeler.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Bir tarihin yıl, ay ve gün bileşenlerini ayıran dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "d" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
[!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]

[Tabloya dön](#table)

<a name="LongDate"></a>

### <a name="the-long-date-d-format-specifier"></a>Uzun Tarih ("D") Biçim belirleyicisi

"D" standart biçim belirticisi geçerli özellik tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> . Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy" değeridir.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirmesini denetleyen nesnenin özellikleri listelenmektedir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "D" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
[!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]

[Tabloya dön](#table)

## <a name="date-and-time-formats"></a>Tarih ve saat biçimleri

Bu grup aşağıdaki biçimleri içerir:

- [Tam Tarih kısa saat ("f") Biçim belirleyicisi](#the-full-date-short-time-f-format-specifier)
- [Tam tarih uzun saat ("F") Biçim belirleyicisi](#the-full-date-long-time-f-format-specifier)
- [Genel Tarih kısa saat ("g") Biçim belirleyicisi](#the-general-date-short-time-g-format-specifier)
- [Genel Tarih uzun saat ("G") Biçim belirleyicisi](#the-general-date-long-time-g-format-specifier)
- [Gidiş dönüş ("O", "o") Biçim belirleyicisi](#the-round-trip-o-o-format-specifier)
- [RFC1123 ("R", "r") Biçim belirleyicisi](#the-rfc1123-r-r-format-specifier)
- [Sıralanabilir ("s") Biçim belirleyicisi](#the-sortable-s-format-specifier)
- [Evrensel sıralanabilir ("u") Biçim belirleyicisi](#the-universal-sortable-u-format-specifier)
- [Evrensel tam ("U") Biçim belirleyicisi](#the-universal-full-u-format-specifier)

<a name="FullDateShortTime"></a>

### <a name="the-full-date-short-time-f-format-specifier"></a>Tam Tarih kısa saat ("f") Biçim belirleyicisi

"f" standart biçim tanımlayıcısı uzun tarih ("D") ve kısa saat ("t") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.

Sonuç dizesi, belirli bir nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> . Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyelebilecek nesne özellikleri listelenmektedir. <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType>Bazı kültürlerin ve özellikleri tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> tüm özellikleri kullanamaz.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Sonuç dizesinin tarih bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "f" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#3)]
[!code-vb[Formatting.DateAndTime.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#3)]

[Tabloya dön](#table)

<a name="FullDateLongTime"></a>

### <a name="the-full-date-long-time-f-format-specifier"></a>Tam tarih uzun saat ("F") Biçim belirleyicisi

"F" standart biçim Belirleyicisi, geçerli özellik tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> . Örneğin, sabit kültür için özel biçim dizesi "dddd, dd MMMM yyyy HH:mm:ss" değeridir.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyelebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin özelliği tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> tüm özellikleri kullanmayabilir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "F" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#4)]
[!code-vb[Formatting.DateAndTime.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#4)]

[Tabloya dön](#table)

<a name="GeneralDateShortTime"></a>

### <a name="the-general-date-short-time-g-format-specifier"></a>Genel Tarih kısa saat ("g") Biçim belirleyicisi

"g" standart biçim tanımlayıcısı kısa tarih ("d") ve kısa saat ("t") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.

Sonuç dizesi, belirli bir nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> . Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyelebilecek nesne özellikleri listelenmektedir. <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>Bazı kültürlerin ve özellikleri tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> tüm özellikleri kullanamaz.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Sonuç dizesinin tarih bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Bir tarihin yıl, ay ve gün bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "g" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#5)]
[!code-vb[Formatting.DateAndTime.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#5)]

[Tabloya dön](#table)

<a name="GeneralDateLongTime"></a>

### <a name="the-general-date-long-time-g-format-specifier"></a>Genel Tarih uzun saat ("G") Biçim belirleyicisi

"G" standart biçim tanımlayıcısı kısa tarih ("d") ve uzun saat ("T") desenlerinin bir boşlukla ayrılarak birleştirilmiş şeklini temsil eder.

Sonuç dizesi, belirli bir nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> . Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyelebilecek nesne özellikleri listelenmektedir. <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>Bazı kültürlerin ve özellikleri tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> tüm özellikleri kullanamaz.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Sonuç dizesinin tarih bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Bir tarihin yıl, ay ve gün bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "G" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#6)]
[!code-vb[Formatting.DateAndTime.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#6)]

[Tabloya dön](#table)

<a name="Roundtrip"></a>

### <a name="the-round-trip-o-o-format-specifier"></a>Gidiş dönüş ("O", "o") Biçim belirleyicisi

"O" veya "o" standart biçim Belirleyicisi, saat dilimi bilgilerini koruyan ve ISO 8601 ile uyumlu bir sonuç dizesi veren bir model kullanarak özel bir tarih ve saat biçim dizesini temsil eder. <xref:System.DateTime>Değerler için, bu Biçim belirleyicisi metin içindeki özelliği ile birlikte tarih ve saat değerlerini korumak için tasarlanmıştır <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> . <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Parametresi öğesine ayarlanmışsa, veya yöntemi kullanılarak biçimlendirilen dize geri ayrıştırılabilir `styles` <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> .

"O" veya "o" standart biçim Belirleyicisi, "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' öğesine karşılık gelir. Gönderildiğinde fffffffK biçiminde "değerler için özel biçim dizesi <xref:System.DateTime> ve" yyyy'-': '-Idd't'hh ': ' mm ': ' ss '. ' fffffffzzz "değerler için özel biçim dizesi <xref:System.DateTimeOffset> . Bu dizede; kısa çizgiler, iki nokta üst üste ve "T" harfi gibi tek karakterleri sınırlayan tek soru işareti çiftleri, tek karakterin değiştirilemeyen bir değişmez değer olduğunu belirtir. Kesme işaretleri çıktı dizesinde görünmez.

"O" veya "o" standart biçim Belirleyicisi (ve "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' Gönderildiğinde fffffffK biçiminde "özel biçim dizesi), ISO 8601 'nin değer özelliğini korumak için saat dilimi bilgilerini temsil eden üç yol avantajlarından yararlanır <xref:System.DateTime.Kind%2A> <xref:System.DateTime> :

- <xref:System.DateTimeKind.Local?displayProperty=nameWithType>Tarih ve saat değerlerinin saat dilimi BILEŞENI UTC 'den bir kaydırmadır (örneğin, + 01:00,-07:00). Tüm <xref:System.DateTimeOffset> değerler bu biçimde de temsil edilir.

- <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>Tarih ve saat değerlerinin saat dilimi BILEŞENI UTC 'yi göstermek için "Z" (sıfır sapmasını temsil eder) kullanır.

- <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> Tarih ve saat değerlerinde saat dilimi bilgisi yok.

"O" veya "o" standart biçim belirticisi uluslararası bir standarda uygun olduğundan, belirtici kullanan biçimlendirme veya ayrıştırma işlemi her zaman sabit kültür ve Gregoryen takvimi kullanır.

`Parse`Ve yöntemlerine geçirilen dizeler, `TryParse` `ParseExact` `TryParseExact` <xref:System.DateTime> <xref:System.DateTimeOffset> bu biçimlerden birinde yer alıyorsa "o" veya "o" biçim belirticisi kullanılarak ayrıştırılabilir. Nesneler söz konusu olduğunda <xref:System.DateTime> , çağırdığınız ayrıştırma aşırı yüklemesi de `styles` değeri olan bir parametre içermelidir <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> . "O" veya "o" biçim belirticisine karşılık gelen özel biçim dizesiyle bir ayrıştırma yöntemi çağırırsanız, "O" veya "o" ile aynı sonuçları almazsınız. Bunun nedeni, özel biçim dizesi kullanan ayrıştırma yöntemlerinin, saat dilimi bileşeni olmayan tarih ve saat değerlerinin dize temsilini ayrıştıramaması veya UTC 'yi göstermek için "Z" kullanmasına yol göstermektir.

Aşağıdaki örnek <xref:System.DateTime> <xref:System.DateTimeOffset> ABD Pasifik saati dilimindeki bir sistem üzerinde bir değer serisi ve bir değeri göstermek için "o" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
[!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]

Aşağıdaki örnek, biçimli bir dize oluşturmak için "o" biçim belirticisini kullanır ve sonra tarih ve saat yöntemini çağırarak özgün tarih ve saat değerini geri yükler `Parse` .

[!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
[!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]

[Tabloya dön](#table)

<a name="RFC1123"></a>

### <a name="the-rfc1123-r-r-format-specifier"></a>RFC1123 ("R", "r") Biçim belirleyicisi

"R" veya "r" standart biçim Belirleyicisi, özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> . Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.

Sonuç dizesi, <xref:System.Globalization.DateTimeFormatInfo> <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> sabit kültürü temsil eden özelliği tarafından döndürülen nesnenin aşağıdaki özelliklerinden etkilenir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Sonuç dizesinin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Sonuç dizesinde görünebilen kısaltılmış gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Sonuç dizesinde görünebilen kısaltılmış ay adlarını tanımlar.|

RFC 1123 standardı bir saati Eşgüdümlü Evrensel Saat (UTC) olarak ifade etse de biçimlendirme işlemi <xref:System.DateTime> biçimlendirilmekte olan nesnenin değerini değiştirmez. Bu nedenle, <xref:System.DateTime> <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> biçimlendirme işlemini gerçekleştirmeden önce yöntemini ÇAĞıRARAK değeri UTC 'ye dönüştürmeniz gerekir. Buna karşılık, <xref:System.DateTimeOffset> değerler bu dönüştürmeyi otomatik olarak gerçekleştirir; <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> biçimlendirme işleminden önce yöntemi çağırmaya gerek yoktur.

Aşağıdaki örnek <xref:System.DateTime> <xref:System.DateTimeOffset> ABD Pasifik saati dilimindeki bir sistemde ve bir değeri göstermek için "r" biçim tanımlayıcısını kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
[!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]

[Tabloya dön](#table)

<a name="Sortable"></a>

### <a name="the-sortable-s-format-specifier"></a>Sıralanabilir ("s") Biçim belirleyicisi

"S" standart biçim Belirleyicisi, özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> . Desen tanımlı bir standardı (ISO 8601) yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd'T'HH':'mm':'ss" değeridir.

"S" Biçim belirticisinin amacı, tarih ve saat değerlerine göre düzenli olarak artan veya azalan düzende sıralayan sonuç dizelerini üretmeniz sağlamaktır. Sonuç olarak, "s" Standart Biçim belirleyicisi bir tarih ve saat değerini tutarlı bir biçimde temsil etse de biçimlendirme işlemi, özelliğini veya değerini yansıtacak şekilde biçimlendirilmekte olan tarih ve saat nesnesinin değerini değiştirmez <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> . Örneğin, 2014-11-15T18:32:17 + 00:00 ve 2014-11-15T18:32:17 + 08:00 gibi tarih ve saat değerlerini biçimlendirirken oluşturulan sonuç dizeleri aynıdır.

Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.

Aşağıdaki örnek <xref:System.DateTime> <xref:System.DateTimeOffset> ABD Pasifik saati dilimindeki bir sistemde ve bir değeri göstermek için "s" biçim tanımlayıcısını kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
[!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]

[Tabloya dön](#table)

<a name="UniversalSortable"></a>

### <a name="the-universal-sortable-u-format-specifier"></a>Evrensel sıralanabilir ("u") Biçim belirleyicisi

"U" standart biçim Belirleyicisi, özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> . Desen tanımlı bir standardı yansıtır ve özellik salt okunurdur. Bu nedenle, kullanılan kültür veya sağlanan biçim sağlayıcısından bağımsız olarak her zaman aynıdır. Özel biçim dizesi "yyyy'-'MM'-'dd HH':'mm':'ss'Z'" değeridir. Bu standart biçim tanımlayıcısı kullanıldığında biçimlendirme ve ayrıştırma işlemi her zaman sabit kültürü kullanır.

Sonuç dizesi bir saati Eşgüdümlü Evrensel Saat (UTC) olarak ifade etmelidir, ancak <xref:System.DateTime> Biçimlendirme işlemi sırasında özgün değerin dönüştürülmesi yapılmaz. Bu nedenle, <xref:System.DateTime> yöntemi biçimlendirmeden önce çağırarak bir DEĞERI UTC 'ye dönüştürmeniz gerekir <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> .  Buna karşılık, <xref:System.DateTimeOffset> değerler bu dönüştürmeyi otomatik olarak gerçekleştirir; <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> biçimlendirme işleminden önce yöntemi çağırmaya gerek yoktur.

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "u" biçim tanımlayıcısını kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
[!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]

[Tabloya dön](#table)

<a name="UniversalFull"></a>

### <a name="the-universal-full-u-format-specifier"></a>Evrensel tam ("U") Biçim belirleyicisi

"U" standart biçim Belirleyicisi, belirtilen bir kültürün özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> . Desen "F" deseni ile aynıdır. Ancak, <xref:System.DateTime> değer biçimlendirilmeden önce UTC 'ye otomatik olarak dönüştürülür.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyelebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin özelliği tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> tüm özellikleri kullanmayabilir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş gün adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

"U" Biçim belirleyicisi tür tarafından desteklenmez <xref:System.DateTimeOffset> ve bir <xref:System.FormatException> değeri biçimlendirmek için kullanılmışsa bir oluşturur <xref:System.DateTimeOffset> .

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "U" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
[!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]

[Tabloya dön](#table)

## <a name="time-formats"></a>Zaman biçimleri

Bu grup aşağıdaki biçimleri içerir:

- [Kısa saat ("t") Biçim belirleyicisi](#the-short-time-t-format-specifier)
- [Uzun saat ("T") Biçim belirleyicisi](#the-long-time-t-format-specifier)

<a name="ShortTime"></a>

### <a name="the-short-time-t-format-specifier"></a>Kısa saat ("t") Biçim belirleyicisi

"T" standart biçim Belirleyicisi, geçerli özellik tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> . Örneğin, sabit kültür için özel biçim dizesi "HH:mm" değeridir.

Sonuç dizesi, belirli bir nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.DateTimeFormatInfo> . Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyelebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin özelliği tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> tüm özellikleri kullanmayabilir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "t" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
[!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]

[Tabloya dön](#table)

<a name="LongTime"></a>

### <a name="the-long-time-t-format-specifier"></a>Uzun saat ("T") Biçim belirleyicisi

"T" standart biçim Belirleyicisi, belirli bir kültürün özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> . Örneğin, sabit kültür için özel biçim dizesi "HH:mm:ss" değeridir.

Aşağıdaki tabloda <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyelebilecek nesne özellikleri listelenmektedir. Bazı kültürlerin özelliği tarafından döndürülen özel biçim belirticisi <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> tüm özellikleri kullanmayabilir.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Sonuç dizesinin saat bileşeninin biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Bir saatin saat, dakika ve saniye bileşenlerini ayıran dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|12 saatlik bir saatte gece yarısı ile öğleden önce arasındaki saatleri belirten dizeyi tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|12 saatlik bir saatte öğleden önce ile gece yarısı arasındaki saatleri belirten dizeyi tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "T" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
[!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]

[Tabloya dön](#table)

## <a name="partial-date-formats"></a>Kısmi tarih biçimleri

Bu grup aşağıdaki biçimleri içerir:

- [Ay ("ı", "d") Biçim belirleyicisi](#the-month-m-m-format-specifier)
- [Yıl ay ("Y", "y") Biçim belirleyicisi](#the-year-month-y-y-format-specifier)

<a name="MonthDay"></a>

### <a name="the-month-m-m-format-specifier"></a>Ay ("ı", "d") Biçim belirleyicisi

"D" veya "d" standart biçim belirticisi geçerli özellik tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> . Örneğin, sabit kültür için özel biçim dizesi "MMMM dd" değeridir.

Aşağıdaki tablo <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyen nesne özelliklerini listeler.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "m" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
[!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]

[Tabloya dön](#table)

<a name="YearMonth"></a>

### <a name="the-year-month-y-y-format-specifier"></a>Yıl ay ("Y", "y") Biçim belirleyicisi

"Y" veya "y" standart biçim Belirleyicisi, <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> belirtilen bir kültürün özelliği tarafından tanımlanan özel bir tarih ve saat biçim dizesini temsil eder. Örneğin, sabit kültür için özel biçim dizesi "yyyy MMMM" değeridir.

Aşağıdaki tablo <xref:System.Globalization.DateTimeFormatInfo> döndürülen dizenin biçimlendirilmesini denetleyen nesne özelliklerini listeler.

|Özellik|Açıklama|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Sonuç dizesinin genel biçimini tanımlar.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Sonuç dizesinde görünebilen yerelleştirilmiş ay adlarını tanımlar.|

Aşağıdaki örnek bir tarih ve saat değerini görüntülemek için "y" biçim tanımlayıcısını kullanır.

[!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
[!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]

[Tabloya dön](#table)

<a name="Notes"></a>

## <a name="control-panel-settings"></a>Denetim Masası Ayarları

Windows 'da, Denetim Masası 'ndaki **bölge ve dil seçenekleri** öğesindeki ayarlar, bir biçimlendirme işlemi tarafından üretilen sonuç dizesini etkiler. Bu ayarlar <xref:System.Globalization.DateTimeFormatInfo> , biçimlendirmeyi yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürüyle ilişkili nesneyi başlatmak için kullanılır. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.

Ayrıca, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> <xref:System.Globalization.CultureInfo> geçerli sistem kültürüyle aynı kültürü temsil eden yeni bir nesne oluşturmak için oluşturucuyu kullanırsanız, Denetim Masası 'ndaki **bölge ve dil seçenekleri** öğesi tarafından belirlenen tüm özelleştirmeler yeni <xref:System.Globalization.CultureInfo> nesneye uygulanır. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29>Oluşturucuyu, <xref:System.Globalization.CultureInfo> sistemin özelleştirmelerini yansıtmayan bir nesne oluşturmak için kullanabilirsiniz.

## <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo özellikleri

Biçimlendirme, geçerli <xref:System.Globalization.DateTimeFormatInfo> iş parçacığı kültürü tarafından örtük olarak veya <xref:System.IFormatProvider> Biçimlendirmeyi çağıran yöntemin parametresi tarafından açıkça sunulan geçerli nesnenin özelliklerinden etkilenir. Parametresi için <xref:System.IFormatProvider> , uygulamanız bir kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesne veya <xref:System.Globalization.DateTimeFormatInfo> belirli bir kültürün tarih ve saat biçimlendirme kurallarını temsil eden bir nesnesi belirtmelidir. Standart Tarih ve saat biçimi belirticileri çoğu, geçerli nesnenin özellikleri tarafından tanımlanan biçimlendirme desenleri için diğer adlardır <xref:System.Globalization.DateTimeFormatInfo> . Uygulamanız, ilgili özelliğin tarih ve saat biçimi düzenlerini değiştirerek bazı standart tarih ve saat biçimi belirticileri tarafından üretilen sonucu değiştirebilir <xref:System.Globalization.DateTimeFormatInfo> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- [Biçimlendirme Türleri](formatting-types.md)
- [Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (C#)](/samples/dotnet/samples/windowsforms-formatting-utility-cs)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (Visual Basic)](/samples/dotnet/samples/windowsforms-formatting-utility-vb)
