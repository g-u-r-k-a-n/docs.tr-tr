---
title: C# 8,0 ' deki yenilikler-C# Kılavuzu
description: C# 8,0 ' de bulunan yeni özelliklere genel bakış alın.
ms.date: 04/07/2020
ms.openlocfilehash: fa31276175733211c74ac54affc8ec222896c87f
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255356"
---
# <a name="whats-new-in-c-80"></a>C# 8.0 sürümündeki yenilikler

C# 8,0, C# diline aşağıdaki özellikleri ve geliştirmeleri ekler:

- [Salt okunur Üyeler](#readonly-members)
- [Varsayılan arabirim metotları](#default-interface-methods)
- [Desenler eşleşen geliştirmeler](#more-patterns-in-more-places):
  - [Anahtar ifadeleri](#switch-expressions)
  - [Özellik desenleri](#property-patterns)
  - [Demet desenleri](#tuple-patterns)
  - [Konumsal desenler](#positional-patterns)
- [Bildirimleri kullanma](#using-declarations)
- [Statik yerel işlevler](#static-local-functions)
- [Atılabilir ref yapıları](#disposable-ref-structs)
- [Boş değer atanabilir başvuru türleri](#nullable-reference-types)
- [Zaman uyumsuz akışlar](#asynchronous-streams)
- [Zaman uyumsuz atılabilir](#asynchronous-disposable)
- [Dizinler ve aralıklar](#indices-and-ranges)
- [Null birleştirme ataması](#null-coalescing-assignment)
- [Yönetilmeyen oluşturulmuş türler](#unmanaged-constructed-types)
- [İç içe ifadelerde stackalloc](#stackalloc-in-nested-expressions)
- [Ara değerli tam dizelerin geliştirilmesi](#enhancement-of-interpolated-verbatim-strings)

C# 8,0, **.NET Core 3. x** ve **.NET Standard 2,1**' de desteklenir. Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../language-reference/configure-language-version.md).

Bu makalenin geri kalanında bu özellikler kısaca açıklanmaktadır. Ayrıntılı makalelerin nerede kullanılabildiği, bu öğreticiler ve genel bakışların bağlantıları sağlanmıştır. Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz `dotnet try` :

1. [DotNet-TRY](https://github.com/dotnet/try/blob/main/DotNetTryLocal.md) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp8* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="readonly-members"></a>Salt okunur Üyeler

`readonly`Değiştiricisini bir yapının üyelerine uygulayabilirsiniz. Üyenin durumu değiştirmediğini belirtir. Bu, `readonly` değiştiricinin bir bildirime uygulanmasıyla daha ayrıntılı bir hale gelir `struct` .  Aşağıdaki kesilebilir yapıyı göz önünde bulundurun:

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

Çoğu yapı gibi `ToString()` Yöntem durumunu değiştirmez. Şu `readonly` bildirime değiştiricisini ekleyerek belirtebilirsiniz `ToString()` :

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Önceki değişiklik bir derleyici uyarısı oluşturur, çünkü `ToString` `Distance` Bu özelliğe erişir, ancak şu şekilde işaretlenmez `readonly` :

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Derleyici, savunma kopyası oluşturması gerektiğinde sizi uyarır.  `Distance`Özelliği durumu değiştirmez, bu nedenle bu uyarıyı, `readonly` bildirime değiştiricisini ekleyerek çözebilirsiniz:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

`readonly`Değiştiricinin salt okunurdur özelliğinde gerekli olduğuna dikkat edin. Derleyici `get` erişimcileri durumu değiştirmez olarak kabul etmez; açıkça bildirmeniz gerekir `readonly` . Otomatik uygulanan özellikler bir özel durumdur; Derleyici, tüm otomatik uygulanan alıcıları olarak değerlendirir `readonly` , bu nedenle `readonly` değiştiriciyi `X` ve özelliklere eklemek gerekmez `Y` .

Derleyici, `readonly` üyelerin durumu değiştirmiyor kuralını zorlar. Değiştirici kaldırmadığınız takdirde aşağıdaki yöntem derlenmez `readonly` :

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Bu özellik, tasarım amacınızı derleyicinin uygulamayı zorunlu kılabilir ve bu amaca göre iyileştirmeler yapabilmesini sağlar.

Daha fazla bilgi için [yapı türleri](../language-reference/builtin-types/struct.md) makalesinin [ `readonly` örnek Üyeler](../language-reference/builtin-types/struct.md#readonly-instance-members) bölümüne bakın.

## <a name="default-interface-methods"></a>Varsayılan arabirim metotları

Artık, arabirimlere Üyeler ekleyebilir ve bu üyeler için bir uygulama sağlayabilirsiniz. Bu dil özelliği, API yazarlarının, bu arabirimin var olan uygulamalarıyla kaynak veya ikili uyumluluğu bozmadan sonraki sürümlerde bir arabirime Yöntemler eklemesine olanak sağlar. Mevcut uygulamalar varsayılan uygulamayı *devralınır* . Bu özellik ayrıca C# ' nin, benzer özellikleri destekleyen Android veya Swift 'Ları hedefleyen API 'lerle birlikte çalışmasını da sağlar. Varsayılan arabirim yöntemleri, "nitelikler" dil özelliğine benzer senaryolar da sağlar.

Varsayılan arabirim yöntemleri birçok senaryoyu ve dil öğelerini etkiler. İlk öğreticimiz [, bir arabirimin varsayılan uygulamalarla güncelleştirilmesini](./tutorials/default-interface-methods-versions.md)kapsamaktadır.

## <a name="more-patterns-in-more-places"></a>Daha fazla yerde daha fazla desen

**Model eşleştirme** , ilişkili ancak farklı veri türleri arasında şekle bağımlı işlevsellik sağlamaya yönelik araçlar sağlar. C# 7,0, ifade ve deyimi kullanılarak tür desenleri ve sabit desenler için sözdizimi sunmuştur [`is`](../language-reference/keywords/is.md) [`switch`](../language-reference/keywords/switch.md) . Bu özellikler, verileri ve işlevselliği birbirinden canlı olarak programlama paradigmalarına desteklemeye yönelik ilk belirsiz adımları temsil eder. Sektör daha fazla mikro hizmete ve diğer bulut tabanlı mimarilere doğru hareket ederken diğer dil araçları gerekir.

C# 8,0, kodunuzda daha fazla yerde daha fazla model ifadesi kullanabilmeniz için bu sözlüğü genişletir. Verileriniz ve işlevselliklerinizin ayrı olması durumunda bu özellikleri göz önünde bulundurun. Algoritmalarınız nesnenin çalışma zamanı türü dışında bir olgusuna bağımlıysa, model eşleştirmeyi düşünün. Bu teknikler, hızlı tasarımlar için başka bir yol sağlar.

Yeni yerlerdeki yeni desenlere ek olarak C# 8,0 **özyinelemeli desenler** ekler. Özyinelemeli desenler, diğer desenleri içerebilen desenlerdir.

### <a name="switch-expressions"></a>Anahtar ifadeleri

Genellikle, bir [`switch`](../language-reference/keywords/switch.md) ifade blokların her birinde bir değer üretir `case` . **Anahtar ifadeleri** , daha kısa ifade sözdizimi kullanmanıza olanak sağlar. Daha az yinelenen `case` ve `break` anahtar sözcük ve daha az küme ayraçları vardır.  Örnek olarak, gökkuşağı renklerini listeleyen aşağıdaki sabit listesini göz önünde bulundurun:

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

Uygulamanız, `RGBColor` ve bileşenlerinden oluşturulmuş bir tür tanımlıysa, bir `R` değeri `G` bir `B` `Rainbow` anahtar IFADESI içeren aşağıdaki yöntemi kullanarak RGB değerlerine dönüştürebilirsiniz:

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

Burada birkaç sözdizimi geliştirmesi vardır:

- Değişkeni, `switch` anahtar sözcüğünden önce gelir. Farklı sıra, switch ifadesinin Switch deyiminin ayırt edilmesini görsel açıdan kolaylaştırır.
- `case`Ve `:` öğeleri ile değiştirilmiştir `=>` . Daha kısa ve sezgisel.
- `default`Durum, bir atma ile değiştirilmiştir `_` .
- Gövdeler deyimlerdir, deyimler değildir.

Klasik deyimin kullanıldığı denk kodla kontrast `switch` :

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

Daha fazla bilgi için bkz. [ `switch` ifadesi](../language-reference/operators/switch-expression.md).

### <a name="property-patterns"></a>Özellik desenleri

**Özellik deseninin** incelenen nesnenin özellikleriyle eşleştirmenize olanak sağlar. Alıcının adresine göre satış vergisini hesaplamak zorunda olan bir eCommerce sitesini düşünün. Bu hesaplama, bir sınıfın temel sorumluluğu değildir `Address` . Büyük olasılıkla, adres biçimi değişikliklerinden daha fazla sıklıkta değişecektir. Satış vergisi miktarı `State` adresin özelliğine bağlıdır. Aşağıdaki yöntem, adresten ve fiyattan satış vergisini hesaplamak için özellik modelini kullanır:

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.075M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

Model eşleştirme, bu algoritmayı ifade etmek için kısa bir sözdizimi oluşturur.

Daha fazla bilgi için, [desenler](../language-reference/operators/patterns.md) makalesinin [özellik düzeni](../language-reference/operators/patterns.md#property-pattern) bölümüne bakın.

### <a name="tuple-patterns"></a>Demet desenleri

Bazı algoritmalar birden fazla girişe bağımlıdır. **Demet desenleri** , [kayıt düzeni](../language-reference/builtin-types/value-tuples.md)olarak ifade edilen birden çok değere göre geçiş yapmanıza olanak sağlar. Aşağıdaki kod, oyun *rock, Paper, makas* için bir switch ifadesi gösterir:

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

İletiler kazanan kişiyi gösterir. Atma durumu, TIES veya diğer metin girişleri için üç birleşimi temsil eder.

### <a name="positional-patterns"></a>Konumsal desenler

Bazı türler `Deconstruct` , özelliklerini ayrı değişkenlere oluşturan bir yöntemi içerir. Bir `Deconstruct` Yöntem erişilebilir olduğunda, nesnenin özelliklerini incelemek ve bu özellikleri bir desen için kullanmak üzere **konumsal desenleri** kullanabilirsiniz.  `Point` `Deconstruct` Ve için ayrık değişkenler oluşturmak üzere bir yöntemi içeren aşağıdaki sınıfı göz önünde `X` bulundurun `Y` :

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

Ayrıca, bir Çeyrekli konumların çeşitli konumlarını temsil eden aşağıdaki sabit listesini göz önünde bulundurun:

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

Aşağıdaki yöntem, ve değerlerini ayıklamak için **konumsal model** kullanır `x` `y` . Sonra, `when` noktanın konumunu tespit etmek için bir yan tümce kullanır `Quadrant` :

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

Önceki anahtardaki atma deseninin ya da 0 olduğunda eşleşir `x` `y` ancak ikisi birden değildir. Switch ifadesinin bir değer üretmesi veya bir özel durum oluşturması gerekir. Durumlardan hiçbiri eşleşmezse, switch ifadesi bir özel durum oluşturur. Anahtar ifadenizde olası tüm durumları kapsamıyorsanız, derleyici sizin için bir uyarı oluşturur.

Bu [Gelişmiş öğreticide, model eşleştirme](../tutorials/pattern-matching.md)tekniklerini inceleyebilirsiniz. Konumsal bir desen hakkında daha fazla bilgi için, [desenler](../language-reference/operators/patterns.md) makalesinin [konumsal düzen](../language-reference/operators/patterns.md#positional-pattern) bölümüne bakın.

## <a name="using-declarations"></a>Bildirimleri kullanma

**Using bildirimi** , anahtar sözcüğünün önünde yer aldığı bir değişken bildirimidir `using` . Derleyiciye, bildirildiği değişkenin kapsayan kapsamın sonunda atılmasını söyler. Örneğin, bir metin dosyası yazan aşağıdaki kodu göz önünde bulundurun:

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

Yukarıdaki örnekte, yöntemi için kapanış ayracı ne zaman ulaşıldığında dosya atıldı. İçinde bildirildiği kapsamın sonu `file` . Yukarıdaki kod, klasik [using ifadesini](../language-reference/keywords/using-statement.md)kullanan aşağıdaki koda eşdeğerdir:

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        int skippedLines = 0;
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
        return skippedLines;
    } // file is disposed here
}
```

Önceki örnekte, ifadesiyle ilişkilendirilen kapanış ayracı aşıldığında dosya atıldı `using` .

Her iki durumda da derleyici çağrısını oluşturur `Dispose()` . Deyimdeki ifade atılabilir değilse derleyici bir hata oluşturur `using` .

## <a name="static-local-functions"></a>Statik yerel işlevler

`static`Yerel işlevin kapsayan kapsamdaki herhangi bir değişkeni yakalamamasına (başvuru) izin vermek için artık [Yerel işlevlere](../programming-guide/classes-and-structs/local-functions.md) değiştiricisini ekleyebilirsiniz. Bunu yapmak `CS8421` , "statik bir yerel işlev için başvuru içeremez \<variable> ."

Aşağıdaki kodu inceleyin. Yerel işlev, `LocalFunction` `y` kapsayan kapsamda (yöntemi) belirtilen değişkenine erişir `M` . Bu nedenle, `LocalFunction` `static` değiştiriciyle bildirilemez:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Aşağıdaki kod statik bir yerel işlev içerir. Bu, kapsayan kapsamdaki herhangi bir değişkene erişemediğinden statik olabilir:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Atılabilir ref yapıları

`struct`Değiştiriciyle belirtilen bir `ref` arabirim uygulayamaz, bu yüzden uygulayamaz <xref:System.IDisposable> . Bu nedenle, bir `ref struct` 'nin atılbilmesini sağlamak için erişilebilir bir `void Dispose()` yöntemi olmalıdır. Bu özellik bildirimler için de geçerlidir `readonly ref struct` .

## <a name="nullable-reference-types"></a>Boş değer atanabilir başvuru türleri

Null olabilen bir ek açıklama bağlamında, başvuru türündeki herhangi bir değişken **null yapılamayan bir başvuru türü** olarak kabul edilir. Bir değişkenin null olabileceğini belirtmek istiyorsanız, değişkeni null olabilen `?` bir **başvuru türü** olarak bildirmek için ile tür adını eklemeniz gerekir.

Null yapılamayan başvuru türleri için derleyici, yerel değişkenlerin bildirildiği sırada null olmayan bir değere başlatıldığından emin olmak için akış analizini kullanır. Alanlar oluşturma sırasında başlatılmalıdır. Derleyici, değişken kullanılabilir oluşturuculardan herhangi birine veya bir başlatıcı tarafından ayarlanmamışsa bir uyarı oluşturur. Ayrıca, null olamayan başvuru türlerine null olabilecek bir değer atanamaz.

Null yapılabilir başvuru türleri atanmamış veya null olarak başlatılmamış olduğundan emin olmak için denetlenmez. Ancak, derleyici, null olabilen bir başvuru türü değişkeninin erişilebilir olması veya null yapılamayan bir başvuruya atanmadan önce null olarak denetlendiğinden emin olmak için akış analizini kullanır.

Özelliği hakkında daha fazla bilgiyi [null yapılabilir başvuru türlerine](../nullable-references.md)genel bakış bölümünde bulabilirsiniz. Bu [null yapılabilir başvuru türleri öğreticisindeki](tutorials/nullable-reference-types.md)yeni bir uygulamada kendiniz deneyin. [Bir uygulamayı, null yapılabilir başvuru türlerini kullanmak için geçirme](tutorials/upgrade-to-nullable-references.md)bölümünde null yapılabilir başvuru türlerini kullanmak için mevcut bir kod temeli geçirme adımları hakkında bilgi edinin.

## <a name="asynchronous-streams"></a>Zaman uyumsuz akışlar

C# 8,0 ' den başlayarak akışları zaman uyumsuz olarak oluşturup kullanabilirsiniz. Zaman uyumsuz akış döndüren bir yöntem üç özelliğe sahiptir:

1. `async`Değiştiriciyle birlikte bildirilmiştir.
1. Döndürür <xref:System.Collections.Generic.IAsyncEnumerable%601> .
1. Yöntemi, `yield return` zaman uyumsuz akıştaki birbirini izleyen öğeleri döndürecek deyimleri içerir.

Zaman uyumsuz bir akışın kullanılması, `await` `foreach` akışın öğelerini Numaralandırdığınızda anahtar kelimeden önce anahtar sözcüğünü eklemenizi gerektirir. `await`Anahtar sözcüğü eklemek, zaman uyumsuz akışı belirten `async` ve değiştirici ile belirtilecek ve bir yöntem için izin verilen bir tür döndürecek yöntemi gerektirir `async` . Genellikle, veya döndürme anlamına <xref:System.Threading.Tasks.Task> gelir <xref:System.Threading.Tasks.Task%601> . Ayrıca, <xref:System.Threading.Tasks.ValueTask> veya olabilir <xref:System.Threading.Tasks.ValueTask%601> . Bir yöntem, zaman uyumsuz bir akış tüketebilir ve üretebilir, yani dönecektir <xref:System.Collections.Generic.IAsyncEnumerable%601> . Aşağıdaki kod, 0 ile 19 arasında bir sıra üretir, her bir sayı üretilmeden 100 ms bekler:

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

Şu ifadeyi kullanarak sırayı numaralandırabilirsiniz `await foreach` :

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Zaman uyumsuz akışları [oluşturma ve](tutorials/generate-consume-asynchronous-stream.md)kullanma öğreticimizde, zaman uyumsuz akışları kendiniz deneyebilirsiniz. Akış öğeleri varsayılan olarak yakalanan bağlamda işlenir. Bağlam yakalamayı devre dışı bırakmak istiyorsanız, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> genişletme yöntemini kullanın. Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz model](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)kullanma başlıklı makaleye bakın.

## <a name="asynchronous-disposable"></a>Zaman uyumsuz atılabilir

C# 8,0 ile başlayarak, dil arabirimi uygulayan zaman uyumsuz atılabilir türlerini destekler <xref:System.IAsyncDisposable?displayProperty=nameWithType> . `await using`Bir zaman uyumsuz atılabilir nesnesiyle çalışmak için ifadesini kullanın. Daha fazla bilgi için, bkz. [DisposeAsync yöntemi uygulama](../../standard/garbage-collection/implementing-disposeasync.md) makalesi.

## <a name="indices-and-ranges"></a>Dizinler ve aralıklar

Dizinler ve aralıklar bir dizideki tek öğelere veya aralıklara erişmek için bir kısa söz dizimi sağlar.

Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:

- <xref:System.Index?displayProperty=nameWithType> bir dizinin dizisini temsil eder.
- `^`Bir dizinin sıranın sonuna göre olduğunu belirten End işlecinden dizin.
- <xref:System.Range?displayProperty=nameWithType> bir dizinin alt aralığını temsil eder.
- `..`Aralık işleci, bir aralığın işlenenlerinin başlangıcını ve sonunu belirtir.

Dizin kurallarıyla başlayalım. Bir dizi düşünün `sequence` . `0`Dizin, ile aynıdır `sequence[0]` . `^0`Dizin, ile aynıdır `sequence[sequence.Length]` . Bunun `sequence[^0]` gibi bir özel durum oluşturur `sequence[sequence.Length]` . Herhangi bir sayı için `n` Dizin `^n` aynı olur `sequence.Length - n` .

Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir. Aralığın başlangıcı dahil, ancak aralığın sonu dışlamalı, ancak *Başlangıç* aralığa dahil değildir ancak *uç* aralığa dahil değildir. Aralık, tüm aralığı temsil eden `[0..^0]` tüm aralığı temsil eder `[0..sequence.Length]` .

Bazı örneklere bakalım. Başlangıç ve bitişten dizin ile açıklana ek olarak, aşağıdaki diziyi göz önünde bulundurun:

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

Son sözcüğü şu `^1` dizine alabilirsiniz:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Aşağıdaki kod, "hızlı", "kahverengi" ve "Fox" sözcüklerinin bulunduğu bir alt Aralık oluşturur. İle içerir `words[1]` `words[3]` . Öğe `words[4]` Aralık içinde değil.

```csharp
var quickBrownFox = words[1..4];
```

Aşağıdaki kod, "Lazy" ve "köpek" ile bir alt Aralık oluşturur. Ve içerir `words[^2]` `words[^1]` . Son dizin `words[^0]` dahil değildir:

```csharp
var lazyDog = words[^2..^0];
```

Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

Aralıkları, değişkenler olarak da bildirebilirsiniz:

```csharp
Range phrase = 1..4;
```

Aralık daha sonra `[` ve karakterleri içinde kullanılabilir `]` :

```csharp
var text = words[phrase];
```

Yalnızca dizin ve aralıkları destekleyen diziler değil. Ayrıca, veya [dizesiyle](../language-reference/builtin-types/reference-types.md#the-string-type)dizin ve aralıklar da kullanabilirsiniz <xref:System.Span%601> <xref:System.ReadOnlySpan%601> . Daha fazla bilgi için bkz. [Dizinler ve aralıklar için destek türü](tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).

Dizinler ve [aralıklar](tutorials/ranges-indexes.md)hakkında öğreticide dizinler ve aralıklar hakkında daha fazla bilgi bulabilirsiniz.

## <a name="null-coalescing-assignment"></a>Null birleştirme ataması

C# 8,0, null birleşim atama işlecini tanıtır `??=` . Sağ işleneninin değerini, sol taraftaki işlenenin `??=` değerini yalnızca sol taraftaki işlenen olarak değerlendirdiğinde atamak için işlecini kullanabilirsiniz `null` .

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

Daha fazla bilgi için?? [ve?? = operatörler](../language-reference/operators/null-coalescing-operator.md) makalesi.

## <a name="unmanaged-constructed-types"></a>Yönetilmeyen oluşturulmuş türler

C# 7,3 ve önceki sürümlerde, oluşturulmuş bir tür (en az bir tür bağımsız değişkeni içeren bir tür) [yönetilmeyen bir tür](../language-reference/builtin-types/unmanaged-types.md)olamaz. C# 8,0 ' den başlayarak, oluşturulmuş bir değer türü yalnızca yönetilmeyen türlerin alanlarını içeriyorsa yönetilmez.

Örneğin, genel türün aşağıdaki tanımı verildiğinde `Coords<T>` :

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

`Coords<int>`tür, C# 8,0 ve sonraki sürümlerde yönetilmeyen bir türdür. Herhangi bir yönetilmeyen tür için olduğu gibi, bu türden bir değişkene bir işaretçi oluşturabilir veya bu türün örnekleri için [yığında bir bellek bloğu ayırabilirsiniz](../language-reference/operators/stackalloc.md) :

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

Daha fazla bilgi için bkz. [yönetilmeyen türler](../language-reference/builtin-types/unmanaged-types.md).

## <a name="stackalloc-in-nested-expressions"></a>İç içe ifadelerde stackalloc

C# 8,0 ' den itibaren, bir [stackalloc](../language-reference/operators/stackalloc.md) ifadesinin sonucu <xref:System.Span%601?displayProperty=nameWithType> veya <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> türü ise, `stackalloc` ifadeyi diğer ifadelerde kullanabilirsiniz:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6, 8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Ara değerli tam dizelerin geliştirilmesi

Birlikte bulunan tam `$` `@` dizelerde ve belirteçlerin sırası herhangi biri olabilir: her ikisi de geçerli bir ara tür [](../language-reference/tokens/interpolated.md) `$@"..."` `@$"..."` dizelerdir. Önceki C# sürümlerinde, `$` belirtecin belirtecin önüne gösterilmesi gerekir `@` .
