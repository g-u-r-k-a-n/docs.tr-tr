---
title: System.Text.Json üzerinde DateTime ve DateTimeOffset desteği
description: DateTime ve DateTimeOffset türlerinin kitaplığındaki System.Text.Jsnasıl desteklenbir genel bakış.
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 6b4e79e6c666731e313ed41e25f601df4158b8d4
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075426"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>System.Text.Json üzerinde DateTime ve DateTimeOffset desteği

Kitaplığındaki System.Text.Js, <xref:System.DateTime> <xref:System.DateTimeOffset> ISO 8601:-2019 genişletilmiş profiline göre ayrıştırır ve yazılır ve değerleri kaydeder.
[Dönüştürücüler](xref:System.Text.Json.Serialization.JsonConverter%601) ile serileştirme ve seri durumdan çıkarma için özel destek sağlar <xref:System.Text.Json.JsonSerializer> .
Ayrıca, ve kullanılırken özel destek de uygulanabilir <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> .

## <a name="support-for-the-iso-8601-12019-format"></a>ISO 8601-1:2019 biçimi desteği

<xref:System.Text.Json.JsonSerializer>,, <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> Ve türleri, <xref:System.Text.Json.JsonElement> <xref:System.DateTime> <xref:System.DateTimeOffset> ISO 8601-1:2019 biçiminin genişletilmiş profiline göre ayrıştırılır ve yazılır ve metin gösterimleridir; Örneğin, 2019-07-26T16:59:57-05:00.

<xref:System.DateTime> ve <xref:System.DateTimeOffset> veriler ile seri hale getirilebilir <xref:System.Text.Json.JsonSerializer> :

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Ayrıca, şu şekilde seri durumdan çıkarılabilirler <xref:System.Text.Json.JsonSerializer> :

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Varsayılan seçeneklerle, giriş <xref:System.DateTime> ve <xref:System.DateTimeOffset> metin temsilleri, genişletilmiş ISO 8601-1:2019 profiline uymalıdır.
Profille uyumlu olmayan temsiller serisini kaldırma girişimi bir oluşturulmasına neden olur <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException> :

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

, <xref:System.Text.Json.JsonDocument> <xref:System.DateTime> Ve temsilleri dahil olmak üzere bir JSON yükünün içeriğine yapılandırılmış erişim sağlar <xref:System.DateTimeOffset> . Aşağıdaki örnekte, bir sıcaklığın toplanması verildiğinde, Mondays ortalama sıcaklık hesaplanabilecek nasıl hesaplanacağı gösterilmektedir:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Uyumsuz gösterimlerle yük verilen ortalama sıcaklığın hesaplanmaya çalışılması, şunu oluşturmasına <xref:System.DateTime> neden olur <xref:System.Text.Json.JsonDocument> <xref:System.FormatException> :

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

Alt düzey <xref:System.Text.Json.Utf8JsonWriter> yazmaları <xref:System.DateTime> ve <xref:System.DateTimeOffset> verileri:

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader> ayrıştırır <xref:System.DateTime> ve <xref:System.DateTimeOffset> veriler:

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Uyumlu olmayan biçimleri okumaya çalışmak <xref:System.Text.Json.Utf8JsonReader> bunun oluşturulmasına neden olur <xref:System.FormatException> :

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Ve için özel destek <xref:System.DateTime><xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Kullanırken <xref:System.Text.Json.JsonSerializer>

Seri hale getiricinin özel ayrıştırma veya biçimlendirme gerçekleştirmesini istiyorsanız [özel dönüştürücüler](xref:System.Text.Json.Serialization.JsonConverter%601)uygulayabilirsiniz.
İşte birkaç örnek:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>`DateTime(Offset).Parse`Ve kullanma`DateTime(Offset).ToString`

Giriş <xref:System.DateTime> veya <xref:System.DateTimeOffset> metin gösterimlerinizin biçimlerini belirleyebulamıyorsanız, `DateTime(Offset).Parse` dönüştürücüyü okuma mantığınızdaki yöntemi kullanabilirsiniz. Bu, kullanmanıza olanak sağlar. <xref:System.DateTime> <xref:System.DateTimeOffset> Iso olmayan 8601 dizeleri ve genişletilmiş ISO 8601-1:2019 PROFILINE uymayan ISO 8601 biçimleri dahil olmak üzere çeşitli ve metin biçimlerini AYRıŞTıRMAK için net kapsamlı destek. Bu yaklaşım, seri hale getiricinin yerel uygulamasını kullanmaktan önemli ölçüde daha az performansız.

Serileştirme için, `DateTime(Offset).ToString` dönüştürücüyü dönüştürücü yazma mantığınızdaki ' de kullanabilirsiniz. Bu, <xref:System.DateTime> <xref:System.DateTimeOffset> [Standart Tarih ve saat biçimlerinden](../base-types/standard-date-and-time-format-strings.md)birini ve [özel tarih ve saat biçimlerini](../base-types/custom-date-and-time-format-strings.md)kullanarak yazmanızı ve değerleri yazmanızı sağlar.
Bu, serileştiricinin yerel uygulamasını kullanmaktan çok önemli ölçüde daha düşüktür.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <xref:System.Text.Json.Serialization.JsonConverter%601>, Ve olduğunda, `T` <xref:System.DateTime> `typeToConvert` parametresi her zaman olur `typeof(DateTime)` .
Parametresi, çok biçimli durumları işlemek için ve genel türler kullanılırken `typeof(T)` performanslı bir şekilde yararlanmak için yararlıdır.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><xref:System.Buffers.Text.Utf8Parser>Ve kullanma<xref:System.Buffers.Text.Utf8Formatter>

Giriş <xref:System.DateTime> veya <xref:System.DateTimeOffset> metin gösterimleriniz "R", "l", "O" veya "G" [Standart Tarih ve saat biçimi dizelerinden](../base-types/standard-date-and-time-format-strings.md)biriyle uyumluysa veya bu biçimlerden birine göre yazmak istiyorsanız, dönüştürücü mantığınızdaki hızlı UTF-8 tabanlı ayrıştırma ve biçimlendirme yöntemlerini kullanabilirsiniz. Bu, ve kullanmaktan çok daha `DateTime(Offset).Parse` hızlıdır `DateTime(Offset).ToString` .

Bu örnekte <xref:System.DateTime> [, değerleri "R" standart biçimine](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier)göre seri hale getirilen ve serileştiren özel bir dönüştürücü gösterilmektedir:

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> "R" standart biçimi her zaman 29 karakter uzunluğunda olacaktır.
>
> Yalnızca ve türleri tarafından desteklendiğinden, "l" (küçük harf "L") biçimi diğer [Standart Tarih ve saat biçimi dizeleriyle](../base-types/standard-date-and-time-format-strings.md) birlikte belgelenmemiştir `Utf8Parser` `Utf8Formatter` . Biçim, küçük harfli RFC 1123 ' dir ("R" biçiminin küçük harfli bir sürümüdür), örneğin: "Per, 25 Tem 2019 06:36:07 GMT".

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>`DateTime(Offset).Parse`Seri hale getiricinin yerel ayrıştırmaya geri dönüş olarak kullanma

Genellikle giriş <xref:System.DateTime> veya <xref:System.DateTimeOffset> VERILERINIZI genişletilmiş ISO 8601-1:2019 profiline uyacak şekilde bekleliyorsanız, serileştiricinin yerel ayrıştırma mantığını kullanabilirsiniz. Ayrıca, bir geri dönüş mekanizmasını tek bir durumda uygulayabilirsiniz.
Bu örnekte, kullanarak bir metin temsilini ayrıştırmaya başarısız olduktan sonra <xref:System.DateTime> <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)> dönüştürücünün verileri başarıyla ayrıştırır <xref:System.DateTime.Parse(System.String)> .

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

#### <a name="using-unix-epoch-date-format"></a>UNIX dönemi tarih biçimini kullanma

Aşağıdaki dönüştürücü, saat dilimi biçimiyle UNIX dönemi işler (gibi değerler `/Date(1590863400000-0700)/` ):

:::code language="csharp" source="../serialization/snippets/system-text-json-how-to-5-0/csharp/CustomConverterUnixEpochDate.cs" id="ConverterOnly":::

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>İle yazarken <xref:System.Text.Json.Utf8JsonWriter>

<xref:System.DateTime>İle özel veya metin temsili yazmak isterseniz, <xref:System.DateTimeOffset> <xref:System.Text.Json.Utf8JsonWriter> özel gösteriminizi bir,, veya olarak biçimlendirebilir, <xref:System.String> `ReadOnlySpan<Byte>` `ReadOnlySpan<Char>` <xref:System.Text.Json.JsonEncodedText> sonra bunu karşılık gelen <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> veya yöntemine geçirebilirsiniz <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> .

Aşağıdaki örnek, ile nasıl özel bir <xref:System.DateTime> biçimin oluşturulabileceğini gösterir <xref:System.DateTime.ToString(System.String,System.IFormatProvider)> ve yöntemi ile yazılır <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> :

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>İle okurken <xref:System.Text.Json.Utf8JsonReader>

<xref:System.DateTime>İle özel veya <xref:System.DateTimeOffset> metin gösterimini okumak istiyorsanız <xref:System.Text.Json.Utf8JsonReader> , geçerli JSON belirtecinin değerini bir using olarak alabilir <xref:System.String> <xref:System.Text.Json.Utf8JsonReader.GetString> ve ardından özel mantık kullanarak değeri ayrıştırın.

Aşağıdaki örnek, kullanarak bir özel <xref:System.DateTimeOffset> metin gösteriminin nasıl alınamayacağını gösterir <xref:System.Text.Json.Utf8JsonReader.GetString> ve kullanılarak ayrıştırılır <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)> :

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>System.Text.Jsüzerinde genişletilmiş ISO 8601-1:2019 profili

### <a name="date-and-time-components"></a>Tarih ve saat bileşenleri

' De uygulanan genişletilmiş ISO 8601-1:2019 profili, <xref:System.Text.Json> Tarih ve saat temsilleri için aşağıdaki bileşenleri tanımlar. Bu bileşenler, ayrıştırma ve biçimlendirme <xref:System.DateTime> ve temsiller için desteklenen çeşitli ayrıntı düzeyi düzeylerini tanımlamak için kullanılır <xref:System.DateTimeOffset> .

| Bileşen       | Biçimlendir                      | Açıklama                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Yıl            | "yyyy"                      | 0001-9999                                                                       |
| Ay           | "AA"                        | 01-12                                                                           |
| Gün             | "dd"                        | 01-28, 01-29, 01-30, 01-31, ay/yıl temelinde                                  |
| Saat            | "HH"                        | 00-23                                                                           |
| Dakika          | "mm"                        | 00-59                                                                           |
| Second          | "ss"                        | 00-59                                                                           |
| İkinci kesir | "FFFFFFF"                   | En az bir rakam, en fazla 16 basamak                                      |
| Zaman boşluğu     | "K"                         | "Z" ya da "(' + '/'-') HH ': ' mm"                                                |
| Kısmi saat    | "HH": ' mm ': ' ss [FFFFFFF] "     | UTC fark bilgisi olmayan süre                                             |
| Tam Tarih       | "yyyy'-'MM'-'dd"            | Takvim tarihi                                                                   |
| Tam zaman       | "' Kısmi time'K"           | Yerel Saat ve UTC arasında saat farkına sahip günün UTC günü veya yerel saati |
| Tarih saat       | "' Tam tarih ' 'T ' ' tam zaman '" | Takvim tarihi ve günün saati, ör. 2019-07-26T16:59:57-05:00                   |

### <a name="support-for-parsing"></a>Ayrıştırma desteği

Aşağıdaki ayrıntı düzeyi, ayrıştırma için tanımlanmıştır:

1. ' Tam tarih '
    1. "yyyy'-'MM'-'dd"

2. "' Tam tarih ' 'T ' ' saat ' ': ' ' dakika '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm"

3. "' Tam tarih ' 'T ' ' kısmi zaman '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss" ([sıralanabilir ("s") Biçim belirleyicisi](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF

4. "' Tam tarih ' 'T ' ' saat saat ' ': ' ' dakika ' ' zaman boşluğu '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mmZ"
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm (' + '/'-') HH ': ' mm"

5. ' Tarih saat '
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ"
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"
    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm"
    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm "

    Bu ayrıntı düzeyi, tarih ve saat bilgilerini karşılıklı olarak değiştiren ISO 8601 ' nin yaygın olarak benimsenen bir profili olan [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6)ile uyumludur. Ancak, System.Text.Jsuygulamadaki bazı kısıtlamalar vardır.

    - RFC 3339, en fazla kesirli saniyelik basamak belirtmez, ancak kesirli ikinci bir bölüm varsa en az bir basamağın süreyi izlemesi gerektiğini belirtir. System.Text.Jsüzerindeki uygulama 16 basamağa kadar (diğer programlama dilleri ve çerçeveleri ile birlikte çalışabilirliği desteklemek için), ancak yalnızca ilk yedi öğesini ayrıştırır. <xref:System.Text.Json.JsonException>Okurken `DateTime` ve örneklerindeki 16 ' dan fazla kesir ikinci basamak varsa, bir oluşturulur `DateTimeOffset` .
    - RFC 3339, "T" ve "Z" karakterlerinin sırasıyla "t" veya "z" olmasına izin verir, ancak uygulamaların desteği yalnızca büyük/küçük varyantlar ile sınırlı olmasına izin verir. Üzerinde System.Text.Jsuygulama için "T" ve "Z" olması gerekir. <xref:System.Text.Json.JsonException>Giriş yükleri, ve örnekleri okurken "t" veya "z" içeriyorsa bir oluşturulur `DateTime` `DateTimeOffset` .
    - RFC 3339, tarih ve saat bölümlerinin "T" ile ayrıldıklarını belirtir, ancak bunun yerine uygulamaların bunları boşlukla ("") ayırmasını sağlar. System.Text.Js, tarih ve saat bölümlerinin "T" ile ayrılması gerekir. <xref:System.Text.Json.JsonException>Giriş yükleri, ve örnekleri okurken bir boşluk ("") içeriyorsa bir oluşturulur `DateTime` `DateTimeOffset` .

Saniyeler için ondalık kesirler varsa, en az bir rakam olmalıdır; `2019-07-26T00:00:00.` izin verilmiyor.
16 ' ya kadar kesirli basamağa izin verildiğinde, yalnızca ilk yedi ayrıştırılır. Bundan sonraki bir şey sıfır olarak kabul edilir.
Örneğin, olduğu `2019-07-26T00:00:00.1234567890` gibi ayrıştırılacaktır `2019-07-26T00:00:00.1234567` .
Bu, <xref:System.DateTime> Bu çözünürlükle sınırlı olan uygulamayla uyumlu kalmasıdır.

Artık saniyeler desteklenmez.

### <a name="support-for-formatting"></a>Biçimlendirme desteği

Biçimlendirme için aşağıdaki ayrıntı düzeyi düzeyleri tanımlanmıştır:

1. "' Tam tarih ' 'T ' ' kısmi zaman '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss" ([sıralanabilir ("s") Biçim belirleyicisi](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))

        <xref:System.DateTime>Kesirli saniyeler olmadan ve hiçbir konum bilgisi olmadan biçimlendirmek için kullanılır.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF

        <xref:System.DateTime>Kesirli saniyeler ile biçimlendirmek için kullanılır, ancak bu bilgiler, konum bilgisi olmadan.

2. ' Tarih saat '
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ"

        <xref:System.DateTime>Kesirli saniyeler olmadan ancak UTC bir uzaklığa göre biçimlendirmek için kullanılır.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"

        <xref:System.DateTime>Kesirli saniye ve UTC bir uzaklığa göre biçimlendirmek için kullanılır.

    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm"

        <xref:System.DateTime> <xref:System.DateTimeOffset> Kesirli saniyeleri veya yerel bir kaydırmadan biçimlendirmek için kullanılır.

    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm "

        Bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> kesirli saniye ve yerel bir uzaklığa göre biçimlendirmek için kullanılır.

    Bu ayrıntı düzeyi, [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6)ile uyumludur.

Bir veya örneğin [gidiş dönüş biçimi](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) temsili <xref:System.DateTime> <xref:System.DateTimeOffset> Kesirli saniyeler içinde sondaki sıfırları içeriyorsa <xref:System.Text.Json.JsonSerializer> ve sonra <xref:System.Text.Json.Utf8JsonWriter> sondaki sıfırları olmadan örneğin bir gösterimini biçimlendirir.
Örneğin, <xref:System.DateTime> [gidiş dönüş biçimi](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) temsili olan bir örnek, `2019-04-24T14:50:17.1010000Z` ve olarak biçimlendirilir `2019-04-24T14:50:17.101Z` <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonWriter> .

Bir veya örneğin [gidiş dönüş biçimi](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) temsili <xref:System.DateTime> <xref:System.DateTimeOffset> kesirli saniye içinde tüm sıfırları içeriyorsa <xref:System.Text.Json.JsonSerializer> ve <xref:System.Text.Json.Utf8JsonWriter> Bu durumda örneğin bir temsilini kesirli saniye olmadan biçimlendirir.
Örneğin, <xref:System.DateTime> [gidiş dönüş biçimi](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) temsili olan bir örnek, `2019-04-24T14:50:17.0000000+02:00` ve olarak biçimlendirilir `2019-04-24T14:50:17+02:00` <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonWriter> .

Kesirli saniyelik basamakların kesilmesinin kesilmesi, yazılacak gidiş dönüş hakkındaki bilgileri korumak için gereken en küçük çıkışın yapılmasına izin verir.

En fazla 7 kesirli saniyelik basamak yazılmıştır. Bu, <xref:System.DateTime> Bu çözünürlükle sınırlı olan uygulamayla hizalanır.
