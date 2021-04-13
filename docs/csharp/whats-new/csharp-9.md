---
title: C# 9,0 ' deki yenilikler-C# Kılavuzu
description: C# 9,0 ' de bulunan yeni özelliklere genel bakış alın.
ms.date: 04/07/2021
ms.openlocfilehash: c2189d2db175a40c24d6a41d20f2ae2d9384513b
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255343"
---
# <a name="whats-new-in-c-90"></a>C# 9.0 sürümündeki yenilikler

C# 9,0, C# diline aşağıdaki özellikleri ve geliştirmeleri ekler:

- [Kayıtlar](#record-types)
- [Yalnızca init ayarlayıcılar](#init-only-setters)
- [Üst düzey deyimler](#top-level-statements)
- [Desen eşleştirme geliştirmeleri](#pattern-matching-enhancements)
- [Performans ve birlikte çalışma](#performance-and-interop)
  - Yerel boyutlu tamsayılar
  - İşlev işaretçileri
  - Yaymayı localsinit bayrağını gösterme
- [Sığdırma ve son özellikler](#fit-and-finish-features)
  - Hedef türü belirtilmiş `new` ifadeler
  - statik anonim işlevler
  - Hedef türü belirlenmiş Koşullu ifadeler
  - Birlikte değişken dönüş türleri
  - `GetEnumerator`Döngüler için uzantı desteği `foreach`
  - Lambda atma parametreleri
  - Yerel işlevlerlerde öznitelikler
- [Kod oluşturucuları için destek](#support-for-code-generators)
  - Modül başlatıcılar
  - Kısmi yöntemlere yönelik yeni özellikler

C# 9,0, **.NET 5**' te desteklenir. Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../language-reference/configure-language-version.md).

[.Net İndirmeleri sayfasından](https://dotnet.microsoft.com/download)en son .NET SDK 'sını indirebilirsiniz.

## <a name="record-types"></a>Kayıt türleri

C# 9,0 ***kayıt türlerini*** tanıtır. `record`Verileri kapsüllemek için yerleşik işlevsellik sağlayan bir başvuru türü tanımlamak için anahtar sözcüğünü kullanırsınız. Konumsal parametreleri veya standart özellik sözdizimini kullanarak, değişmez özelliklerle kayıt türleri oluşturabilirsiniz:

:::code language="csharp" source="../language-reference/builtin-types/snippets/shared/RecordType.cs" id="PositionalRecord":::
:::code language="csharp" source="../language-reference/builtin-types/snippets/shared/RecordType.cs" id="ImmutableRecord":::

Ayrıca, değişebilir Özellikler ve alanlarla kayıt türleri de oluşturabilirsiniz:

:::code language="csharp" source="../language-reference/builtin-types/snippets/shared/RecordType.cs" id="MutableRecord":::

Kayıtlar değişebilir olsa da, Bunlar öncelikle sabit veri modellerini desteklemeye yöneliktir. Kayıt türü aşağıdaki özellikleri sunar:

* [Sabit özelliklerle başvuru türü oluşturmak için kısa sözdizimi](#positional-syntax-for-property-definition)
* Davranış, veri merkezli bir başvuru türü için yararlıdır:
  * [Değer eşitlik](#value-equality)
  * [Geri dönüşlü mutasyon için kısa sözdizimi](#nondestructive-mutation)
  * [Görüntüleme için yerleşik biçimlendirme](#built-in-formatting-for-display)
* [Devralma hiyerarşileri için destek](#inheritance)

Değer eşitlik ve çok az davranış sağlayan veri merkezli türler tasarlamak için [yapı türlerini](../language-reference/builtin-types/struct.md) kullanabilirsiniz. Ancak görece büyük veri modelleri için yapı türlerinin bazı dezavantajları vardır:

* Devralma desteği yoktur.
* Değer eşitliğini belirlemede daha az verimlidir. Değer türlerinde, <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> yöntemi tüm alanları bulmak için yansıma kullanır. Kayıtlar için derleyici `Equals` yöntemini oluşturur. Uygulamada, kayıtlardaki değer eşitlik uygulaması yaşamları daha hızlıdır.
* Her örnek tüm verilerin tamamen bir kopyasına sahip olduğundan, bazı senaryolarda daha fazla bellek kullanırlar. Kayıt türleri [başvuru türlerdir](../language-reference/builtin-types/reference-types.md), bu nedenle bir kayıt örneği yalnızca verilerin bir başvurusunu içerir.

### <a name="positional-syntax-for-property-definition"></a>Özellik tanımı için Konumsal sözdizimi

Bir kaydın özelliklerini bildirmek ve bir örnek oluştururken özellik değerlerini başlatmak için Konumsal parametreleri kullanabilirsiniz:

:::code language="csharp" source="../language-reference/builtin-types/snippets/shared/RecordType.cs" id="InstantiatePositional":::

Özellik tanımı için Konumsal sözdizimini kullandığınızda, derleyici şunları oluşturur:

* Kayıt bildiriminde belirtilen her Konumsal parametre için genel bir init-tek otomatik uygulanan özellik. [Yalnızca bir init](../language-reference/keywords/init.md) özelliği, oluşturucuda veya bir özellik başlatıcısı kullanılarak ayarlanabilir.
* Parametreleri, kayıt bildiriminde konumsal parametrelerle eşleşen bir birincil Oluşturucu.
* `Deconstruct` `out` Kayıt bildiriminde belirtilen her Konumsal parametre için parametreye sahip bir yöntem.

Daha fazla bilgi için bkz. kayıtlar hakkında C# dil başvurusu makalesindeki [konumsal sözdizimi](../language-reference/builtin-types/record.md#positional-syntax-for-property-definition) .

### <a name="immutability"></a>Değiştirilemezlik

Kayıt türü sabit değildir. Özellikleri, `set` erişimciler ve olmayan alanlarla bildirebilirsiniz `readonly` . Ancak kayıtlar değişebilir, ancak değişmez veri modelleri oluşturmayı kolaylaştırır. Konumsal sözdizimi kullanarak oluşturduğunuz özellikler sabittir.

Bir karma tabloda, veri merkezli bir türün iş parçacığı açısından güvenli olmasını veya karma kodun aynı kalmasını istediğinizde yararlı olabilir. Bir bağımsız değişkeni bir yönteme başvuruya göre geçirdiğinizde meydana gelen hataları önleyebilir ve Yöntem bağımsız değişken değerini beklenmedik şekilde değiştirir.

Kayıt türlerine özgü özellikler derleyici birleştirilmemiş yöntemler tarafından uygulanır ve bu yöntemlerin hiçbiri, nesne durumunu değiştirerek değişiklik imkanlarını önler.

### <a name="value-equality"></a>Değer eşitlik

Değer eşitliği, türlerin eşleşmesi ve tüm özellik ve alan değerleri eşleşiyorsa bir kayıt türünün iki değişkeninin eşit olduğu anlamına gelir. Diğer başvuru türleri için eşitlik, kimlik anlamına gelir. Diğer bir deyişle, bir başvuru türünün iki değişkeni aynı nesneye başvurduklarında eşittir.

Aşağıdaki örnek, kayıt türlerinin değer eşitliğini gösterir:

:::code language="csharp" source="../language-reference/builtin-types/snippets/shared/RecordType.cs" id="Equality":::

Türler ' de `class` , eşitlik yöntemlerini ve işleçleri değer eşitlik elde etmek için el ile geçersiz kılabilirsiniz, ancak bu kodun geliştirilmesi ve test edilmesi zaman alabilir ve hataya açıktır. Bu işlevin yerleşik olması, özellikler veya alanlar eklendiğinde veya değiştirildiğinde özel geçersiz kılma kodunu güncelleştirmeye neden olan hataları önler.

Daha fazla bilgi için bkz. kayıtlar hakkında C# dil başvurusu makalesindeki [değer eşitlik](../language-reference/builtin-types/record.md#value-equality) .

### <a name="nondestructive-mutation"></a>Geri dönüşlü mutasyon

Bir kayıt örneğinin sabit özelliklerini mukumanız gerekirse, geri dönüşlü bir zaman `with` elde etmek için bir ifade kullanabilirsiniz . Bir `with` ifade, belirtilen özellikler ve alanlarla değiştirilen mevcut bir kayıt örneğinin kopyası olan yeni bir kayıt örneği oluşturur. Aşağıdaki örnekte gösterildiği gibi, değiştirilecek değerleri belirtmek için [nesne Başlatıcısı](../programming-guide/classes-and-structs/object-and-collection-initializers.md) sözdizimini kullanın:

:::code language="csharp" source="../language-reference/builtin-types/snippets/shared/RecordType.cs" id="WithExpressions":::

Daha fazla bilgi için bkz. kayıtlar hakkında C# dil başvurusu makalesindeki geri [dönüşlü bir mutasyon](../language-reference/builtin-types/record.md#nondestructive-mutation) .

### <a name="built-in-formatting-for-display"></a>Görüntüleme için yerleşik biçimlendirme

Kayıt türlerinde <xref:System.Object.ToString%2A> , ortak özelliklerin ve alanların adlarını ve değerlerini görüntüleyen bir derleyici tarafından oluşturulan yöntem vardır. `ToString`Yöntemi aşağıdaki biçimde bir dize döndürür:

> \<record type name> { \<property name> = \<value>, \<property name> = \<value>, ...}

Başvuru türleri için, özelliğin başvurduğu nesnenin tür adı, özellik değeri yerine görüntülenir. Aşağıdaki örnekte, dizi bir başvuru türüdür, bu nedenle `System.String[]` gerçek dizi öğesi değerleri yerine görüntülenir:

```
Person { FirstName = Nancy, LastName = Davolio, ChildNames = System.String[] }
```

Daha fazla bilgi için bkz. kayıtlar hakkında C# dil başvurusu makalesindeki [yerleşik biçimlendirme](../language-reference/builtin-types/record.md#built-in-formatting-for-display) .

### <a name="inheritance"></a>Devralma

Bir kayıt, başka bir kayıttan devralınabilir. Ancak, bir kayıt bir sınıftan devralınabilir ve bir sınıf bir kayıttan devralınabilir.

Aşağıdaki örnek, konumsal Özellik söz dizimi ile devralmayı göstermektedir:

:::code language="csharp" source="../language-reference/builtin-types/snippets/shared/RecordType.cs" id="PositionalInheritance":::

İki kayıt değişkeninin eşit olması için, çalışma zamanı türünün eşit olması gerekir. Kapsayan değişkenlerin türleri farklı olabilir. Bu, aşağıdaki kod örneğinde gösterilmektedir:

:::code language="csharp" source="../language-reference/builtin-types/snippets/shared/RecordType.cs" id="InheritanceEquality":::

Örnekte, tüm örnekler aynı özelliklere ve aynı özellik değerlerine sahiptir. `student == teacher`, Ancak `False` her iki `Person` tür değişken de döndürür. Ve `student == student2` `True` biri değişken, diğeri ise bir `Person` `Student` değişkendir.

Türetilmiş ve temel türlerin tüm ortak özellikleri ve alanları `ToString` , aşağıdaki örnekte gösterildiği gibi çıkışa dahil edilmiştir:

:::code language="csharp" source="../language-reference/builtin-types/snippets/shared/RecordType.cs" id="ToStringInheritance":::

Daha fazla bilgi için bkz. kayıtlar hakkında C# dil başvurusu makalesindeki [Devralma](../language-reference/builtin-types/record.md#inheritance) .

## <a name="init-only-setters"></a>Yalnızca init ayarlayıcılar

***Init Only Setter*** bir nesnenin üyelerini başlatmak için tutarlı sözdizimi sağlar. Özellik başlatıcıları, hangi değerin hangi özelliğin ayarlanmasını temizlesin. Downsıde, bu özelliklerin ayarlanabilir olması gerekir. C# 9,0 ' den başlayarak, `init` `set` Özellikler ve Dizin oluşturucular için erişimciler yerine erişimciler oluşturabilirsiniz. Çağıranlar, oluşturma ifadelerinde bu değerleri ayarlamak için özellik başlatıcısı sözdizimini kullanabilir, ancak oluşturma işlemi tamamlandıktan sonra bu özellikler salt okunur yapılır. Init Only ayarlayıcıları, durumu değiştirecek bir pencere sağlar. Bu pencere, oluşturma aşaması sona erdiğinde kapanır. Özellik başlatıcıları ve WITH ifadeleri dahil olmak üzere, oluşturma aşaması, tüm başlatma sonrasında etkili bir şekilde sona erer.

`init`Yalnızca yazdığınız herhangi bir tür için ayarlayıcıları bildirebilirsiniz. Örneğin, aşağıdaki yapı bir hava durumu izleme yapısını tanımlar:

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="DeclareWeatherObservation":::

Çağıranlar, değerleri ayarlamak için özellik başlatıcısı sözdizimini kullanabilir, ancak yine de dengesizin kullanılabilirliği korunur:

:::code language="csharp" source="snippets/whats-new-csharp9/WeatherObservation.cs" ID="UseWeatherObservation":::

Başlatma sonrasında bir gözlemden sonra bir izleme değişikliği girişimi bir derleyici hatası ile sonuçlanır:

```csharp
// Error! CS8852.
now.TemperatureInCelsius = 18;
```

Yalnızca Init ayarlayıcıları, türetilmiş sınıflardan temel sınıf özellikleri ayarlamak için yararlı olabilir. Ayrıca, bir temel sınıftaki yardımcılar aracılığıyla türetilmiş özellikleri de ayarlayabilir. Konumsal kayıtlar yalnızca init ayarlayıcıları kullanarak özellikleri bildirir. Bu ayarlayıcılar,-ifadelerinde kullanılır. Herhangi bir `class` , veya tanımladığınız için init Only ayarlayıcıları bildirebilirsiniz `struct` `record` .

Daha fazla bilgi için bkz. [init (C# Başvurusu)](../language-reference/keywords/init.md).

## <a name="top-level-statements"></a>Üst düzey deyimler

***Üst düzey deyimler*** pek çok uygulamadan gereksiz seremonony 'yi kaldırır. "Merhaba Dünya!" kurallı öğesini düşünün programda

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Her şeyi yapan tek bir kod satırı vardır. En üst düzey deyimlerle, bu ortak olan tüm ortak, `using` yönergeyi ve işi yapan tek satırı değiştirebilirsiniz:

:::code language="csharp" source="snippets/whats-new-csharp9/Program.cs" ID="TopLevelStatements":::

Tek satırlık bir program istediyseniz, `using` yönergeyi kaldırabilir ve tam nitelikli tür adını kullanabilirsiniz:

```csharp
System.Console.WriteLine("Hello World!");
```

Uygulamanızdaki yalnızca bir dosya en üst düzey deyimleri kullanabilir. Derleyici birden çok kaynak dosyasında en üst düzey deyimler bulursa, bu bir hatadır. En üst düzey deyimleri, genellikle bir yöntemi olan, belirtilen bir program giriş noktası yöntemiyle birleştirirseniz de bir hatadır `Main` . Bir anlamda, bir dosyanın normalde bir sınıf yönteminde olacak deyimleri içerdiğini düşünebilirsiniz `Main` `Program` .  

Bu özellik için en yaygın kullanımdan biri eğitim malzemeleri oluşturuyor. Başlangıç C# geliştiricileri kurallı "Merhaba Dünya!" yazabilir kodda bir veya iki satırda. Ek sertifika gerekmez. Bununla birlikte, deneyimli geliştiriciler bu özellik için birçok kullanım de bulacaktır. En üst düzey deyimler, Jupneter Not defterlerinin sağladığı deneme için bir komut dosyası benzeri deneyim sağlar. En üst düzey deyimler, küçük konsol programları ve yardımcı programlar için harika. [Azure işlevleri](/azure/azure-functions/) , en üst düzey deyimler için ideal bir kullanım durumdur.

En önemlisi, üst düzey deyimler uygulamanızın kapsamını veya karmaşıklığını sınırlamaz. Bu deyimler, herhangi bir .NET sınıfına erişebilir veya kullanabilir. Ayrıca, komut satırı bağımsız değişkenlerinin veya dönüş değerlerinin kullanımını sınırlamaz. Üst düzey deyimler, adlı bir dizeler dizisine erişebilir `args` . En üst düzey deyimler bir tamsayı değeri döndürirse, bu değer sentezlenmiş bir yöntemden tamsayı dönüş kodu olur `Main` . En üst düzey deyimler zaman uyumsuz ifadeler içerebilir. Bu durumda, birleştirilmiş giriş noktası bir `Task` veya döndürür `Task<int>` .

Daha fazla bilgi için C# programlama kılavuzundaki [en üst düzey deyimler](../programming-guide/main-and-command-args/top-level-statements.md) bölümüne bakın.

## <a name="pattern-matching-enhancements"></a>Desen eşleştirme geliştirmeleri

C# 9, yeni bir model eşleşme geliştirmeleri içerir:

- ***Tür desenleri*** bir değişkenle eşleşiyor tür
- ***Parantez Içine alınmış desenler*** , desen birleşimlerinin önceliğini uygular veya vurgular
- ***Ayırt edici `and` desenler*** , her iki desen de eşleşmesini gerektirir
- Ayırt edici ***`or` desenler*** eşleşmesi gereken her iki model
- ***Değillenmiş `not` desenler*** bir düzenin eşleşmemesi gerekir
- ***İlişkisel desenler*** , girişin küçüktür, büyüktür, küçüktür veya eşittir veya belirtilen bir sabitten büyük veya eşit olması gerekir.

Bu desenler, desenlerin sözdizimini zenginleştirin. Aşağıdaki örnekleri göz önünde bulundurun:

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterPattern":::

Daha yüksek önceliğe sahip olması için isteğe bağlı parantezle `and` `or` :

:::code language="csharp" source="snippets/whats-new-csharp9/PatternUtilities.cs" ID="IsLetterOrSeparatorPattern":::

En yaygın kullanımdan biri null denetimi için yeni bir sözdizimidir:

```csharp
if (e is not null)
{
    // ...
}
```

Bu desenlerden herhangi biri desenleri izin verilen herhangi bir bağlamda kullanılabilir: `is` desen ifadeleri, `switch` ifadeler, iç içe desenler ve bir `switch` deyimin `case` etiketinin deseni.

Daha fazla bilgi için bkz. [desenler (C# Başvurusu)](../language-reference/operators/patterns.md).

Daha fazla bilgi için, [desenler](../language-reference/operators/patterns.md) makalesinin [Ilişkisel desenleri](../language-reference/operators/patterns.md#relational-patterns) ve [mantıksal desenler](../language-reference/operators/patterns.md#logical-patterns) bölümlerine bakın.

## <a name="performance-and-interop"></a>Performans ve birlikte çalışma

Üç yeni özellik, yüksek performans gerektiren yerel birlikte çalışma ve alt düzey kitaplıklar desteğini geliştirir: yerel boyutlu tamsayılar, işlev işaretçileri ve `localsinit` bayrağı atlama.

Yerel boyutlu tamsayılar `nint` ve `nuint` , tamsayı türleridir. Bunlar, temel alınan türler ve ile ifade edilir <xref:System.IntPtr?displayProperty=nameWithType> <xref:System.UIntPtr?displayProperty=nameWithType> . Derleyici, bu türler için ek dönüştürmeler ve işlemleri yerel olarak gösterir. Yerel boyutlu tamsayılar veya özelliklerini tanımlar `MaxValue` `MinValue` . Bu değerler, Hedef makinedeki bir tamsayının yerel boyutuna bağlı olduğundan, derleme zamanı sabitleri olarak ifade edilemez. Çalışma zamanında bu değerler salt okunur. `nint`[.. Aralığında için sabit değerler kullanabilirsiniz. `int.MinValue` `int.MaxValue`]. `nuint`[.. Aralığında için sabit değerler kullanabilirsiniz. `uint.MinValue` `uint.MaxValue`]. Derleyici ve türlerini kullanarak tüm birli ve ikili işleçler için sabit katlama gerçekleştirir <xref:System.Int32?displayProperty=nameWithType> <xref:System.UInt32?displayProperty=nameWithType> . Sonuç 32 bite sığmazsa, işlem çalışma zamanında yürütülür ve bir sabit kabul edilmez. Yerel boyutlu tamsayılar, tamsayı matematiğinin yaygın olarak kullanıldığı ve en yüksek performansa sahip olması gereken senaryolarda performansı artırabilir. Daha fazla bilgi için bkz. [ `nint` ve `nuint` türleri](../language-reference/builtin-types/nint-nuint.md)

İşlev işaretçileri, Il işlem kodları ve ' a erişmek için kolay bir sözdizimi sağlar `ldftn` `calli` . Yeni sözdizimini kullanarak işlev işaretçileri bildirebilirsiniz `delegate*` . `delegate*`Tür bir işaretçi türüdür. Yöntemi, `delegate*` yöntemini kullanan `calli` bir temsilcinin aksine, türünü çağırır `callvirt` `Invoke()` . Sözdizimi, çağırma aynıdır. İşlev işaretçisi çağrısı, `managed` çağırma kuralını kullanır. `unmanaged` `delegate*` Çağırma kuralına istediğinizi bildirmek için sözdiziminden sonra anahtar sözcüğünü eklersiniz `unmanaged` . Diğer çağırma kuralları, bildirimde öznitelikler kullanılarak belirtilebilir `delegate*` . Daha fazla bilgi için bkz. [güvenli olmayan kod ve işaretçi türleri](../language-reference/unsafe-code.md).

Son olarak, <xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute?displayProperty=nameWithType> derleyicinin bayrağı yaymamasını sağlamak için öğesini ekleyebilirsiniz `localsinit` . Bu bayrak, CLR 'ye tüm yerel değişkenleri sıfıra başlatmasını söyler. `localsinit`Bayrak, 1,0 sonrasındaki C# için varsayılan davranıştır. Ancak, ek sıfır başlatma bazı senaryolarda ölçülebilir performans etkisine sahip olabilir. Özellikle, kullandığınızda `stackalloc` . Bu gibi durumlarda, ekleyebilirsiniz <xref:System.Runtime.CompilerServices.SkipLocalsInitAttribute> . Tek bir yönteme veya özelliğe veya bir `class` ,, `struct` `interface` veya hatta bir modüle ekleyebilirsiniz. Bu öznitelik yöntemleri etkilemez `abstract` ; uygulama için oluşturulan kodu etkiler. Daha fazla bilgi için bkz. [ `SkipLocalsInit` özniteliği](../language-reference/attributes/general.md#skiplocalsinit-attribute).

Bu özellikler, bazı senaryolarda performansı iyileştirebilir. Bunlar yalnızca, benimseme öncesinde ve sonrasında eklendikten sonra kullanılmalıdır. Yerel boyutlu tamsayılar içeren kodun, farklı tamsayı boyutlarına sahip birden çok hedef platformda test olması gerekir. Diğer özellikler güvenli olmayan kod gerektirir.

## <a name="fit-and-finish-features"></a>Sığdırma ve son özellikler

Diğer özelliklerin çoğu, daha verimli bir şekilde kod yazmanıza yardımcı olur. C# 9,0 ' de, oluşturulan nesnenin türü zaten biliniyorsa bir [ `new` ifadede](../language-reference/operators/new-operator.md) türü atlayabilirsiniz. En yaygın kullanım, alan bildirimlerinde bulunur:

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="WeatherStationField":::

`new`Bir yönteme bağımsız değişken olarak geçirmek için yeni bir nesne oluşturmanız gerektiğinde, target türü de kullanılabilir. `ForecastFor()`Aşağıdaki imzaya sahip bir yöntem düşünün:

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="ForecastSignature":::

Bunu şu şekilde çağırabilirsiniz:

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="TargetTypeNewArgument":::

Bu özellik için bir diğer iyi kullanım, yeni bir nesneyi başlatmak için yalnızca init özellikleriyle birlikte birleştirilmenize yöneliktir:

:::code language="csharp" source="snippets/whats-new-csharp9/FitAndFinish.cs" ID="InitWeatherStation":::

Bir ifadesini kullanarak varsayılan Oluşturucu tarafından oluşturulan bir örnek döndürebilirsiniz `return new();` .

Benzer bir özellik, [koşullu ifadelerin](../language-reference/operators/conditional-operator.md)hedef tür çözümlemesini geliştirir. Bu değişiklik ile, iki ifadenin bir öğesinden diğerine örtük dönüştürmesi gerekmez, ancak her ikisi de hedef tür için örtük Dönüştürmelere sahip olabilir. Büyük olasılıkla bu değişikliği fark edeceksiniz. Ne fark edeceksiniz, daha önce gerekli olan veya derlenmeyen bazı Koşullu ifadeler artık çalışır.

C# 9,0 ' den başlayarak `static` [lambda ifadelerine](../language-reference/operators/lambda-expressions.md) veya [anonim yöntemlere](../language-reference/operators/delegate-operator.md)değiştiricisini ekleyebilirsiniz. Statik lambda ifadeleri `static` Yerel işlevlere benzerdir: statik lambda veya anonim yöntem yerel değişkenleri veya örnek durumunu yakalayabilir. `static`Değiştirici yanlışlıkla diğer değişkenleri yakalamaya engel olur.

Covaryant dönüş türleri, [geçersiz kılma](../language-reference/keywords/override.md) yöntemlerinin dönüş türleri için esneklik sağlar. Geçersiz kılma yöntemi, geçersiz kılınan temel yöntemin dönüş türünden türetilmiş bir tür döndürebilir. Bu, kayıtlar ve sanal kopya ya da fabrika yöntemlerini destekleyen diğer türler için yararlı olabilir.

Buna ek olarak, [ `foreach` döngü](../language-reference/keywords/foreach-in.md) , başka bir şekilde onu karşılayan bir genişletme yöntemi tanır ve kullanır `GetEnumerator` `foreach` . Bu değişiklik, `foreach` zaman uyumsuz model ve model tabanlı ayrıştırma gibi diğer model tabanlı kurulumlarını ile tutarlıdır. Uygulamada, bu değişiklik `foreach` herhangi bir türe destek ekleyebileceğiniz anlamına gelir. Bir nesne Numaralandırırken tasarımınızda anlamlı hale geldiğinde kullanımını sınırlamanız gerekir.

Sonra, Lambda ifadelerinde parametre olarak atar ' i kullanabilirsiniz. Bu kolaylık, bağımsız değişkeni adlandırmayı önlemenize olanak sağlar ve derleyici bunu kullanmaktan kaçınabilir. `_`Herhangi bir bağımsız değişken için öğesini kullanırsınız. Daha fazla bilgi için [lambda ifadeleri](../language-reference/operators/lambda-expressions.md) makalesinin [lambda ifadesinin giriş parametreleri](../language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression) bölümüne bakın.

Son olarak, artık [Yerel işlevlere](../programming-guide/classes-and-structs/local-functions.md)öznitelikler uygulayabilirsiniz. Örneğin, yerel işlevlere [null yapılabilir öznitelik ek açıklamaları](../language-reference/attributes/nullable-analysis.md) uygulayabilirsiniz.

## <a name="support-for-code-generators"></a>Kod oluşturucuları için destek

İki son özellik C# kod üreteçleri destekler. C# kod oluşturucuları, bir Roslyn çözümleyicisine veya kod düzeltmesine benzer şekilde yazabileceğiniz bir bileşendir. Fark, kod oluşturucuların kodu çözümlemelerine ve derleme sürecinin bir parçası olarak yeni kaynak kodu dosyaları yazmanızdır. Tipik bir kod üreticisi öznitelikleri veya diğer kuralları arar.

Kod Oluşturucu, Roslyn Analysis API 'Lerini kullanarak öznitelikleri veya diğer kod öğelerini okur. Bu bilgilerden, derlemeye yeni kod ekler. Kaynak oluşturucuları yalnızca kod ekleyebilir; Bu kişiler, derlemede var olan herhangi bir kodu değiştirmesine izin verilmez.

Kod üreticileri için eklenen iki özellik, ***kısmi Yöntem sözdizimi** _ ve _ *_Modül başlatıcıları_* * için uzantılardır. Birincisi, kısmi metotlarda yapılan değişiklikler. C# 9,0 öncesi, kısmi Yöntemler, bir `private` erişim değiştiricisi `void` belirtmemelidir, geri dönemeyebilir ve parametrelere sahip olamaz `out` . Bu kısıtlamalar, hiçbir yöntem uygulama sağlanmazsa, derleyicinin kısmi yönteme yapılan tüm çağrıları kaldırmasının anlamına gelir. C# 9,0 bu kısıtlamaları ortadan kaldırır, ancak kısmi Yöntem bildirimlerinin bir uygulamaya sahip olmasını gerektirir. Kod oluşturucuları, bu uygulamayı sağlayabilir. Yeni bir değişiklik yapmaktan kaçınmak için, derleyici eski kuralları takip etmek üzere bir erişim değiştiricisi olmadan herhangi bir kısmi yöntemi dikkate alır. Kısmi Yöntem `private` erişim değiştiricisini içeriyorsa, yeni kurallar bu kısmi yöntemi yönetir. Daha fazla bilgi için bkz. [kısmi Yöntem (C# Başvurusu)](../language-reference/keywords/partial-method.md).

Kod üreticileri için ikinci yeni özellik ***Modül başlatıcılarına*** yöneliktir. Modül başlatıcıları, <xref:System.Runtime.CompilerServices.ModuleInitializerAttribute> kendisine eklenmiş özniteliği olan yöntemlerdir. Bu yöntemler, tüm modülün içindeki başka bir alan erişimi veya yöntem çağrısından önce çalışma zamanı tarafından çağırılır. Modül başlatıcısı yöntemi:

- Statik olmalıdır
- Parametresiz olmalıdır
- Void döndürmelidir
- Genel bir yöntem olmamalıdır
- Genel bir sınıfta içerilmemelidir
- Kapsayan modülden erişilebilir olmalıdır

Bu son madde işareti noktası, yöntemin ve kapsayan sınıfın iç veya genel olması gerektiği anlamına gelir. Yöntem yerel bir işlev olamaz. Daha fazla bilgi için bkz. [ `ModuleInitializer` özniteliği](../language-reference/attributes/general.md#moduleinitializer-attribute).
