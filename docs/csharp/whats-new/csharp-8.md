---
title: C# 8,0 C# kılavuzundaki yenilikler
description: 8,0 ' de C# bulunan yeni özelliklere genel bakış alın.
ms.date: 09/20/2019
ms.openlocfilehash: 6b5602db6ee61b1d9db4c906d6a14ea2f918ad0a
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275776"
---
# <a name="whats-new-in-c-80"></a>C# 8,0 sürümündeki yenilikler

C#8,0 aşağıdaki özellikleri ve geliştirmeleri C# dile ekler:

- [Salt okunur Üyeler](#readonly-members)
- [Varsayılan arabirim yöntemleri](#default-interface-methods)
- [Desenler eşleşen geliştirmeler](#more-patterns-in-more-places):
  - [Anahtar ifadeleri](#switch-expressions)
  - [Özellik desenleri](#property-patterns)
  - [Demet desenleri](#tuple-patterns)
  - [Konumsal desenler](#positional-patterns)
- [Bildirimleri kullanma](#using-declarations)
- [Statik yerel işlevler](#static-local-functions)
- [Atılabilir ref yapıları](#disposable-ref-structs)
- [Null yapılabilir başvuru türleri](#nullable-reference-types)
- [Zaman uyumsuz akışlar](#asynchronous-streams)
- [Dizinler ve aralıklar](#indices-and-ranges)
- [Null birleştirme ataması](#null-coalescing-assignment)
- [Yönetilmeyen oluşturulmuş türler](#unmanaged-constructed-types)
- [iç içe ifadelerde stackalloc](#stackalloc-in-nested-expressions)
- [Ara değerli tam dizelerin geliştirilmesi](#enhancement-of-interpolated-verbatim-strings)

Bu makalenin geri kalanında bu özellikler kısaca açıklanmaktadır. Ayrıntılı makalelerin nerede kullanılabildiği, bu öğreticiler ve genel bakışların bağlantıları sağlanmıştır. @No__t-0 genel aracını kullanarak ortamınızda bu özellikleri keşfedebilirsiniz:

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp8* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="readonly-members"></a>Salt okunur Üyeler

@No__t-0 değiştiricisini bir yapının herhangi bir üyesine uygulayabilirsiniz. Üyenin durumu değiştirmediğini belirtir. @No__t-0 değiştiricisinin `struct` bildirimine uygulanmasıyla daha ayrıntılı bir hale gelir.  Aşağıdaki kesilebilir yapıyı göz önünde bulundurun:

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

Çoğu yapı gibi `ToString()` yöntemi durumu değiştirmez. @No__t-0 değiştiricisini `ToString()` bildirimine ekleyerek belirtebilirsiniz:

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Yukarıdaki değişiklik bir derleyici uyarısı oluşturur, çünkü `ToString` `Distance` özelliğine eriştiğinde `readonly` işaretlenmez:

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Derleyici, savunma kopyası oluşturması gerektiğinde sizi uyarır.  @No__t-0 özelliği durumu değiştirmez, bu nedenle bildirime `readonly` değiştiricisi ekleyerek bu uyarıyı çözebilirsiniz:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Salt okuma özelliğinde `readonly` değiştiricinin gerekli olduğuna dikkat edin. Derleyici @no__t kabul etmez-0 erişimcileri durumu değiştirmez; `readonly` ' i açıkça bildirmeniz gerekir. Derleyici `readonly` üyelerinin durumu değiştirmediğinden kuralı zorlar. @No__t-0 değiştiricisini kaldırmadığınız müddetçe aşağıdaki yöntem derlenmeyecektir:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Bu özellik, tasarım amacınızı derleyicinin uygulamayı zorunlu kılabilir ve bu amaca göre iyileştirmeler yapabilmesini sağlar.

## <a name="default-interface-methods"></a>Varsayılan arabirim yöntemleri

Artık, arabirimlere Üyeler ekleyebilir ve bu üyeler için bir uygulama sağlayabilirsiniz. Bu dil özelliği, API yazarlarının, bu arabirimin var olan uygulamalarıyla kaynak veya ikili uyumluluğu bozmadan sonraki sürümlerde bir arabirime Yöntemler eklemesine olanak sağlar. Mevcut uygulamalar varsayılan uygulamayı *devralınır* . Bu özellik aynı zamanda C# , benzer özellikleri destekleyen Android veya Swift 'Ları hedefleyen API 'Lerle birlikte çalışmaya de olanak sağlar. Varsayılan arabirim yöntemleri, "nitelikler" dil özelliğine benzer senaryolar da sağlar.

Varsayılan arabirim yöntemleri birçok senaryoyu ve dil öğelerini etkiler. İlk öğreticimiz [, bir arabirimin varsayılan uygulamalarla güncelleştirilmesini](../tutorials/default-interface-methods-versions.md)kapsamaktadır. Diğer öğreticiler ve başvuru güncelleştirmeleri genel sürüm için zaman içinde geliyor.

## <a name="more-patterns-in-more-places"></a>Daha fazla yerde daha fazla desen

**Model eşleştirme** , ilişkili ancak farklı veri türleri arasında şekle bağımlı işlevsellik sağlamaya yönelik araçlar sağlar. C#7,0 [`is`](../language-reference/keywords/is.md) ifadesi ve [`switch`](../language-reference/keywords/switch.md) deyimi kullanılarak tür desenleri ve sabit desenler için sözdizimi sunuldu. Bu özellikler, verileri ve işlevselliği birbirinden canlı olarak programlama paradigmalarına desteklemeye yönelik ilk belirsiz adımları temsil eder. Sektör daha fazla mikro hizmete ve diğer bulut tabanlı mimarilere doğru hareket ederken diğer dil araçları gerekir.

C#8,0, kodunuzda daha fazla yerde daha fazla model ifadesi kullanabilmeniz için bu sözlüğü genişletir. Verileriniz ve işlevselliklerinizin ayrı olması durumunda bu özellikleri göz önünde bulundurun. Algoritmalarınız nesnenin çalışma zamanı türü dışında bir olgusuna bağımlıysa, model eşleştirmeyi düşünün. Bu teknikler, hızlı tasarımlar için başka bir yol sağlar.

Yeni yerlerdeki yeni desenlere ek olarak C# 8,0 **özyinelemeli desenler**ekler. Herhangi bir model ifadesinin sonucu bir ifadedir. Özyinelemeli bir model, sadece başka bir model ifadesinin çıktısına uygulanan bir model ifadesi olur.

### <a name="switch-expressions"></a>anahtar ifadeleri

Genellikle [`switch`](../language-reference/keywords/switch.md) bir ifade, `case` bloklarının her birinde bir değer üretir. **Anahtar ifadeleri** , daha kısa ifade sözdizimi kullanmanıza olanak sağlar. Daha az sayıda yinelenen `case` ve `break` anahtar sözcüğü ve daha az küme ayraçları vardır.  Örnek olarak, gökkuşağı renklerini listeleyen aşağıdaki sabit listesini göz önünde bulundurun:

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

Uygulamanız `R`, `G` ve `B` bileşenlerinden oluşturulan bir `RGBColor` türü tanımlıysa, bir anahtar ifadesi içeren aşağıdaki yöntemi kullanarak bir @no__t 4 değerini RGB değerlerine dönüştürebilirsiniz:

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

- Değişken `switch` anahtar sözcüğünden önce gelir. Farklı sıra, switch ifadesinin Switch deyiminin ayırt edilmesini görsel açıdan kolaylaştırır.
- @No__t-0 ve `:` öğeleri `=>` ile değiştirilmiştir. Daha kısa ve sezgisel.
- @No__t-0 durumu `_` atimiyle değiştirilmiştir.
- Gövdeler deyimlerdir, deyimler değildir.

Klasik `switch` ifadesini kullanarak denk kodla kontrast:

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

### <a name="property-patterns"></a>Özellik desenleri

**Özellik deseninin** incelenen nesnenin özellikleriyle eşleştirmenize olanak sağlar. Alıcının adresine göre satış vergisini hesaplamak zorunda olan bir eCommerce sitesini düşünün. Bu hesaplama `Address` sınıfının temel sorumluluğu değildir. Büyük olasılıkla, adres biçimi değişikliklerinden daha fazla sıklıkta değişecektir. Satış vergisinin miktarı, adresin `State` özelliğine bağlıdır. Aşağıdaki yöntem, adresten ve fiyattan satış vergisini hesaplamak için özellik modelini kullanır:

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

Model eşleştirme, bu algoritmayı ifade etmek için kısa bir sözdizimi oluşturur.

### <a name="tuple-patterns"></a>Demet desenleri

Bazı algoritmalar birden fazla girişe bağımlıdır. **Demet desenleri** , [kayıt düzeni](../tuples.md)olarak ifade edilen birden çok değere göre geçiş yapmanıza olanak sağlar.  Aşağıdaki kod, oyun *rock, Paper, makas*için bir switch ifadesi gösterir:

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

Bazı türler, özelliklerini ayrı değişkenlere oluşturan `Deconstruct` yöntemini içerir. @No__t-0 yöntemine erişilebilir olduğunda, nesnenin özelliklerini incelemek ve bu özellikleri bir desen için kullanmak üzere **konumsal desenleri** kullanabilirsiniz.  @No__t-2 ve `Y` için ayrık değişkenler oluşturmak üzere bir `Deconstruct` yöntemi içeren aşağıdaki `Point` sınıfını göz önünde bulundurun:

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

Aşağıdaki yöntem, `x` ve `y` değerlerini ayıklamak için **konumsal bir model** kullanır. Sonra, noktanın `Quadrant` ' i belirlemekte `when` yan tümcesini kullanır:

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

Önceki anahtardaki atma deseninin `x` veya `y` olduğu zaman eşleşir, ancak her ikisi birden değildir. Switch ifadesinin bir değer üretmesi veya bir özel durum oluşturması gerekir. Durumlardan hiçbiri eşleşmezse, switch ifadesi bir özel durum oluşturur. Anahtar ifadenizde olası tüm durumları kapsamıyordıysanız, derleyici sizin için bir uyarı oluşturur.

Bu [Gelişmiş öğreticide, model eşleştirme](../tutorials/pattern-matching.md)tekniklerini inceleyebilirsiniz.

## <a name="using-declarations"></a>bildirimleri kullanma

**Using bildirimi** , `using` anahtar sözcüğünün önünde yer aldığı bir değişken bildirimidir. Derleyiciye, bildirildiği değişkenin kapsayan kapsamın sonunda atılmasını söyler. Örneğin, bir metin dosyası yazan aşağıdaki kodu göz önünde bulundurun:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

Yukarıdaki örnekte, yöntemi için kapanış ayracı ne zaman ulaşıldığında dosya atıldı. @No__t-0 ' ın bildirildiği kapsamın sonu. Yukarıdaki kod, klasik [using ifadesini](../language-reference/keywords/using-statement.md)kullanan aşağıdaki koda eşdeğerdir:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

Yukarıdaki örnekte, `using` ifadesiyle ilişkilendirilen kapanış ayracı erişildiğinde dosya atıldı.

Her iki durumda da derleyici `Dispose()` ' a çağrı üretir. @No__t-0 deyimindeki ifade atılabilir değilse derleyici bir hata oluşturur.

## <a name="static-local-functions"></a>Statik yerel işlevler

Yerel işlevin kapsayan kapsamdaki herhangi bir değişkeni yakalamamasına (başvuru) izin vermek için artık yerel işlevlere `static` değiştiricisini ekleyebilirsiniz. Bunu yapmak `CS8421`, "statik bir yerel işlev \<variable > başvuru içeremez." 

Aşağıdaki kodu göz önünde bulundurun. @No__t-0 yerel işlevi, kapsayan kapsamda (`M` yöntemi) belirtilen `y` değişkenine erişir. Bu nedenle, `LocalFunction` `static` değiştiricisi ile bildirilemez:

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

@No__t-1 değiştiricisi ile tanımlanan `struct` hiçbir arabirim uygulayamaz, bu nedenle <xref:System.IDisposable> uygulayamaz. Bu nedenle, bir @no__t, atılmayacak şekilde etkinleştirmek için, erişilebilir bir `void Dispose()` yöntemi olmalıdır. Bu, `readonly ref struct` bildirimleri için de geçerlidir.

## <a name="nullable-reference-types"></a>Null yapılabilir başvuru türleri

Null olabilen bir ek açıklama bağlamında, başvuru türündeki herhangi bir değişken **null yapılamayan bir başvuru türü**olarak kabul edilir. Bir değişkenin null olabileceğini belirtmek istiyorsanız, değişkeni null olabilen bir **başvuru türü**olarak bildirmek için tür adını `?` ile eklemeniz gerekir.

Null yapılamayan başvuru türleri için derleyici, yerel değişkenlerin bildirildiği sırada null olmayan bir değere başlatıldığından emin olmak için akış analizini kullanır. Alanlar oluşturma sırasında başlatılmalıdır. Değişken, kullanılabilir oluşturuculardan herhangi birine veya bir başlatıcı tarafından ayarlanmamışsa, derleyici bir uyarı oluşturur. Ayrıca, null olamayan başvuru türlerine null olabilecek bir değer atanamaz.

Null yapılabilir başvuru türleri atanmamış veya null olarak başlatılmamış olduğundan emin olmak için denetlenmez. Ancak, derleyici, null olabilen bir başvuru türü değişkeninin erişilebilir olması veya null yapılamayan bir başvuruya atanmadan önce null olarak denetlendiğinden emin olmak için akış analizini kullanır.

Özelliği hakkında daha fazla bilgiyi [null yapılabilir başvuru türlerine](../nullable-references.md)genel bakış bölümünde bulabilirsiniz. Bu [null yapılabilir başvuru türleri öğreticisindeki](../tutorials/nullable-reference-types.md)yeni bir uygulamada kendiniz deneyin. [Bir uygulamayı, null yapılabilir başvuru türlerini kullanmak için geçirme](../tutorials/upgrade-to-nullable-references.md)bölümünde null yapılabilir başvuru türlerini kullanmak için mevcut bir kod temeli geçirme adımları hakkında bilgi edinin.

## <a name="asynchronous-streams"></a>Zaman uyumsuz akışlar

8,0 ile C# başlayarak akışları zaman uyumsuz olarak oluşturabilir ve kullanabilirsiniz. Zaman uyumsuz akış döndüren bir yöntem üç özelliğe sahiptir:

1. @No__t-0 değiştiricisi ile birlikte bildirilmiştir.
1. @No__t-0 döndürür.
1. Yöntemi, zaman uyumsuz akıştaki birbirini izleyen öğeleri döndürmek için `yield return` deyimlerini içerir.

Zaman uyumsuz bir akışın kullanılması, akışın öğelerini Numaralandırdığınızda `foreach` anahtar sözcüğünden önce `await` anahtar sözcüğünü eklemenizi gerektirir. @No__t-0 anahtar sözcüğünü eklemek, zaman uyumsuz akışı belirten ve `async` değiştiricisiyle belirtilecek ve `async` yöntemi için izin verilen bir tür döndürecek yöntemi gerektirir. Genellikle bu, <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> döndüren anlamına gelir. Ayrıca, <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601> olabilir. Bir yöntem, bir zaman uyumsuz akış tüketebilir ve üretebilir, bu da <xref:System.Collections.Generic.IAsyncEnumerable%601> döndürmesi anlamına gelir. Aşağıdaki kod, 0 ile 19 arasında bir sıra üretir, her bir sayı üretilmeden 100 ms bekler:

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

@No__t-0 ifadesini kullanarak sırayı numaralandırabilirsiniz:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Zaman uyumsuz akışları [oluşturma ve](../tutorials/generate-consume-asynchronous-stream.md)kullanma öğreticimizde, zaman uyumsuz akışları kendiniz deneyebilirsiniz.

## <a name="indices-and-ranges"></a>Dizinler ve aralıklar

Dizinler ve aralıklar bir dizideki tek öğelere veya aralıklara erişmek için bir kısa söz dizimi sağlar.

Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:

- <xref:System.Index?displayProperty=nameWithType> bir dizinin bir dizinini temsil eder.
- Bir dizinin dizinin sonuna göre olduğunu belirten `^` bitiş işlecinden dizin.
- <xref:System.Range?displayProperty=nameWithType> bir dizinin alt aralığını temsil eder.
- Aralık işleci `..`, bir aralığın işlenenleri olarak başlangıcını ve sonunu belirtir.

Dizin kurallarıyla başlayalım. Bir dizi @no__t düşünün-0. @No__t-0 dizini, `sequence[0]` ile aynıdır. @No__t-0 dizini, `sequence[sequence.Length]` ile aynıdır. @No__t-0 ' ın, `sequence[sequence.Length]` olduğu gibi bir özel durum oluşturmadığını unutmayın. @No__t-0 olan herhangi bir sayı için, `^n` dizini `sequence.Length - n` ile aynıdır.

Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir. Aralığın başlangıcı dahil, ancak aralığın sonu dışlamalı, ancak *Başlangıç* aralığa dahil değildir ancak *bitiş* aralığa eklenmez. @No__t-0 aralığı tüm aralığı temsil eder, tıpkı `[0..sequence.Length]` tüm aralığı temsil eder.

Birkaç örneğe bakalım. Başlangıç ve bitişten dizin ile açıklana ek olarak, aşağıdaki diziyi göz önünde bulundurun:

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

Son kelimeyi `^1` diziniyle alabilirsiniz:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Aşağıdaki kod, "quick", "brown" ve "fox" sözcüklerinin bulunduğu bir alt aralık oluşturur. @No__t-0 ile `words[3]` aralığını içerir. @No__t-0 öğesi aralık içinde değildir.

```csharp
var quickBrownFox = words[1..4];
```

Aşağıdaki kod, "lazy" ve "dog" sözcüklerini içeren bir alt aralık oluşturur. @No__t-0 ile `words[^1]` aralığını içerir. @No__t-0 bitiş dizini dahil değildir:

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

Aralık daha sonra `[` ve `]` karakterleri içinde kullanılabilir:

```csharp
var text = words[phrase];
```

Yalnızca dizin ve aralıkları destekleyen diziler değil. Dizin ve aralıkları [dize](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> ile de kullanabilirsiniz. Daha fazla bilgi için bkz. [Dizinler ve aralıklar için destek türü](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).

Dizinler ve [aralıklar](../tutorials/ranges-indexes.md)hakkında öğreticide dizinler ve aralıklar hakkında daha fazla bilgi bulabilirsiniz.

## <a name="null-coalescing-assignment"></a>Null birleştirme ataması

C#8,0, `??=` ' i null birleşim atama işlecini tanıtır. Sağ işleneninin değerini yalnızca sol taraftaki işlenenin `null` olarak değerlendirilirse, sol taraftaki işlenenin değerini atamak için `??=` işlecini kullanabilirsiniz.

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

7,3 ve önceki sürümlerde, oluşturulmuş bir tür (en az bir tür bağımsız değişkeni içeren bir tür) yönetilmeyen bir tür olamaz. [](../language-reference/builtin-types/unmanaged-types.md) C# 8,0 ile C# başlayarak, oluşturulmuş bir değer türü yalnızca yönetilmeyen türlerin alanlarını içeriyorsa yönetilmez.

Örneğin, genel `Coords<T>` türünün Aşağıdaki tanımı verildiğinde:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

`Coords<int>` türü, C# 8,0 ve sonraki sürümlerde yönetilmeyen bir türdür. Herhangi bir yönetilmeyen tür için olduğu gibi, bu türden bir değişkene bir işaretçi oluşturabilir veya bu türün örnekleri için [yığında bir bellek bloğu ayırabilirsiniz](../language-reference/operators/stackalloc.md) :

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

Daha fazla bilgi için bkz. [yönetilmeyen türler](../language-reference/builtin-types/unmanaged-types.md).

## <a name="stackalloc-in-nested-expressions"></a>iç içe ifadelerde stackalloc

8,0 ile C# başlayarak, bir [stackalloc](../language-reference/operators/stackalloc.md) ifadesinin sonucu <xref:System.Span%601?displayProperty=nameWithType> veya <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> türünde ise, diğer ifadelerde `stackalloc` ifadesini kullanabilirsiniz:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Ara değerli tam dizelerin geliştirilmesi

@No__t-0 ve `@` belirteçlerinin sırası, [enterpolasyonlu](../language-reference/tokens/interpolated.md) harfine dizelerdeki herhangi biri olabilir: hem `$@"..."` hem de `@$"..."` geçerli bir arada bulunan dizeler. Önceki C# sürümlerde `$` belirtecinin `@` belirtecinden önce görünmesi gerekir.
