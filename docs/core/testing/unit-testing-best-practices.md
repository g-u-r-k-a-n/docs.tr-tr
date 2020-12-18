---
title: Birim testlerini yazmak için en iyi uygulamalar
description: .NET Core ve .NET Standard projeleri için Code Quality ve esnekliği çalıştıran birim testlerini yazmak için en iyi yöntemleri öğrenin.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 56f51cde0e52a9e6a38e5291c81470beee61adef
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678109"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a>.NET Core ve .NET Standard ile birim testi en iyi uygulamaları

Birim testlerini yazmanın çok sayıda avantajı vardır; gerileme sayesinde, belge sağlar ve iyi tasarımı kolaylaştırır. Ancak, okuma ve Brittle birim testleri, kod tabanınız üzerinde wreak düzensizliğe olabilir. Bu makalede, .NET Core ve .NET Standard projeleriniz için birim testi tasarımı ile ilgili bazı en iyi yöntemler açıklanmaktadır.

Bu kılavuzda, testlerinizi dayanıklı ve kolay bir şekilde anlamak için birim testlerini yazarken bazı en iyi yöntemleri öğreneceksiniz.

[John Reese](https://reese.dev) tarafından, [Roy Osherove](https://osherove.com/) için teşekkürler

## <a name="why-unit-test"></a>Birim testi neden?

### <a name="less-time-performing-functional-tests"></a>İşlevsel testleri daha az zaman gerçekleştiriyor

İşlevsel testler pahalıdır. Genellikle uygulamayı açıp, beklenen davranışı doğrulamak için sizin (ya da başka birinin) izlemeniz gereken bir dizi adımı gerçekleştirerek. Bu adımlar, her zaman sınayıcı tarafından bilinmeyebilir, bu da testi yürütmek için alana daha bilgili bir kişiye ulaşmaları gerektiği anlamına gelir. Kendisini test etmek, önemsiz değişiklikler için saniye veya daha büyük değişiklikler için dakikalar alabilir. Son olarak, bu işlem sistemde yaptığınız her değişiklik için tekrarlanmış olmalıdır.

Diğer yandan birim testleri, diğer taraftan, bir düğmenin basakında çalışabilir ve çok büyük bir sistem bilgisi gerektirmez. Testin başarılı veya başarısız olmasına bakılmaksızın, bireysel olarak değil Test Çalıştırıcısına.

### <a name="protection-against-regression"></a>Gerileme karşı koruma

Gerileme hataları, uygulamada bir değişiklik yapıldığında ortaya çıkan arızalardır. Test ediciler için, yalnızca yeni özelliklerini test etmek ve daha önce uygulanan özelliklerin beklendiği gibi çalıştığını doğrulamak için önceden varolan özellikleri test etmek yaygın bir özelliktir.

Birim testinde, her derlemeden sonra veya bir kod satırını değiştirdikten sonra bile tüm test paketlerinizi yeniden çalıştırmak mümkündür. Yeni kodunuzun mevcut işlevselliği bozmadığından emin olabilirsiniz.

### <a name="executable-documentation"></a>Yürütülebilir belge

Belirli bir yöntemin ne yaptığını veya belirli bir giriş verilen bir girişi nasıl davranacağını her zaman açık olmayabilir. Kendinize şunu sorabilirsiniz: boş bir dize geçirdiğimde bu yöntem nasıl davranır? Değer?

Bir iyi adlı birim testi paketiniz olduğunda, her bir test, belirli bir giriş için beklenen çıktıyı açıkça açıklayabilmelidir. Ayrıca, aslında gerçekten çalıştığını doğrulayabilmelidir.

### <a name="less-coupled-code"></a>Daha az bağlanmış kod

Kod sıkı bir şekilde birleştirildiğinde, birim testi zor olabilir. Yazmakta olduğunuz kod için birim testleri oluşturmadan, bağlantısı daha az görünebilir.

Kodunuz için yazma testleri doğal olarak kodunuzu ayırır, çünkü aksi takdirde test daha zordur.

## <a name="characteristics-of-a-good-unit-test"></a>İyi birim testinin özellikleri

- **Hızlı**. Yetişkinlere yönelik projelerin binlerce birim testi olması için bu, yaygın olmayan bir durumdur. Birim testlerinin çalışması çok az zaman almalıdır. Mayacak.
- **Yalıtılmış**. Birim testleri tek başına, yalıtımıyla çalıştırılabilir ve dosya sistemi veya veritabanı gibi herhangi bir dış faktörde bağımlılığı yoktur.
- **Yinelenebilir**. Bir birim testinin çalıştırılması sonuçlarıyla tutarlı olmalıdır, diğer bir deyişle, çalışma arasındaki herhangi bir şeyi değiştirmemelisiniz, her zaman aynı sonucu döndürür.
- **Kendi kendine denetim**. Testin, herhangi bir insan etkileşimi olmadan başarılı veya başarısız olup olmadığını otomatik olarak algılayabilmesi gerekir.
- **Zamanında**. Bir birim testinin, test edilmekte olan koda kıyasla yazılması, ne zaman orantılı bir şekilde sürmemelidir. Kodu yazmaya kıyasla kodun büyük bir süre sürmesi sınamasını fark ederseniz, daha fazla test edilen bir tasarıma göz önünde bulundurun.

## <a name="code-coverage"></a>Kod kapsamı

Yüksek kod kapsamı yüzdesi genellikle daha yüksek bir kod kalitesiyle ilişkilendirilir. Ancak, *ölçümün kendisi kodun kalitesini belirleyemez.* Aşırı hırslı kod kapsamı yüzdesi hedefini ayarlamak, karşı üretken olabilir. Binlerce koşullu dalı olan karmaşık bir projeyi düşünün ve %95 kod kapsamının hedefini ayarlayadığınızı düşünelim. Şu anda proje %90 kod kapsamını tutar. Kalan %5 ' teki tüm uç durumlarının hesaba alınması için gereken süre, büyük ölçüde düşük bir miktar olabilir ve değer teklifi hızla azalmıştır.

Yüksek kod kapsamı yüzdesi başarı göstergesi değildir ve yüksek kod kalitesini göstermez. Yalnızca birim testleri kapsamındaki kod miktarını temsil eder. Daha fazla bilgi için bkz. [birim testi kod kapsamı](unit-testing-code-coverage.md).

## <a name="lets-speak-the-same-language"></a>Aynı dili konuşalım

Test hakkında konuşurken, *sahte* terimi genellikle kötüye kullanılır. Aşağıdaki noktaları, birim testlerini yazarken en yaygın *Fakes* türlerini tanımlar:

*Sahte* -sahte, bir saplama veya bir sahte nesne tanımlamakta kullanılabilecek genel bir terimdir. Bunun bir saplama veya bir sahte olup olmadığı, kullanıldığı bağlama göre değişir. Diğer bir deyişle, sahte bir saplama veya bir sahte olabilir.

*Sahte nesne* , sistem içindeki bir birim testinin geçtiğini veya başarısız olduğunu belirten sahte bir nesnedir. Bir sahte, buna karşılık gelene kadar sahte olarak başlatılır.

*Saplama* -bir saplama, sistemdeki mevcut bir bağımlılık (veya ortak çalışan) için denetlenebilir bir değiştirme işlemi olur. Bir saplama kullanarak, doğrudan bağımlılık ile ilgilenmeden kodunuzu test edebilirsiniz. Varsayılan olarak, bir saplama sahte olarak başlatılır.

Aşağıdaki kod parçacığını göz önünde bulundurun:

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Bu, sahte olarak başvurulan bir saplama örneği olacaktır. Bu durumda, bir saplama olur. Siparişi, örneklendirilecek (test edilen sistem) bir yol olarak geçiriyoruz `Purchase` . Ad `MockOrder` aynı zamanda yanıltıcı olduğundan, sıra bir sahte değildir.

Daha iyi bir yaklaşım

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Sınıfını olarak yeniden adlandırarak, sınıfı çok `FakeOrder` daha genel hale getirdiğiniz için sınıf, bir sahte veya saplama olarak kullanılabilir. Test çalışması için ne olursa daha iyidir. Yukarıdaki örnekte, `FakeOrder` bir saplama olarak kullanılır. `FakeOrder`Onaylama sırasında herhangi bir şekil veya formda öğesini kullanmıyoruz. `FakeOrder``Purchase`, oluşturucunun gereksinimlerini karşılamak için sınıfına geçildi.

Bunu bir sahte olarak kullanmak için şöyle bir şey yapabilirsiniz

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

Bu durumda, bir özelliği sahte (buna karşı) olarak denetlemekte, yukarıdaki kod parçacığında bir `mockOrder` sahte olur.

> [!IMPORTANT]
> Bu terminolojinin doğru olması önemlidir. Saplailerinizi "izlerinizi" çağırırsanız, diğer geliştiriciler sizin amacınızla ilgili yanlış varsayımlar yapar.

Her şeyi ve saplamalar hakkında hatırlayabilmeniz gereken ana şey, her bir saplamaya benzer ancak sahte nesne ile ilgili olarak sizin için onay almanız gerekir.

## <a name="best-practices"></a>En iyi uygulamalar

Birim testlerini yazarken altyapıya bağımlılıklar tanıtmamanızda deneyin. Bunlar testleri yavaş ve Brittle yapar ve tümleştirme testleri için ayrılmış olmalıdır. [Açık bağımlılıklar ilkesini](https://deviq.com/explicit-dependencies-principle) Izleyerek ve [bağımlılık ekleme](../extensions/dependency-injection.md)'yi kullanarak uygulamanızdaki bu bağımlılıklardan kaçınabilirsiniz. Ayrıca, birim testlerinizi tümleştirme testlerinizden ayrı bir projede tutabilirsiniz. Bu, birim testi projenizin altyapı paketlerine yönelik başvuruları veya bağımlılıkları olmamasını sağlar.

### <a name="naming-your-tests"></a>Testlerinizi adlandırma

Testinizin adı üç bölümden oluşmalıdır:

- Test edilmekte olan yöntemin adı.
- Altında test edilmekte olan senaryo.
- Senaryo çağrıldığında beklenen davranış.

#### <a name="why"></a>Neden?

- Adlandırma standartları, testin amacını açıkça ifade ettiğinden önemlidir.

Testler yalnızca kodunuzun çalıştığından emin olmanızı sağlamaktan daha fazla. Yalnızca birim testleri paketine bakarak, kodun kendisini araymaksızın bile kodunuzun davranışını çıkarsanbilmelisiniz. Ayrıca, testler başarısız olduğunda, beklentilerinizi tam olarak hangi senaryoların karşılayabileceğini görebilirsiniz.

#### <a name="bad"></a>Kötü:

[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>Görünmesi

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>Testlerinizi düzenleme

Birim testi yaparken, **düzenleme, Yasası, onaylama** ortak bir modeldir. Adından da anlaşılacağı gibi, üç ana eylemden oluşur:

- Nesnelerinizi *düzenleyin* , oluşturma ve bunları gerektiği şekilde ayarlama.
- Bir nesne üzerinde *işlem* yapın.
- Bir şeyin beklenildiği konusunda bir *onaylama* .

#### <a name="why"></a>Neden?

- , *Düzenleme* ve *onaylama* adımlarından ne test edildiğini açıkça ayırır.
- "Yasası" kodu ile onayların nasıl karıştıracağından daha az şans vardır.

Okunabilirlik, bir testi yazarken en önemli yönlerden biridir. Test içindeki bu eylemlerin her birini, kodunuzun çağrılması için gereken bağımlılıkları, kodunuzun nasıl çağrılacağını ve ne yapmaya çalıştığınız hakkında açık bir şekilde vurgulayın. Bazı adımları birleştirmek ve testinizin boyutunu azaltmak mümkün olsa da, birincil hedef, testi mümkün olduğunca okunabilir hale getirmek olacaktır.

#### <a name="bad"></a>Kötü:

[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>Görünmesi

[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>Testleri en düşük düzeyde geçirmeyi yaz

Bir birim testinde kullanılacak giriş, şu anda sınamakta olduğunuz davranışı doğrulamak için en basit olabilmelidir.

#### <a name="why"></a>Neden?

- Testler, kod temelinin gelecekteki değişikliklerine daha dayanıklı hale gelir.
- Uygulama üzerinde test davranışına daha yakın.

Testi geçirmek için gerekenden daha fazla bilgi içeren testlerin, teste hata ekleme şansı daha yüksektir ve testin amacını daha az net hale getirebilirsiniz. Testleri yazarken davranışa odaklanmak istersiniz. Modellerdeki ek özellikleri ayarlama veya gerekmediği zaman sıfır olmayan değerler kullanma, yalnızca kanıtlamaya çalıştığınız kadar olan özelliklerden arının.

#### <a name="bad"></a>Kötü:

[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>Görünmesi

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>Sihirli dizelerinden kaçının

Birim testlerinde adlandırma değişkenleri, daha önemli değilse, üretim kodundaki adlandırma değişkenlerinden daha önemli değildir. Birim testleri sihirli dizeler içermemelidir.

#### <a name="why"></a>Neden?

- , Değeri özel hale getiren şeyi anlamak için test okuyucunun üretim kodunu incelemesi gereksinimini ortadan önler.
- *Gerçekleştirmeyi* denemek yerine açıkça *kanıtlamaya* çalıştığınız öğeleri gösterir.

Sihirli dizeler, testlerinizin okuyucularına karışmasına neden olabilir. Bir dize sıradan görünüyorsa, bir parametre veya dönüş değeri için belirli bir değerin seçili olduğunu merak edebilir. Bu, bunlara, teste odaklanmak yerine uygulama ayrıntılarına daha yakından bakmasına neden olabilir.

> [!TIP]
> Testleri yazarken, mümkün olduğunca çok amaç ifade etmeniz gerekir. Sihirli dizeler söz konusu olduğunda, bu değerleri sabitlere atamak iyi bir yaklaşımdır.

#### <a name="bad"></a>Kötü:

[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>Görünmesi

[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>Sınamalarda mantığın

Birim testlerinizi yazarken,,,, `if` `while` `for` vb. el ile dize birleştirmesini ve mantıksal koşulları önleyin `switch` .

#### <a name="why"></a>Neden?

- Testlerinizin içindeki bir hatayı tanıtmak için daha az şans.
- Uygulama ayrıntıları yerine son sonuca odaklanın.

Test paketiniz için mantık tanıdığınızda, hataya bir hata tanıtma olasılığı önemli ölçüde artar. Bir hata bulmak istediğiniz son yer, test paketinizin içindedir. Testlerinizin çalışması için yüksek düzeyde bir güveniniz olması gerekir, aksi takdirde bunlara güvenmemelisiniz. Güvenmediğiniz testler, hiçbir değer sağlamaz. Bir test başarısız olduğunda, kodunuzun kodunuzda gerçekten yanlış olduğunu ve yoksayılıp yoksayılmayacağını belirten bir fikir sahibi olmak istersiniz.

> [!TIP]
> Testinizin mantığı kaçınılmaz görünüyorsa, testi iki veya daha fazla farklı teste bölmeyi göz önünde bulundurun.

#### <a name="bad"></a>Kötü:

[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>Görünmesi

[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>Kurulum ve test etmek için yardımcı yöntemleri tercih etme

Testleriniz için benzer bir nesne veya durum gerekiyorsa, kullanmaktan `Setup` ve niteliklerinden bir yardımcı yöntemi tercih edin `Teardown` .

#### <a name="why"></a>Neden?

- Tüm kod her test içinde görünür olduğundan testleri okurken daha az karışıklık vardır.
- Verilen test için çok fazla veya çok az olma olasılığı daha düşüktür.
- Testler arasında istenmeyen bağımlılıklar oluşturan testler arasında durum paylaşma şansı daha düşüktür.

Birim testi çerçeveleri ' nde, `Setup` test paketinizdeki her bir ve her birim testinin önünde çağrılır. Bazıları bunu yararlı bir araç olarak görebilir, ancak testleri okumak için genellikle önde gelen ve zor olacak şekilde sona erer. Her test, testi çalıştırmak ve çalıştırmak için genellikle farklı gereksinimlere sahip olur. Ne yazık ki, `Setup` her test için tam olarak aynı gereksinimleri kullanmanıza zorlar.

> [!NOTE]
> xUnit, sürüm 2. x itibariyle kurulum ve test düzeyini kaldırdı

#### <a name="bad"></a>Kötü:

[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>Görünmesi

[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>Çoklu Onaylamalar kullanmaktan kaçının

Testlerinizi yazarken, her test için yalnızca bir onaylama eklemeyi deneyin. Yalnızca bir onay kullanımı için yaygın yaklaşımlar şunlardır:

- Her onaylama için ayrı bir test oluşturun.
- Parametreli testleri kullanın.

#### <a name="why"></a>Neden?

- Bir onaylama başarısız olursa, sonraki onaylar değerlendirilmeyecektir.
- Testlerinizde birden çok durumu ele almanızı sağlar.
- Testlerinizin neden başarısız olduğuna ilişkin tüm resmi verir.

Bir test çalışması için birden fazla onay tanıtımı yaparken, tüm Onaylamalar yürütülecektir. Çoğu birim testi çerçevesi içinde, bir onaylama işlemi bir birim testinde başarısız olduktan sonra, devam eden testler otomatik olarak başarısız sayılır. Bu, gerçekten çalışmakta olan bir işlev kadar kafa karıştırıcı olabilir, ancak başarısız olarak gösterilir.

> [!NOTE]
> Bu kural için genel bir özel durum, bir nesneye yönelik olarak ele geçmiştir. Bu durumda, nesnenin içinde olmasını istediğiniz durumda olduğundan emin olmak için her bir özelliğe karşı birden fazla onay sağlamak kabul edilebilir.

#### <a name="bad"></a>Kötü:

[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>Görünmesi

[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>Özel metotları birim testi genel yöntemlerine göre doğrula

Çoğu durumda, özel bir yöntemi test etmek zorunda değildir. Özel yöntemler bir uygulama ayrıntısıyla yapılır. Bunu şu şekilde düşünebilirsiniz: özel yöntemler hiçbir şekilde yalıtımına yok. Bir noktada, uygulamasının bir parçası olarak özel yöntemi çağıran bir genel kullanıma yönelik yöntem olacaktır. İlgilenmelisiniz, özel bir yönteme çağrı yapan genel metodun nihai sonucudur.

Aşağıdaki durumu göz önünde bulundurun

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

`TrimInput`Yöntemin beklendiği gibi çalıştığından emin olmak istediğiniz için ilk yeniden eyleminiz bir test yazmaya başlayabilir. Ancak, bu `ParseLogLine` `sanitizedInput` şekilde, bir testi gereksiz bir şekilde işlemek için beklenmez `TrimInput` .

Gerçek test, `ParseLogLine` en sonunda ilgilenmelisiniz çünkü bu, son önem verdiğiniz şeydir.

```csharp
public void ParseLogLine_StartsAndEndsWithSpace_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

Bu görüş açısından, özel bir yöntem görürseniz ortak yöntemi bulun ve testlerinizi bu yönteme göre yazın. Özel bir yöntem beklenen sonucu döndürdüğünden, sonuçta özel yöntemi çağıran sistem sonucu doğru bir şekilde kullanır.

### <a name="stub-static-references"></a>Saplama statik başvuruları

Bir birim testinin prensipleri, test altındaki sistem üzerinde tam denetime sahip olması gerekir. Bu, üretim kodu statik başvurulara çağrı içerdiğinde (örneğin,) sorunlu olabilir `DateTime.Now` . Aşağıdaki kodu göz önünde bulundurun

```csharp
public int GetDiscountedPrice(int price)
{
    if (DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

Bu kod büyük olasılıkla birim test edilebilir mi? Şöyle bir yaklaşım deneyebilirsiniz

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

Ne yazık ki testlerinizde birkaç sorun olduğunu hızla fark edersiniz.

- Test paketi bir Salı üzerinde çalışıyorsa ikinci test geçer, ancak ilk test başarısız olur.
- Test paketi başka bir gün üzerinde çalışıyorsa, ilk test geçer, ancak ikinci test başarısız olur.

Bu sorunları gidermek için, üretim kodunuzda bir *yhar* belirlemeniz gerekir. Bir yaklaşım, bir arabirimde denetim yapmanız gereken kodu sarmanın ve üretim kodunun bu arabirime bağlı olmasını kullanmaktır.

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if (dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

Test paketiniz artık

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

Artık test paketinin üzerinde tam denetimi vardır `DateTime.Now` ve yöntemine çağrı yapıldığında herhangi bir değer bulunabilir.
