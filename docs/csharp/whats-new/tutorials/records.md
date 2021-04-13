---
title: Kayıt türlerini kullanma-C# öğreticisi
description: Kayıt türlerini kullanma, kayıt hiyerarşileri oluşturma ve sınıflar üzerinde kayıt seçme hakkında bilgi edinin.
ms.date: 11/12/2020
ms.openlocfilehash: c8a1922fdf113d046dc087ec289accce4312c4ae
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075543"
---
# <a name="create-record-types"></a>Kayıt türleri oluşturma

C# 9, sınıflar veya yapılar yerine oluşturabileceğiniz yeni bir başvuru türü olan [*kayıtları*](../../language-reference/builtin-types/record.md)tanıtır. Kayıtlar, kayıt türlerindeki sınıflardan farklıdır ve *değer tabanlı eşitlik* kullanır. Kayıt türünün iki değişkeni, kayıt türü tanımları özdeş ise eşittir ve her alan için her iki kayıttaki değerler eşittir. Başvurulan nesneler aynı sınıf türünde ise ve değişkenler aynı nesneye başvurursanız, bir sınıf türünün iki değişkeni eşittir. Değer tabanlı eşitlik, muhtemelen kayıt türlerinde istediğiniz diğer özellikleri gösterir. Derleyici, bir yerine bir tane bildirdiğinizde bu üyelerin birçoğunu üretir `record` `class` .

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:

> [!div class="checklist"]
>
> - ' A veya ' i bildirmeniz gerekip gerekmediğine karar verin `class` `record` .
> - Kayıt türlerini ve Konumsal kayıt türlerini bildirin.
> - Derleyici tarafından oluşturulan metotlar için yöntemlerinizi değiştirin.

## <a name="prerequisites"></a>Önkoşullar

C# 9,0 veya üzeri derleyicisi dahil olmak üzere makinenizi .NET 5 veya sonraki bir sürümünü çalıştıracak şekilde ayarlamanız gerekir. C# 9,0 derleyicisi, [Visual Studio 2019 sürüm 16,8](https://visualstudio.microsoft.com/vs) veya [.NET 5,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

## <a name="characteristics-of-records"></a>Kayıtların özellikleri

 `record` Ya da `class` anahtar sözcüğü yerine anahtar sözcüğünü içeren bir tür bildirerek bir kayıt tanımlarsınız `struct` . Kayıt, başvuru türüdür ve değer tabanlı eşitlik semantiğini izler. Değer semantiğini zorlamak için, derleyici kayıt türü için birkaç yöntem üretir:

- Bir geçersiz kılma <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> .
- `Equals`Parametresi kayıt türü olan bir sanal yöntem.
- Bir geçersiz kılma <xref:System.Object.GetHashCode?displayProperty=nameWithType> .
- Ve için `operator ==` yöntemleri `operator !=` .
- Kayıt türleri uygular <xref:System.IEquatable%601?displayProperty=nameWithType> .

Ayrıca, kayıtlar bir geçersiz kılma sağlar <xref:System.Object.ToString?displayProperty=nameWithType> . Derleyici, kullanarak kayıtları görüntüleme yöntemlerini birleştirir <xref:System.Object.ToString?displayProperty=nameWithType> . Bu öğretici için kodu yazarken bu üyeleri keşfedebilirsiniz. `with`, Bozucu olmayan kayıtları etkinleştirmek için destek ifadelerini kaydeder.

Ayrıca, daha kısa bir sözdizimi kullanarak *konumsal kayıtlar* bildirebilirsiniz. Bu derleyici, konumsal kayıtları bildirdiğinizde sizin için daha fazla yöntem sentezler:

- Parametreleri, kayıt bildiriminde konumsal parametrelerle eşleşen bir birincil Oluşturucu.
- Birincil oluşturucunun her parametresi için yalnızca genel init özellikleri.
- `Deconstruct`Kayıttan özellikleri ayıklamaya yönelik bir yöntem.

## <a name="build-temperature-data"></a>Sıcaklık verileri oluşturma

Veriler ve istatistikler, kayıtları kullanmak isteyeceğiniz senaryolar arasındadır. Bu öğreticide, farklı kullanımlar için *derece günler* hesaplayan bir uygulama oluşturacaksınız. *Derece günler* , bir gün, hafta veya ay boyunca bir ısı (veya ısı eksikliği) bir ölçüdür. Derece günler enerji kullanımını izleyip tahmin eder. Daha fazla kullanım günü daha fazla hava anlamına gelir ve daha fazla kora günü daha fazla sayıda kullanım anlamına gelir. Derece günler, Tesis popülasyonlarını yönetmenize ve mevsimler değiştikçe tesis artışına bağıntılı bir yardım sağlar. Derece günler, kligayı eşleştirmek için seyahat eden türler için bir hayvan geçişi izlemenize yardımcı olur.

Formül, belirli bir gün ve temel sıcaklığa göre ortalama sıcaklığa dayanır. Süreyi zaman içinde hesaplamak için, her gün bir süre için yüksek ve düşük sıcaklık gerekir. Yeni bir uygulama oluşturarak başlayalım. Yeni bir konsol uygulaması oluşturun. "Dailysıcaklık. cs" adlı yeni bir dosyada yeni bir kayıt türü oluşturun:

:::code language="csharp" source="snippets/record-types/InterimSteps.cs" ID="DailyRecord":::

Yukarıdaki kod bir *konumsal kayıt* tanımlar. İki özellik içeren bir başvuru türü oluşturdunuz: `HighTemp` , ve `LowTemp` . Bu özellikler, oluşturucuda ayarlanabilecekleri veya bir özellik başlatıcısı kullanmanın anlamı *yalnızca init özelliklerdir*. `DailyTemperature`Türün Ayrıca iki özelliği olan iki parametresi olan bir *birincil Oluşturucusu* vardır. Birincil oluşturucuyu kullanarak bir `DailyTemperature` kayıt başlatın:

:::code language="csharp" source="snippets/record-types/Program.cs" ID="DeclareData":::

Konumsal kayıtlar dahil olmak üzere, kayıtlara kendi özelliklerinizi veya yöntemlerinizi ekleyebilirsiniz. Her gün için ortalama sıcaklığın hesaplanması gerekir. Bu özelliği `DailyTemperature` kayda ekleyebilirsiniz:

:::code language="csharp" source="snippets/record-types/DailyTemperature.cs" ID="TemperatureRecord":::

Bu verileri kullanabileceizin olalım. Aşağıdaki kodu yönteminizin içine ekleyin `Main` :

```csharp
foreach (var item in data)
    Console.WriteLine(item);
```

Uygulamanızı çalıştırın ve aşağıdaki ekranda gösterilene benzer bir çıktı görürsünüz (boşluk için birkaç satır kaldırılır):

```dotnetcli
DailyTemperature { HighTemp = 57, LowTemp = 30, Mean = 43.5 }
DailyTemperature { HighTemp = 60, LowTemp = 35, Mean = 47.5 }


DailyTemperature { HighTemp = 80, LowTemp = 60, Mean = 70 }
DailyTemperature { HighTemp = 85, LowTemp = 66, Mean = 75.5 }
```

Yukarıdaki kod, `ToString` derleyici tarafından sentezlenen geçersiz kılmanın çıktısını gösterir. Farklı metin tercih ediyorsanız, `ToString` derleyicinin sizin için bir sürümü birleştirmelerini engelleyen kendi sürümünüzü yazabilirsiniz.

## <a name="compute-degree-days"></a>İşlem Derecesi Günleri

Derece günleri hesaplamak için, belirli bir gün için bir temel sıcaklığın ve ortalama sıcaklığın farkını alırsınız. Zaman içinde sıcaklığın ölçülmesi için, ortalama sıcaklık taban çizgisinin altında olduğu günleri atabilirsiniz. Soğuk zamana göre ölçmek için, ortalama sıcaklığın taban çizgisinin üzerinde olduğu günleri atabilirsiniz. Örneğin ABD, hem Isıtma hem de soğutma derecesi günü için temel olarak 65F kullanır. Bu, herhangi bir ısıtma veya soğutma gerektirmeyen sıcaklığa sahiptir. Bir gün, 70F 'nin ortalama sıcaklığını içeriyorsa, bu gün 5 soğutma derecesi günü ve 0 Isıtma derecesi günü olur. Buna karşılık, ortalama sıcaklık 55F ise, bu gün 10 Isıtma derecesi gün ve 0 soğutma derecesi günü olur.

Bu formülleri küçük bir kayıt türleri hiyerarşisi olarak ifade edebilirsiniz: bir soyut derece gün türü ve Isıtma derecesi gün ve soğutma derecesi için iki somut tür. Bu türler Ayrıca konumsal kayıtlar olabilir. Bunlar, birincil oluşturucunun bağımsız değişkenleri olarak bir taban çizgisi sıcaklığı ve günlük sıcaklık kayıtları sırası alırlar:

:::code language="csharp" source="snippets/record-types/InterimSteps.cs" ID="DegreeDaysRecords":::

Soyut `DegreeDays` kayıt, ve kayıtlarının her ikisi için de paylaşılan temel `HeatingDegreeDays` sınıftır `CoolingDegreeDays` . Türetilmiş kayıtlardaki birincil Oluşturucu bildirimleri, temel kayıt başlatmanın nasıl yönetileceğini gösterir. Türetilmiş kaydınız, temel kayıt birincil oluşturucudaki tüm parametrelerin parametrelerini bildirir. Temel kayıt bu özellikleri bildirir ve başlatır. Türetilmiş kayıt onları gizlemez, ancak temel kaydında bildirilmeyen parametreler için Özellikler oluşturur ve başlatır. Bu örnekte, türetilen kayıtlar yeni birincil Oluşturucu parametreleri eklemez. Aşağıdaki kodu yönteminizin içine ekleyerek kodunuzu test edin `Main` :

:::code language="csharp" source="snippets/record-types/Program.cs" ID="HeatingAndCooling":::

Aşağıdaki ekran gibi bir çıktı alırsınız:

```dotnetcli
HeatingDegreeDays { BaseTemperature = 65, TempRecords = record_types.DailyTemperature[], DegreeDays = 85 }
CoolingDegreeDays { BaseTemperature = 65, TempRecords = record_types.DailyTemperature[], DegreeDays = 71.5 }
```

## <a name="define-compiler-synthesized-methods"></a>Derleyici birleştirilmemiş yöntemleri tanımlama

Kodunuz, bu süre içinde doğru Isıtma ve soğutma derecesi gün sayısını hesaplar. Ancak bu örnekte, kayıtların bazı birleştirilmiş yöntemlerini nasıl değiştirmek isteyebileceğiniz gösterilmektedir. Derleme türü dışında, derleyici sentezlenmiş yöntemlerin herhangi birinin kendi sürümünüzü bir kayıt türünde bildirebilirsiniz. Clone yönteminin derleyicinin ürettiği bir adı vardır ve farklı bir uygulama sağlayamezsiniz. Bu birleştirilmemiş Yöntemler bir kopya Oluşturucu, arabirimin üyeleri, <xref:System.IEquatable%601?displayProperty=nameWithType> eşitlik ve eşitsizlik testleri ve ' i içerir <xref:System.Object.GetHashCode> . Bu amaçla, sentezleştir `PrintMembers` . Ayrıca kendi kendinize de bildirebilirsiniz `ToString` , ancak `PrintMembers` Devralma senaryoları için daha iyi bir seçenek sağlar. Sentezlenmiş yöntemin kendi sürümünüzü sağlamak için imza, sentezlenmiş metotla eşleşmelidir.

`TempRecords`Konsol çıkışında öğesi yararlı değildir. Türü görüntüler, ancak başka hiçbir şey yapmaz. Bu davranışı, kendi kendine birleştirilmiş metodun uygulamanızı sağlayarak değiştirebilirsiniz `PrintMembers` . İmza, bildirime uygulanan değiştiricilere bağlıdır `record` :

- Bir kayıt türü ise `sealed` imza `private bool PrintMembers(StringBuilder builder);`
- Bir kayıt türü `sealed` ve türetilmemişse (yani `object` , bir temel kayıt bildirmiyor), imza `protected virtual bool PrintMembers(StringBuilder builder);`
- Bir kayıt türü başka bir `sealed` Kayıttan değilse ve bu kayıtlardan türetilmemişse, imza `protected override bool PrintMembers(StringBuilder builder);`

Amacını anlamak için bu kurallar en kolay anlarsınız `PrintMembers` . `PrintMembers` bir kayıt türündeki her bir özellik hakkındaki bilgileri bir dizeye ekler. Sözleşme, üyelerini görüntüsüne eklemek için temel kayıtlar gerektirir ve türetilmiş üyelerin üyelerini eklemesini kabul eder. Her kayıt türü `ToString` , aşağıdaki örneğe benzer bir geçersiz kılma işlemini birleştirir `HeatingDegreeDays` :

```csharp
public override string ToString()
{
    StringBuilder stringBuilder = new StringBuilder();
    stringBuilder.Append("HeatingDegreeDays");
    stringBuilder.Append(" { ");
    if (PrintMembers(stringBuilder))
    {
        stringBuilder.Append(" ");
    }
    stringBuilder.Append("}");
    return stringBuilder.ToString();
}
```

`PrintMembers`Kayıt içinde, `DegreeDays` koleksiyonun türünü yazdırmaz bir yöntemi bildirirsiniz:

:::code language="csharp" source="snippets/record-types/DegreeDays.cs" ID="AddPrintMembers":::

İmza, `virtual protected` derleyicinin sürümüyle eşleşmesi için bir yöntem bildirir. Erişimcileri yanlış alırsanız endişelenmeyin; Dil doğru imzayı zorlar. Herhangi bir sentezlenmiş yöntemin doğru değiştiricilerini unutursanız, derleyici doğru imzayı almanıza yardımcı olan uyarıları veya hataları verir.

## <a name="non-destructive-mutation"></a>Bozucu olmayan mutasyon

Konumsal bir kayıttaki birleştirilmemiş Üyeler kaydın durumunu değiştirmez. Amaç, sabit kayıtları daha kolay bir şekilde oluşturabilir. Ve için önceki bildirimlerde tekrar bakın `HeatingDegreeDays` `CoolingDegreeDays` . Eklenen Üyeler kayıt için değerler üzerinde hesaplamalar gerçekleştirir, ancak hiçbir zaman durum vermez. Konumsal kayıtlar, değişmez başvuru türleri oluşturmanızı kolaylaştırır.

Değişmez başvuru türleri oluşturmak, bozucu olmayan bir mutasyon kullanmak isteyeceğiniz anlamına gelir. [ `with` İfadeleri](../../language-reference/operators/with-expression.md)kullanarak varolan kayıt örneklerine benzer yeni kayıt örnekleri oluşturursunuz. Bu ifadeler, kopyayı değiştiren ek atamalara sahip bir kopyalama yapımı. Sonuç, her bir özelliğin mevcut kayıttan kopyalandığı ve isteğe bağlı olarak değiştirildiği yeni bir kayıt örneğidir. Özgün kayıt değiştirilmez.

Programınıza, ifadeleri gösteren birkaç özellik ekleyelim `with` . İlk olarak, aynı verileri kullanarak büyüyen derece günleri hesaplamak için yeni bir kayıt oluşturalım. *Büyüyen derece günler* genellikle temel olarak 41F kullanır ve taban çizgisinin üzerindeki sıcaklıkları ölçer. Aynı verileri kullanmak için, `coolingDegreeDays` ancak farklı bir temel sıcaklığa sahip olan yeni bir kayıt oluşturabilirsiniz:

:::code language="csharp" source="snippets/record-types/Program.cs" ID="GrowingDegreeDays":::

Hesaplanan sayıların sayısını, daha yüksek bir temel sıcaklığa sahip olan sayılarla karşılaştırabilirsiniz. Kayıtların *başvuru türleri* olduğunu ve bu kopyaların basit kopyalardır olduğunu unutmayın. Verilerin dizisi kopyalanmaz, ancak her iki kayıt de aynı verilere başvurur. Bu olgu, başka bir senaryoda avantajlıdır. Büyüyen derece gün boyunca, önceki 5 güne ait toplamın izlenmesi yararlı olur. İfadeleri kullanarak farklı kaynak verilerle yeni kayıtlar oluşturabilirsiniz `with` . Aşağıdaki kod bu accumulations koleksiyonunu oluşturur, sonra değerleri görüntüler:

:::code language="csharp" source="snippets/record-types/Program.cs" ID="RunningFiveDayTotal":::

Ayrıca, `with` kayıtların kopyalarını oluşturmak için ifadeleri kullanabilirsiniz. İfadenin küme ayraçları arasında herhangi bir özellik belirtmeyin `with` . Bu, bir kopya oluşturma ve hiçbir özelliği değiştirmeyin anlamına gelir:

```csharp
var growingDegreeDaysCopy = growingDegreeDays with { };
```

Sonuçları görmek için tamamlanmış uygulamayı çalıştırın.

## <a name="summary"></a>Özet

Bu öğretici kayıtların çeşitli yönlerini gösterdi. Kayıtlar, temel kullanım verilerinin depolandığı başvuru türleri için kısa sözdizimi sağlar. Nesne odaklı sınıflar için temel kullanım, sorumlulukları tanımlıyor. Bu öğreticide, bir kaydın yalnızca init özelliklerini bildirmek için kısa bir sözdizimi kullanabileceğiniz *konumsal kayıtlara* odaklanılmıştır. Derleyici, kayıtları kopyalamak ve karşılaştırmak için kaydın birkaç üyesini birleştirir. Kayıt türleriniz için gereken diğer üyeleri ekleyebilirsiniz. Derleyici tarafından oluşturulan üyelerden hiçbirinin durum olarak bilinmediği farkında olmak üzere sabit kayıt türleri oluşturabilirsiniz. Ve `with` ifadeleri, bozucu olmayan mutasyon desteğini desteklemeyi kolaylaştırır.

Kayıtlar, türleri tanımlamaya yönelik başka bir yol ekler. `class`Nesnelerin sorumluluklarına ve davranışına odaklanarak nesne odaklı hiyerarşiler oluşturmak için tanımları kullanırsınız. `struct`Verileri depolayan ve kopyalamaya yetecek kadar az olan veri yapıları için türler oluşturursunuz. `record`Değer tabanlı eşitlik ve karşılaştırma istediğinizde, değerleri kopyalamak istemezsiniz ve başvuru değişkenlerini kullanmak istiyorsanız türler oluşturabilirsiniz.

Kayıt türü ve [Önerilen kayıt türü belirtimi](~/_csharplang/proposals/csharp-9.0/records.md) [için C# dil başvurusu makalesini](../../language-reference/builtin-types/record.md) okuyarak kayıtların tüm açıklamasını öğrenebilirsiniz.
