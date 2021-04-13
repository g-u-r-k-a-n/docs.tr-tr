---
title: Sürümünden Newtonsoft.Json .net 'e System.Text.Json geçiş
description: "' Den ' ye geçiş yapmayı öğrenin Newtonsoft.Json System.Text.Json . Örnek kod içerir."
author: tdykstra
ms.author: tdykstra
no-loc:
- System.Text.Json
- Newtonsoft.Json
ms.date: 12/14/2020
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 97c16d773805a0fce61fe224b6a23f1f876c2ac2
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075388"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json

Bu makalede, ' den ' e nasıl geçiş yapılacağı gösterilmektedir [Newtonsoft.Json](https://www.newtonsoft.com/json) <xref:System.Text.Json> .

`System.Text.Json`Ad alanı, JavaScript nesne gösterimi (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar. `System.Text.Json`Kitaplık [.net Core 3,1](https://dotnet.microsoft.com/download/dotnet/3.1) ve üzeri sürümler için çalışma zamanına dahildir. Diğer hedef çerçeveler için [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yükler. Paket şunları destekler:

* .NET Standard 2,0 ve sonraki sürümler
* .NET Framework 4.7.2 ve sonraki sürümler
* .NET Core 2,0, 2,1 ve 2,2

`System.Text.Json` Öncelikle performans, güvenlik ve standartlar uyumluluğuna odaklanır. Varsayılan davranışta bazı önemli farklılıklar vardır ve ile özellik eşliği yoktur `Newtonsoft.Json` . Bazı senaryolarda `System.Text.Json` yerleşik işlevselliği yoktur, ancak önerilen geçici çözümler vardır. Diğer senaryolar için geçici çözümler pratik bir şekilde yapılır. Uygulamanız eksik bir özelliğe bağımlıysa, senaryonuza yönelik desteğin eklenip eklenemediğine ulaşmak için [bir sorun](https://github.com/dotnet/runtime/issues/new) yerleştirmeyi düşünün.

Bu makalenin çoğu, API 'yi kullanma ile <xref:System.Text.Json.JsonSerializer> ilgilidir, ancak aynı zamanda <xref:System.Text.Json.JsonDocument> (belge nesne MODELI veya DOM), <xref:System.Text.Json.Utf8JsonReader> ve türlerini temsil eder <xref:System.Text.Json.Utf8JsonWriter> .

Visual Basic ' de kullanamazsınız <xref:System.Text.Json.Utf8JsonReader> , bu da özel dönüştürücüler yazamıyoruz anlamına gelir. Burada sunulan geçici çözümlerin çoğu için özel dönüştürücüler yazmanız gerekir. C# dilinde özel bir dönüştürücü yazabilir ve bunu bir Visual Basic projesine kaydedebilirsiniz. Daha fazla bilgi için bkz. [Visual Basic desteği](system-text-json-how-to.md#visual-basic-support).

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>Ve arasındaki farklar tablosu Newtonsoft.JsonSystem.Text.Json

Aşağıdaki tabloda `Newtonsoft.Json` Özellikler ve eşdeğerleri listelenmektedir `System.Text.Json` . Eşdeğerleri aşağıdaki kategorilere ayrılır:

* Yerleşik işlevsellik tarafından desteklenir. Benzer davranış alma `System.Text.Json` , bir öznitelik veya genel seçenek kullanımını gerektirebilir.
* Desteklenmez, geçici çözüm mümkündür. Geçici çözümler, işlevlerle tamamen eşlik sağlamayan [özel dönüştürücülerdir](system-text-json-converters-how-to.md) `Newtonsoft.Json` . Bunlardan bazılarının örnek kodu örnek olarak verilmiştir. Bu özelliklerden yararlandıysanız `Newtonsoft.Json` geçiş, .NET nesne modellerinizde veya diğer kod değişikliklerinde değişiklik yapılmasını gerektirir.
* Desteklenmez, geçici çözüm pratik veya mümkün değildir. Bu özelliklerden yararlandıysanız `Newtonsoft.Json` geçiş önemli değişiklikler yapılmadan mümkün olmayacaktır.

::: zone pivot="dotnet-5-0"

| Newtonsoft.Json özelliği                               | System.Text.Json değerinin |
|-------------------------------------------------------|-----------------------------|
| Varsayılan olarak büyük/küçük harfe duyarsız seri hale           | ✔️ [Propertynamecaseduyarsız genel ayarı](#case-insensitive-deserialization) |
| Camel-Case Özellik adları                             | ✔️ [Propertynamingpolicy genel ayarı](system-text-json-customize-properties.md#use-camel-case-for-all-json-property-names) |
| En az karakter kaçış                            | ✔️ [katı karakter kaçış, yapılandırılabilir](#minimal-character-escaping) |
| `NullValueHandling.Ignore` Genel ayar             | ✔️ [DefaultIgnoreCondition genel seçeneği](system-text-json-ignore-properties.md#ignore-all-null-value-properties) |[Özelliği koşullu olarak Yoksay](#conditionally-ignore-a-property)
| Açıklamalara izin ver                                        | ✔️ [ReadCommentHandling genel ayarı](#comments) |
| Sondaki virgüllerin kullanılmasına izin ver                                 | ✔️ [Allowtrailingvirgüller genel ayarı](#trailing-commas) |
| Özel dönüştürücü kaydı                         | ✔️ [öncelik sırası farklı](#converter-registration-precedence) |
| Varsayılan olarak en fazla derinlik yok                           | ✔️ [varsayılan en yüksek derinlik 64, yapılandırılabilir](#maximum-depth) |
| `PreserveReferencesHandling` Genel ayar           | ✔️ [Referencehandling genel ayarı](#preserve-object-references-and-handle-loops) |
| Tırnak işaretleri içindeki sayıları seri hale getirme veya serisini kaldırma            | ✔️ [numberhandling genel ayarı, [JsonNumberHandling] özniteliği](#allow-or-write-numbers-in-quotes) |
| Sabit sınıflar ve yapılar için seri durumdan çıkarma          | ✔️ [Jsonconstructor, C# 9 kayıtları](#deserialize-to-immutable-classes-and-structs) |
| Alanlar için destek                                    | ✔️ [ıncludefields genel ayarı, [Jsonınclude] özniteliği](#public-and-non-public-fields) |
| `DefaultValueHandling` Genel ayar                 | ✔️ [DefaultIgnoreCondition genel ayarı](#conditionally-ignore-a-property) |
| `NullValueHandling` ayar açık `[JsonProperty]`       | ✔️ [Jsonıgnore özniteliği](#conditionally-ignore-a-property)  |
| `DefaultValueHandling` ayar açık `[JsonProperty]`    | ✔️ [Jsonıgnore özniteliği](#conditionally-ignore-a-property)  |
| `Dictionary`Dize olmayan anahtarla seri durumdan çıkarma          | ✔️ [destekleniyor](#dictionary-with-non-string-key) |
| Ortak olmayan özellik ayarlayıcıları ve alıcılar için destek   | ✔️ [Jsonınclude özniteliği](#non-public-property-setters-and-getters) |
| `[JsonConstructor]` özniteliği                         | ✔️ [[Jsonconstructor] özniteliği](#specify-constructor-to-use-when-deserializing) |
| Geniş kapsamlı türler için destek                    | ⚠️[Bazı türler için özel dönüştürücüler gerekir](#types-without-built-in-support) |
| Polimorfik serileştirme                             | ⚠️[Desteklenmez, geçici çözüm, örnek](#polymorphic-serialization) |
| Polimorfik seri kaldırma                           | ⚠️[Desteklenmez, geçici çözüm, örnek](#polymorphic-deserialization) |
| Çıkarılan türden özellikleri seri durumdan çıkar `object`      | ⚠️[Desteklenmez, geçici çözüm, örnek](#deserialization-of-object-properties) |
| JSON `null` sabit değerinin null yapılamayan değer türlerine serisini kaldırma | ⚠️[Desteklenmez, geçici çözüm, örnek](#deserialize-null-to-non-nullable-type) |
| `Required`özniteliği üzerinde ayarlama `[JsonProperty]`        | ⚠️[Desteklenmez, geçici çözüm, örnek](#required-properties) |
| `DefaultContractResolver` özellikleri yoksaymak için       | ⚠️[Desteklenmez, geçici çözüm, örnek](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` Ayarlar   | ⚠️[Desteklenmez, geçici çözüm, örnek](#specify-date-format) |
| Geri Çağırmalar                                             | ⚠️[Desteklenmez, geçici çözüm, örnek](#callbacks) |
| `JsonConvert.PopulateObject` yöntemi                   | ⚠️[Desteklenmez, geçici çözüm](#populate-existing-objects) |
| `ObjectCreationHandling` Genel ayar               | ⚠️[Desteklenmez, geçici çözüm](#reuse-rather-than-replace-properties) |
| Ayarlayıcısız koleksiyonlara Ekle                    | ⚠️[Desteklenmez, geçici çözüm](#add-to-collections-without-setters) |
| `ReferenceLoopHandling` Genel ayar                | ❌ [Desteklenmez](#preserve-object-references-and-handle-loops) |
| Öznitelikler için destek `System.Runtime.Serialization` | ❌ [Desteklenmez](#systemruntimeserialization-attributes) |
| `MissingMemberHandling` Genel ayar                | ❌ [Desteklenmez](#missingmemberhandling) |
| Tırnak işaretleri olmadan özellik adlarına izin ver                   | ❌ [Desteklenmez](#json-strings-property-names-and-string-values) |
| Dize değerlerinin çevresinde tek tırnak işaretlerine izin ver              | ❌ [Desteklenmez](#json-strings-property-names-and-string-values) |
| Dize özellikleri için dize olmayan JSON değerlerine izin ver    | ❌ [Desteklenmez](#non-string-values-for-string-properties) |
| `TypeNameHandling.All` Genel ayar                 | ❌ [Desteklenmez](#typenamehandlingall-not-supported) |
::: zone-end

::: zone pivot="dotnet-core-3-1"

| Newtonsoft.Json özelliği                               | System.Text.Json değerinin |
|-------------------------------------------------------|-----------------------------|
| Varsayılan olarak büyük/küçük harfe duyarsız seri hale           | ✔️ [Propertynamecaseduyarsız genel ayarı](#case-insensitive-deserialization) |
| Camel-Case Özellik adları                             | ✔️ [Propertynamingpolicy genel ayarı](system-text-json-customize-properties.md#use-camel-case-for-all-json-property-names) |
| En az karakter kaçış                            | ✔️ [katı karakter kaçış, yapılandırılabilir](#minimal-character-escaping) |
| `NullValueHandling.Ignore` Genel ayar             | ✔️ [ıgnorenullvalues genel seçeneği](system-text-json-ignore-properties.md#ignore-all-null-value-properties) |
| Açıklamalara izin ver                                        | ✔️ [ReadCommentHandling genel ayarı](#comments) |
| Sondaki virgüllerin kullanılmasına izin ver                                 | ✔️ [Allowtrailingvirgüller genel ayarı](#trailing-commas) |
| Özel dönüştürücü kaydı                         | ✔️ [öncelik sırası farklı](#converter-registration-precedence) |
| Varsayılan olarak en fazla derinlik yok                           | ✔️ [varsayılan en yüksek derinlik 64, yapılandırılabilir](#maximum-depth) |
| Geniş kapsamlı türler için destek                    | ⚠️[Bazı türler için özel dönüştürücüler gerekir](#types-without-built-in-support) |
| Dizeleri sayı olarak seri durumdan çıkarma                        | ⚠️[Desteklenmez, geçici çözüm, örnek](#allow-or-write-numbers-in-quotes) |
| `Dictionary`Dize olmayan anahtarla seri durumdan çıkarma          | ⚠️[Desteklenmez, geçici çözüm, örnek](#dictionary-with-non-string-key) |
| Polimorfik serileştirme                             | ⚠️[Desteklenmez, geçici çözüm, örnek](#polymorphic-serialization) |
| Polimorfik seri kaldırma                           | ⚠️[Desteklenmez, geçici çözüm, örnek](#polymorphic-deserialization) |
| Çıkarılan türden özellikleri seri durumdan çıkar `object`      | ⚠️[Desteklenmez, geçici çözüm, örnek](#deserialization-of-object-properties) |
| JSON `null` sabit değerinin null yapılamayan değer türlerine serisini kaldırma | ⚠️[Desteklenmez, geçici çözüm, örnek](#deserialize-null-to-non-nullable-type) |
| Sabit sınıflar ve yapılar için seri durumdan çıkarma          | ⚠️[Desteklenmez, geçici çözüm, örnek](#deserialize-to-immutable-classes-and-structs) |
| `[JsonConstructor]` özniteliği                         | ⚠️[Desteklenmez, geçici çözüm, örnek](#specify-constructor-to-use-when-deserializing) |
| `Required`özniteliği üzerinde ayarlama `[JsonProperty]`        | ⚠️[Desteklenmez, geçici çözüm, örnek](#required-properties) |
| `NullValueHandling`özniteliği üzerinde ayarlama `[JsonProperty]` | ⚠️[Desteklenmez, geçici çözüm, örnek](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`özniteliği üzerinde ayarlama `[JsonProperty]` | ⚠️[Desteklenmez, geçici çözüm, örnek](#conditionally-ignore-a-property)  |
| `DefaultValueHandling` Genel ayar                 | ⚠️[Desteklenmez, geçici çözüm, örnek](#conditionally-ignore-a-property) |
| `DefaultContractResolver` özellikleri yoksaymak için       | ⚠️[Desteklenmez, geçici çözüm, örnek](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` Ayarlar   | ⚠️[Desteklenmez, geçici çözüm, örnek](#specify-date-format) |
| Geri Çağırmalar                                             | ⚠️[Desteklenmez, geçici çözüm, örnek](#callbacks) |
| Ortak ve genel olmayan alanlar için destek              | ⚠️[Desteklenmez, geçici çözüm](#public-and-non-public-fields) |
| Ortak olmayan özellik ayarlayıcıları ve alıcılar için destek   | ⚠️[Desteklenmez, geçici çözüm](#non-public-property-setters-and-getters) |
| `JsonConvert.PopulateObject` yöntemi                   | ⚠️[Desteklenmez, geçici çözüm](#populate-existing-objects) |
| `ObjectCreationHandling` Genel ayar               | ⚠️[Desteklenmez, geçici çözüm](#reuse-rather-than-replace-properties) |
| Ayarlayıcısız koleksiyonlara Ekle                    | ⚠️[Desteklenmez, geçici çözüm](#add-to-collections-without-setters) |
| `PreserveReferencesHandling` Genel ayar           | ❌ [Desteklenmez](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling` Genel ayar                | ❌ [Desteklenmez](#preserve-object-references-and-handle-loops) |
| Öznitelikler için destek `System.Runtime.Serialization` | ❌ [Desteklenmez](#systemruntimeserialization-attributes) |
| `MissingMemberHandling` Genel ayar                | ❌ [Desteklenmez](#missingmemberhandling) |
| Tırnak işaretleri olmadan özellik adlarına izin ver                   | ❌ [Desteklenmez](#json-strings-property-names-and-string-values) |
| Dize değerlerinin çevresinde tek tırnak işaretlerine izin ver              | ❌ [Desteklenmez](#json-strings-property-names-and-string-values) |
| Dize özellikleri için dize olmayan JSON değerlerine izin ver    | ❌ [Desteklenmez](#non-string-values-for-string-properties) |
| `TypeNameHandling.All` Genel ayar                 | ❌ [Desteklenmez](#typenamehandlingall-not-supported) |
::: zone-end

Bu, özelliklerin kapsamlı bir listesi değildir `Newtonsoft.Json` . Listede, [GitHub sorunları](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) veya [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) gönderileri için istenen birçok senaryo bulunur. Burada listelenen senaryolardan biri için şu anda örnek kodu olmayan bir geçici çözüm uygularsanız ve çözümünüzü paylaşmak istiyorsanız, bu sayfanın altındaki **geri bildirim** bölümünde **Bu sayfayı** seçin. Bu, bu belgenin GitHub deposunda bir sorun oluşturur ve bu sayfadaki **geri bildirim** bölümünde de listeler.

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Varsayılan JsonSerializer davranışındaki farklılıklar Newtonsoft.Json

<xref:System.Text.Json> Varsayılan olarak katı olur ve arayan adına tahmin veya yorumlamayı önler, belirleyici davranışı vurgulayarak. Kitaplık, performans ve güvenlik için kasıtlı olarak bu şekilde tasarlanmıştır. `Newtonsoft.Json` Varsayılan olarak esnektir. Tasarımda bu temel fark, varsayılan davranıştaki aşağıdaki belirli farklılıklardan birçoğın arkasında bulunur.

### <a name="case-insensitive-deserialization"></a>Büyük/küçük harfe duyarsız seri hale

Seri durumdan çıkarma sırasında, `Newtonsoft.Json` Varsayılan olarak büyük/küçük harfe duyarsız Özellik adı eşleştirmeyi yapar. <xref:System.Text.Json>Varsayılan değer büyük/küçük harfe duyarlıdır ve tam bir eşleşme yaptığından daha iyi performans sağlar. Büyük/küçük harfe duyarsız eşleşme yapma hakkında daha fazla bilgi için bkz. [büyük/küçük harfe duyarsız Özellik eşleştirme](system-text-json-character-casing.md).

`System.Text.Json`ASP.NET Core kullanarak dolaylı olarak kullanıyorsanız, gibi davranışları almak için herhangi bir şey yapmanız gerekmez `Newtonsoft.Json` . ASP.NET Core, kullandığı [Camel özellik adlarına](system-text-json-customize-properties.md#use-camel-case-for-all-json-property-names) ve büyük/küçük harfe duyarsız eşleştirmeye yönelik ayarları belirtir `System.Text.Json` .

::: zone pivot="dotnet-5-0"
ASP.NET Core Ayrıca, [alıntılanmış sayıların](#allow-or-write-numbers-in-quotes) varsayılan olarak serisini kaldırmada de etkinleştirilir.
::: zone-end

### <a name="minimal-character-escaping"></a>En az karakter kaçış

Serileştirme sırasında, `Newtonsoft.Json` karakterlerin kaçış olmadan üzerinden izin verme konusunda görece bir şekilde izin verilir. Diğer bir deyişle, bunları `\uxxxx` `xxxx` karakterin kod noktası olduğu yerde değiştirmez. Burada kaçış yaptığı yerlerde, `\` karakterden önce bir (örneğin, `"` olur) bir olarak yayarak bunu yapar `\"` . <xref:System.Text.Json> siteler arası betik (XSS) veya bilgi açıklama saldırılarına karşı derinlemesine savunma korumaları sağlamak için varsayılan olarak daha fazla karakter çıkar ve altı karakterli sırayı kullanarak bu şekilde yapılır. `System.Text.Json` ASCII olmayan tüm karakterleri varsayılan olarak çıkar, bu nedenle içinde kullanıyorsanız herhangi bir şey yapmanız gerekmez `StringEscapeHandling.EscapeNonAscii` `Newtonsoft.Json` . `System.Text.Json` Ayrıca, varsayılan olarak HTML duyarlı karakterleri de çıkar. Varsayılan davranışı geçersiz kılma hakkında daha fazla bilgi için `System.Text.Json` bkz. [karakter kodlamasını özelleştirme](system-text-json-character-encoding.md).

### <a name="comments"></a>Yorumlar

Seri durumdan çıkarma sırasında, `Newtonsoft.Json` Varsayılan olarak JSON 'daki açıklamaları yoksayar. <xref:System.Text.Json> [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtiminde bunları içermediğinden, açıklamalar için özel durumlar oluşturmak varsayılan değer. Açıklamalara izin verme hakkında daha fazla bilgi için bkz. [yorumlara Izin verme ve sondaki virgüller](system-text-json-invalid-json.md).

### <a name="trailing-commas"></a>Sondaki virgüller

Seri durumdan çıkarma sırasında, `Newtonsoft.Json` Varsayılan olarak sondaki virgüllerin yok sayılır. Ayrıca, birden çok sondaki virgül yoksayar (örneğin, `[{"Color":"Red"},{"Color":"Green"},,]` ). Varsayılan olarak, <xref:System.Text.Json> [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi bunlara izin vermediğinden, sondaki virgüller için özel durumlar throw. Bunları kabul etme hakkında daha fazla bilgi için `System.Text.Json` bkz. [yorumlara izin verme ve sondaki virgüller](system-text-json-invalid-json.md). Birden çok bitiş virgülne izin vermenin bir yolu yoktur.

### <a name="converter-registration-precedence"></a>Dönüştürücü kayıt önceliği

`Newtonsoft.Json`Özel dönüştürücüler için kayıt önceliği aşağıdaki gibidir:

* Özelliğindeki öznitelik
* Türündeki öznitelik
* [Dönüştürücüler](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm) koleksiyonu

Bu sıra, koleksiyondaki bir özel dönüştürücünün `Converters` tür düzeyinde bir öznitelik uygulanarak kaydedilen bir dönüştürücü tarafından geçersiz kılındığı anlamına gelir. Bu kayıtların her ikisi de özellik düzeyindeki bir öznitelik tarafından geçersiz kılınır.

<xref:System.Text.Json>Özel dönüştürücüler için kayıt önceliği farklıdır:

* Özelliğindeki öznitelik
* <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyon
* Türündeki öznitelik

Buradaki fark, koleksiyondaki özel dönüştürücünün `Converters` tür düzeyinde bir özniteliği geçersiz kılmanızdır. Bu öncelik sırasının arkasındaki amaç, çalışma zamanı değişikliklerinin tasarım zamanı seçimlerini geçersiz kılmasını sağlamak olacaktır. Önceliği değiştirme yolu yoktur.

Özel dönüştürücü kaydı hakkında daha fazla bilgi için bkz. [özel dönüştürücüyü kaydetme](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="maximum-depth"></a>En yüksek derinlik

`Newtonsoft.Json` Varsayılan olarak en yüksek derinlik sınırına sahip değildir. <xref:System.Text.Json>Varsayılan 64 için bir sınır vardır ve bu ayar tarafından yapılandırılabilir <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType> .

`System.Text.Json`ASP.NET Core kullanarak dolaylı olarak kullanıyorsanız, varsayılan derinlik üst sınırı 32 ' dir. Varsayılan değer model bağlama ile aynıdır ve [Jsonoptions sınıfında](https://github.com/dotnet/aspnetcore/blob/1f56888ea03f6a113587a6c4ac4d8b2ded326ffa/src/Mvc/Mvc.Core/src/JsonOptions.cs#L17-L20)ayarlanır.

### <a name="json-strings-property-names-and-string-values"></a>JSON dizeleri (özellik adları ve dize değerleri)

Seri durumdan çıkarma sırasında, `Newtonsoft.Json` çift tırnak, tek tırnak veya tırnak işaretleri olmadan çevrelenmiş özellik adlarını kabul eder. Çift tırnak veya tek tırnak işareti içine alınmış dize değerlerini kabul eder. Örneğin, `Newtonsoft.Json` AŞAĞıDAKI JSON 'yi kabul eder:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json` yalnızca çift tırnak içindeki özellik adlarını ve dize değerlerini kabul eder çünkü bu biçim, [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi için gereklidir ve geçerli JSON olarak kabul edilen tek biçimdir.

Tek tırnak içine alınmış bir değer, aşağıdaki iletiyle birlikte bir [Jsonexception](xref:System.Text.Json.JsonException) ile sonuçlanır:

```output
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Dize özellikleri için dize olmayan değerler

`Newtonsoft.Json` sayı veya sabit değerler gibi dize olmayan değerleri kabul eder `true` ve `false` tür dizesinin özelliklerine seri durumdan çıkarmak için. Aşağıdaki sınıfa başarıyla seri hale getirilen bir JSON örneği aşağıda verilmiştir `Newtonsoft.Json` :

```json
{
  "String1": 1,
  "String2": true,
  "String3": false
}
```

```csharp
public class ExampleClass
{
    public string String1 { get; set; }
    public string String2 { get; set; }
    public string String3 { get; set; }
}
```

`System.Text.Json` dize olmayan değerlerin dize özelliklerine serileştirmez. Bir dize alanı için alınan dize olmayan bir değer, aşağıdaki iletiyle birlikte bir [Jsonexception](xref:System.Text.Json.JsonException) ile sonuçlanır:

```output
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer"></a>JsonSerializer kullanan senaryolar

Aşağıdaki senaryolardan bazıları yerleşik işlevsellik tarafından desteklenmez, ancak geçici çözümler olasıdır. Geçici çözümler, işlevlerle tamamen eşlik sağlamayan [özel dönüştürücülerdir](system-text-json-converters-how-to.md) `Newtonsoft.Json` . Bunlardan bazılarının örnek kodu örnek olarak verilmiştir. Bu özelliklerden yararlandıysanız `Newtonsoft.Json` geçiş, .NET nesne modellerinizde veya diğer kod değişikliklerinde değişiklik yapılmasını gerektirir.

Aşağıdaki senaryolardan bazıları için geçici çözümler pratik veya mümkün değildir. Bu özelliklerden yararlandıysanız `Newtonsoft.Json` geçiş önemli değişiklikler yapılmadan mümkün olmayacaktır.

### <a name="allow-or-write-numbers-in-quotes"></a>Tırnak işaretleri halinde izin ver veya yaz

::: zone pivot="dotnet-5-0"
`Newtonsoft.Json` JSON dizeleri (tırnak içine alınmış) tarafından temsil edilen sayıları seri hale getirme veya seri durumdan çıkarma. Örneğin, yerine şunları kabul edebilir: `{"DegreesCelsius":"23"}` `{"DegreesCelsius":23}` . İçindeki bu davranışı etkinleştirmek için <xref:System.Text.Json> , <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> veya olarak <xref:System.Text.Json.Serialization.JsonNumberHandling.WriteAsString> ayarlayın <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString> veya [[jsonnumberhandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) özniteliğini kullanın.

`System.Text.Json`ASP.NET Core kullanarak dolaylı olarak kullanıyorsanız, gibi davranışları almak için herhangi bir şey yapmanız gerekmez `Newtonsoft.Json` . ASP.NET Core [Web varsayılanlarını](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) kullandığında `System.Text.Json` , Web Varsayılanları tırnak içine alınmış sayılara izin verir.

Daha fazla bilgi için bkz. [tekliflere Izin verme veya yazma numaraları](system-text-json-invalid-json.md).
::: zone-end

::: zone pivot="dotnet-core-3-1"
`Newtonsoft.Json` JSON dizeleri (tırnak içine alınmış) tarafından temsil edilen sayıları seri hale getirme veya seri durumdan çıkarma. Örneğin, yerine şunları kabul edebilir: `{"DegreesCelsius":"23"}` `{"DegreesCelsius":23}` . .NET Core 3,1 ' de bu davranışı etkinleştirmek için <xref:System.Text.Json> , aşağıdaki örnekte olduğu gibi özel bir dönüştürücü uygulayın. Dönüştürücü şu şekilde tanımlanan özellikleri işler `long` :

* Onları JSON dizeleri olarak serileştirir.
* Seri durumdan çıkarılırken, tırnak içindeki JSON numaralarını ve sayıları kabul eder.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/LongToStringConverter.cs":::

Tek tek özelliklerde [bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) `long` veya [çeviriciyi koleksiyona ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) bu özel dönüştürücüyü kaydettirin <xref:System.Text.Json.JsonSerializerOptions.Converters> .
::: zone-end

### <a name="specify-constructor-to-use-when-deserializing"></a>Seri durumdan çıkarılırken kullanılacak oluşturucuyu belirtin

`Newtonsoft.Json` `[JsonConstructor]` Özniteliği bir poco 'ya seri durumdan çıkarılırken hangi oluşturucunun çağrılacağını belirtmenizi sağlar.

::: zone pivot="dotnet-5-0"
`System.Text.Json` Ayrıca bir [[Jsonconstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) özniteliğine sahiptir. Daha fazla bilgi için bkz. [Sabit türler ve kayıtlar](system-text-json-immutability.md).
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> .NET Core 3,1 'de yalnızca parametresiz oluşturucular desteklenir. Geçici bir çözüm olarak, özel bir dönüştürücüde hangi oluşturucuyu ihtiyacınız olduğunu çağırabilirsiniz. [Sabit sınıflar ve yapılar Için seri durumdan çıkarma](#deserialize-to-immutable-classes-and-structs)örneğine bakın.
::: zone-end

### <a name="conditionally-ignore-a-property"></a>Özelliği koşullu olarak Yoksay

`Newtonsoft.Json` serileştirme veya seri durumdan çıkarma için bir özelliği koşullu olarak yoksaymanın birkaç yolu vardır:

* `DefaultContractResolver` Rastgele ölçütlere göre dahil edilecek veya yoksayılacak özellikleri seçmenizi sağlar.
* `NullValueHandling`Ve `DefaultValueHandling` ayarları, `JsonSerializerSettings` tüm null değer veya varsayılan değer özelliklerinin yoksayılmasını belirtmenize izin verir.
* `NullValueHandling` `DefaultValueHandling` Öznitelikteki ve ayarları, `[JsonProperty]` null veya varsayılan değer olarak ayarlandığında yoksayılacak tek tek özellikleri belirtmenize izin verir.

::: zone pivot="dotnet-5-0"

<xref:System.Text.Json> serileştirilirken özellikleri veya alanları yoksaymak için aşağıdaki yolları sağlar:

* Bir özellikte [[Jsonıgnore]](system-text-json-ignore-properties.md#ignore-individual-properties) özniteliği, serileştirme SıRASıNDA özelliğin JSON 'dan atlanmasına neden olur.
* [Ignorereadonlyproperties](system-text-json-ignore-properties.md#ignore-all-read-only-properties) genel seçeneği, tüm salt okuma özelliklerini yoksaymanıza imkan tanır.
* [Alanlar dahil](system-text-json-how-to.md#include-fields)ediyorsanız, <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> genel seçeneği tüm salt okuma alanlarını yoksaymanıza izin verir.
* `DefaultIgnoreCondition`Genel seçeneği, [varsayılan değerlere sahip tüm değer türü özelliklerini yoksaymanıza](system-text-json-ignore-properties.md#ignore-all-default-value-properties)veya [null değere sahip tüm başvuru türü özelliklerini yoksaymanıza](system-text-json-ignore-properties.md#ignore-all-null-value-properties)olanak sağlar.

::: zone-end

::: zone pivot="dotnet-core-3-1"

<xref:System.Text.Json> .NET Core 3,1, serileştirme sırasında özellikleri yoksaymak için aşağıdaki yolları sağlar:

* Bir özellikte [[Jsonıgnore]](system-text-json-ignore-properties.md#ignore-individual-properties) özniteliği, serileştirme SıRASıNDA özelliğin JSON 'dan atlanmasına neden olur.
* [Ignorenullvalues](system-text-json-ignore-properties.md#ignore-all-null-value-properties) genel seçeneği, tüm null değer özelliklerini yoksaymanıza imkan tanır.
* [Ignorereadonlyproperties](system-text-json-ignore-properties.md#ignore-all-read-only-properties) genel seçeneği, tüm salt okuma özelliklerini yoksaymanıza imkan tanır.
::: zone-end

Bu seçenekler **şunları yapmanızı sağlar** :

::: zone pivot="dotnet-5-0"

* Çalışma zamanında değerlendirilen rastgele ölçütlere göre seçili özellikleri yoksayın.

::: zone-end

::: zone pivot="dotnet-core-3-1"

* Türü için varsayılan değere sahip tüm özellikleri yoksayın.
* Türü için varsayılan değere sahip seçili özellikleri yoksayın.
* Değerleri null ise seçili özellikleri yoksayın.
* Çalışma zamanında değerlendirilen rastgele ölçütlere göre seçili özellikleri yoksayın.

::: zone-end

Bu işlevsellik için özel bir dönüştürücü yazabilirsiniz. İşte bu yaklaşımı gösteren örnek bir POCO ve özel dönüştürücü.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecastRuntimeIgnoreConverter.cs":::

Dönüştürücü, `Summary` değeri null, boş bir dize veya "N/A" ise, özelliğin Serileştirmeden atlanmasına neden olur.

Bu özel dönüştürücüyü [sınıfında bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya [dönüştürücüyü koleksiyona ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydedin <xref:System.Text.Json.JsonSerializerOptions.Converters> .

Bu yaklaşım aşağıdaki durumlarda ek mantık gerektirir:

* POCO, karmaşık özellikler içerir.
* Gibi öznitelikleri `[JsonIgnore]` veya özel kodlayıcılar gibi seçenekleri işlemeniz gerekir.

### <a name="public-and-non-public-fields"></a>Ortak ve genel olmayan alanlar

`Newtonsoft.Json` alanları seri hale getirmek ve seri durumdan çıkarmak için özellikleri.

::: zone pivot="dotnet-5-0"
İçinde <xref:System.Text.Json> , <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> serileştirme veya seri durumdan çıkarma sırasında ortak alanları dahil etmek için genel ayarını veya [[jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın. Bir örnek için bkz. [içerme alanları](system-text-json-how-to.md#include-fields).
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> .NET Core 3,1 ' de yalnızca ortak özelliklerle birlikte kullanılabilir. Özel dönüştürücüler, bu işlevselliği sağlayabilir.
::: zone-end

### <a name="preserve-object-references-and-handle-loops"></a>Nesne başvurularını koruma ve döngüleri işleme

Varsayılan olarak, `Newtonsoft.Json` değere göre serileştirir. Örneğin, bir nesne aynı nesneye bir başvuru içeren iki özellik içeriyorsa `Person` , bu `Person` nesnenin ÖZELLIKLERININ değerleri JSON içinde yinelenir.

`Newtonsoft.Json` , `PreserveReferencesHandling` `JsonSerializerSettings` başvuruya göre serileştirmenize olanak sağlayan üzerinde bir ayarı vardır:

* İlk nesne için oluşturulan JSON 'a bir tanımlayıcı meta verileri eklenir `Person` .
* İkinci nesne için oluşturulan JSON, `Person` özellik değerleri yerine bu tanımlayıcıya bir başvuru içerir.

`Newtonsoft.Json` Ayrıca, `ReferenceLoopHandling` bir özel durum oluşturmak yerine döngüsel başvuruları yoksaymanıza imkan tanıyan bir ayara sahiptir.

::: zone pivot="dotnet-5-0"
Başvuruları korumak ve ' de döngüsel başvuruları işlemek için <xref:System.Text.Json> , <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A?displayProperty=nameWithType> olarak ayarlayın <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> . `ReferenceHandler.Preserve`Ayarı, ile eşdeğerdir `PreserveReferencesHandling`  =  `PreserveReferencesHandling.All` `Newtonsoft.Json` .

Newtonsoft.Json [ReferenceResolver](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializer_ReferenceResolver.htm)gibi, <xref:System.Text.Json.Serialization.ReferenceResolver?displayProperty=fullName> sınıfı serileştirme ve seri durumundan çıkarma için başvuruları koruma davranışını tanımlar. Özel davranışı belirtmek için türetilmiş bir sınıf oluşturun. Bir örnek için bkz. [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).

Bazı ilgili `Newtonsoft.Json` özellikler desteklenmez:

* [JsonPropertyAttribute. IsReference](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonPropertyAttribute_IsReference.htm)
* [JsonPropertyAttribute. ReferenceLoopHandling](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonPropertyAttribute_ReferenceLoopHandling.htm)
* [JsonSerializerSettings. ReferenceLoopHandling](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_ReferenceLoopHandling.htm)

Daha fazla bilgi için bkz. [başvuruları koruma ve döngüsel başvuruları işleme](system-text-json-preserve-references.md).
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> .NET Core 3,1 yalnızca değere göre serileştirme destekler ve döngüsel başvurular için bir özel durum oluşturur.
::: zone-end

### <a name="dictionary-with-non-string-key"></a>Dize olmayan anahtarla sözlük

::: zone pivot="dotnet-5-0"
Hem hem de `Newtonsoft.Json` `System.Text.Json` türündeki koleksiyonları destekler `Dictionary<TKey, TValue>` . Ancak, içinde `System.Text.Json` , `TKey` özel bir tür değil, temel bir tür olmalıdır. Daha fazla bilgi için bkz. [desteklenen anahtar türleri](system-text-json-supported-collection-types.md#supported-key-types).

> [!CAUTION]
> Bir WHERE 'nin seri durumundan çıkarma, `Dictionary<TKey, TValue>` `TKey` `string` tüketen uygulamada bir güvenlik açığı ortaya çıkarabilir. Daha fazla bilgi için bkz. [DotNet/Runtime # 4761](https://github.com/dotnet/runtime/issues/4761).

::: zone-end

::: zone pivot="dotnet-core-3-1"
`Newtonsoft.Json` türündeki koleksiyonları destekler `Dictionary<TKey, TValue>` . .NET Core 3,1 ' deki sözlük koleksiyonları için yerleşik destek <xref:System.Text.Json> ile sınırlıdır `Dictionary<string, TValue>` . Diğer bir deyişle, anahtar bir dize olmalıdır.

.NET Core 3,1 ' deki anahtar olarak tamsayı veya diğer tür içeren bir sözlüğü desteklemek için, [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)bölümünde örnek gibi bir dönüştürücü oluşturun.
::: zone-end

### <a name="types-without-built-in-support"></a>Yerleşik destek olmadan türler

<xref:System.Text.Json> , aşağıdaki türler için yerleşik destek sağlamaz:

* <xref:System.Data.DataTable> ve ilgili türler
::: zone pivot="dotnet-5-0"
* [Ayırt edici birleşimler](../../fsharp/language-reference/discriminated-unions.md)gibi F # türleri. [Kayıt türleri](../../fsharp/language-reference/records.md) ve [anonim kayıt türleri](../../fsharp/language-reference/anonymous-records.md) , sabit bir Pocos olarak değerlendirilir ve bu nedenle desteklenir.
::: zone-end
::: zone pivot="dotnet-core-3-1"
* [Ayırt edici birleşimler](../../fsharp/language-reference/discriminated-unions.md), [kayıt türleri](../../fsharp/language-reference/records.md)ve [anonim kayıt türleri](../../fsharp/language-reference/anonymous-records.md)gibi F # türleri.
::: zone-end
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple> ve ilişkili genel türleri

Özel dönüştürücüler, yerleşik desteği olmayan türler için uygulanabilir.

### <a name="polymorphic-serialization"></a>Polimorfik serileştirme

`Newtonsoft.Json` otomatik olarak polimorfik serileştirme yapar. ' Nin sınırlı çok biçimli serileştirme özellikleri hakkında daha fazla bilgi için <xref:System.Text.Json> bkz. [türetilmiş sınıfların serileştirme özellikleri](system-text-json-polymorphism.md).

Açıklanan geçici çözüm, türü olarak türetilmiş sınıflar içerebilen özellikleri tanımlamaktır `object` . Bu mümkün değilse, diğer bir seçenek de `Write` [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#support-polymorphic-deserialization)içindeki örnek gibi tüm devralma türü hiyerarşisi için bir yöntemle dönüştürücü oluşturmaktır.

### <a name="polymorphic-deserialization"></a>Polimorfik seri kaldırma

`Newtonsoft.Json``TypeNameHandling`serileştirme SıRASıNDA JSON 'a tür adı meta verileri ekleyen bir ayara sahiptir. Seri durumdan çıkarma sırasında çok biçimli seri kaldırma işlemi yaparken meta verileri kullanır. <xref:System.Text.Json> çok sayıda [polimorfik serileştirme](system-text-json-polymorphism.md) , ancak polimorfik seri hale getirme işlemi yapabilir.

Polimorfik serisini desteklemek için [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#support-polymorphic-deserialization)bölümünde örnek gibi bir dönüştürücü oluşturun.

### <a name="deserialization-of-object-properties"></a>Nesne özelliklerinin serisini kaldırma

`Newtonsoft.Json`Seri <xref:System.Object> hale geldiğinde:

* , JSON yükünde (dışındaki) ilkel değerlerin türünü `null` ve depolanan `string` , `long` , `double` , `boolean` veya `DateTime` paketlenmiş nesne olarak döndürür. *İlkel değerler* , JSON numarası, dize,, veya gıbı tek JSON değerleridir `true` `false` `null` .
* `JObject` `JArray` JSON yükünde karmaşık değerler için bir veya döndürür. *Karmaşık değerler* , küme ayracı () içinde JSON anahtar-değer çiftleri `{}` veya köşeli ayraç () içindeki değer listelerinde yer alan koleksiyonlardır `[]` . Küme ayraçları ve köşeli ayraçlar içindeki Özellikler ve değerler ek özelliklere veya değerlere sahip olabilir.
* Yükün JSON sabit değeri olduğunda bir null başvurusu döndürür `null` .

<xref:System.Text.Json>`JsonElement`seri durumdan çıkarma sırasında hem ilkel hem de karmaşık değerler için paketlenmiş bir depolar <xref:System.Object> , örneğin:

* Bir `object` özellik.
* `object`Sözlük değeri.
* Bir `object` dizi değeri.
* Bir kök `object` .

Ancak, `System.Text.Json` `null` ile aynı şekilde davranır `Newtonsoft.Json` ve yük `null` içindeki JSON değişmez değeri olduğunda bir null başvurusu döndürür.

Özellikler için tür çıkarımı uygulamak için `object` , [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)bölümünde örnek gibi bir dönüştürücü oluşturun.

### <a name="deserialize-null-to-non-nullable-type"></a>Null olamayan tür için null serisini kaldırma

`Newtonsoft.Json` Aşağıdaki senaryoda özel durum oluşturmaz:

* `NullValueHandling` , olarak ayarlanır `Ignore` ve
* Seri durumdan çıkarma sırasında JSON null yapılamayan bir değer türü için null değer içerir.

Aynı senaryoda <xref:System.Text.Json> bir özel durum oluşturur. (' De karşılık gelen null işleme ayarı `System.Text.Json` <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>  =  `true` .)

Hedef türün sahibiyseniz, en iyi geçici çözüm, özelliğin boş değer atanabilir olması (örneğin, `int` olarak değiştirin `int?` ).

Farklı bir geçici çözüm, türler için null değerleri işleyen aşağıdaki örnek gibi tür için bir dönüştürücü hale getirme örneğidir `DateTimeOffset` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetNullHandlingConverter.cs":::

Bu özel dönüştürücüyü [, özellik üzerindeki bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) veya [dönüştürücüyü koleksiyona ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydettirin <xref:System.Text.Json.JsonSerializerOptions.Converters> .

**Note:** Yukarıdaki dönüştürücü,  `Newtonsoft.Json` varsayılan değerleri belirten Pocos için, null değerleri farklı işler. Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithDefault":::

Ve önceki dönüştürücüyü kullanarak aşağıdaki JSON 'nin seri durumdan çıkarıldığını varsayalım:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Seri durumdan çıktıktan sonra, `Date` özelliği 1/1/0001 ( `default(DateTimeOffset)` ) değerini içerir, diğer bir deyişle, oluşturucuda ayarlanan değerin üzerine yazılır. Aynı POCO ve JSON olarak verildiğinde, `Newtonsoft.Json` seri durumdan çıkarma özelliğinde 1/1/2001 ' i bırakır `Date` .

### <a name="deserialize-to-immutable-classes-and-structs"></a>Sabit sınıflar ve yapılar için seri durumdan çıkarma

`Newtonsoft.Json` parametreleri olan oluşturucuları kullanabilmesi için, sabit sınıflar ve yapılar için seri hale getirebilirsiniz.

::: zone pivot="dotnet-5-0"
İçinde <xref:System.Text.Json> , parametreli bir oluşturucunun kullanımını belirtmek için [[jsonconstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) özniteliğini kullanın. C# 9 ' daki kayıtlar da sabittir ve seri durumundan çıkarma hedefi olarak desteklenir. Daha fazla bilgi için bkz. [Sabit türler ve kayıtlar](system-text-json-immutability.md).
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> .NET Core 3,1 ' de yalnızca ortak parametresiz oluşturucular desteklenir. Geçici bir çözüm olarak, özel bir dönüştürücüde parametreleri olan bir Oluşturucu çağırabilirsiniz.

İşte birden çok Oluşturucu parametresi olan değişmez bir struct:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ImmutablePoint.cs" id="ImmutablePoint":::

İşte bu yapıyı seri hale getirir ve seri hale getirir:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ImmutablePointConverter.cs":::

[Dönüştürücüyü koleksiyona ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) bu özel dönüştürücüyü kaydedin <xref:System.Text.Json.JsonSerializerOptions.Converters> .

Açık genel özellikleri işleyen benzer dönüştürücünün bir örneği için bkz. [anahtar-değer çiftleri için yerleşik dönüştürücü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).
::: zone-end

### <a name="required-properties"></a>Gerekli özellikler

' De `Newtonsoft.Json` , özniteliği için bir özelliğin gerekli olduğunu belirtirsiniz `Required` `[JsonProperty]` . `Newtonsoft.Json` JSON içinde gerekli olarak işaretlenmiş bir özellik için hiçbir değer alınmadığında bir özel durum oluşturur.

<xref:System.Text.Json> hedef türün özelliklerinden biri için hiçbir değer alınmazsa özel durum oluşturmaz. Örneğin, bir `WeatherForecast` sınıfınız varsa:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

Aşağıdaki JSON, hata olmadan seri durumdan çıkarılacak:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

JSON içinde herhangi bir özellik yoksa seriyi kaldırma başarısız olması için `Date` özel bir dönüştürücü uygulayın. Aşağıdaki örnek dönüştürücü kodu, `Date` seri kaldırma tamamlandıktan sonra özellik ayarlanmamışsa bir özel durum oluşturur:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecastRequiredPropertyConverter.cs":::

[Dönüştürücüyü koleksiyona ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) bu özel dönüştürücüyü kaydedin <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> .

Dönüştürücüyü yinelemeli olarak çağırmanın bu deseninin <xref:System.Text.Json.JsonSerializerOptions> bir özniteliği kullanarak değil kullanarak dönüştürücüyü kaydetmesi gerekir. Dönüştürücüyü bir özniteliği kullanarak kaydettiğinizde, özel dönüştürücü özyinelemeli olarak kendine çağırır. Sonuç, yığın taşması özel durumuyla biten sonsuz bir döngüdür.

Options nesnesini kullanarak dönüştürücüyü kaydettiğinizde, veya özyinelemeli bir döngüden, yinelemeli olarak veya çağrılırken Options nesnesine geçirilmeyen bir döngüden kaçının <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.JsonSerializer.Deserialize%2A> . Options nesnesi <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> koleksiyonu içerir. Veya ' a geçirirseniz, `Serialize` `Deserialize` özel dönüştürücü kendi kendine çağrı yapar ve yığın taşması özel durumuna neden olan sonsuz bir döngü sağlar. Varsayılan seçenekler uygun değilse, gereken ayarlarla seçeneklerin yeni bir örneğini oluşturun. Her yeni örnek bağımsız olarak önbelleğe aldığından bu yaklaşım yavaş olur.

Dönüştürülecek sınıfta kayıt kullanılabilecek alternatif bir model vardır `JsonConverterAttribute` . Bu yaklaşımda dönüştürücü kodu, `Serialize` `Deserialize` dönüştürülecek sınıftan türeyen bir sınıfı çağırır. Türetilmiş sınıf `JsonConverterAttribute` kendisine uygulanmış değil. Aşağıdaki örnekte, bu alternatif aşağıda verilmiştir:

* `WeatherForecastWithRequiredPropertyConverterAttribute` , seri durumdan çıkarılacak ve ona uygulanmış olan sınıftır `JsonConverterAttribute` .
* `WeatherForecastWithoutRequiredPropertyConverterAttribute` , Converter özniteliğine sahip olmayan türetilmiş sınıftır.
* Dönüştürücüdeki kod, `Serialize` `Deserialize` `WeatherForecastWithoutRequiredPropertyConverterAttribute` sonsuz bir döngüden kaçınmak için ve öğesini çağırır. Ek bir nesne örneklemesi ve özellik değerlerinin kopyalanması nedeniyle serileştirme üzerinde bu yaklaşımın performans maliyeti vardır.

`WeatherForecast*`Türler şunlardır:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithReqPptyConverterAttr":::

Dönüştürücü şöyledir:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecastRequiredPropertyConverterForAttributeRegistration.cs":::

Gerekli özellikler Dönüştürücüsü, [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) gibi öznitelikleri veya özel kodlayıcılar gibi farklı seçenekleri işlemeniz gerekiyorsa ek mantık gerektirir. Ayrıca, örnek kod, oluşturucuda varsayılan bir değer ayarlanan özellikleri işlemez. Bu yaklaşım aşağıdaki senaryolar arasında ayrım yapmaz:

* JSON 'da bir özellik eksik.
* Null atanamaz bir tür için bir özellik JSON içinde bulunur, ancak değer, türü için sıfır gibi varsayılan değerdir `int` .
* JSON 'da null olabilen bir değer türü özelliği var, ancak değer null.

### <a name="specify-date-format"></a>Tarih biçimini belirtin

`Newtonsoft.Json` , `DateTime` ve `DateTimeOffset` türlerinin özelliklerinin serileştirilme ve seri durumdan çıkarılme biçimini denetlemek için çeşitli yollar sağlar:

* `DateTimeZoneHandling`Ayar, tüm `DateTime` değerleri UTC tarihleri olarak seri hale getirmek için kullanılabilir.
* `DateFormatString`Ayar ve `DateTime` dönüştürücüler, tarih dizelerinin biçimini özelleştirmek için kullanılabilir.

<xref:System.Text.Json> , RFC 3339 profili de dahil olmak üzere ISO 8601-1:2019 ' u destekler. Bu biçim yaygın olarak benimsenmiştir, net bir şekilde gerçekleştirilir ve gidiş dönüşlerin kesin bir şekilde Başka bir biçim kullanmak için özel bir dönüştürücü oluşturun. Örneğin, aşağıdaki dönüştürücü, saat dilimi biçimiyle UNIX dönemi kullanan JSON 'u serileştirir ve seri hale getirir (gibi değerler `/Date(1590863400000-0700)/` ):

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterUnixEpochDate.cs" id="ConverterOnly":::

Daha fazla bilgi için, bkz. [' de System.Text.Json DateTime ve DateTimeOffset desteği ](../datetime/system-text-json-support.md).

### <a name="callbacks"></a>Geri Çağırmalar

`Newtonsoft.Json` serileştirme veya seri kaldırma işleminde özel kodu birkaç noktada yürütmenize imkan tanır:

* Onserisini kaldırma (bir nesnenin serisini kaldırmada başlayan)
* Onseri durumdan çıkarılan (bir nesnenin serisini kaldırma tamamlandığında)
* Onserileştirilme (bir nesne seri hale getirilmeye Başlarken)
* Onserileştirilmiş (bir nesne serileştirildiğinde)

<xref:System.Text.Json>' De, özel bir dönüştürücü yazarak geri çağırmaların benzetimini yapabilirsiniz. Aşağıdaki örnek bir POCO için özel dönüştürücüyü gösterir. Dönüştürücü, bir geri aramaya karşılık gelen her bir noktada bir ileti görüntüleyen kodu içerir `Newtonsoft.Json` .

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecastCallbacksConverter.cs":::

[Dönüştürücüyü koleksiyona ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) bu özel dönüştürücüyü kaydedin <xref:System.Text.Json.JsonSerializerOptions.Converters> .

Önceki örneği takip eden özel bir dönüştürücü kullanıyorsanız:

* `OnDeserializing`Kodun yenı POCO örneğine erişimi yok. Yeni POCO örneğini serisini kaldırma başlangıcında işlemek için, bu kodu POCO yapıcısına koyun.
* Özyinelemeli bir döngüden kaçınarak, Seçenekler nesnesine dönüştürücüyü kaydederek ve yinelemeli olarak ya da çağrılırken Options nesnesine geçirmekten kaçının `Serialize` `Deserialize` .

Yinelemeli olarak çağıran özel dönüştürücüler hakkında daha fazla bilgi `Serialize` için `Deserialize` , bu makalenin önceki kısımlarında yer alan [gerekli özellikler](#required-properties) bölümüne bakın.

### <a name="non-public-property-setters-and-getters"></a>Genel olmayan özellik ayarlayıcıları ve alıcılar

`Newtonsoft.Json` özniteliği aracılığıyla özel ve iç özellik ayarlayıcıları ve alıcıları öğeleri kullanılabilir `JsonProperty` .

::: zone pivot="dotnet-5-0"
<xref:System.Text.Json> , [[Jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliği aracılığıyla özel ve iç özellik ayarlayıcıları ve geticileri destekler. Örnek kod için bkz. [genel olmayan özellik erişimcileri](system-text-json-immutability.md).
::: zone-end

::: zone pivot="dotnet-core-3-1"
<xref:System.Text.Json> .NET Core 3,1 ' de yalnızca genel ayarlayıcıları desteklenir. Özel dönüştürücüler, bu işlevselliği sağlayabilir.
::: zone-end

### <a name="populate-existing-objects"></a>Mevcut nesneleri doldur

`JsonConvert.PopulateObject`İçindeki yöntemi, BIR `Newtonsoft.Json` JSON belgesini, yeni bir örnek oluşturmak yerine, bir sınıfın varolan bir örneğine kaldırma. <xref:System.Text.Json> her zaman varsayılan genel parametresiz oluşturucuyu kullanarak hedef türün yeni bir örneğini oluşturur. Özel dönüştürücüler, var olan bir örneğe serisini kaldıramıyor.

### <a name="reuse-rather-than-replace-properties"></a>Özellikleri değiştirmek yerine yeniden kullan

`Newtonsoft.Json` `ObjectCreationHandling` Ayar, özellikleri içindeki nesnelerin seri durumundan çıkarma sırasında yerine kullanılması gerektiğini belirtmenize olanak tanır. <xref:System.Text.Json> her zaman özelliklerde nesneleri değiştirir.  Özel dönüştürücüler, bu işlevselliği sağlayabilir.

### <a name="add-to-collections-without-setters"></a>Ayarlayıcısız koleksiyonlara Ekle

Seri durumundan çıkarma sırasında, `Newtonsoft.Json` özelliğin ayarlayıcısı olmasa bile nesneleri bir koleksiyona ekler. <xref:System.Text.Json> ayarlayıcıları olmayan özellikleri yoksayar. Özel dönüştürücüler, bu işlevselliği sağlayabilir.

### <a name="systemruntimeserialization-attributes"></a>System. Runtime. Serialization öznitelikleri

<xref:System.Text.Json>`System.Runtime.Serialization`, ve gibi ad alanındaki öznitelikleri desteklemez `DataMemberAttribute` `IgnoreDataMemberAttribute` .

### <a name="octal-numbers"></a>Sekizlik sayılar

`Newtonsoft.Json` sayıları, sekizli sayı olarak önünde sıfır ile değerlendirir. <xref:System.Text.Json>[RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi bunlara izin vermediğinden önde gelen sıfıra izin vermez.

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json` JSON, hedef türünde eksik olan özellikler içeriyorsa, seri durumdan çıkarma sırasında özel durumlar atmak üzere yapılandırılabilir. <xref:System.Text.Json>[[Jsonextensiondata] özniteliğini](system-text-json-handle-overflow.md)kullandığınız durumlar dışında, JSON 'daki ek özellikleri yoksayar. Eksik üye özelliği için geçici çözüm yoktur.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json``TraceWriter`serileştirme veya seri durumdan çıkarma tarafından oluşturulan günlükleri görüntülemek için kullanarak hata ayıklamanıza olanak sağlar. <xref:System.Text.Json> günlüğe kaydetme yapmaz.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JToken (JObject, JArray gibi) ile karşılaştırılan JsonDocument ve JsonElement

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> , var olan JSON yüklerden **salt okunurdur** belge nesne MODELI (DOM) ayrıştırabilme ve derleme olanağı sağlar. DOM, bir JSON yükünde verilere rastgele erişim sağlar. Yükü oluşturan JSON öğelerine tür aracılığıyla erişilebilir <xref:System.Text.Json.JsonElement> . `JsonElement`Türü, JSON metnini ortak .net türlerine dönüştürmek Için API 'ler sağlar. `JsonDocument` bir <xref:System.Text.Json.JsonDocument.RootElement> özellik sunar.

### <a name="jsondocument-is-idisposable"></a>JsonDocument, IDisposable

`JsonDocument` havuza alınmış arabellekte verilerin bellek içi bir görünümünü oluşturur. Bu nedenle, veya öğelerinden farklı olarak `JObject` `JArray` `Newtonsoft.Json` , `JsonDocument` türü, `IDisposable` bir using bloğu içinde kullanılması gerekir.

Yalnızca API 'nizden `JsonDocument` , yaşam süresi sahipliğini aktarmak ve arayan sorumluluğunu atmak istiyorsanız ' ı geri döndürün. Çoğu senaryoda, bu gerekli değildir. Çağıranın tüm JSON belgesi ile çalışması gerekiyorsa, <xref:System.Text.Json.JsonElement.Clone%2A> <xref:System.Text.Json.JsonDocument.RootElement%2A> ' ın ' i döndürün <xref:System.Text.Json.JsonElement> . Çağıranın JSON belgesi içinde belirli bir öğeyle çalışması gerekiyorsa, ' ın ' i döndürün <xref:System.Text.Json.JsonElement.Clone%2A> <xref:System.Text.Json.JsonElement> . Ya da bir `RootElement` alt öğeyi doğrudan bir olmadan geri `Clone` döndürülürsünüz, çağıran, `JsonElement` `JsonDocument` kendisine ait olan öğesinden sonra döndürülen öğesine erişemez.

İşte şunları yapmanızı gerektiren bir örnek `Clone` :

```csharp
public JsonElement LookAndLoad(JsonElement source)
{
    string json = File.ReadAllText(source.GetProperty("fileName").GetString());

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        return doc.RootElement.Clone();
    }
}
```

Yukarıdaki kod, bir özellik içeren bir için bekliyor `JsonElement` `fileName` . JSON dosyasını açar ve bir oluşturur `JsonDocument` . Yöntemi, çağıranın tüm belge ile çalışmak istediğini varsayar, bu yüzden öğesinin öğesini döndürür `Clone` `RootElement` .

Bir alır ve bir `JsonElement` alt öğe döndürüyorsa, alt öğenin bir kısmını döndürmek gerekli değildir `Clone` . Çağıran, `JsonDocument` geçirilen ' ın ait olduğu canlı tutmanın sorumluluğundadır `JsonElement` . Örnek:

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument salt okunurdur

<xref:System.Text.Json>Dom, JSON öğeleri ekleyemez, kaldıramaz veya değiştiremez. Bu, performans için bu şekilde tasarlanmıştır ve ortak JSON yük boyutlarını (yani, < 1 MB) ayrıştırmak için ayırmaları azaltır. Senaryonuz Şu anda değiştirilebilir bir DOM kullanıyorsa, aşağıdaki geçici çözümlerden biri uygulanabilir olabilir:

* Sıfırdan bir oluşturmak için `JsonDocument` (diğer bir deyişle, varolan BIR JSON yükünü `Parse` yöntemine geçirmeden), kullanarak JSON metnini yazın `Utf8JsonWriter` ve yeni bir yapmak için çıktıyı ayrıştırın `JsonDocument` .
* Varolan bir değişikliği değiştirmek için `JsonDocument` , JSON metni yazmak, yazarken değişiklikler yapmak ve yeni bir hale getirmek için bu çıkışı ayrıştırmak üzere kullanın `JsonDocument` .
* Var olan JSON belgelerini, veya API 'leri ile eşdeğer olacak şekilde birleştirmek için `JObject.Merge` `JContainer.Merge` `Newtonsoft.Json` [Bu GitHub sorununa](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)bakın.

### <a name="jsonelement-is-a-union-struct"></a>JsonElement bir UNION yapısı

`JsonDocument` bir `RootElement` <xref:System.Text.Json.JsonElement> UNION, HERHANGI bir JSON öğesini kapsayan yapı türü olan türü bir özellik olarak gösterir. `Newtonsoft.Json` ,, ve gibi adanmış sıradüzenli türler kullanır `JObject` `JArray` `JToken` . `JsonElement` üzerinde arama ve listeleme yapabilecekleriniz vardır ve `JsonElement` JSON öğelerini .net türlerine getirmek için kullanabilirsiniz.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Bir JsonDocument ve JsonElement öğelerini alt öğeler için arama

`JObject` `JArray` Bazı sözlüklerde arama yapıldığından, ya da ' dan veya ' den yararlanarak JSON belirteçlerini arar `Newtonsoft.Json` . Karşılaştırmayla, ' deki aramalar `JsonElement` Özellikler için sıralı bir arama gerektirir ve bu nedenle nispeten yavaş olur (örneğin, kullanılırken `TryGetProperty` ). <xref:System.Text.Json> Arama süresi yerine ilk ayrıştırma süresini en aza indirmek için tasarlanmıştır. Bu nedenle, bir nesnede arama yaparken performansı iyileştirmek için aşağıdaki yaklaşımları kullanın `JsonDocument` :

* <xref:System.Text.Json.JsonElement.EnumerateArray%2A> <xref:System.Text.Json.JsonElement.EnumerateObject%2A> Kendi dizin oluşturma veya döngülerinizi yapmak yerine yerleşik numaralandırıcıları (ve) kullanın.
* Kullanarak her bir özelliğin tamamında sıralı bir arama yapmayın `JsonDocument` `RootElement` . Bunun yerine, JSON verilerinin bilinen yapısına bağlı olarak iç içe geçmiş JSON nesnelerinde arama yapın. Örneğin, `Grade` nesnelerde bir özelliği arıyorsanız `Student` , özellikler için arama yapmak yerine nesneler üzerinde döngü yapın `Student` ve `Grade` her biri için değerini alın `JsonElement` `Grade` . İkincisini yapmak, aynı verilerin üzerinde gereksiz bir şekilde geçiş oluşmasına neden olur.

Kod örneği için bkz. [veri erişimi Için JsonDocument kullanma](write-custom-serializer-deserializer.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader, JsonTextReader ile karşılaştırılır

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>, UTF-8 kodlu JSON metnine yönelik yüksek performanslı, düşük bir ayırma, Salt ilet okuyucu, [Readonlyspan \<byte> ](xref:System.ReadOnlySpan%601) veya [readonlysequence \<byte> ](xref:System.Buffers.ReadOnlySequence%601)tarafından okunabilir. , `Utf8JsonReader` Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür.

Aşağıdaki bölümlerde, kullanımı için önerilen programlama düzenleri açıklanmaktadır `Utf8JsonReader` .

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader bir başvuru yapısı

`Utf8JsonReader`Tür bir *başvuru yapısı* olduğundan, [belirli sınırlamalar](../../csharp/language-reference/builtin-types/struct.md#ref-struct)vardır. Örneğin, bir sınıf veya yapı üzerinde bir başvuru yapısı dışında bir alan olarak depolanamaz. Yüksek performans elde etmek için, bu tür bir `ref struct` başvuru yapısı olan giriş [ \<byte> readonlyspan](xref:System.ReadOnlySpan%601)' i önbelleğe alma gerektirdiğinden bir olmalıdır. Ayrıca, bu tür durum taşıdığı için değişebilir olur. Bu nedenle, bunu değere göre değil **ref 'e geçirin** . Değere göre geçirmek bir yapı kopyasının oluşmasına neden olur ve durum değişiklikleri arayan tarafından görülemez. Bu, öğesinden bu yana farklılık gösterir `Newtonsoft.Json` `Newtonsoft.Json` `JsonTextReader` . Başvuru yapıları kullanma hakkında daha fazla bilgi için bkz. [Write Safe ve verimli C# kodu](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>UTF-8 metnini oku

Kullanırken en iyi performansı elde etmek için `Utf8JsonReader` , UTF-16 dizeleri yerine zaten UTF-8 ile KODLANMıŞ JSON yüklerini okuyun. Kod örneği için bkz. [Utf8JsonReader kullanarak filtre verileri](write-custom-serializer-deserializer.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Stream veya Pıpereader ile okuma

, `Utf8JsonReader` UTF-8 kodlamalı [Readonlyspan \<byte> ](xref:System.ReadOnlySpan%601) veya [ \<byte> readonlysequence](xref:System.Buffers.ReadOnlySequence%601) (bir öğesinden okuma sonucu) ile okumayı destekler <xref:System.IO.Pipelines.PipeReader> .

Zaman uyumlu okuma için, akışın sonuna kadar bir bayt dizisine kadar JSON yükünü okuyabilir ve bunu okuyucuya geçirebilirsiniz. Dizeden okumak için (UTF-16 olarak kodlanır), çağırın <xref:System.Text.Encoding.UTF8> .<xref:System.Text.Encoding.GetBytes%2A> İlk olarak dizeyi bir UTF-8 kodlu bayt dizisine dönüştürme. Ardından bunu öğesine geçirin `Utf8JsonReader` .

`Utf8JsonReader`GIRIŞIN JSON metni olduğunu düşündüğü IÇIN UTF-8 bayt sırası işareti (BOM) GEÇERSIZ JSON olarak kabul edilir. Çağıranın verileri okuyucuya geçirmeden önce onu filtrelemeniz gerekir.

Kod örnekleri için bkz. [Use Utf8JsonReader](write-custom-serializer-deserializer.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Çok kesimli ReadOnlySequence ile oku

JSON girdisi [Readonlyspan \<byte> ](xref:System.ReadOnlySpan%601)ise, `ValueSpan` okuma döngüsüne gittiğinizde her JSON öğesine okuyucudaki özellikten erişilebilir. Ancak, giriş, [Readonlysequence \<byte> ](xref:System.Buffers.ReadOnlySequence%601) ise (bir öğesinden okunması sonucu <xref:System.IO.Pipelines.PipeReader> ), bazı JSON öğeleri nesnenin birden fazla segmentine Straddle `ReadOnlySequence<byte>` . Bu öğelere <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> , bir ardışık bellek bloğunun içinden erişilemez. Bunun yerine, giriş olarak çok bölgeli her seferinde, `ReadOnlySequence<byte>` <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> geçerli JSON öğesine nasıl erişebileceğinizi anlamak için okuyucudaki özelliği yoklayın. Önerilen bir model aşağıda verilmiştir:

```csharp
while (reader.Read())
{
    switch (reader.TokenType)
    {
        // ...
        ReadOnlySpan<byte> jsonElement = reader.HasValueSequence ?
            reader.ValueSequence.ToArray() :
            reader.ValueSpan;
        // ...
    }
}
```

### <a name="use-valuetextequals-for-property-name-lookups"></a>Özellik adı aramaları için ValueTextEquals kullanın

<xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A>Özellik adı aramalarını çağırarak bayt başına karşılaştırmalar yapmak için kullanmayın <xref:System.MemoryExtensions.SequenceEqual%2A> . <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A>Bunun yerine çağırın, çünkü bu yöntem JSON 'da kaçan tüm karakterleri kaldırır. "Ad" adlı bir özelliğin nasıl aranacağını gösteren bir örnek aşağıda verilmiştir:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ValueTextEqualsExample.cs" id="DefineUtf8Var":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ValueTextEqualsExample.cs" id="UseUtf8Var" highlight="9":::

### <a name="read-null-values-into-nullable-value-types"></a>Null değerleri null yapılabilir değer türlerine oku

`Newtonsoft.Json` döndüren API 'Ler sağlar; örneğin <xref:System.Nullable%601> `ReadAsBoolean` , `Null` `TokenType` bir döndürür `bool?` . Yerleşik `System.Text.Json` API 'ler yalnızca null yapılamayan değer türleri döndürüyor. Örneğin, <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> bir döndürür `bool` . JSON içinde bulursa bir özel durum oluşturur `Null` . Aşağıdaki örneklerde, bir tane null yapılabilir değer türü döndürerek ve bir tane varsayılan değeri döndürerek, null değerlerini işlemek için iki yol gösterilmektedir:

```csharp
public bool? ReadAsNullableBoolean()
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return null;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

```csharp
public bool ReadAsBoolean(bool defaultValue)
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return defaultValue;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

### <a name="multi-targeting"></a>Çoklu hedefleme

`Newtonsoft.Json`Belirli hedef çerçeveler için kullanmaya devam etmeniz gerekiyorsa, çoklu hedefleyebilir ve iki uygulamanız vardır. Ancak, bu önemsiz değildir ve bazı `#ifdefs` ve kaynak yinelemesi gerektirir. Mümkün olduğunca çok kodu paylaşmanın bir yolu, `ref struct` ve etrafında bir sarmalayıcı oluşturmaktır `Utf8JsonReader` `Newtonsoft.Json` `JsonTextReader` . Bu sarmalayıcı, davranış farklarını yalıtma sırasında genel yüzey alanını birleştirecektir. Bu, değişiklikleri öncelikle tür oluşturma ile birlikte ayırmanızı sağlar ve yeni türü başvuruya göre geçirerek. Bu, [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) kitaplığı 'nın izlediği düzendir:

* [UnifiedJsonReader.JsonTextReader. cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader. Utf8JsonReader. cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter, JsonTextWriter ile karşılaştırılır

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> , ve gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur `String` `Int32` `DateTime` . Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür.

Aşağıdaki bölümlerde, kullanımı için önerilen programlama düzenleri açıklanmaktadır `Utf8JsonWriter` .

### <a name="write-with-utf-8-text"></a>UTF-8 metniyle yazma

Kullanırken en iyi performansı elde etmek için `Utf8JsonWriter` , WRITE JSON YÜKLERINI UTF-16 dizeleri yerıne UTF-8 ile kodlanmış olarak yazın. <xref:System.Text.Json.JsonEncodedText>Bilinen dize özellik adlarını ve değerlerini sıra olarak önbelleğe almak ve önceden kodlamak için kullanın ve UTF-16 dize sabit değerleri kullanmak yerine yazıcıya geçirin. Bu, önbelleğe alma ve UTF-8 bayt dizilerini kullanmayla daha hızlıdır.

Özel kaçış yapmanız gerekiyorsa bu yaklaşım da geçerlidir. `System.Text.Json` bir dize yazarken kaçış özelliğini devre dışı bırakmanızı sağlar. Bununla birlikte, yazıcıya kendi özel <xref:System.Text.Encodings.Web.JavaScriptEncoder> bir seçenek olarak geçirebilirsiniz ya da `JsonEncodedText` kaçış yapmak için kendi uygulamanızı kullanarak kendi `JavascriptEncoder` öğesini oluşturabilir ve sonra `JsonEncodedText` dize yerine yazın. Daha fazla bilgi için bkz. [karakter kodlamasını özelleştirme](system-text-json-character-encoding.md).

### <a name="write-raw-values"></a>Ham değerleri yaz

`Newtonsoft.Json` `WriteRawValue` Yöntemi, bir değerin beklenildiği ham JSON yazar. <xref:System.Text.Json> doğrudan eşdeğeri yoktur, ancak şu şekilde yalnızca geçerli JSON yazılmasını sağlayan bir geçici çözüm verilmiştir:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Karakter kaçış 'yi özelleştirme

[Stringescapehandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) AYARı, `JsonTextWriter` ASCII olmayan tüm karakterleri **veya** HTML karakterlerinin kaçış seçeneklerini sunar. Varsayılan olarak, `Utf8JsonWriter` ASCII olmayan **ve** HTML karakterlerinin hepsini çıkar. Bu kaçış, derinlemesine savunma güvenlik nedenleriyle yapılır. Farklı bir kaçış ilkesi belirtmek için, oluşturun <xref:System.Text.Encodings.Web.JavaScriptEncoder> ve ayarlayın <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [karakter kodlamasını özelleştirme](system-text-json-character-encoding.md).

### <a name="customize-json-format"></a>JSON biçimini Özelleştir

`JsonTextWriter` eşdeğeri olmayan, için aşağıdaki ayarları içerir `Utf8JsonWriter` :

* [Girintileme](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) -girintilemek için kaç karakter kullanılacağını belirtir. `Utf8JsonWriter` her zaman 2 karakterlik girintileme yapar.
* [Inztchar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) -girintileme için kullanılacak karakteri belirtir.  `Utf8JsonWriter` her zaman boşluk kullanır.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) -dize değerlerini çevrelemek için kullanılacak karakteri belirtir.  `Utf8JsonWriter` her zaman çift tırnak kullanır.
* [QUOTENAME](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) -özellik adlarının tırnak işaretleriyle saranıp çevrelenmeyeceğini belirtir.  `Utf8JsonWriter` her zaman tırnak işaretleriyle çevreler.

Tarafından üretilen JSON 'yi bu şekillerde özelleştirmenizi sağlayan geçici çözümler yoktur `Utf8JsonWriter` .

### <a name="write-null-values"></a>Null değerleri yaz

Kullanarak null değerler yazmak için `Utf8JsonWriter` şunu çağırın:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A> değer olarak null ile bir anahtar-değer çifti yazmak.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A> JSON dizisinin bir öğesi olarak null yazmak için.

Dize özelliği için, dize null ise ve <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> `WriteNull` ile eşdeğerdir `WriteNullValue` .

### <a name="write-timespan-uri-or-char-values"></a>TimeSpan, Uri veya Char değerlerini yaz

`JsonTextWriter``WriteValue` [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)ve [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) değerleri için yöntemler sağlar. `Utf8JsonWriter` eşdeğer yöntemlere sahip değildir. Bunun yerine, bu değerleri dizeler olarak biçimlendirin ( `ToString()` Örneğin, çağırarak) ve çağırın <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> .

### <a name="multi-targeting"></a>Çoklu hedefleme

`Newtonsoft.Json`Belirli hedef çerçeveler için kullanmaya devam etmeniz gerekiyorsa, çoklu hedefleyebilir ve iki uygulamanız vardır. Ancak, bu önemsiz değildir ve bazı `#ifdefs` ve kaynak yinelemesi gerektirir. Mümkün olduğunca çok kodu paylaşmanın bir yolu, ve etrafında bir sarmalayıcı oluşturmaktır `Utf8JsonWriter` `Newtonsoft` `JsonTextWriter` . Bu sarmalayıcı, davranış farklarını yalıtma sırasında genel yüzey alanını birleştirecektir. Bu, değişiklikleri genellikle türün yapılacağı şekilde yalıtmanızı sağlar. [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) kitaplığı aşağıdaki gibidir:

* [ OnTextWriter. csUnifiedJsonWriter.Js](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter. Utf8JsonWriter. cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="typenamehandlingall-not-supported"></a>TypeNameHandling. All desteklenmiyor

' Den hariç tutulacak ve eşdeğer işlevselliğe yönelik karar, `TypeNameHandling.All` `System.Text.Json` kasıtlı olarak gerçekleştirildi. JSON yükünün kendi tür bilgilerini belirtmesini sağlamak, Web uygulamalarında sık karşılaşılan bir güvenlik açığı kaynağıdır. Özellikle, ile yapılandırmak `Newtonsoft.Json` , `TypeNameHandling.All` uzak istemcinin tüm yürütülebilir BIR uygulamayı JSON yükünün içinde eklemesine izin vererek, Web uygulamasının serisini kaldırma işlemi sırasında gömülü kodu ayıklar ve çalıştırır. Daha fazla bilgi için, bkz. [12. JSON saldırılarına](https://www.blackhat.com/docs/us-17/thursday/us-17-Munoz-Friday-The-13th-Json-Attacks.pdf) yönelik olarak Cuma ve [13. JSON saldırıları ayrıntılarının](https://www.blackhat.com/docs/us-17/thursday/us-17-Munoz-Friday-The-13th-JSON-Attacks-wp.pdf)Cuma.

## <a name="additional-resources"></a>Ek kaynaklar

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JSON’u seri hale getirme ve seri halden çıkarma](system-text-json-how-to.md)
* [JsonSerializerOptions örneklerinin örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harf duyarlı eşlemeyi etkinleştirme](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksayma](system-text-json-ignore-properties.md)
* [Geçersiz JSON’a izin verme](system-text-json-invalid-json.md)
* [Sap taşması JSON’ı](system-text-json-handle-overflow.md)
* [Başvuruları koruma](system-text-json-preserve-references.md)
* [Sabit türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [Karakter kodlamasını özelleştirme](system-text-json-character-encoding.md)
* [Özel serileştiriciler ve seri hale getiriciler yazma](write-custom-serializer-deserializer.md)
* [JSON serileştirme için özel dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
