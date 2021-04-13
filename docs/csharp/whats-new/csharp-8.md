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
# <a name="whats-new-in-c-80"></a><span data-ttu-id="41890-103">C# 8.0 sürümündeki yenilikler</span><span class="sxs-lookup"><span data-stu-id="41890-103">What's new in C# 8.0</span></span>

<span data-ttu-id="41890-104">C# 8,0, C# diline aşağıdaki özellikleri ve geliştirmeleri ekler:</span><span class="sxs-lookup"><span data-stu-id="41890-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="41890-105">Salt okunur Üyeler</span><span class="sxs-lookup"><span data-stu-id="41890-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="41890-106">Varsayılan arabirim metotları</span><span class="sxs-lookup"><span data-stu-id="41890-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="41890-107">[Desenler eşleşen geliştirmeler](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="41890-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="41890-108">Anahtar ifadeleri</span><span class="sxs-lookup"><span data-stu-id="41890-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="41890-109">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="41890-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="41890-110">Demet desenleri</span><span class="sxs-lookup"><span data-stu-id="41890-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="41890-111">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="41890-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="41890-112">Bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="41890-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="41890-113">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="41890-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="41890-114">Atılabilir ref yapıları</span><span class="sxs-lookup"><span data-stu-id="41890-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="41890-115">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="41890-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="41890-116">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="41890-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="41890-117">Zaman uyumsuz atılabilir</span><span class="sxs-lookup"><span data-stu-id="41890-117">Asynchronous disposable</span></span>](#asynchronous-disposable)
- [<span data-ttu-id="41890-118">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="41890-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="41890-119">Null birleştirme ataması</span><span class="sxs-lookup"><span data-stu-id="41890-119">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="41890-120">Yönetilmeyen oluşturulmuş türler</span><span class="sxs-lookup"><span data-stu-id="41890-120">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="41890-121">İç içe ifadelerde stackalloc</span><span class="sxs-lookup"><span data-stu-id="41890-121">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="41890-122">Ara değerli tam dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="41890-122">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="41890-123">C# 8,0, **.NET Core 3. x** ve **.NET Standard 2,1**' de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="41890-123">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="41890-124">Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="41890-124">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="41890-125">Bu makalenin geri kalanında bu özellikler kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41890-125">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="41890-126">Ayrıntılı makalelerin nerede kullanılabildiği, bu öğreticiler ve genel bakışların bağlantıları sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="41890-126">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="41890-127">Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz `dotnet try` :</span><span class="sxs-lookup"><span data-stu-id="41890-127">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="41890-128">[DotNet-TRY](https://github.com/dotnet/try/blob/main/DotNetTryLocal.md) küresel aracını yükler.</span><span class="sxs-lookup"><span data-stu-id="41890-128">Install the [dotnet-try](https://github.com/dotnet/try/blob/main/DotNetTryLocal.md) global tool.</span></span>
1. <span data-ttu-id="41890-129">[DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="41890-129">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="41890-130">*TRY-Samples* deposu için geçerli dizini *csharp8* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="41890-130">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="41890-131">`dotnet try` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="41890-131">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="41890-132">Salt okunur Üyeler</span><span class="sxs-lookup"><span data-stu-id="41890-132">Readonly members</span></span>

<span data-ttu-id="41890-133">`readonly`Değiştiricisini bir yapının üyelerine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41890-133">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="41890-134">Üyenin durumu değiştirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="41890-134">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="41890-135">Bu, `readonly` değiştiricinin bir bildirime uygulanmasıyla daha ayrıntılı bir hale gelir `struct` .</span><span class="sxs-lookup"><span data-stu-id="41890-135">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="41890-136">Aşağıdaki kesilebilir yapıyı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="41890-136">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="41890-137">Çoğu yapı gibi `ToString()` Yöntem durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="41890-137">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="41890-138">Şu `readonly` bildirime değiştiricisini ekleyerek belirtebilirsiniz `ToString()` :</span><span class="sxs-lookup"><span data-stu-id="41890-138">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="41890-139">Önceki değişiklik bir derleyici uyarısı oluşturur, çünkü `ToString` `Distance` Bu özelliğe erişir, ancak şu şekilde işaretlenmez `readonly` :</span><span class="sxs-lookup"><span data-stu-id="41890-139">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="41890-140">Derleyici, savunma kopyası oluşturması gerektiğinde sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="41890-140">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="41890-141">`Distance`Özelliği durumu değiştirmez, bu nedenle bu uyarıyı, `readonly` bildirime değiştiricisini ekleyerek çözebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41890-141">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="41890-142">`readonly`Değiştiricinin salt okunurdur özelliğinde gerekli olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="41890-142">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="41890-143">Derleyici `get` erişimcileri durumu değiştirmez olarak kabul etmez; açıkça bildirmeniz gerekir `readonly` .</span><span class="sxs-lookup"><span data-stu-id="41890-143">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="41890-144">Otomatik uygulanan özellikler bir özel durumdur; Derleyici, tüm otomatik uygulanan alıcıları olarak değerlendirir `readonly` , bu nedenle `readonly` değiştiriciyi `X` ve özelliklere eklemek gerekmez `Y` .</span><span class="sxs-lookup"><span data-stu-id="41890-144">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as `readonly`, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="41890-145">Derleyici, `readonly` üyelerin durumu değiştirmiyor kuralını zorlar.</span><span class="sxs-lookup"><span data-stu-id="41890-145">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="41890-146">Değiştirici kaldırmadığınız takdirde aşağıdaki yöntem derlenmez `readonly` :</span><span class="sxs-lookup"><span data-stu-id="41890-146">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="41890-147">Bu özellik, tasarım amacınızı derleyicinin uygulamayı zorunlu kılabilir ve bu amaca göre iyileştirmeler yapabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-147">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

<span data-ttu-id="41890-148">Daha fazla bilgi için [yapı türleri](../language-reference/builtin-types/struct.md) makalesinin [ `readonly` örnek Üyeler](../language-reference/builtin-types/struct.md#readonly-instance-members) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="41890-148">For more information, see the [`readonly` instance members](../language-reference/builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../language-reference/builtin-types/struct.md) article.</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="41890-149">Varsayılan arabirim metotları</span><span class="sxs-lookup"><span data-stu-id="41890-149">Default interface methods</span></span>

<span data-ttu-id="41890-150">Artık, arabirimlere Üyeler ekleyebilir ve bu üyeler için bir uygulama sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41890-150">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="41890-151">Bu dil özelliği, API yazarlarının, bu arabirimin var olan uygulamalarıyla kaynak veya ikili uyumluluğu bozmadan sonraki sürümlerde bir arabirime Yöntemler eklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-151">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="41890-152">Mevcut uygulamalar varsayılan uygulamayı *devralınır* .</span><span class="sxs-lookup"><span data-stu-id="41890-152">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="41890-153">Bu özellik ayrıca C# ' nin, benzer özellikleri destekleyen Android veya Swift 'Ları hedefleyen API 'lerle birlikte çalışmasını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-153">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="41890-154">Varsayılan arabirim yöntemleri, "nitelikler" dil özelliğine benzer senaryolar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-154">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="41890-155">Varsayılan arabirim yöntemleri birçok senaryoyu ve dil öğelerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="41890-155">Default interface methods affect many scenarios and language elements.</span></span> <span data-ttu-id="41890-156">İlk öğreticimiz [, bir arabirimin varsayılan uygulamalarla güncelleştirilmesini](./tutorials/default-interface-methods-versions.md)kapsamaktadır.</span><span class="sxs-lookup"><span data-stu-id="41890-156">Our first tutorial covers [updating an interface with default implementations](./tutorials/default-interface-methods-versions.md).</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="41890-157">Daha fazla yerde daha fazla desen</span><span class="sxs-lookup"><span data-stu-id="41890-157">More patterns in more places</span></span>

<span data-ttu-id="41890-158">**Model eşleştirme** , ilişkili ancak farklı veri türleri arasında şekle bağımlı işlevsellik sağlamaya yönelik araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-158">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="41890-159">C# 7,0, ifade ve deyimi kullanılarak tür desenleri ve sabit desenler için sözdizimi sunmuştur [`is`](../language-reference/keywords/is.md) [`switch`](../language-reference/keywords/switch.md) .</span><span class="sxs-lookup"><span data-stu-id="41890-159">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="41890-160">Bu özellikler, verileri ve işlevselliği birbirinden canlı olarak programlama paradigmalarına desteklemeye yönelik ilk belirsiz adımları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="41890-160">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="41890-161">Sektör daha fazla mikro hizmete ve diğer bulut tabanlı mimarilere doğru hareket ederken diğer dil araçları gerekir.</span><span class="sxs-lookup"><span data-stu-id="41890-161">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="41890-162">C# 8,0, kodunuzda daha fazla yerde daha fazla model ifadesi kullanabilmeniz için bu sözlüğü genişletir.</span><span class="sxs-lookup"><span data-stu-id="41890-162">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="41890-163">Verileriniz ve işlevselliklerinizin ayrı olması durumunda bu özellikleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="41890-163">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="41890-164">Algoritmalarınız nesnenin çalışma zamanı türü dışında bir olgusuna bağımlıysa, model eşleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="41890-164">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="41890-165">Bu teknikler, hızlı tasarımlar için başka bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-165">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="41890-166">Yeni yerlerdeki yeni desenlere ek olarak C# 8,0 **özyinelemeli desenler** ekler.</span><span class="sxs-lookup"><span data-stu-id="41890-166">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="41890-167">Özyinelemeli desenler, diğer desenleri içerebilen desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="41890-167">Recursive patterns are patterns that can contain other patterns.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="41890-168">Anahtar ifadeleri</span><span class="sxs-lookup"><span data-stu-id="41890-168">Switch expressions</span></span>

<span data-ttu-id="41890-169">Genellikle, bir [`switch`](../language-reference/keywords/switch.md) ifade blokların her birinde bir değer üretir `case` .</span><span class="sxs-lookup"><span data-stu-id="41890-169">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="41890-170">**Anahtar ifadeleri** , daha kısa ifade sözdizimi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-170">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="41890-171">Daha az yinelenen `case` ve `break` anahtar sözcük ve daha az küme ayraçları vardır.</span><span class="sxs-lookup"><span data-stu-id="41890-171">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="41890-172">Örnek olarak, gökkuşağı renklerini listeleyen aşağıdaki sabit listesini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="41890-172">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="41890-173">Uygulamanız, `RGBColor` ve bileşenlerinden oluşturulmuş bir tür tanımlıysa, bir `R` değeri `G` bir `B` `Rainbow` anahtar IFADESI içeren aşağıdaki yöntemi kullanarak RGB değerlerine dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41890-173">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="41890-174">Burada birkaç sözdizimi geliştirmesi vardır:</span><span class="sxs-lookup"><span data-stu-id="41890-174">There are several syntax improvements here:</span></span>

- <span data-ttu-id="41890-175">Değişkeni, `switch` anahtar sözcüğünden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="41890-175">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="41890-176">Farklı sıra, switch ifadesinin Switch deyiminin ayırt edilmesini görsel açıdan kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="41890-176">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="41890-177">`case`Ve `:` öğeleri ile değiştirilmiştir `=>` .</span><span class="sxs-lookup"><span data-stu-id="41890-177">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="41890-178">Daha kısa ve sezgisel.</span><span class="sxs-lookup"><span data-stu-id="41890-178">It's more concise and intuitive.</span></span>
- <span data-ttu-id="41890-179">`default`Durum, bir atma ile değiştirilmiştir `_` .</span><span class="sxs-lookup"><span data-stu-id="41890-179">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="41890-180">Gövdeler deyimlerdir, deyimler değildir.</span><span class="sxs-lookup"><span data-stu-id="41890-180">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="41890-181">Klasik deyimin kullanıldığı denk kodla kontrast `switch` :</span><span class="sxs-lookup"><span data-stu-id="41890-181">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

<span data-ttu-id="41890-182">Daha fazla bilgi için bkz. [ `switch` ifadesi](../language-reference/operators/switch-expression.md).</span><span class="sxs-lookup"><span data-stu-id="41890-182">For more information, see [`switch` expression](../language-reference/operators/switch-expression.md).</span></span>

### <a name="property-patterns"></a><span data-ttu-id="41890-183">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="41890-183">Property patterns</span></span>

<span data-ttu-id="41890-184">**Özellik deseninin** incelenen nesnenin özellikleriyle eşleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-184">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="41890-185">Alıcının adresine göre satış vergisini hesaplamak zorunda olan bir eCommerce sitesini düşünün.</span><span class="sxs-lookup"><span data-stu-id="41890-185">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="41890-186">Bu hesaplama, bir sınıfın temel sorumluluğu değildir `Address` .</span><span class="sxs-lookup"><span data-stu-id="41890-186">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="41890-187">Büyük olasılıkla, adres biçimi değişikliklerinden daha fazla sıklıkta değişecektir.</span><span class="sxs-lookup"><span data-stu-id="41890-187">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="41890-188">Satış vergisi miktarı `State` adresin özelliğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="41890-188">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="41890-189">Aşağıdaki yöntem, adresten ve fiyattan satış vergisini hesaplamak için özellik modelini kullanır:</span><span class="sxs-lookup"><span data-stu-id="41890-189">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="41890-190">Model eşleştirme, bu algoritmayı ifade etmek için kısa bir sözdizimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41890-190">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

<span data-ttu-id="41890-191">Daha fazla bilgi için, [desenler](../language-reference/operators/patterns.md) makalesinin [özellik düzeni](../language-reference/operators/patterns.md#property-pattern) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="41890-191">For more information, see the [Property pattern](../language-reference/operators/patterns.md#property-pattern) section of the [Patterns](../language-reference/operators/patterns.md) article.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="41890-192">Demet desenleri</span><span class="sxs-lookup"><span data-stu-id="41890-192">Tuple patterns</span></span>

<span data-ttu-id="41890-193">Bazı algoritmalar birden fazla girişe bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="41890-193">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="41890-194">**Demet desenleri** , [kayıt düzeni](../language-reference/builtin-types/value-tuples.md)olarak ifade edilen birden çok değere göre geçiş yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-194">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../language-reference/builtin-types/value-tuples.md).</span></span> <span data-ttu-id="41890-195">Aşağıdaki kod, oyun *rock, Paper, makas* için bir switch ifadesi gösterir:</span><span class="sxs-lookup"><span data-stu-id="41890-195">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="41890-196">İletiler kazanan kişiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="41890-196">The messages indicate the winner.</span></span> <span data-ttu-id="41890-197">Atma durumu, TIES veya diğer metin girişleri için üç birleşimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="41890-197">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="41890-198">Konumsal desenler</span><span class="sxs-lookup"><span data-stu-id="41890-198">Positional patterns</span></span>

<span data-ttu-id="41890-199">Bazı türler `Deconstruct` , özelliklerini ayrı değişkenlere oluşturan bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="41890-199">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="41890-200">Bir `Deconstruct` Yöntem erişilebilir olduğunda, nesnenin özelliklerini incelemek ve bu özellikleri bir desen için kullanmak üzere **konumsal desenleri** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41890-200">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="41890-201">`Point` `Deconstruct` Ve için ayrık değişkenler oluşturmak üzere bir yöntemi içeren aşağıdaki sınıfı göz önünde `X` bulundurun `Y` :</span><span class="sxs-lookup"><span data-stu-id="41890-201">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="41890-202">Ayrıca, bir Çeyrekli konumların çeşitli konumlarını temsil eden aşağıdaki sabit listesini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="41890-202">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="41890-203">Aşağıdaki yöntem, ve değerlerini ayıklamak için **konumsal model** kullanır `x` `y` .</span><span class="sxs-lookup"><span data-stu-id="41890-203">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="41890-204">Sonra, `when` noktanın konumunu tespit etmek için bir yan tümce kullanır `Quadrant` :</span><span class="sxs-lookup"><span data-stu-id="41890-204">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="41890-205">Önceki anahtardaki atma deseninin ya da 0 olduğunda eşleşir `x` `y` ancak ikisi birden değildir.</span><span class="sxs-lookup"><span data-stu-id="41890-205">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="41890-206">Switch ifadesinin bir değer üretmesi veya bir özel durum oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41890-206">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="41890-207">Durumlardan hiçbiri eşleşmezse, switch ifadesi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41890-207">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="41890-208">Anahtar ifadenizde olası tüm durumları kapsamıyorsanız, derleyici sizin için bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41890-208">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="41890-209">Bu [Gelişmiş öğreticide, model eşleştirme](../tutorials/pattern-matching.md)tekniklerini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41890-209">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span> <span data-ttu-id="41890-210">Konumsal bir desen hakkında daha fazla bilgi için, [desenler](../language-reference/operators/patterns.md) makalesinin [konumsal düzen](../language-reference/operators/patterns.md#positional-pattern) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="41890-210">For more information about a positional pattern, see the [Positional pattern](../language-reference/operators/patterns.md#positional-pattern) section of the [Patterns](../language-reference/operators/patterns.md) article.</span></span>

## <a name="using-declarations"></a><span data-ttu-id="41890-211">Bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="41890-211">Using declarations</span></span>

<span data-ttu-id="41890-212">**Using bildirimi** , anahtar sözcüğünün önünde yer aldığı bir değişken bildirimidir `using` .</span><span class="sxs-lookup"><span data-stu-id="41890-212">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="41890-213">Derleyiciye, bildirildiği değişkenin kapsayan kapsamın sonunda atılmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="41890-213">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="41890-214">Örneğin, bir metin dosyası yazan aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="41890-214">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="41890-215">Yukarıdaki örnekte, yöntemi için kapanış ayracı ne zaman ulaşıldığında dosya atıldı.</span><span class="sxs-lookup"><span data-stu-id="41890-215">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="41890-216">İçinde bildirildiği kapsamın sonu `file` .</span><span class="sxs-lookup"><span data-stu-id="41890-216">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="41890-217">Yukarıdaki kod, klasik [using ifadesini](../language-reference/keywords/using-statement.md)kullanan aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="41890-217">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="41890-218">Önceki örnekte, ifadesiyle ilişkilendirilen kapanış ayracı aşıldığında dosya atıldı `using` .</span><span class="sxs-lookup"><span data-stu-id="41890-218">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="41890-219">Her iki durumda da derleyici çağrısını oluşturur `Dispose()` .</span><span class="sxs-lookup"><span data-stu-id="41890-219">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="41890-220">Deyimdeki ifade atılabilir değilse derleyici bir hata oluşturur `using` .</span><span class="sxs-lookup"><span data-stu-id="41890-220">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="41890-221">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="41890-221">Static local functions</span></span>

<span data-ttu-id="41890-222">`static`Yerel işlevin kapsayan kapsamdaki herhangi bir değişkeni yakalamamasına (başvuru) izin vermek için artık [Yerel işlevlere](../programming-guide/classes-and-structs/local-functions.md) değiştiricisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41890-222">You can now add the `static` modifier to [local functions](../programming-guide/classes-and-structs/local-functions.md) to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="41890-223">Bunu yapmak `CS8421` , "statik bir yerel işlev için başvuru içeremez \<variable> ."</span><span class="sxs-lookup"><span data-stu-id="41890-223">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span>

<span data-ttu-id="41890-224">Aşağıdaki kodu inceleyin.</span><span class="sxs-lookup"><span data-stu-id="41890-224">Consider the following code.</span></span> <span data-ttu-id="41890-225">Yerel işlev, `LocalFunction` `y` kapsayan kapsamda (yöntemi) belirtilen değişkenine erişir `M` .</span><span class="sxs-lookup"><span data-stu-id="41890-225">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="41890-226">Bu nedenle, `LocalFunction` `static` değiştiriciyle bildirilemez:</span><span class="sxs-lookup"><span data-stu-id="41890-226">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="41890-227">Aşağıdaki kod statik bir yerel işlev içerir.</span><span class="sxs-lookup"><span data-stu-id="41890-227">The following code contains a static local function.</span></span> <span data-ttu-id="41890-228">Bu, kapsayan kapsamdaki herhangi bir değişkene erişemediğinden statik olabilir:</span><span class="sxs-lookup"><span data-stu-id="41890-228">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="41890-229">Atılabilir ref yapıları</span><span class="sxs-lookup"><span data-stu-id="41890-229">Disposable ref structs</span></span>

<span data-ttu-id="41890-230">`struct`Değiştiriciyle belirtilen bir `ref` arabirim uygulayamaz, bu yüzden uygulayamaz <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="41890-230">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="41890-231">Bu nedenle, bir `ref struct` 'nin atılbilmesini sağlamak için erişilebilir bir `void Dispose()` yöntemi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41890-231">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="41890-232">Bu özellik bildirimler için de geçerlidir `readonly ref struct` .</span><span class="sxs-lookup"><span data-stu-id="41890-232">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="41890-233">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="41890-233">Nullable reference types</span></span>

<span data-ttu-id="41890-234">Null olabilen bir ek açıklama bağlamında, başvuru türündeki herhangi bir değişken **null yapılamayan bir başvuru türü** olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="41890-234">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="41890-235">Bir değişkenin null olabileceğini belirtmek istiyorsanız, değişkeni null olabilen `?` bir **başvuru türü** olarak bildirmek için ile tür adını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="41890-235">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="41890-236">Null yapılamayan başvuru türleri için derleyici, yerel değişkenlerin bildirildiği sırada null olmayan bir değere başlatıldığından emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="41890-236">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="41890-237">Alanlar oluşturma sırasında başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41890-237">Fields must be initialized during construction.</span></span> <span data-ttu-id="41890-238">Derleyici, değişken kullanılabilir oluşturuculardan herhangi birine veya bir başlatıcı tarafından ayarlanmamışsa bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41890-238">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="41890-239">Ayrıca, null olamayan başvuru türlerine null olabilecek bir değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="41890-239">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="41890-240">Null yapılabilir başvuru türleri atanmamış veya null olarak başlatılmamış olduğundan emin olmak için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="41890-240">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="41890-241">Ancak, derleyici, null olabilen bir başvuru türü değişkeninin erişilebilir olması veya null yapılamayan bir başvuruya atanmadan önce null olarak denetlendiğinden emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="41890-241">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="41890-242">Özelliği hakkında daha fazla bilgiyi [null yapılabilir başvuru türlerine](../nullable-references.md)genel bakış bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41890-242">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="41890-243">Bu [null yapılabilir başvuru türleri öğreticisindeki](tutorials/nullable-reference-types.md)yeni bir uygulamada kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="41890-243">Try it yourself in a new application in this [nullable reference types tutorial](tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="41890-244">[Bir uygulamayı, null yapılabilir başvuru türlerini kullanmak için geçirme](tutorials/upgrade-to-nullable-references.md)bölümünde null yapılabilir başvuru türlerini kullanmak için mevcut bir kod temeli geçirme adımları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="41890-244">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="41890-245">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="41890-245">Asynchronous streams</span></span>

<span data-ttu-id="41890-246">C# 8,0 ' den başlayarak akışları zaman uyumsuz olarak oluşturup kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41890-246">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="41890-247">Zaman uyumsuz akış döndüren bir yöntem üç özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="41890-247">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="41890-248">`async`Değiştiriciyle birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41890-248">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="41890-249">Döndürür <xref:System.Collections.Generic.IAsyncEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="41890-249">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="41890-250">Yöntemi, `yield return` zaman uyumsuz akıştaki birbirini izleyen öğeleri döndürecek deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="41890-250">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="41890-251">Zaman uyumsuz bir akışın kullanılması, `await` `foreach` akışın öğelerini Numaralandırdığınızda anahtar kelimeden önce anahtar sözcüğünü eklemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="41890-251">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="41890-252">`await`Anahtar sözcüğü eklemek, zaman uyumsuz akışı belirten `async` ve değiştirici ile belirtilecek ve bir yöntem için izin verilen bir tür döndürecek yöntemi gerektirir `async` .</span><span class="sxs-lookup"><span data-stu-id="41890-252">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="41890-253">Genellikle, veya döndürme anlamına <xref:System.Threading.Tasks.Task> gelir <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="41890-253">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="41890-254">Ayrıca, <xref:System.Threading.Tasks.ValueTask> veya olabilir <xref:System.Threading.Tasks.ValueTask%601> .</span><span class="sxs-lookup"><span data-stu-id="41890-254">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="41890-255">Bir yöntem, zaman uyumsuz bir akış tüketebilir ve üretebilir, yani dönecektir <xref:System.Collections.Generic.IAsyncEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="41890-255">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="41890-256">Aşağıdaki kod, 0 ile 19 arasında bir sıra üretir, her bir sayı üretilmeden 100 ms bekler:</span><span class="sxs-lookup"><span data-stu-id="41890-256">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="41890-257">Şu ifadeyi kullanarak sırayı numaralandırabilirsiniz `await foreach` :</span><span class="sxs-lookup"><span data-stu-id="41890-257">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="41890-258">Zaman uyumsuz akışları [oluşturma ve](tutorials/generate-consume-asynchronous-stream.md)kullanma öğreticimizde, zaman uyumsuz akışları kendiniz deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41890-258">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](tutorials/generate-consume-asynchronous-stream.md).</span></span> <span data-ttu-id="41890-259">Akış öğeleri varsayılan olarak yakalanan bağlamda işlenir.</span><span class="sxs-lookup"><span data-stu-id="41890-259">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="41890-260">Bağlam yakalamayı devre dışı bırakmak istiyorsanız, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> genişletme yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="41890-260">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="41890-261">Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz model](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)kullanma başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="41890-261">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

## <a name="asynchronous-disposable"></a><span data-ttu-id="41890-262">Zaman uyumsuz atılabilir</span><span class="sxs-lookup"><span data-stu-id="41890-262">Asynchronous disposable</span></span>

<span data-ttu-id="41890-263">C# 8,0 ile başlayarak, dil arabirimi uygulayan zaman uyumsuz atılabilir türlerini destekler <xref:System.IAsyncDisposable?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="41890-263">Starting with C# 8.0, the language supports asynchronous disposable types that implement the <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="41890-264">`await using`Bir zaman uyumsuz atılabilir nesnesiyle çalışmak için ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="41890-264">You use the `await using` statement to work with an asynchronously disposable object.</span></span> <span data-ttu-id="41890-265">Daha fazla bilgi için, bkz. [DisposeAsync yöntemi uygulama](../../standard/garbage-collection/implementing-disposeasync.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="41890-265">For more information, see the [Implement a DisposeAsync method](../../standard/garbage-collection/implementing-disposeasync.md) article.</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="41890-266">Dizinler ve aralıklar</span><span class="sxs-lookup"><span data-stu-id="41890-266">Indices and ranges</span></span>

<span data-ttu-id="41890-267">Dizinler ve aralıklar bir dizideki tek öğelere veya aralıklara erişmek için bir kısa söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="41890-267">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="41890-268">Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:</span><span class="sxs-lookup"><span data-stu-id="41890-268">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="41890-269"><xref:System.Index?displayProperty=nameWithType> bir dizinin dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="41890-269"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="41890-270">`^`Bir dizinin sıranın sonuna göre olduğunu belirten End işlecinden dizin.</span><span class="sxs-lookup"><span data-stu-id="41890-270">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="41890-271"><xref:System.Range?displayProperty=nameWithType> bir dizinin alt aralığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="41890-271"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="41890-272">`..`Aralık işleci, bir aralığın işlenenlerinin başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="41890-272">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="41890-273">Dizin kurallarıyla başlayalım.</span><span class="sxs-lookup"><span data-stu-id="41890-273">Let's start with the rules for indexes.</span></span> <span data-ttu-id="41890-274">Bir dizi düşünün `sequence` .</span><span class="sxs-lookup"><span data-stu-id="41890-274">Consider an array `sequence`.</span></span> <span data-ttu-id="41890-275">`0`Dizin, ile aynıdır `sequence[0]` .</span><span class="sxs-lookup"><span data-stu-id="41890-275">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="41890-276">`^0`Dizin, ile aynıdır `sequence[sequence.Length]` .</span><span class="sxs-lookup"><span data-stu-id="41890-276">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="41890-277">Bunun `sequence[^0]` gibi bir özel durum oluşturur `sequence[sequence.Length]` .</span><span class="sxs-lookup"><span data-stu-id="41890-277">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="41890-278">Herhangi bir sayı için `n` Dizin `^n` aynı olur `sequence.Length - n` .</span><span class="sxs-lookup"><span data-stu-id="41890-278">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="41890-279">Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir.</span><span class="sxs-lookup"><span data-stu-id="41890-279">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="41890-280">Aralığın başlangıcı dahil, ancak aralığın sonu dışlamalı, ancak *Başlangıç* aralığa dahil değildir ancak *uç* aralığa dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="41890-280">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="41890-281">Aralık, tüm aralığı temsil eden `[0..^0]` tüm aralığı temsil eder `[0..sequence.Length]` .</span><span class="sxs-lookup"><span data-stu-id="41890-281">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="41890-282">Bazı örneklere bakalım.</span><span class="sxs-lookup"><span data-stu-id="41890-282">Let's look at a few examples.</span></span> <span data-ttu-id="41890-283">Başlangıç ve bitişten dizin ile açıklana ek olarak, aşağıdaki diziyi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="41890-283">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="41890-284">Son sözcüğü şu `^1` dizine alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41890-284">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="41890-285">Aşağıdaki kod, "hızlı", "kahverengi" ve "Fox" sözcüklerinin bulunduğu bir alt Aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41890-285">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="41890-286">İle içerir `words[1]` `words[3]` .</span><span class="sxs-lookup"><span data-stu-id="41890-286">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="41890-287">Öğe `words[4]` Aralık içinde değil.</span><span class="sxs-lookup"><span data-stu-id="41890-287">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="41890-288">Aşağıdaki kod, "Lazy" ve "köpek" ile bir alt Aralık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41890-288">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="41890-289">Ve içerir `words[^2]` `words[^1]` .</span><span class="sxs-lookup"><span data-stu-id="41890-289">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="41890-290">Son dizin `words[^0]` dahil değildir:</span><span class="sxs-lookup"><span data-stu-id="41890-290">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="41890-291">Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="41890-291">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="41890-292">Aralıkları, değişkenler olarak da bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41890-292">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="41890-293">Aralık daha sonra `[` ve karakterleri içinde kullanılabilir `]` :</span><span class="sxs-lookup"><span data-stu-id="41890-293">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="41890-294">Yalnızca dizin ve aralıkları destekleyen diziler değil.</span><span class="sxs-lookup"><span data-stu-id="41890-294">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="41890-295">Ayrıca, veya [dizesiyle](../language-reference/builtin-types/reference-types.md#the-string-type)dizin ve aralıklar da kullanabilirsiniz <xref:System.Span%601> <xref:System.ReadOnlySpan%601> .</span><span class="sxs-lookup"><span data-stu-id="41890-295">You can also use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="41890-296">Daha fazla bilgi için bkz. [Dizinler ve aralıklar için destek türü](tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="41890-296">For more information, see [Type support for indices and ranges](tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="41890-297">Dizinler ve [aralıklar](tutorials/ranges-indexes.md)hakkında öğreticide dizinler ve aralıklar hakkında daha fazla bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41890-297">You can explore more about indices and ranges in the tutorial on [indices and ranges](tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="41890-298">Null birleştirme ataması</span><span class="sxs-lookup"><span data-stu-id="41890-298">Null-coalescing assignment</span></span>

<span data-ttu-id="41890-299">C# 8,0, null birleşim atama işlecini tanıtır `??=` .</span><span class="sxs-lookup"><span data-stu-id="41890-299">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="41890-300">Sağ işleneninin değerini, sol taraftaki işlenenin `??=` değerini yalnızca sol taraftaki işlenen olarak değerlendirdiğinde atamak için işlecini kullanabilirsiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="41890-300">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="41890-301">Daha fazla bilgi için?? [ve?? = operatörler](../language-reference/operators/null-coalescing-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="41890-301">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="41890-302">Yönetilmeyen oluşturulmuş türler</span><span class="sxs-lookup"><span data-stu-id="41890-302">Unmanaged constructed types</span></span>

<span data-ttu-id="41890-303">C# 7,3 ve önceki sürümlerde, oluşturulmuş bir tür (en az bir tür bağımsız değişkeni içeren bir tür) [yönetilmeyen bir tür](../language-reference/builtin-types/unmanaged-types.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="41890-303">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="41890-304">C# 8,0 ' den başlayarak, oluşturulmuş bir değer türü yalnızca yönetilmeyen türlerin alanlarını içeriyorsa yönetilmez.</span><span class="sxs-lookup"><span data-stu-id="41890-304">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="41890-305">Örneğin, genel türün aşağıdaki tanımı verildiğinde `Coords<T>` :</span><span class="sxs-lookup"><span data-stu-id="41890-305">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="41890-306">`Coords<int>`tür, C# 8,0 ve sonraki sürümlerde yönetilmeyen bir türdür.</span><span class="sxs-lookup"><span data-stu-id="41890-306">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="41890-307">Herhangi bir yönetilmeyen tür için olduğu gibi, bu türden bir değişkene bir işaretçi oluşturabilir veya bu türün örnekleri için [yığında bir bellek bloğu ayırabilirsiniz](../language-reference/operators/stackalloc.md) :</span><span class="sxs-lookup"><span data-stu-id="41890-307">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="41890-308">Daha fazla bilgi için bkz. [yönetilmeyen türler](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="41890-308">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="41890-309">İç içe ifadelerde stackalloc</span><span class="sxs-lookup"><span data-stu-id="41890-309">Stackalloc in nested expressions</span></span>

<span data-ttu-id="41890-310">C# 8,0 ' den itibaren, bir [stackalloc](../language-reference/operators/stackalloc.md) ifadesinin sonucu <xref:System.Span%601?displayProperty=nameWithType> veya <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> türü ise, `stackalloc` ifadeyi diğer ifadelerde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41890-310">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6, 8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="41890-311">Ara değerli tam dizelerin geliştirilmesi</span><span class="sxs-lookup"><span data-stu-id="41890-311">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="41890-312">Birlikte bulunan tam `$` `@` dizelerde ve belirteçlerin sırası herhangi biri olabilir: her ikisi de geçerli bir ara tür [](../language-reference/tokens/interpolated.md) `$@"..."` `@$"..."` dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="41890-312">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="41890-313">Önceki C# sürümlerinde, `$` belirtecin belirtecin önüne gösterilmesi gerekir `@` .</span><span class="sxs-lookup"><span data-stu-id="41890-313">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
