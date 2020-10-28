---
title: Özel tarih ve saat biçim dizeleri
description: Tarih saat veya DateTimeOffset değerlerini metin temsillerine dönüştürmek veya tarih & süreleri için dizeleri ayrıştırmak üzere özel tarih ve saat biçimi dizelerini kullanmayı öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.topic: reference
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
ms.assetid: 98b374e3-0cc2-4c78-ab44-efb671d71984
ms.openlocfilehash: d58bcc4008c706395aaeee3b5dc9ea3fa96cce9b
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888717"
---
# <a name="custom-date-and-time-format-strings"></a>Özel tarih ve saat biçim dizeleri

Tarih ve saat biçimi dizesi, bir <xref:System.DateTime> <xref:System.DateTimeOffset> biçimlendirme işleminin sonucu olan bir veya değerinin metin temsilini tanımlar. Ayrıca, dizeyi tarih ve saate başarılı bir şekilde dönüştürmek için bir ayrıştırma işleminde gerekli olan tarih ve saat değerinin bildirimini tanımlayabilir. Özel biçim dizesi, bir veya daha fazla özel tarih ve saat biçimi belirleyicisinden oluşur. [Standart Tarih ve saat biçimi dizesi](standard-date-and-time-format-strings.md) olmayan herhangi bir dize, özel bir tarih ve saat biçim dizesi olarak yorumlanır.

> [!TIP]
> Sayısal veya tarih ve saat değerlerine biçim dizeleri uygulamanızı sağlayan ve sonuç dizesini görüntüleyen bir .NET Core Windows Forms uygulaması olan **biçimlendirme yardımcı programını** indirebilirsiniz. Kaynak kodu [C#](/samples/dotnet/samples/windowsforms-formatting-utility-cs) ve [Visual Basic](/samples/dotnet/samples/windowsforms-formatting-utility-vb)için kullanılabilir.

Özel tarih ve saat biçim dizeleri, ve değerleri ile birlikte <xref:System.DateTime> kullanılabilir <xref:System.DateTimeOffset> .

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a> Biçimlendirme işlemlerinde, özel tarih ve saat biçim dizeleri, `ToString` bir tarih ve saat örneği yöntemiyle ya da bileşik biçimlendirmeyi destekleyen bir yöntemle kullanılabilir. Aşağıdaki örnek her iki kullanımı da gösterir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
[!code-vb[Formatting.DateAndTime.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

Ayrıştırma işlemlerinde, özel tarih ve saat biçim dizeleri,,, <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> ve yöntemleriyle birlikte kullanılabilir <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> . Bu yöntemler, ayrıştırma işleminin başarılı olması için bir giriş dizesinin tam olarak belirli bir düzene uymasını gerektirir. Aşağıdaki örnek, <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> bir gün, ay ve iki basamaklı bir yıl içermesi gereken bir tarihi ayrıştırmak için yöntemine yapılan çağrıyı gösterir.

[!code-csharp[Formatting.DateAndTime.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
[!code-vb[Formatting.DateAndTime.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

Aşağıdaki tabloda özel tarih ve saat biçimi belirteçleri açıklanır ve her biçim belirticisi tarafından üretilen bir sonuç dizesini görüntülenir. Varsayılan olarak, sonuç dizeleri en-US kültürünün, biçimlendirme kurallarını yansıtır. Belirli bir biçim belirticisi yerelleştirilmiş bir sonuç dizesi üretirse örnek aynı zamanda sonuç dizesinin uygulanacağı kültürü de not alır. Özel tarih ve saat biçimi dizelerini kullanma hakkında daha fazla bilgi için [Notlar](#notes) bölümüne bakın.

| Biçim belirteci | Açıklama | Örnekler |
|--|--|--|
| "d" | 1 İle 31 arasında ayın günü.<br /><br /> Daha fazla bilgi: ["d" Özel Biçim belirleyicisi](#dSpecifier). | 2009-06-01T13:45:30-> 1<br /><br /> 2009-06-15T13:45:30-> 15 |
| "dd" | 01 İle 31 arasında ayın günü.<br /><br /> Daha fazla bilgi: ["gg" Özel Biçim belirleyicisi](#ddSpecifier). | 2009-06-01T13:45:30-> 01<br /><br /> 2009-06-15T13:45:30-> 15 |
| "ddd" | Haftanın günü, kısaltılmış adı.<br /><br /> Daha fazla bilgi: ["ddd" Özel Biçim belirleyicisi](#dddSpecifier). | 2009-06-15T13:45:30-> Mon (en-US)<br /><br /> 2009-06-15T13:45:30-> пн (ru-RU)<br /><br /> 2009-06-15T13:45:30-> LUN. (fr-FR) |
| "dddd" | Haftanın gününün tam adı.<br /><br /> Daha fazla bilgi: ["dddd" Özel Biçim belirleyicisi](#ddddSpecifier). | 2009-06-15T13:45:30-> Pazartesi (en-US)<br /><br /> 2009-06-15T13:45:30-> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30-> Lundi (fr-FR) |
| "f" | Saniyenin onda biri bir tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["f" Özel Biçim belirleyicisi](#fSpecifier). | 2009-06-15T13:45:30.6170000-> 6<br /><br /> 2009-06-15T13:45:30.05-> 0 |
| "ff" | Tarih ve saat değerindeki saniyenin yüzde biri.<br /><br /> Daha fazla bilgi: ["FF" Özel Biçim belirleyicisi](#ffSpecifier). | 2009-06-15T13:45:30.6170000-> 61<br /><br /> 2009-06-15T13:45:30.0050000-> 00 |
| "fff" | Tarih ve saat değerindeki milisaniye.<br /><br /> Daha fazla bilgi: ["fff" Özel Biçim belirleyicisi](#fffSpecifier). | 6/15/2009 13:45:30.617-> 617<br /><br /> 6/15/2009 13:45:30.0005 > 000 |
| "ffff" | Saniyenin on binde birindeki tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["ffff" Özel Biçim belirleyicisi](#ffffSpecifier). | 2009-06-15T13:45:30.6175000-> 6175<br /><br /> 2009-06-15T13:45:30.0000500-> 0000 |
| "fffff" | Tarih ve saat değerindeki saniyenin yüz binde biri.<br /><br /> Daha fazla bilgi: ["fffff" Özel Biçim belirleyicisi](#fffffSpecifier). | 2009-06-15T13:45:30.6175400-> 61754<br /><br /> 6/15/2009 13:45:30.000005-> 00000 |
| "ffffff" | Tarih ve saat değerindeki saniyenin milyonda biri.<br /><br /> Daha fazla bilgi: ["FFFFFF" Özel Biçim belirleyicisi](#ffffffSpecifier). | 2009-06-15T13:45:30.6175420-> 617542<br /><br /> 2009-06-15T13:45:30.0000005-> 000000 YAZıN |
| "fffffff" | Saniyenin on milyonda birindeki tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["fffffff" Özel Biçim belirleyicisi](#fffffffSpecifier). | 2009-06-15T13:45:30.6175425-> 6175425<br /><br /> 2009-06-15T13:45:30.0001150-> 0001150 |
| "F" | Sıfır olmayan, saniyenin onda biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["F" Özel Biçim belirleyicisi](#F_Specifier). | 2009-06-15T13:45:30.6170000-> 6<br /><br /> 2009-06-15T13:45:30.0500000-> (çıktı yok) |
| "FF" | Sıfır olmayan, saniyenin yüzde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FF" Özel Biçim belirleyicisi](#FF_Specifier). | 2009-06-15T13:45:30.6170000-> 61<br /><br /> 2009-06-15T13:45:30.0050000-> (çıktı yok) |
| "FFF" | Sıfır olmayan, milisaniye cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFF" Özel Biçim belirleyicisi](#FFF_Specifier). | 2009-06-15T13:45:30.6170000-> 617<br /><br /> 2009-06-15T13:45:30.0005000-> (çıktı yok) |
| "FFFF" | Sıfır olmayan, saniyenin on binde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["ffff" Özel Biçim belirleyicisi](#FFFF_Specifier). | 2009-06-15T13:45:30.5275000-> 5275<br /><br /> 2009-06-15T13:45:30.0000500-> (çıktı yok) |
| "FFFFF" | Sıfır olmayan, saniyenin yüz binde biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFF" Özel Biçim belirleyicisi](#FFFFF_Specifier). | 2009-06-15T13:45:30.6175400-> 61754<br /><br /> 2009-06-15T13:45:30.0000050-> (çıktı yok) |
| "FFFFFF" | Sıfır olmayan, saniyenin milyonda birinde cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["FFFFFF" Özel Biçim belirleyicisi](#FFFFFF_Specifier). | 2009-06-15T13:45:30.6175420-> 617542<br /><br /> 2009-06-15T13:45:30.0000005-> (çıktı yok) |
| "FFFFFFF" | Sıfır olmayan, saniyenin on milyonda biri cinsinden tarih ve saat değeri.<br /><br /> Daha fazla bilgi: ["fffffff" Özel Biçim belirleyicisi](#FFFFFFF_Specifier). | 2009-06-15T13:45:30.6175425-> 6175425<br /><br /> 2009-06-15T13:45:30.0001150-> 000115 |
| "g", "gg" | Süre veya dönem.<br /><br /> Daha fazla bilgi: ["g" veya "gg" Özel Biçim belirleyicisi](#gSpecifier). | 2009-06-15T13:45:30.6170000-> M.S. |
| "h" | Saat, 12 saatlik biçimde, 1 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["h" Özel Biçim belirleyicisi](#hSpecifier). | 2009-06-15T01:45:30-> 1<br /><br /> 2009-06-15T13:45:30-> 1 |
| "hh" | Saat, 12 saatlik biçimde, 01 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["hh" Özel Biçim belirleyicisi](#hhSpecifier). | 2009-06-15T01:45:30-> 01<br /><br /> 2009-06-15T13:45:30-> 01 |
| "H" | 24 saat, 0 ile 23 arasında bir saat kullanıyor.<br /><br /> Daha fazla bilgi: ["H" Özel Biçim belirleyicisi](#H_Specifier). | 2009-06-15T01:45:30-> 1<br /><br /> 2009-06-15T13:45:30-> 13 |
| "HH" | Saat, 24 saatlik biçimde, 00 ile 23 arasında.<br /><br /> Daha fazla bilgi: ["hh" Özel Biçim belirleyicisi](#HH_Specifier). | 2009-06-15T01:45:30-> 01<br /><br /> 2009-06-15T13:45:30-> 13 |
| "K" | Saat dilimi bilgileri.<br /><br /> Daha fazla bilgi: ["K" Özel Biçim belirleyicisi](#KSpecifier). | Şu <xref:System.DateTime> değerlerle:<br /><br /> 2009-06-15T13:45:30, tür belirtilmemiş-><br /><br /> 2009-06-15T13:45:30, tür UTC-> Z<br /><br /> 2009-06-15T13:45:30, tür yerel->-07:00 (yerel bilgisayar ayarlarına bağlıdır)<br /><br /> Şu <xref:System.DateTimeOffset> değerlerle:<br /><br /> 2009-06-15T01:45:30-07:00-->-07:00<br /><br /> 2009-06-15T08:45:30 + 00:00--> + 00:00 |
| "m" | Dakika, 0 ile 59 arasında.<br /><br /> Daha fazla bilgi: ["d" Özel Biçim belirleyicisi](#mSpecifier). | 2009-06-15T01:09:30-> 9<br /><br /> 2009-06-15T13:29:30-> 29 |
| "mm" | Dakika, 00 ile 59 arasında.<br /><br /> Daha fazla bilgi: ["mm" Özel Biçim belirleyicisi](#mmSpecifier). | 2009-06-15T01:09:30-> 09<br /><br /> 2009-06-15T01:45:30-> 45 |
| "M" | Ay, 1 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["d" Özel Biçim belirleyicisi](#M_Specifier). | 2009-06-15T13:45:30-> 6 |
| "AA" | Ay, 01 ile 12 arasında.<br /><br /> Daha fazla bilgi: ["mm" Özel Biçim belirleyicisi](#MM_Specifier). | 2009-06-15T13:45:30-> 06 |
| "AAA" | Ayın kısaltılmış adı.<br /><br /> Daha fazla bilgi: ["mmm" Özel Biçim belirleyicisi](#MMM_Specifier). | 2009-06-15T13:45:30-> Haz (en-US)<br /><br /> 2009-06-15T13:45:30-> JUIN (fr-FR)<br /><br /> 2009-06-15T13:45:30-> Haz (zu-ZA) |
| "AAAA" | Ayın tam adı.<br /><br /> Daha fazla bilgi: ["mmmm" Özel Biçim belirleyicisi](#MMMM_Specifier). | 2009-06-15T13:45:30-> Haziran (en-US)<br /><br /> 2009-06-15T13:45:30-> junı (da-DK)<br /><br /> 2009-06-15T13:45:30-> Ujunı (zu-ZA) |
| "s" | Saniye, 0'dan 59'a kadardır.<br /><br /> Daha fazla bilgi: ["s" Özel Biçim belirleyicisi](#sSpecifier). | 2009-06-15T13:45:09-> 9 |
| "ss" | Saniye, 00'dan 59'a kadardır.<br /><br /> Daha fazla bilgi: ["ss" Özel Biçim belirleyicisi](#ssSpecifier). | 2009-06-15T13:45:09-> 09 |
| "t" | AM/PM göstergesinin ilk karakteri.<br /><br /> Daha fazla bilgi: ["t" Özel Biçim belirleyicisi](#tSpecifier). | 2009-06-15T13:45:30-> P (en-US)<br /><br /> 2009-06-15T13:45:30-> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30-> (fr-FR) |
| "tt" | AM/PM göstergesi.<br /><br /> Daha fazla bilgi: ["tt" Özel Biçim belirleyicisi](#ttSpecifier). | 2009-06-15T13:45:30-> PM (en-US)<br /><br /> 2009-06-15T13:45:30-> 午後 (ja-JP)<br /><br /> 2009-06-15T13:45:30-> (fr-FR) |
| "y" | 0 dan 99 'a kadar yıl.<br /><br /> Daha fazla bilgi: ["y" Özel Biçim belirleyicisi](#ySpecifier). | 0001-01-01T00:00:00-> 1<br /><br /> 0900-01-01T00:00:00-> 0<br /><br /> 1900-01-01T00:00:00-> 0<br /><br /> 2009-06-15T13:45:30-> 9<br /><br /> 2019-06-15T13:45:30-> 19 |
| "yy" | 00 dan 99 'a kadar yıl.<br /><br /> Daha fazla bilgi: ["yy" Özel Biçim belirleyicisi](#yySpecifier). | 0001-01-01T00:00:00-> 01<br /><br /> 0900-01-01T00:00:00-> 00<br /><br /> 1900-01-01T00:00:00-> 00<br /><br /> 2019-06-15T13:45:30-> 19 |
| "yyy" | En az üç basamaklı olarak yıl.<br /><br /> Daha fazla bilgi: ["yyy" Özel Biçim belirleyicisi](#yyySpecifier). | 0001-01-01T00:00:00-> 001<br /><br /> 0900-01-01T00:00:00-> 900<br /><br /> 1900-01-01T00:00:00-> 1900<br /><br /> 2009-06-15T13:45:30-> 2009 |
| "yyyy" | Dört basamaklı bir sayı olarak yıl.<br /><br /> Daha fazla bilgi: ["yyyy" Özel Biçim belirleyicisi](#yyyySpecifier). | 0001-01-01T00:00:00-> 0001<br /><br /> 0900-01-01T00:00:00-> 0900<br /><br /> 1900-01-01T00:00:00-> 1900<br /><br /> 2009-06-15T13:45:30-> 2009 |
| "yyyyy" | Beş basamaklı bir sayı olarak yıl.<br /><br /> Daha fazla bilgi: ["yyyyy" Özel Biçim belirleyicisi](#yyyyySpecifier). | 0001-01-01T00:00:00-> 00001<br /><br /> 2009-06-15T13:45:30-> 02009 |
| "z" | Önünde sıfır olmadan UTC biçiminden saat uzaklığı.<br /><br /> Daha fazla bilgi: ["z" Özel Biçim belirleyicisi](#zSpecifier). | 2009-06-15T13:45:30-07:00->-7 |
| "zz" | Önünde sıfır bulunan tek basamaklı değerden oluşan UTC biçiminden saat uzaklığı.<br /><br /> Daha fazla bilgi: ["ZZ" Özel Biçim belirleyicisi](#zzSpecifier). | 2009-06-15T13:45:30-07:00->-07 |
| "zzz" | UTC biçiminden saat ve dakika uzaklığı.<br /><br /> Daha fazla bilgi: ["zzz" Özel Biçim belirleyicisi](#zzzSpecifier). | 2009-06-15T13:45:30-07:00->-07:00 |
| ":" | Zaman ayırıcı.<br /><br /> Daha fazla bilgi: [":" Özel Biçim belirleyicisi](#timeSeparator). | 2009-06-15T13:45:30->: (en-US)<br /><br /> 2009-06-15T13:45:30->. (it-IT)<br /><br /> 2009-06-15T13:45:30->: (ja-JP) |
| "/" | Tarih ayırıcı.<br /><br /> Daha fazla bilgi: ["/" Özel Biçim belirleyicisi](#dateSeparator). | 2009-06-15T13:45:30->/(en-US)<br /><br /> 2009-06-15T13:45:30->-(ar-DZ)<br /><br /> 2009-06-15T13:45:30->. (tr-TR) |
| " *String* "<br /><br /> ' *String* ' | Değişmez dize sınırlayıcısı.<br /><br /> Daha fazla bilgi: [karakter sabit değerleri](#Literals). | 2009-06-15T13:45:30 ("ARR:" s:d t)-> ARR: 1:45 P<br /><br /> 2009-06-15T13:45:30 (' ARR: ' s:d t)-> ARR: 1:45 P |
| % | Aşağıdaki karakteri özel biçim belirticisi olarak tanımlar.<br /><br /> Daha fazla bilgi:[tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers). | 2009-06-15T13:45:30 (% h)-> 1 |
| &#92; | "\" çıkış karakteri.<br /><br /> Daha fazla bilgi: [karakter değişmezleri](#Literals) ve [Çıkış karakterini kullanma](#escape). | 2009-06-15T13:45:30 (h \h)-> 1 h |
| Başka bir karakter | Karakter, değişmeyen sonuç dizesine kopyalanır.<br /><br /> Daha fazla bilgi: [karakter sabit değerleri](#Literals). | 2009-06-15T01:45:30 (ARR hh: mm t)-> ARR 01:45 A |

Aşağıdaki bölümlerde, her özel tarih ve saat biçim belirticisi hakkında ek bilgi sağlanır. Aksi belirtilmedikçe, her belirtici bir değer veya değer ile kullanılıp kullanılmadığına bakılmaksızın özdeş bir dize temsili üretir <xref:System.DateTime> <xref:System.DateTimeOffset> .

## <a name="day-d-format-specifier"></a>Gün "d" Biçim belirleyicisi

### <a name="the-d-custom-format-specifier"></a><a name="dSpecifier"></a> "D" Özel Biçim belirleyicisi

"d" özel biçim belirticisi, 1 ile 31 arasında bir sayı olarak ayın gününü temsil eder. Tek basamaklı gün önünde sıfır olmadan biçimlendirilir.

"D" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "d" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek birçok biçim dizesinde "d" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
[!code-vb[Formatting.DateAndTime.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

[Tabloya dön](#table)

### <a name="the-dd-custom-format-specifier"></a><a name="ddSpecifier"></a> "Gg" Özel Biçim belirleyicisi

"dd" özel biçim dizesi, 01 ile 31 arasında bir sayı olarak ayın gününü temsil eder. Tek basamaklı gün önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "dd" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Tabloya dön](#table)

### <a name="the-ddd-custom-format-specifier"></a><a name="dddSpecifier"></a> "Ddd" Özel Biçim belirleyicisi

"ddd" özel biçim belirticisi haftanın gününün kısaltılmış adını temsil eder. Haftanın gününün yerelleştirilmiş kısaltılmış adı, <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültürün özelliğinden alınır.

Aşağıdaki örnek bir özel biçim dizesinde "ddd" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Tabloya dön](#table)

### <a name="the-dddd-custom-format-specifier"></a><a name="ddddSpecifier"></a> "Gggg" Özel Biçim belirleyicisi

"dddd" özel biçim belirticisi (artı herhangi bir sayıda ek "d" tanımlayıcısı) haftanın gününün tam adını temsil eder. Haftanın gününün yerelleştirilmiş adı, <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültürün özelliğinden alınır.

Aşağıdaki örnek bir özel biçim dizesinde "dddd" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Tabloya dön](#table)

## <a name="lowercase-seconds-f-fraction-specifier"></a>Küçük saniye "f" kesir Belirleyicisi

### <a name="the-f-custom-format-specifier"></a><a name="fSpecifier"></a> "F" Özel Biçim belirleyicisi

"f" özel biçim belirticisi saniye bölümünün en önemli basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin onda birini temsil eder.

"F" biçim belirticisi diğer biçim belirticileri olmadan kullanıldığında, "f" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

,, Veya yöntemine sağlanan biçim dizesinin parçası olarak "f" biçim belirticilerini kullandığınızda <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> <xref:System.DateTimeOffset.ParseExact%2A> <xref:System.DateTimeOffset.TryParseExact%2A> , "f" biçim Belirticilerinin sayısı, dizeyi başarıyla ayrıştırmak için olması gereken saniye kesirinin en önemli basamak sayısını gösterir.

Aşağıdaki örnek bir özel biçim dizesinde "f" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

### <a name="the-ff-custom-format-specifier"></a><a name="ffSpecifier"></a> "FF" Özel Biçim belirleyicisi

"ff" özel biçim belirticisi saniye bölümünün en önemli iki basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüzde birini temsil eder.

Aşağıdaki örnek, özel biçim dizesindeki "ff" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

### <a name="the-fff-custom-format-specifier"></a><a name="fffSpecifier"></a> "Fff" Özel Biçim belirleyicisi

"fff" özel biçim belirticisi saniye bölümünün en önemli üç basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin binde birini temsil eder.

Aşağıdaki örnek bir özel biçim dizesinde "fff" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

### <a name="the-ffff-custom-format-specifier"></a><a name="ffffSpecifier"></a> "Ffff" Özel Biçim belirleyicisi

"ffff" özel biçim belirticisi saniye bölümünün en önemli dört basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on binde birini temsil eder.

Bir zaman değerinin ikinci bileşenlerinden on binde 'ı göstermek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 sürümünde (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

### <a name="the-fffff-custom-format-specifier"></a><a name="fffffSpecifier"></a> "Fffff" Özel Biçim belirleyicisi

"fffff" özel biçim belirticisi saniye bölümünün en önemli beş basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüz binde birini temsil eder.

Bir zaman değerinin ikinci bir bileşeninin yüz binde gösterilmesi mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

### <a name="the-ffffff-custom-format-specifier"></a><a name="ffffffSpecifier"></a> "FFFFFF" Özel Biçim belirleyicisi

"ffffff" özel biçim belirticisi saniye bölümünün en önemli altı basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin milyonda birini temsil eder.

Bir zaman değerinin ikinci bileşeninin milionkesini göstermek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

### <a name="the-fffffff-custom-format-specifier"></a><a name="fffffffSpecifier"></a> "Fffffff" Özel Biçim belirleyicisi

"fffffff" özel biçim belirticisi saniye bölümünün en önemli yedi basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on milyonda birini temsil eder.

Bir zaman değerinin ikinci bileşenlerinden oluşan on milüzde görüntülenmek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="uppercase-seconds-f-fraction-specifier"></a>Büyük saniye "F" kesir Belirleyicisi

### <a name="the-f-custom-format-specifier"></a><a name="F_Specifier"></a> "F" Özel Biçim belirleyicisi

"F" özel biçim belirticisi saniye bölümünün en önemli basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin onda birini temsil eder. Basamak sıfırsa hiçbir şey görüntülenmez.

"F" biçim belirticisi diğer biçim belirticileri olmadan kullanıldığında, "F" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

,, Veya yöntemiyle kullanılan "F" biçim belirleyicilerinin sayısı, <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> <xref:System.DateTimeOffset.ParseExact%2A> <xref:System.DateTimeOffset.TryParseExact%2A> dizeyi başarıyla ayrıştırmak için mevcut olabilecek en önemli basamak sayısını belirtir.

Aşağıdaki örnek bir özel biçim dizesinde "F" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

### <a name="the-ff-custom-format-specifier"></a><a name="FF_Specifier"></a> "FF" Özel Biçim belirleyicisi

"FF" özel biçim belirticisi saniye bölümünün en önemli iki basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüzde birini temsil eder. Ancak sondaki sıfırlar veya iki sıfır basamak görüntülenmez.

Aşağıdaki örnek bir özel biçim dizesinde "FF" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

### <a name="the-fff-custom-format-specifier"></a><a name="FFF_Specifier"></a> "FFF" Özel Biçim belirleyicisi

"FFF" özel biçim belirticisi saniye bölümünün en önemli üç basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin binde birini temsil eder. Ancak sondaki sıfırlar veya üç sıfır basamak görüntülenmez.

Aşağıdaki örnek bir özel biçim dizesinde "FFF" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Tabloya dön](#table)

### <a name="the-ffff-custom-format-specifier"></a><a name="FFFF_Specifier"></a> "FFFF" Özel Biçim belirleyicisi

"FFFF" özel biçim belirticisi saniye bölümünün en önemli dört basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on binde birini temsil eder. Ancak sondaki sıfırlar veya dört sıfır basamak görüntülenmez.

Bir zaman değerinin ikinci bileşenlerinden on binde 'ı göstermek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

### <a name="the-fffff-custom-format-specifier"></a><a name="FFFFF_Specifier"></a> "FFFFF" Özel Biçim belirleyicisi

"FFFFF" özel biçim belirticisi saniye bölümünün en önemli beş basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin yüz binde birini temsil eder. Ancak sondaki sıfırlar veya beş sıfır basamak görüntülenmez.

Bir zaman değerinin ikinci bir bileşeninin yüz binde gösterilmesi mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

### <a name="the-ffffff-custom-format-specifier"></a><a name="FFFFFF_Specifier"></a> "FFFFFF" Özel Biçim belirleyicisi

"FFFFFF" özel biçim belirticisi saniye bölümünün en önemli altı basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin milyonda birini temsil eder. Ancak sondaki sıfırlar veya altı sıfır basamak görüntülenmez.

Bir zaman değerinin ikinci bileşeninin milionkesini göstermek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

### <a name="the-fffffff-custom-format-specifier"></a><a name="FFFFFFF_Specifier"></a> "FFFFFFF" Özel Biçim belirleyicisi

"FFFFFFF" özel biçim belirticisi saniye bölümünün en önemli yedi basamağını temsil eder; diğer bir deyişle, tarih ve saat değerinde saniyenin on milyonda birini temsil eder. Ancak sondaki sıfırlar veya yedi sıfır basamak görüntülenmez.

Bir zaman değerinin ikinci bileşenlerinden oluşan on milüzde görüntülenmek mümkün olsa da, bu değer anlamlı olmayabilir. Tarih ve saat değerlerinin duyarlığı, sistem saatinin çözünürlüğüne bağlıdır. Windows NT 3.5 (ve sonraki sürümler) ve Windows Vista işletim sistemlerinde, saatin çözünürlüğü yaklaşık 10-15 milisaniyedir.

[Tabloya dön](#table)

## <a name="era-g-format-specifier"></a>Dönem "g" Biçim belirleyicisi

### <a name="the-g-or-gg-custom-format-specifier"></a><a name="gSpecifier"></a> "G" veya "gg" Özel Biçim belirleyicisi

"g" veya "gg" özel biçim belirticileri (artı herhangi bir sayıda ek "g" belirticisi) M.S. gibi bir dönem veya çağı temsil eder Biçimlendirme işlemi, biçimlendirilecek tarihin ilişkili bir dönemi veya dönem dizesi yoksa bu belirticisi yoksayar.

"G" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "g" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek bir özel biçim dizesinde "g" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
[!code-vb[Formatting.DateAndTime.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

[Tabloya dön](#table)

## <a name="lowercase-hour-h-format-specifier"></a>Küçük harf saat "h" Biçim belirleyicisi

### <a name="the-h-custom-format-specifier"></a><a name="hSpecifier"></a> "H" Özel Biçim belirleyicisi

"h" özel biçim belirticisi 1 ile 12 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından veya öğleden itibaren tam saatleri sayan 12 saatlik zaman biçimi ile temsil edilir. Gece yarısından sonraki bir saat, öğleden sonraki aynı saatle ayırt edilemez. Saat yuvarlanmaz ve önünde sıfır olmadan tek basamaklı bir saat biçimlendirilir. Örneğin, sabah veya öğleden sonra 5:43 saati verildiğinde bu özel biçim belirtici "5" görüntüler.

"H" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi belirleyicisi olarak yorumlanır ve bir oluşturur <xref:System.FormatException> . Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek bir özel biçim dizesinde "h" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya dön](#table)

### <a name="the-hh-custom-format-specifier"></a><a name="hhSpecifier"></a> "Hh" Özel Biçim belirleyicisi

"hh" özel biçim belirticisi (artı herhangi bir sayıda ek "h" belirticisi) 01 ile 12 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, tam saatleri gece yarısından veya öğleden itibaren sayan 12 saatlik zaman biçimi ile temsil edilir. Gece yarısından sonraki bir saat, öğleden sonraki aynı saatle ayırt edilemez. Saat yuvarlanmaz ve önünde sıfır ile birlikte tek basamaklı bir saat biçimlendirilir. Örneğin, sabah veya öğleden sonra 5:43 saati verildiğinde bu biçim belirtici "05" görüntüler.

Aşağıdaki örnek bir özel biçim dizesinde "hh" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya dön](#table)

## <a name="uppercase-hour-h-format-specifier"></a>Büyük saat "H" Biçim belirleyicisi

### <a name="the-h-custom-format-specifier"></a><a name="H_Specifier"></a> "H" Özel Biçim belirleyicisi

"H" özel biçim belirticisi 0 ile 23 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından itibaren sayan sıfır tabanlı bir 24 saatlik zaman biçimi ile temsil edilir. Tek basamaklı saat önünde sıfır olmadan biçimlendirilir.

"H" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi belirleyicisi olarak yorumlanır ve bir oluşturur <xref:System.FormatException> . Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek bir özel biçim dizesinde "H" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
[!code-vb[Formatting.DateAndTime.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

[Tabloya dön](#table)

### <a name="the-hh-custom-format-specifier"></a><a name="HH_Specifier"></a> "HH" Özel Biçim belirleyicisi

"HH" özel biçim belirticisi (artı herhangi bir sayıda ek "H" belirticisi) 00 ile 23 arasında bir sayı olarak saati temsil eder; diğer bir deyişle, saat, saatleri gece yarısından itibaren sayan sıfır tabanlı bir 24 saatlik zaman biçimi ile temsil edilir. Tek basamaklı saat önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "HH" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
[!code-vb[Formatting.DateAndTime.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

[Tabloya dön](#table)

## <a name="time-zone-k-format-specifier"></a>Saat dilimi "K" Biçim belirleyicisi

### <a name="the-k-custom-format-specifier"></a><a name="KSpecifier"></a> "K" Özel Biçim belirleyicisi

"K" özel biçim belirticisi bir tarih ve saat değerinin saat dilimi bilgisini temsil eder. Bu biçim belirticisi <xref:System.DateTime> değerleriyle kullanıldığında, sonuç dizesi özelliğin değeri tarafından tanımlanır <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> :

- Yerel Saat dilimi (bir <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değeri <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ) için, bu belirtici "zzz" belirticisi ile eşdeğerdir ve yerel Eşgüdümlü Evrensel Saat (UTC) ile yerel sapmayı içeren bir sonuç dizesi oluşturur; örneğin, "-07:00".

- UTC saati için ( <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değeri <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ), sonuç dizesi UTC tarihini temsil eden bir "Z" karakteri içerir.

- Belirtilmeyen bir saat diliminden bir zaman (özelliği eşittir olan bir süre <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> ) için, sonuç değerine eşdeğerdir <xref:System.String.Empty?displayProperty=nameWithType> .

<xref:System.DateTimeOffset>Değerler için, "K" biçim belirticisi "zzz" biçim belirticisine eşdeğerdir ve DEĞERIN UTC 'nin sapmasını içeren bir sonuç dizesi oluşturur <xref:System.DateTimeOffset> .

"K" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi belirleyicisi olarak yorumlanır ve bir oluşturur <xref:System.FormatException> . Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek, "K" Özel Biçim belirticisinin <xref:System.DateTime> <xref:System.DateTimeOffset> ABD Pasifik saat dilimindeki bir sistemde çeşitli ve değerlerle kullanılması sonucunda elde edilen dizeyi görüntüler.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
[!code-vb[Formatting.DateAndTime.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

[Tabloya dön](#table)

## <a name="minute-m-format-specifier"></a>Dakika "d" Biçim belirleyicisi

### <a name="the-m-custom-format-specifier"></a><a name="mSpecifier"></a> "D" Özel Biçim belirleyicisi

"m" özel biçim belirticisi, 0 ile 59 arasında bir sayı olarak dakikayı temsil eder. Dakika, son saatten beri geçen tam dakikaları temsil eder. Tek basamaklı dakika önünde sıfır olmadan biçimlendirilir.

"D" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "d" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek bir özel biçim dizesinde "m" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya dön](#table)

### <a name="the-mm-custom-format-specifier"></a><a name="mmSpecifier"></a> "Mm" Özel Biçim belirleyicisi

"m" özel biçim belirticisi (artı herhangi bir sayıda ek "m" belirticisi) 00 ile 59 arasında bir sayı olarak dakikayı temsil eder. Dakika, son saatten beri geçen tam dakikaları temsil eder. Tek basamaklı dakika önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "mm" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya dön](#table)

## <a name="month-m-format-specifier"></a>Ay "d" Biçim belirleyicisi

### <a name="the-m-custom-format-specifier"></a><a name="M_Specifier"></a> "D" Özel Biçim belirleyicisi

"M" özel biçim belirticisi, 1 ile 12 arasında (veya 13 ay içeren takvimler için 1 ile 13 arasında) bir sayı olarak ayı temsil eder. Tek basamaklı ay önünde sıfır olmadan biçimlendirilir.

"D" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "d" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek bir özel biçim dizesinde "M" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
[!code-vb[Formatting.DateAndTime.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

[Tabloya dön](#table)

### <a name="the-mm-custom-format-specifier"></a><a name="MM_Specifier"></a> "MM" Özel Biçim belirleyicisi

"MM" özel biçim belirticisi, 01 ile 12 arasında (veya 13 ay içeren takvimler için 1 ile 13 arasında) bir sayı olarak ayı temsil eder. Tek basamaklı ay önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "MM" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Tabloya dön](#table)

### <a name="the-mmm-custom-format-specifier"></a><a name="MMM_Specifier"></a> "MMM" Özel Biçim belirleyicisi

"MMM" özel biçim belirticisi ayın gününün kısaltılmış adını temsil eder. Ayın yerelleştirilmiş kısaltılmış adı, <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> geçerli ya da belirtilen kültürün özelliğinden alınır.

Aşağıdaki örnek bir özel biçim dizesinde "MMM" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Tabloya dön](#table)

### <a name="the-mmmm-custom-format-specifier"></a><a name="MMMM_Specifier"></a> "MMMM" Özel Biçim belirleyicisi

"MMMM" özel biçim belirticisi ayın gününün tam adını temsil eder. Ayın yerelleştirilmiş adı, <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> geçerli veya belirtilen kültürün özelliğinden alınır.

Aşağıdaki örnek bir özel biçim dizesinde "MMMM" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Tabloya dön](#table)

## <a name="seconds-s-format-specifier"></a>Saniye "s" Biçim belirleyicisi

### <a name="the-s-custom-format-specifier"></a><a name="sSpecifier"></a> "S" Özel Biçim belirleyicisi

"s" özel biçim belirticisi, 0 ile 59 arasında bir sayı olarak saniyeyi temsil eder. Sonuç, son dakikadan beri geçen tam saniyeleri temsil eder. Tek basamaklı saniye önünde sıfır olmadan biçimlendirilir.

"S" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "s" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek bir özel biçim dizesinde "s" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya dön](#table)

### <a name="the-ss-custom-format-specifier"></a><a name="ssSpecifier"></a> "Ss" Özel Biçim belirleyicisi

"ss" özel biçim belirticisi (artı herhangi bir sayıda ek "s" belirticisi) 00 ile 59 arasında bir sayı olarak saniyeyi temsil eder. Sonuç, son dakikadan beri geçen tam saniyeleri temsil eder. Tek basamaklı saniye önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "ss" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya dön](#table)

## <a name="meridiem-t-format-specifier"></a>Meridem "t" Biçim belirleyicisi

### <a name="the-t-custom-format-specifier"></a><a name="tSpecifier"></a> "T" Özel Biçim belirleyicisi

"t" özel biçim belirticisi AM/PM göstergelerinin ilk karakterini temsil eder. Uygun yerelleştirilmiş gösterge, <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> geçerli veya özel kültürün veya özelliğinden alınır. AM göstergesi, 0:00:00 (gece yarısı) ile 11:59:59.999 arasındaki tüm zamanlar için kullanılır. PM göstergesi, 12:00:00 (öğlen) ile 23:59:59.999 arasındaki tüm zamanlar için kullanılır.

"T" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "t" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek bir özel biçim dizesinde "t" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Tabloya dön](#table)

### <a name="the-tt-custom-format-specifier"></a><a name="ttSpecifier"></a> "Tt" Özel Biçim belirleyicisi

"tt" özel biçim belirticisi (artı herhangi bir sayıda ek "t" belirticisi) tüm AM/PM göstergelerini temsil eder. Uygun yerelleştirilmiş gösterge, <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> geçerli veya özel kültürün veya özelliğinden alınır. AM göstergesi, 0:00:00 (gece yarısı) ile 11:59:59.999 arasındaki tüm zamanlar için kullanılır. PM göstergesi, 12:00:00 (öğlen) ile 23:59:59.999 arasındaki tüm zamanlar için kullanılır.

ÖÖ ve PM arasındaki ayrımı sürdürmek için gereken diller için "tt" belirticisini kullandığınızdan emin olun. Japonca buna bir örnektir; AM ve PM göstergeleri birinci karakter yerine ikinci karakterde farklılık gösterir.

Aşağıdaki örnek bir özel biçim dizesinde "tt" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Tabloya dön](#table)

## <a name="year-y-format-specifier"></a>Yıl "y" Biçim belirleyicisi

### <a name="the-y-custom-format-specifier"></a><a name="ySpecifier"></a> "Y" Özel Biçim belirleyicisi

"y" özel biçim belirticisi tek basamaklı veya iki basamaklı bir sayı olarak yılı temsil eder. Yılda ikiden fazla basamak varsa, yalnızca son kısımdaki iki basamak sonuçta görünür. İki basamaklı yılın ilk basamağı sıfır ise (örneğin, 2008), sayı önünde sıfır olmadan biçimlendirilir.

"Y" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, "y" standart tarih ve saat biçimi belirleyicisi olarak yorumlanır. Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek bir özel biçim dizesinde "y" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

### <a name="the-yy-custom-format-specifier"></a><a name="yySpecifier"></a> "Yy" Özel Biçim belirleyicisi

"yy" özel biçim belirticisi iki basamaklı bir sayı olarak yılı temsil eder. Yılda ikiden fazla basamak varsa, yalnızca son kısımdaki iki basamak sonuçta görünür. İki basamaklı yılda ikiden az belirtici basamak varsa, iki basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

Bir ayrıştırma işleminde, "yy" Özel Biçim belirleyicisi kullanılarak ayrıştırılmış iki basamaklı bir yıl, <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> biçim sağlayıcısının geçerli takviminin özelliğine göre yorumlanır. Aşağıdaki örnek, bu durumda en-US kültürü olan geçerli kültürün varsayılan Gregoryen takvimini kullanarak iki basamaklı yıl içeren bir tarih dize gösterimini ayrıştırır. Daha sonra, geçerli kültürün <xref:System.Globalization.CultureInfo> nesnesini özelliği değiştirilmiş bir nesneyi kullanacak şekilde değiştirir <xref:System.Globalization.GregorianCalendar> <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> .

[!code-csharp-interactive[Formatting.DateAndTime.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
[!code-vb[Formatting.DateAndTime.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

Aşağıdaki örnek bir özel biçim dizesinde "yy" özel biçim belirticisini içerir.

[!code-csharp[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

### <a name="the-yyy-custom-format-specifier"></a><a name="yyySpecifier"></a> "Yyy" Özel Biçim belirleyicisi

"yyy" özel biçim belirticisi en az üç basamakla yılı temsil eder. Yılda üçten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl üçten az basamaktan oluşuyorsa, üç basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

> [!NOTE]
> Beş basamaklı yıllar içeren Thai Budist takvimi için bu biçim belirtici tüm basamakları görüntüler.

Aşağıdaki örnek bir özel biçim dizesinde "yyy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

### <a name="the-yyyy-custom-format-specifier"></a><a name="yyyySpecifier"></a> "Yyyy" Özel Biçim belirleyicisi

"yyyy" özel biçim belirticisi en az dört basamakla yılı temsil eder. Yılda dörtten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl dörtten az basamaktan oluşuyorsa, dört basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

> [!NOTE]
> Beş basamaklı yıllar içeren Thai Budist takvimi için bu biçim belirtici en az dört basamak görüntüler.

Aşağıdaki örnek bir özel biçim dizesinde "yyyy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

### <a name="the-yyyyy-custom-format-specifier"></a><a name="yyyyySpecifier"></a> "Yyyyy" Özel Biçim belirleyicisi

"yyyyy" özel biçim belirticisi (artı herhangi bir sayıda ek "y" belirticisi) en az beş basamakla yılı temsil eder. Yılda beşten fazla belirtici basamak varsa, bunlar sonuç dizesine eklenir. Yıl beşten az basamaktan oluşuyorsa, beş basamak oluşturulabilmesi için sayının önüne sıfır eklenir.

Ek "y" belirticileri varsa sayının önüne "y" belirticileriyle aynı sayıda olacak kadar sıfır eklenir.

Aşağıdaki örnek bir özel biçim dizesinde "yyyyy" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Tabloya dön](#table)

## <a name="offset-z-format-specifier"></a>"Z" biçim belirticisini

### <a name="the-z-custom-format-specifier"></a><a name="zSpecifier"></a> "Z" Özel Biçim belirleyicisi

<xref:System.DateTime>Değerler ile, "z" özel biçim belirticisi yerel işletim sisteminin saat diliminin, saat cinsinden ölçülen evrensel saat (UTC) olarak imzalanmış uzaklığını temsil eder. Bir örneğin özelliğinin değerini yansıtmaz <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> . Bu nedenle, "z" Biçim belirticisinin değerleriyle kullanılması önerilmez <xref:System.DateTime> .

<xref:System.DateTimeOffset>Değerler ile, bu biçim belirticisi <xref:System.DateTimeOffset> değerin UTC 'den saat cinsinden sapmasını temsil eder.

Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır olmadan biçimlendirilir.

"Z" biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi belirleyicisi olarak yorumlanır ve bir oluşturur <xref:System.FormatException> . Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

Aşağıdaki örnek bir özel biçim dizesinde "z" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Tabloya dön](#table)

### <a name="the-zz-custom-format-specifier"></a><a name="zzSpecifier"></a> "ZZ" Özel Biçim belirleyicisi

<xref:System.DateTime>Değerler ile, "ZZ" özel biçim belirticisi yerel işletim sisteminin saat diliminin saat olarak ölçülen, UTC 'den imzalanmış uzaklığını temsil eder. Bir örneğin özelliğinin değerini yansıtmaz <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> . Bu nedenle, "ZZ" Biçim belirticisinin değerleriyle kullanılması önerilmez <xref:System.DateTime> .

<xref:System.DateTimeOffset>Değerler ile, bu biçim belirticisi <xref:System.DateTimeOffset> değerin UTC 'den saat cinsinden sapmasını temsil eder.

Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "zz" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Tabloya dön](#table)

### <a name="the-zzz-custom-format-specifier"></a><a name="zzzSpecifier"></a> "Zzz" Özel Biçim belirleyicisi

<xref:System.DateTime>Değerler ile, "zzz" özel biçim belirticisi yerel işletim sisteminin saat DILIMININ UTC 'den saat ve dakikada ölçülen imzalı uzaklığını temsil eder. Bir örneğin özelliğinin değerini yansıtmaz <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> . Bu nedenle, "zzz" Biçim belirticisinin değerleriyle kullanılması önerilmez <xref:System.DateTime> .

<xref:System.DateTimeOffset>Değerler ile, bu biçim belirticisi <xref:System.DateTimeOffset> değerin UTC 'den saat ve dakika cinsinden sapmasını temsil eder.

Uzaklık her zaman önünde bir işaretle görüntülenir. Artı işareti (+) UTC'den önceki saatleri belirtir, eksi işareti (-) UTC'den sonraki saatleri belirtir. Tek basamaklı sapma önünde sıfır ile biçimlendirilir.

Aşağıdaki örnek bir özel biçim dizesinde "zzz" özel biçim belirticisini içerir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Tabloya dön](#table)

## <a name="date-and-time-separator-specifiers"></a>Tarih ve saat ayırıcı belirticileri

### <a name="the--custom-format-specifier"></a><a name="timeSeparator"></a> ":" Özel Biçim belirleyicisi
":" özel biçim belirticisi, saat, dakika ve saniyeyi ayırt etmek için kullanılan zaman ayırıcıyı temsil eder. Uygun yerelleştirilmiş zaman ayırıcısı, <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> geçerli veya belirtilen kültürün özelliğinden alınır.

> [!NOTE]
> Belirli bir tarih ve saat dizesinin zaman ayırıcısını değiştirmek için, bir sabit dize sınırlayıcısı içinde ayırıcı karakterini belirtin. Örneğin, özel biçim dizesi `hh'_'dd'_'ss` " \_ " (alt çizgi) her zaman zaman ayırıcısı olarak kullanılan bir sonuç dizesi üretir. Bir kültürün tüm tarihlerinin zaman ayırıcısını değiştirmek için, <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> geçerli kültürün özelliğinin değerini değiştirin ya da bir nesne örneği oluşturun <xref:System.Globalization.DateTimeFormatInfo> , karakteri <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> özelliğine atayın ve bir parametre içeren biçimlendirme yönteminin aşırı yüklemesini çağırın <xref:System.IFormatProvider> .

":" Biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi belirleyicisi olarak yorumlanır ve bir oluşturur <xref:System.FormatException> . Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

[Tabloya dön](#table)

### <a name="the--custom-format-specifier"></a><a name="dateSeparator"></a> "/" Özel Biçim belirleyicisi

"/" özel biçim belirticisi, yıl, ay ve günü ayırt etmek için kullanılan tarih ayırıcıyı temsil eder. Uygun yerelleştirilmiş Tarih ayırıcısı, <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> geçerli veya belirtilen kültürün özelliğinden alınır.

> [!NOTE]
> Belirli bir tarih ve saat dizesinin tarih ayırıcısını değiştirmek için, bir sabit dize sınırlayıcısı içinde ayırıcı karakterini belirtin. Örneğin, özel biçim dizesi, `mm'/'dd'/'yyyy` "/" ın her zaman Tarih ayırıcısı olarak kullanıldığı bir sonuç dizesi üretir. Bir kültürün tüm tarihlerinin tarih ayırıcısını değiştirmek için, <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> geçerli kültürün özelliğinin değerini değiştirin ya da bir nesne örneği oluşturun <xref:System.Globalization.DateTimeFormatInfo> , karakteri <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> özelliğine atayın ve bir parametre içeren biçimlendirme yönteminin aşırı yüklemesini çağırın <xref:System.IFormatProvider> .

"/" Biçim belirticisi diğer özel biçim belirticileri olmadan kullanıldığında, standart tarih ve saat biçimi belirleyicisi olarak yorumlanır ve bir oluşturur <xref:System.FormatException> . Tek bir biçim belirticisi kullanma hakkında daha fazla bilgi için, bu makalede daha sonra [tek özel biçim belirticileri kullanma](#UsingSingleSpecifiers) bölümüne bakın.

[Tabloya dön](#table)

## <a name="character-literals"></a><a name="Literals"></a> Karakter sabit değerleri

Özel bir tarih ve saat biçim dizesinde aşağıdaki karakterler ayrılmıştır ve her zaman biçimlendirme karakterleri olarak yorumlanır veya,,, `"` `'` ve durumunda `/` `\` özel karakterler olarak yorumlanır.

|     |     |     |     |     |
|-----|-----|-----|-----|-----|
| `F` | `H` | `K` | `M` | `d` |
| `f` | `g` | `h` | `m` | `s` |
| `t` | `y` | `z` | `%` | `:` |
| `/` | `"` | `'` | `\` |     |

Tüm diğer karakterler her zaman karakter değişmezleri olarak yorumlanır ve bir biçimlendirme işleminde, sonuç dizesine değiştirilmeden dahil edilir.  Bir ayrıştırma işleminde, giriş dizesindeki karakterlerle tam olarak eşleşmesi gerekir; Karşılaştırma büyük/küçük harfe duyarlıdır.

Aşağıdaki örnek, bir biçim dizesindeki yerel saat dilimini göstermek için "PST" (Pasifik standart saati için) ve "Pasifik saati" (Pasifik yaz saati için) sabit karakterlerini içerir. Dizenin sonuç dizesine dahil edildiğini ve yerel saat dilimi dizesini içeren bir dizenin de başarıyla ayrıştırıldığı unutulmamalıdır.

[!code-csharp[Formatting.DateAndTime.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
[!code-vb[Formatting.DateAndTime.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

Karakterlerin, bir sonuç dizesine eklenebilir veya bir giriş dizesinde başarıyla ayrıştırılabilmeleri için, ayrılmış karakterler olarak değil, karakterlerin değişmez karakter olarak yorumlanabileceğini belirten iki yol vardır:

- Her bir ayrılmış karakteri kaçarak. Daha fazla bilgi için bkz. [kaçış karakterini kullanma](#escape).

Aşağıdaki örnek, bir biçim dizesinde yerel saat dilimini temsil etmek için "PST" (Pasifik standart saati için) sabit karakterlerini içerir. Hem "s" hem de "t" özel biçim dizeleri olduğundan, karakter değişmez değerleri olarak yorumlanmaması için her iki karakterin de kaçışılması gerekir.

[!code-csharp[Formatting.DateAndTime.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
[!code-vb[Formatting.DateAndTime.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- Sabit değer dizesinin tamamını tırnak işaretleri veya kesme işareti içine alarak. Aşağıdaki örnek önceki bir gibidir. "PST" değeri, tüm sınırlandırılmış dizenin karakter sabit değerleri olarak yorumlanması gerektiğini belirtmek için tırnak içine alınmalıdır.

[!code-csharp[Formatting.DateAndTime.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
[!code-vb[Formatting.DateAndTime.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

## <a name="notes"></a>Notlar

### <a name="using-single-custom-format-specifiers"></a><a name="UsingSingleSpecifiers"></a> Tek özel biçim belirticileri kullanma

Özel tarih ve saat biçimi dizesi iki veya daha fazla karakterden oluşur. Tarih ve saat biçimlendirme yöntemleri, herhangi tek karakterli dizeyi standart tarih ve saat biçim dizesi olarak yorumlar. Karakteri geçerli bir biçim belirticisi olarak tanımadığı takdirde bir oluşturur <xref:System.FormatException> . Örneğin, yalnızca belirleyici "h" içeren bir biçim dizesi standart tarih ve saat biçimi dizesi olarak yorumlanır. Ancak, bu durumda "h" standart tarih ve saat biçimi belirticisi olmadığından bir özel durum oluşturulur.

Bir biçim dizesinde tek belirleyici olarak özel tarih ve saat biçimi belirleyicilerinden birini kullanmak için ("d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" veya "/" özel biçim belirleyicisinin kendisi), belirleyiciden önce veya sonra bir boşluk bırakın veya tek özel tarih ve saat belirleyicisinden önce yüzde ("%") biçim belirleyicisi ekleyin.

Örneğin, " `%h"` geçerli tarih ve saat değeri ile temsil edilen saati gösteren özel bir tarih ve saat biçim dizesi olarak yorumlanır. Sonuç dizesinde saatin yanında bir boşluk içerse de " h" veya "h " biçimlendirme dizisini de kullanabilirsiniz. Aşağıdaki örnek bu üç biçim dizesini gösterir.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
[!code-vb[Formatting.DateAndTime.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

#### <a name="using-the-escape-character"></a><a name="escape"></a> Kaçış karakterini kullanma

Bir biçim dizesindeki "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" veya "/" karakterleri, değişmez karakterler olarak değil özel biçim belirticileri olarak yorumlanır. Bir karakterin Biçim belirleyicisi olarak yorumlanmasını engellemek için, çıkış karakteri olan bir ters eğik çizgiyle () önüne getirebilirsiniz \\ . Çıkış karakteri, aşağıdaki karakterin değiştirilmeden sonuç dizesini dahil edilmesi gereken bir karakter sabiti olduğunu belirtir.

Bir sonuç dizesinde ters eğik çizgi eklemek için, başka bir ters eğik çizgiyle () kaçış yapmanız gerekir `\\` .

> [!NOTE]
> C++ ve C# derleyicileri gibi bazı derleyiciler, tek bir ters eğik çizgiyi çıkış karakteri olarak yorumlayabilir. Bir dizenin yalnızca düzgün biçimlendirildiğinde yorumlanmasını sağlamak için C# içinde dizeden önce değişmez değer karakterini (@ karakteri) kullanabilirsiniz veya C# ve C++ içinde her ters eğik çizgiden önce bir ters eğik çizgi daha ekleyebilirsiniz. Aşağıdaki C# örneği her iki yaklaşımı da gösterir.

Aşağıdaki örnek, biçimlendirme işleminin "h" ve "m" karakterlerini biçim belirticileri olarak yorumlamasını önlemek için çıkış karakteri kullanır.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
[!code-vb[Formatting.DateAndTime.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>Denetim Masası Ayarları

Denetim Masası 'ndaki **bölge ve dil seçenekleri** ayarları, özel tarih ve saat biçimi Belirticilerinin çoğunu içeren bir biçimlendirme işlemi tarafından üretilen sonuç dizesini etkiler. Bu ayarlar <xref:System.Globalization.DateTimeFormatInfo> , biçimlendirmeyi yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürüyle ilişkili nesneyi başlatmak için kullanılır. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.

Ayrıca, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> <xref:System.Globalization.CultureInfo> geçerli sistem kültürüyle aynı kültürü temsil eden yeni bir nesne oluşturmak için oluşturucuyu kullanırsanız, Denetim Masası 'ndaki **bölge ve dil seçenekleri** öğesi tarafından belirlenen tüm özelleştirmeler yeni <xref:System.Globalization.CultureInfo> nesneye uygulanır. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29>Oluşturucuyu, <xref:System.Globalization.CultureInfo> sistemin özelleştirmelerini yansıtmayan bir nesne oluşturmak için kullanabilirsiniz.

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo özellikleri

Biçimlendirme, geçerli <xref:System.Globalization.DateTimeFormatInfo> iş parçacığı kültürü tarafından örtük olarak veya <xref:System.IFormatProvider> Biçimlendirmeyi çağıran yöntemin parametresi tarafından açıkça sunulan geçerli nesnenin özelliklerinden etkilenir. Parametresi için bir <xref:System.IFormatProvider> <xref:System.Globalization.CultureInfo> kültürü veya bir nesneyi temsil eden bir nesnesi belirtmeniz gerekir <xref:System.Globalization.DateTimeFormatInfo> .

Özel tarih ve saat biçimi belirticileri tarafından üretilen sonuç dizesi ayrıca geçerli nesnesinin özelliklerine de bağlıdır <xref:System.Globalization.DateTimeFormatInfo> . Uygulamanız, ilgili özelliği değiştirerek bazı özel tarih ve saat biçimi belirticileri tarafından üretilen sonucu değiştirebilir <xref:System.Globalization.DateTimeFormatInfo> . Örneğin, "ddd" Biçim belirleyicisi dize dizisinde bulunan kısaltılmış bir gün adını <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> sonuç dizesine ekler. Benzer şekilde, "aaaa" Biçim Belirleyicisi, <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> sonuç dizesine dize dizisinde bulunan tam bir ay adı ekler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- [Biçimlendirme türleri](formatting-types.md)
- [Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (C#)](/samples/dotnet/samples/windowsforms-formatting-utility-cs)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (Visual Basic)](/samples/dotnet/samples/windowsforms-formatting-utility-vb)
