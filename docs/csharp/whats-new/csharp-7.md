---
title: C# 7,0 ' deki yenilikler-C# Kılavuzu
description: C# dilinin sürüm 7,0 ' deki yeni özelliklere genel bakış alın.
ms.date: 10/02/2020
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 0c57a030497d13b783960152612de27d5fc73c3c
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255031"
---
# <a name="whats-new-in-c-70-through-c-73"></a>C# 7,3 ile c# 7,0 yenilikleri

C# 7,0 7,3 ile c# arasında bir dizi özellik ve geliştirme deneyiminize yönelik artımlı iyileştirmeler c# ile getirildi. Bu makalede, yeni dil özelliklerine ve derleyici seçeneklerine bir genel bakış sunulmaktadır. Açıklamalar, .NET Framework tabanlı uygulamalar için desteklenen en son sürüm olan C# 7,3 davranışını tanımlar.

[Dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesi C# 7,1 ile eklenmiştir ve bu, proje dosyanızda derleyici dili sürümünü belirtmenize olanak sağlar.

C# 7.0-7.3 Bu özellikleri ve temaları C# diline ekler:

- [Tanımlama grupları ve atma](#tuples-and-discards)
  - Birden çok ortak alan içeren hafif, adlandırılmamış türler oluşturabilirsiniz. Derleyiciler ve IDE araçları bu türlerin semantiğini anlayın.
  - Atama, atanan değer hakkında endişelenmezseniz atamalar içinde kullanılan geçici, salt yazılır değişkenlerdir. Bunlar, tanımlama grupları ve Kullanıcı tanımlı türler oluştururken ve parametreleri ile Yöntemler çağrılırken faydalıdır `out` .
- [Model eşleştirme](#pattern-matching)
  - Bu türlerin üyelerinin rastgele türlerini ve değerlerini temel alarak dallanma mantığı oluşturabilirsiniz.
- [`async``Main`yöntemi](#async-main)
  - Bir uygulama için giriş noktası değiştiriciye sahip olabilir `async` .
- [Yerel Işlevler](#local-functions)
  - Kendi kapsamını ve görünürlüğünü sınırlamak için işlevleri diğer işlevlerde iç içe geçirebilirsiniz.
- [Daha fazla ifade-Bodied Üyeler](#more-expression-bodied-members)
  - İfadeler kullanılarak yazılabilir üyelerin listesi artmıştır.
- [`throw` İfadelerde](#throw-expressions)
  - Daha önce izin verilmeyen kod yapılarında özel durumlar oluşturabilir, çünkü `throw` bir deyimidir.
- [`default` değişmez değer ifadeleri](#default-literal-expressions)
  - Hedef türü çıkarsanamıyor varsayılan değer ifadelerinde varsayılan değişmez ifadeleri kullanabilirsiniz.
- [Sayısal sabit değer sözdizimi geliştirmeleri](#numeric-literal-syntax-improvements)
  - Yeni belirteçler Sayısal sabitler için okunabilirliği geliştirir.
- [`out` değişkenlerinin](#out-variables)
  - `out`Değerleri, kullanıldığı yönteme bağımsız değişken olarak satır içi olarak bildirebilirsiniz.
- [Girintili olmayan adlandırılmış bağımsız değişkenler](#non-trailing-named-arguments)
  - Adlandırılmış bağımsız değişkenlerin ardından konumsal bağımsız değişkenler gelebilir.
- [`private protected` erişim değiştiricisi](#private-protected-access-modifier)
  - `private protected`Erişim değiştiricisi aynı derlemede türetilmiş sınıflar için erişim imkanı sunar.
- [Geliştirilmiş aşırı yükleme çözümlemesi](#improved-overload-candidates)
  - Aşırı yükleme çözümleme belirsizliğe çözüm için yeni kurallar.
- [Güvenli verimli kod yazma teknikleri](#enabling-more-efficient-safe-code)
  - Başvuru semantiğinin kullanıldığı değer türleriyle çalışmayı sağlayan sözdizimi geliştirmelerinden oluşan bir bileşim.

Son olarak, derleyici yeni seçeneklere sahiptir:

- `-refout` ve `-refonly` Bu denetim [Başvuru derleme oluşturma](#reference-assembly-generation).
- `-publicsign` Açık kaynak yazılım (OSS) derlemelerinin imzalanmasını etkinleştirmek için.
- `-pathmap` Kaynak dizinlere eşleme sağlamak için.

Bu makalenin geri kalanında her özelliğe bir genel bakış sunulmaktadır. Her özellik için, arkasındaki ve söz dizimi hakkında bilgi edineceksiniz. Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz `dotnet try` :

1. [DotNet-TRY](https://github.com/dotnet/try/blob/main/DotNetTryLocal.md) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="tuples-and-discards"></a>Tanımlama grupları ve atma

C#, tasarım amacını açıklamak için kullanılan sınıflar ve yapılar için zengin bir sözdizimi sağlar. Ancak bazen zengin söz dizimi çok az avantajlı ek iş gerektirir. Genellikle birden fazla veri öğesi içeren basit bir yapıya ihtiyacı olan Yöntemler yazabilirsiniz. Bu *senaryoları desteklemek* için C# ' ye eklenmiştir. Tanımlama grupları, veri üyelerini temsil etmek için birden çok alan içeren hafif veri yapılarıdır. Alanlar doğrulanmaz ve kendi yöntemlerinizi tanımlayamazsınız. C# demet türleri destekler `==` `!=` . Daha fazla bilgi için.

> [!NOTE]
> Tanımlama grupları C# 7,0 ' den önce kullanılabilir, ancak verimsiz ve dil desteği yoktu. Bu, demet öğelerine yalnızca olarak başvurulabilir `Item1` , `Item2` vb. anlamına gelir. C# 7,0, tanımlama grupları için dil desteğini tanıtır ve bu, yeni, daha verimli demet türleri kullanarak bir kayıt düzeni alanları için anlamsal adlar sağlar.

Her üyeye bir değer atayarak ve isteğe bağlı olarak tanımlama grubu üyelerinin her birine anlamsal adlar sağlayarak bir tanımlama grubu oluşturabilirsiniz:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters`Kayıt düzeni ve olarak adlandırılan alanları içerir `Alpha` `Beta` . Bu adlar yalnızca derleme sırasında bulunur ve korunmaz, örneğin, çalışma zamanında yansıma kullanarak tanımlama grubu incelenirken.

Tanımlama grubu atamasında, atamanın sağ tarafındaki alanların adlarını da belirtebilirsiniz:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Bir yöntemden döndürülen bir tanımlama grubunun üyelerinin paketini kaldırmak istediğiniz zamanlar olabilir.  Bu, kayıt grubundaki her bir değer için ayrı değişkenler bildirerek yapabilirsiniz. Bu paketten *çıkarılması* , kayıt düzeninin kaldırılması olarak adlandırılır:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Ayrıca, .NET 'teki herhangi bir tür için benzer bir deme sağlayabilirsiniz. Bir `Deconstruct` yöntemi sınıfının bir üyesi olarak yazarsınız. Bu `Deconstruct` Yöntem `out` , ayıklamak istediğiniz her bir özellik için bir dizi bağımsız değişken sağlar. `Point`Ve koordinatlarını çıkaran bir Deconstructor yöntemi sağlayan bu sınıfı göz önünde `X` bulundurun `Y` :

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Bir tanımlama grubu 'na atayarak tek tek alanları ayıklayabilirsiniz `Point` :

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Bir tanımlama grubu başlattığınızda, atamanın sağ tarafında kullanılan değişkenler demet öğeleri için istediğiniz adlarla aynı olur: demet öğelerinin adları, kayıt kümesini başlatmak için kullanılan değişkenlerden çıkarsanamıyor:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

[Demet türleri](../language-reference/builtin-types/value-tuples.md) makalesinde bu özellik hakkında daha fazla bilgi edinebilirsiniz.

Genellikle, bir tanımlama grubu oluştururken veya parametreler ile bir yöntemi çağırırken `out` , değeri ilgilenmediğiniz ve kullanmayı planlamadığınız bir değişken tanımlamaya zorlanır. C#, bu senaryoyu işlemek için *atma* desteği ekler. Bir atma, adı `_` (alt çizgi karakteri) olan salt yazılır bir değişkendir; atmayı planladığınız tüm değerleri tek bir değişkene atayabilirsiniz. Bir atma atanmamış değişken gibidir; atama ifadesinden ayrı olarak, atma kodda kullanılamaz.

Atma, aşağıdaki senaryolarda desteklenir:

- Tanımlama grupları veya Kullanıcı tanımlı türler kaldırılıyor.
- [Out](../language-reference/keywords/out-parameter-modifier.md) parametreleri ile Yöntemler çağrılırken.
- WITH ve [Switch](../language-reference/keywords/switch.md) deyimleriyle bir kalıp [](../language-reference/keywords/is.md) eşleştirme işleminde.
- Bir atamanın değerini bir atma olarak açıkça tanımlamak istediğinizde tek başına tanımlayıcı olarak.

Aşağıdaki örnek, `QueryCityDataForYears` iki farklı yıl için şehir için veri içeren 6 demet döndüren bir yöntemi tanımlar. Örnekteki yöntem çağrısı yalnızca yöntemi tarafından döndürülen iki popülasyon değeriyle ilgilidir ve bu nedenle, kayıt düzeni oluşturulduğunda, kayıt düzeninde kalan değerleri atma olarak değerlendirir.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Daha fazla bilgi için bkz. [atma](../discards.md).

## <a name="pattern-matching"></a>Desen eşleştirme

*Model eşleştirme* , kodunuzda hızlı denetim akışını sağlayan yeni yollar sağlayan bir özellikler kümesidir. Değişkenlerini türlerine, değerlerine veya özelliklerinin değerlerine göre test edebilirsiniz. Bu teknikler daha okunabilir kod akışı oluşturur.

Model eşleştirme `is` , ifadeleri ve `switch` ifadeleri destekler. Her biri, nesnenin aranan düzene karşılayıp karşılamadığını tespit etmek için bir nesne ve özelliklerini inceleyerek sağlar. `when`Modele ek kurallar belirtmek için anahtar sözcüğünü kullanırsınız.

`is`Model ifadesi, bir nesneyi türü hakkında sorgulamak ve sonucu bir yönergede atamak için tanıdık [ `is` işleci](../language-reference/keywords/is.md#pattern-matching-with-is) genişletir. Aşağıdaki kod, bir değişkenin bir olduğunu denetler `int` ve varsa, geçerli Sum 'a ekler:

```csharp
if (input is int count)
    sum += count;
```

Önceki küçük örnek, ifadeye yönelik geliştirmeleri gösterir `is` . Aynı zamanda değer türlerine ve başvuru türlerine karşı test edebilirsiniz ve başarılı sonucu doğru türdeki yeni bir değişkene atayabilirsiniz.

Anahtar eşleşme ifadesi, `switch` C# dilinin zaten bir parçası olan bildirime göre tanıdık bir sözdizimine sahiptir. Güncelleştirilmiş switch ifadesinin çeşitli yeni yapıları vardır:

- Bir ifadenin yöneten türü `switch` artık, `Enum` `string` Bu türlerden birine karşılık gelen tamsayı türleri, türleri veya null olabilen bir türle sınırlı değildir. Herhangi bir tür kullanılabilir.
- `switch`Her etikette ifadenin türünü test edebilirsiniz `case` . İfadesinde olduğu gibi `is` , bu türe yeni bir değişken atayabilirsiniz.
- `when`O değişkende daha fazla test koşullarına bir yan tümce ekleyebilirsiniz.
- `case`Etiketlerin sırası artık önemlidir. Eşleştirilecek ilk dal yürütülür; diğerleri atlanır.

Aşağıdaki kod bu yeni özellikleri göstermektedir:

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- `case 0:` sabit bir [örüntü](../language-reference/operators/patterns.md#constant-pattern).
- `case IEnumerable<int> childSequence:` bir [bildirim deseninin](../language-reference/operators/patterns.md#declaration-and-type-patterns).
- `case int n when n > 0:` , ek bir koşula sahip bir bildirim modelidir `when` .
- `case null:` sabit bir modeldir `null` .
- `default:` tanıdık varsayılan durumdur.

C# 7,1 ile başlayarak, `is` ve `switch` tür deseninin model ifadesi bir genel tür parametresinin türüne sahip olabilir. Bu, ya da türünde olabilecek türler denetlenirken `struct` `class` ve kutulamayı önlemek istediğiniz durumlarda yararlı olabilir.

[C# ' de model eşleştirme](../pattern-matching.md)ile model eşleştirme hakkında daha fazla bilgi edinebilirsiniz.

## <a name="async-main"></a>Zaman uyumsuz ana

*Zaman uyumsuz Main* yöntemi, `await` yöntekinizdeki kullanmanıza olanak sağlar `Main` . Daha önce yazmanız gerekir:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Artık şunu yazabilirsiniz:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Programınız çıkış kodu döndürmezse, şunu `Main` döndüren bir yöntem bildirebilirsiniz <xref:System.Threading.Tasks.Task> :

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Programlama kılavuzundaki [zaman uyumsuz ana](../programming-guide/main-and-command-args/index.md) makaledeki ayrıntılar hakkında daha fazla bilgi edinebilirsiniz.

## <a name="local-functions"></a>Yerel işlevler

Sınıfların pek çok tasarımı yalnızca bir konumdan çağrılan yöntemleri içerir. Bu ek özel yöntemler her bir yöntemi küçük ve odaklanmış olarak tutar. *Yerel işlevler* , yöntemleri başka bir yöntem bağlamı içinde bildirmenize olanak tanır. Yerel işlevler, sınıfının okuyucularının, yerel yöntemin yalnızca bildirildiği bağlamdan çağrıldığını görmesini kolaylaştırır.

Yerel işlevler için iki yaygın kullanım durumu vardır: genel Yineleyici yöntemleri ve genel zaman uyumsuz yöntemler. Her iki yöntem türü, programcılar tarafından daha sonra oluşabilecek hataları raporlayan kodu oluşturur. Yineleyici metotlarda, tüm özel durumlar yalnızca döndürülen sırayı belirten kod çağrılırken izlenir. Zaman uyumsuz metotlarda, tüm özel durumlar yalnızca döndürülen geri beklendiğinde gözlemlenir `Task` . Aşağıdaki örnek, yerel bir işlev kullanarak Yineleyici uygulamasından parametre doğrulamayı ayırmayı gösterir:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

`async`Bağımsız değişken doğrulamasından doğan özel durumların, zaman uyumsuz iş başlamadan önce oluşturulması için yöntemler ile aynı yöntem kullanılabilir:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Bu sözdizimi artık desteklenmektedir:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Özniteliği, `SomeThingAboutFieldAttribute` için derleyicinin oluşturduğu yedekleme alanına uygulanır `SomeProperty` . Daha fazla bilgi için bkz. C# programlama kılavuzundaki [öznitelikler](../programming-guide/concepts/attributes/index.md) .

> [!NOTE]
> Yerel işlevler tarafından desteklenen tasarımlardan bazıları *lambda ifadeleri* kullanılarak da gerçekleştirilebilir. Daha fazla bilgi için bkz [. yerel işlevler ve lambda ifadeleri](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).

## <a name="more-expression-bodied-members"></a>Daha fazla ifade-Bodied Üyeler

C# 6 ifadesi-üye işlevleri ve salt okunurdur özellikler için Bodied eklenen üyeler. C# 7,0, ifade olarak uygulanabilecek izin verilen üyeleri genişletir. C# 7,0 ' de,   `get` `set` *Özellikler* ve *Dizin oluşturucular* üzerinde oluşturucular, sonlandırıcılar ve erişimciler uygulayabilirsiniz. Aşağıdaki kod, her birinin örneklerini gösterir:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Bu örnekte sonlandırıcısı gerekmez, ancak söz dizimini göstermek için gösterilir. Yönetilmeyen kaynakları serbest bırakmak gerekmedikçe, sınıfınıza sonlandırıcıyı uygulamamalısınız. Ayrıca, <xref:System.Runtime.InteropServices.SafeHandle> yönetilmeyen kaynakları doğrudan yönetmek yerine sınıfını kullanmayı göz önünde bulundurmanız gerekir.

İfade için bu yeni konumlar C# dili için önemli bir kilometre taşını temsil eder: Bu özellikler, açık kaynaklı [Roslyn](https://github.com/dotnet/Roslyn) projesinde çalışan topluluk üyeleri tarafından uygulanmıştır.

Bir yöntemi bir ifade ile değiştirmek, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)olur.

## <a name="throw-expressions"></a>Throw ifadeleri

C# ' de `throw` her zaman bir ifade olmuştur. Bir `throw` ifade değil, bir deyim olduğundan, bunu kullanamadığı Için C# yapıları vardı. Bu dahil edilen Koşullu ifadeler, null birleştirme ifadeleri ve bazı lambda ifadeleri. İfade bululmuş üyelerin eklenmesi, ifadelerin yararlı olacağı daha fazla konum ekler `throw` . Bu yapıların herhangi birini yazmak için C# 7,0, [*throw ifadelerini*](../language-reference/keywords/throw.md#the-throw-expression)tanıtır.

Bu ek, daha fazla ifade tabanlı kod yazmayı kolaylaştırır. Hata denetimi için ek deyimlere ihtiyacınız yoktur.

## <a name="default-literal-expressions"></a>Varsayılan değişmez değer ifadeleri

Varsayılan değişmez değer ifadeleri varsayılan değer ifadelerine yönelik bir geliştirmedir. Bu ifadeler varsayılan değere bir değişken başlatır. Daha önce yazdığınız yer:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Artık başlatmanın sağ tarafındaki türü atlayabilirsiniz:

```csharp
Func<string, bool> whereClause = default;
```

Daha fazla bilgi için [varsayılan işleç](../language-reference/operators/default.md) makalesinin [varsayılan değişmez değeri](../language-reference/operators/default.md#default-literal) bölümüne bakın.

## <a name="numeric-literal-syntax-improvements"></a>Sayısal sabit değer sözdizimi geliştirmeleri

Hatalı okuma sayısal sabitleri, ilk kez okurken kodu daha zor hale getirir. Bit maskeleri veya diğer sembolik değerler yanlış anlama eğilimindedir. C# 7,0, tasarlanan kullanım için en okunabilir şekilde sayı yazmak üzere iki yeni özellik içerir: *ikili sabit değerler* ve *basamak ayırıcıları*.

Bit maskeleri oluştururken veya bir sayının ikili gösteriminin en çok okunabilen kodu yaptığı durumlarda bu süreler için bu sayıyı binary olarak yazın:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

`0b`Sabitin başlangıcında, sayının bir ikili sayı olarak yazıldığını gösterir. İkili sayılar uzun sürebilir, bu nedenle, `_` önceki örnekteki ikili Sabitte gösterildiği gibi, bir rakam ayırıcısı olarak girerek bit desenlerini görmeniz genellikle daha kolay olur. Sayı ayırıcısı, sabit içinde herhangi bir yerde görünebilir. 10 tabanında sayı için bu, binlerce ayırıcı olarak kullanılması yaygındır. Onaltılı ve ikili sayısal değişmez değerler bir ile başlayabilir `_` :

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Rakam ayırıcısı,, ve türleri ile birlikte kullanılabilir `decimal` `float` `double` :

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Birlikte çalışarak, sayısal sabitleri çok daha okunaklı bir şekilde bildirebilirsiniz.

## <a name="out-variables"></a>`out` değişkenlerinin

Parametreleri destekleyen mevcut sözdizimi `out` C# 7 ' de geliştirilmiştir. Artık `out` değişkenleri, ayrı bir bildirim bildirimi yazmak yerine bir yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

`out`Yukarıdaki örnekte gösterildiği gibi, açıklık için değişkenin türünü belirtmek isteyebilirsiniz. Ancak, dil örtük olarak yazılmış bir yerel değişken kullanmayı destekler:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Kodu daha kolay okunabilir.
  - Yukarıdaki kod satırında değil, kullandığınız yerde çıkış değişkenini bildirirsiniz.
- İlk değer atamaya gerek yoktur.
  - `out`Yöntemi bir yöntem çağrısında kullanıldığı yerde bildirerek, yanlışlıkla onu atanmadan kullanamazsınız.

Değişken bildirimlerine izin vermek için C# 7,0 ' ye eklenen söz dizimi, `out` alan başlatıcıları, özellik başlatıcıları, Oluşturucu başlatıcıları ve sorgu yan tümcelerini kapsayacak şekilde genişletilmiştir. Aşağıdaki örnek gibi kodu sunar:

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

## <a name="non-trailing-named-arguments"></a>Girintili olmayan adlandırılmış bağımsız değişkenler

Yöntem çağrıları artık, adlandırılmış bağımsız değişkenler doğru konumlarda olduğunda Konumsal bağımsız değişkenlerden önce gelen adlandırılmış bağımsız değişkenleri kullanabilir. Daha fazla bilgi için bkz. [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="private-protected-access-modifier"></a>*özel korumalı* erişim değiştiricisi

Yeni bir bileşik erişim değiştiricisi: `private protected` bir üyeye, aynı derlemede belirtilen sınıf veya türetilmiş sınıfları içeren bir üyeye erişilebildiğini gösterir. `protected internal`Aynı derlemede bulunan türetilmiş sınıfların veya sınıfların erişimine izin verdiğinden, `private protected` aynı derlemede belirtilen türetilmiş türlere erişimi kısıtlar.

Daha fazla bilgi için bkz. dil başvurusunda [erişim değiştiriciler](../language-reference/keywords/access-modifiers.md) .

## <a name="improved-overload-candidates"></a>Geliştirilmiş aşırı yükleme adayları

Her sürümde, aşırı yükleme çözümleme kuralları belirsiz Yöntem etkinleştirmeleri "belirgin" bir seçeneğe sahip olduğu durumlara göre güncelleştirilir. Bu sürüm, derleyicinin açık seçimi seçmesini sağlamaya yardımcı olmak için üç yeni kural ekler:

1. Bir yöntem grubu hem örnek hem de statik üye içerdiğinde, yöntem bir örnek alıcısı veya bağlamı olmadan çağrılırsa, derleyici örnek üyelerini atar. Yöntem bir örnek alıcısıyla çağrılırsa derleyici statik üyeleri atar. Alıcı olmadığında, derleyici statik bir bağlamda yalnızca statik üyeleri ve statik ve örnek üyelerini içerir. Alıcı bir örnek veya tür ındexattributes, derleyici her ikisini de içerir. Örtük bir örnek alıcısının kullanıldığı statik bir bağlam, statik üyeler gibi, hiçbir üyenin, örneğin, `this` `this` `this` alan başlatıcıları ve Oluşturucu başlatıcıları gibi kullanılamayan yerleri de içerir.
1. Bir yöntem grubu, tür bağımsız değişkenleri kısıtlamalarını karşılamadığı bazı genel yöntemler içerdiğinde, bu üyeler aday kümesinden kaldırılır.
1. Bir yöntem grubu dönüştürmesi için, dönüş türü, temsilcinin dönüş türüyle eşleşmeyen aday Yöntemler kümeden kaldırılır.

Bu değişikliği yalnızca, hangi yöntemin daha iyi olduğundan emin olduğunuzda belirsiz yöntem aşırı yüklemeleri için daha az derleyici hatası bulacağınız için fark edeceksiniz.

## <a name="enabling-more-efficient-safe-code"></a>Daha verimli güvenli kod etkinleştirme

Güvenli olmayan kodun yanı sıra, güvenli bir şekilde C# kodu yazmanız gerekir. Güvenli kod, arabellek taşmaları, başıya işaretçileri ve diğer bellek erişim hataları gibi hata sınıflarını önler. Bu yeni özellikler, doğrulanabilir güvenli kod yeteneklerini genişletir. Güvenli yapılar kullanarak kodunuzun daha fazlasını yazmak için çaba harcar. Bu özellikler daha kolay hale getirir.

Aşağıdaki yeni özellikler, güvenli kod için daha iyi performans temasını destekler:

- Sabitlemeden sabit alanlara erişebilirsiniz.
- `ref`Yerel değişkenleri yeniden atayabilirsiniz.
- Dizilerde başlatıcıları kullanabilirsiniz `stackalloc` .
- `fixed`Deyimlerini, bir kalıbı destekleyen herhangi bir türle birlikte kullanabilirsiniz.
- Ek genel kısıtlamalar kullanabilirsiniz.
- `in`Bir bağımsız değişkenin başvuruya göre geçirilmesini, ancak çağrılan yöntem tarafından değiştirilmediğinden emin olmak için parametrelerde değiştirici. `in`Bir bağımsız değişkene değiştirici eklemek, kaynak ile [uyumlu bir değişiklik](version-update-considerations.md#source-compatible-changes)olur.
- Yöntem `ref readonly` üzerinde değiştirici, bir yöntemin değerini başvuruya göre döndürdüğünü ancak bu nesneye yazma izni olmadığını belirtmek için döndürür. Değiştirici eklemek `ref readonly` , döndürme bir değere atanmışsa, [kaynak ile uyumlu bir değişiklik](version-update-considerations.md#source-compatible-changes)olur. `readonly`Değiştirici varolan bir `ref` Return ifadesine eklendiğinde [uyumsuz bir değişiklik](version-update-considerations.md#incompatible-changes)vardır. Çağrıcıların `ref` , değiştiricisini içermesi için yerel değişkenlerin bildirimini güncelleştirmesi gerekir `readonly` .
- `readonly struct`Bir yapının sabit olduğunu ve onun üye yöntemlerine bir parametre olarak geçirilmesi gerektiğini göstermek için bildirimi `in` . Değiştirici, `readonly` var olan bir struct bildirimine eklendiğinde, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)bulunur.
- `ref struct`Bir yapı türünün doğrudan yönetilen belleğe eriştiğini ve her zaman yığın ayrılması gerektiğini göstermek için bildirimi. `ref`Değiştirici varolan bir `struct` bildirime eklendiğinde [uyumsuz bir değişiklik](version-update-considerations.md#incompatible-changes)vardır. Bir `ref struct` sınıfın üyesi olamaz veya yığın üzerinde ayrılabileceği diğer konumlarda kullanılabilir.

Bu değişiklikler hakkında daha fazla bilgi için [yazma güvenli verimli kod](../write-safe-efficient-code.md)' a erişebilirsiniz.

### <a name="ref-locals-and-returns"></a>Ref Yereller ve geri dönüşler

Bu özellik, tarafından kullanılan ve başka bir yerde tanımlanan değişkenlere başvuru döndüren algoritmaların yapılmasını sağlar. Bir örnek büyük matrislerle çalışıyor ve belirli özelliklere sahip tek bir konum buluyor. Aşağıdaki yöntem, matriste bu depolama için bir **başvuru** döndürür:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

`ref`Aşağıdaki kodda gösterildiği gibi, dönüş değerini bir olarak bildirebilir ve matriste bu değeri değiştirebilirsiniz:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# dili, yerelleri yanlış kullanmanızı ve şunu döndürdüğünü koruyan çeşitli kurallara sahiptir `ref` :

- `ref`Anahtar sözcüğünü Yöntem imzasına ve `return` bir yöntemindeki tüm deyimlere eklemeniz gerekir.
  - Bu, yöntem boyunca başvuruya göre döndürülen yöntemi temizler.
- Bir `ref return` değer değişkenine veya bir `ref` değişkene atanabilir.
  - Çağıran, dönüş değerinin kopyalanıp kopyalanmadığını denetler. `ref`Dönüş değerini atarken değiştiricinin atlanması, çağıranın depolama için bir başvuru değil, değer kopyasının istediğini gösterir.
- Bir yerel değişkene standart bir yöntem dönüş değeri atayamazsınız `ref` .
  - Şunun gibi deyimler izin vermez `ref int i = sequence.Count();`
- `ref`Ömrü, yönteminin yürütülmesinden daha fazla genişlemeyen bir değişkene geri dönemez.
  - Bu, yerel bir değişkene veya benzer kapsama sahip bir değişkene bir başvuru döndüremeyeceğiniz anlamına gelir.
- `ref` Yereller ve geri dönüş, zaman uyumsuz yöntemlerle kullanılamaz.
  - Zaman uyumsuz yöntem döndürüldüğünde, derleyici başvurulan değişkenin son değerine ayarlandığını bilemez.

Ref Yereller ve ref işlevinin eklenmesi, değerleri kopyalamayı önleyerek veya birden çok kez başvuru işlemleri gerçekleştirerek daha etkili olan algoritmaların kullanılmasına izin verir.

`ref`Dönüş değerine ekleme, [kaynak ile uyumlu bir değişikdir](version-update-considerations.md#source-compatible-changes). Varolan kod derlenir, ancak ref dönüş değeri atandığında kopyalanır. Çağıranlar, döndürmeyi `ref` bir başvuru olarak depolamak için dönüş değeri için depolamayı yerel bir değişkene güncelleştirmelidir.

Şimdi `ref` Yereller, başlatıldıktan sonra farklı örneklere başvuracak şekilde yeniden atanabilir. Aşağıdaki kod artık derlenir:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Daha fazla bilgi için bkz. [ `ref` `ref` dönüşler ve yerel öğeler](../programming-guide/classes-and-structs/ref-returns.md)ve hakkındaki makale [`foreach`](../language-reference/keywords/foreach-in.md) .

Daha fazla bilgi için bkz. [ref anahtar sözcüğü](../language-reference/keywords/ref.md) makalesi.

### <a name="conditional-ref-expressions"></a>Koşullu `ref` ifadeler

Son olarak, koşullu ifade bir değer sonucu yerine bir başvuru sonucu üretebilir. Örneğin, iki diziden birindeki ilk öğeye başvuru almak için aşağıdakini yazın:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

Değişken, `r` veya içindeki ilk değere bir başvurudur `arr` `otherArr` .

Daha fazla bilgi için bkz. dil başvurusunda [koşullu işleç (?:)](../language-reference/operators/conditional-operator.md) .

### <a name="in-parameter-modifier"></a>`in` parametre değiştiricisi

`in`Anahtar sözcüğü, bağımsız değişkenleri başvuruya göre geçirmek için mevcut ref ve out anahtar sözcüklerini tamamlar. `in`Anahtar sözcüğü, bağımsız değişkeni başvuruya göre geçirmeyi belirtir, ancak çağrılan yöntem değeri değiştirmez.

Aşağıdaki kodda gösterildiği gibi, değere göre veya ReadOnly başvuruya göre geçen aşırı yüklemeleri bildirebilirsiniz:

```csharp
static void M(S arg);
static void M(in S arg);
```

By değeri (önceki örnekte ilk) aşırı yükleme, salt okunur başvuru sürümünden daha iyidir. Salt okunur başvuru bağımsız değişkeniyle sürümü çağırmak için, `in` yöntemini çağırırken değiştiricisini dahil etmeniz gerekir.

Daha fazla bilgi için, [ `in` parametre değiştiricisiyle](../language-reference/keywords/in-parameter-modifier.md)ilgili makaleye bakın.

### <a name="more-types-support-the-fixed-statement"></a>Daha fazla tür, `fixed` ifadeyi destekler

`fixed`İfade sınırlı bir tür kümesi destekliyordu. C# 7,3 ' den başlayarak, veya döndüren bir yöntemi içeren herhangi bir tür olabilir `GetPinnableReference()` `ref T` `ref readonly T` `fixed` . Bu özelliği eklemek, `fixed` ve ilgili türlerle birlikte kullanılabilecek anlamına gelir <xref:System.Span%601?displayProperty=nameWithType> .

Daha fazla bilgi için bkz. dil başvurusu içindeki [ `fixed` ifade](../language-reference/keywords/fixed-statement.md) makalesi.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Dizin oluşturma `fixed` alanları sabitleme gerektirmez

Bu yapıyı göz önünde bulundurun:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

C# ' nin önceki sürümlerinde, öğesinin parçası olan tamsayıların birine erişmek için bir değişkeni sabitlemeyi gerekiyordu `myFixedField` . Şimdi, aşağıdaki kod değişkeni `p` ayrı bir ifadeye sabitlemeden derler `fixed` :

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

Değişkeni `p` içindeki bir öğeye erişir `myFixedField` . Ayrı bir değişken bildirmeniz gerekmez `int*` . Yine de bir `unsafe` bağlam gerekir. C# ' nin önceki sürümlerinde ikinci bir sabit işaretçi bildirmeniz gerekir:

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

Daha fazla bilgi için, [ `fixed` deyimindeki](../language-reference/keywords/fixed-statement.md)makaleye bakın.

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` diziler, başlatıcıları destekler

Bir dizideki öğeler için değerleri, başlatma sırasında belirtebilirsiniz:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Artık, ile belirtilen dizilere aynı söz dizimi uygulanabilir `stackalloc` :

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Daha fazla bilgi için bkz. [ `stackalloc` operatör](../language-reference/operators/stackalloc.md) makalesi.

### <a name="enhanced-generic-constraints"></a>Gelişmiş genel kısıtlamalar

Artık tür <xref:System.Enum?displayProperty=nameWithType> <xref:System.Delegate?displayProperty=nameWithType> parametresi için türü veya temel sınıf kısıtlamalarını belirtebilirsiniz.

Yeni `unmanaged` kısıtlamayı, bir tür parametresinin null yapılamayan [yönetilmeyen bir tür](../language-reference/builtin-types/unmanaged-types.md)olması gerektiğini belirtmek için de kullanabilirsiniz.

Daha fazla bilgi için bkz. tür parametrelerinde [ `where` genel kısıtlamalar](../language-reference/keywords/where-generic-type-constraint.md) ve [kısıtlamalar](../programming-guide/generics/constraints-on-type-parameters.md)hakkında makaleler.

Bu kısıtlamaları var olan türlere eklemek uyumsuz bir [değişiklik](version-update-considerations.md#incompatible-changes). Kapalı genel türler artık bu yeni kısıtlamaları karşılamayabilir.

### <a name="generalized-async-return-types"></a>Genelleştirilmiş zaman uyumsuz dönüş türleri

`Task`Zaman uyumsuz metotlardan bir nesne döndürmek, belirli yollarda performans sorunlarını ortaya çıkarabilir. `Task` bir başvuru türüdür, bu nedenle bu bir nesne ayırma anlamına gelir. Değiştirici ile belirtilen bir yöntemin `async` önbelleğe alınmış bir sonuç döndürdüğü veya zaman uyumlu olarak tamamladığı durumlarda, ek ayırmalar kodun performans açısından kritik bölümlerinde önemli bir zaman maliyeti olabilir. Bu ayırmalar sıkı Döngülerde gerçekleşirse maliyetli hale gelebilir.

Yeni dil özelliği, zaman uyumsuz yöntem dönüş türlerinin `Task` , ve ile sınırlı olmadığı anlamına gelir `Task<T>` `void` . Döndürülen türün zaman uyumsuz düzene uygun olması gerekir, yani bir `GetAwaiter` yönteme erişilebilir olması gerekir. Tek bir somut örnek olarak, `ValueTask` Bu yeni dil özelliğinin kullanılması için tür .net 'e eklenmiştir:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/)Türünü kullanmak Için NuGet paketini > eklemeniz gerekir <xref:System.Threading.Tasks.ValueTask%601> .

Bu geliştirme, en çok bir performans kritik kodunda ayırmayı önlemek için kitaplık yazarları için yararlıdır `Task` .

## <a name="new-compiler-options"></a>Yeni derleyici seçenekleri

Yeni derleyici seçenekleri C# programları için yeni derleme ve DevOps senaryolarını destekler.

### <a name="reference-assembly-generation"></a>Başvuru derlemesi oluşturma

*Yalnızca başvuru derlemeler* üreten iki yeni derleyici seçeneği vardır: [**ProduceReferenceAssembly**](../language-reference/compiler-options/output.md#producereferenceassembly) ve [**ProduceOnlyReferenceAssembly**](../language-reference/compiler-options/code-generation.md#produceonlyreferenceassembly).
Bağlantılı makaleler, bu seçenekleri ve başvuru derlemelerini daha ayrıntılı bir şekilde açıklamaktadır.

### <a name="public-or-open-source-signing"></a>Ortak veya açık kaynak imzalama

**Publicsign** derleyici seçeneği derleyicinin bir ortak anahtar kullanarak derlemeyi imzalamasını ister. Derleme imzalanmış olarak işaretlenir, ancak imza ortak anahtardan alınır. Bu seçenek, açık kaynaklı projelerden ortak anahtar kullanarak imzalı derlemeler oluşturmanıza olanak sağlar.

Daha fazla bilgi için bkz. [ **publicsign** derleyici seçeneği](../language-reference/compiler-options/security.md#publicsign) makalesi.

### <a name="pathmap"></a>pathmap

**Pathmap** derleyici seçeneği, derleyicinin kaynak yollarını, derleme ortamından eşlenen kaynak yollarıyla değiştirmesini söyler. **Pathmap** seçeneği, DERLEYICI tarafından pdb dosyalarına veya için yazılan kaynak yolunu denetler <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> .

Daha fazla bilgi için bkz. [ **pathmap** derleyici seçeneği](../language-reference/compiler-options/advanced.md#pathmap) makalesi.
