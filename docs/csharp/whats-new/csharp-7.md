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
# <a name="whats-new-in-c-70-through-c-73"></a><span data-ttu-id="50017-103">C# 7,3 ile c# 7,0 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="50017-103">What's new in C# 7.0 through C# 7.3</span></span>

<span data-ttu-id="50017-104">C# 7,0 7,3 ile c# arasında bir dizi özellik ve geliştirme deneyiminize yönelik artımlı iyileştirmeler c# ile getirildi.</span><span class="sxs-lookup"><span data-stu-id="50017-104">C# 7.0 through C# 7.3 brought a number of features and incremental improvements to your development experience with C#.</span></span> <span data-ttu-id="50017-105">Bu makalede, yeni dil özelliklerine ve derleyici seçeneklerine bir genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="50017-105">This article provides an overview of the new language features and compiler options.</span></span> <span data-ttu-id="50017-106">Açıklamalar, .NET Framework tabanlı uygulamalar için desteklenen en son sürüm olan C# 7,3 davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="50017-106">The descriptions describe the behavior for C# 7.3, which is the most recent version supported for .NET Framework-based applications.</span></span>

<span data-ttu-id="50017-107">[Dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesi C# 7,1 ile eklenmiştir ve bu, proje dosyanızda derleyici dili sürümünü belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="50017-107">The [language version selection](../language-reference/configure-language-version.md) configuration element was added with C# 7.1, which enables you to specify the compiler language version in your project file.</span></span>

<span data-ttu-id="50017-108">C# 7.0-7.3 Bu özellikleri ve temaları C# diline ekler:</span><span class="sxs-lookup"><span data-stu-id="50017-108">C# 7.0-7.3 adds these features and themes to the C# language:</span></span>

- [<span data-ttu-id="50017-109">Tanımlama grupları ve atma</span><span class="sxs-lookup"><span data-stu-id="50017-109">Tuples and discards</span></span>](#tuples-and-discards)
  - <span data-ttu-id="50017-110">Birden çok ortak alan içeren hafif, adlandırılmamış türler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-110">You can create lightweight, unnamed types that contain multiple public fields.</span></span> <span data-ttu-id="50017-111">Derleyiciler ve IDE araçları bu türlerin semantiğini anlayın.</span><span class="sxs-lookup"><span data-stu-id="50017-111">Compilers and IDE tools understand the semantics of these types.</span></span>
  - <span data-ttu-id="50017-112">Atama, atanan değer hakkında endişelenmezseniz atamalar içinde kullanılan geçici, salt yazılır değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="50017-112">Discards are temporary, write-only variables used in assignments when you don't care about the value assigned.</span></span> <span data-ttu-id="50017-113">Bunlar, tanımlama grupları ve Kullanıcı tanımlı türler oluştururken ve parametreleri ile Yöntemler çağrılırken faydalıdır `out` .</span><span class="sxs-lookup"><span data-stu-id="50017-113">They're most useful when deconstructing tuples and user-defined types, as well as when calling methods with `out` parameters.</span></span>
- [<span data-ttu-id="50017-114">Model eşleştirme</span><span class="sxs-lookup"><span data-stu-id="50017-114">Pattern Matching</span></span>](#pattern-matching)
  - <span data-ttu-id="50017-115">Bu türlerin üyelerinin rastgele türlerini ve değerlerini temel alarak dallanma mantığı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-115">You can create branching logic based on arbitrary types and values of the members of those types.</span></span>
- [<span data-ttu-id="50017-116">`async``Main`yöntemi</span><span class="sxs-lookup"><span data-stu-id="50017-116">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="50017-117">Bir uygulama için giriş noktası değiştiriciye sahip olabilir `async` .</span><span class="sxs-lookup"><span data-stu-id="50017-117">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="50017-118">Yerel Işlevler</span><span class="sxs-lookup"><span data-stu-id="50017-118">Local Functions</span></span>](#local-functions)
  - <span data-ttu-id="50017-119">Kendi kapsamını ve görünürlüğünü sınırlamak için işlevleri diğer işlevlerde iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-119">You can nest functions inside other functions to limit their scope and visibility.</span></span>
- [<span data-ttu-id="50017-120">Daha fazla ifade-Bodied Üyeler</span><span class="sxs-lookup"><span data-stu-id="50017-120">More expression-bodied members</span></span>](#more-expression-bodied-members)
  - <span data-ttu-id="50017-121">İfadeler kullanılarak yazılabilir üyelerin listesi artmıştır.</span><span class="sxs-lookup"><span data-stu-id="50017-121">The list of members that can be authored using expressions has grown.</span></span>
- [<span data-ttu-id="50017-122">`throw` İfadelerde</span><span class="sxs-lookup"><span data-stu-id="50017-122">`throw` Expressions</span></span>](#throw-expressions)
  - <span data-ttu-id="50017-123">Daha önce izin verilmeyen kod yapılarında özel durumlar oluşturabilir, çünkü `throw` bir deyimidir.</span><span class="sxs-lookup"><span data-stu-id="50017-123">You can throw exceptions in code constructs that previously weren't allowed because `throw` was a statement.</span></span>
- [<span data-ttu-id="50017-124">`default` değişmez değer ifadeleri</span><span class="sxs-lookup"><span data-stu-id="50017-124">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="50017-125">Hedef türü çıkarsanamıyor varsayılan değer ifadelerinde varsayılan değişmez ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-125">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="50017-126">Sayısal sabit değer sözdizimi geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="50017-126">Numeric literal syntax improvements</span></span>](#numeric-literal-syntax-improvements)
  - <span data-ttu-id="50017-127">Yeni belirteçler Sayısal sabitler için okunabilirliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="50017-127">New tokens improve readability for numeric constants.</span></span>
- [<span data-ttu-id="50017-128">`out` değişkenlerinin</span><span class="sxs-lookup"><span data-stu-id="50017-128">`out` variables</span></span>](#out-variables)
  - <span data-ttu-id="50017-129">`out`Değerleri, kullanıldığı yönteme bağımsız değişken olarak satır içi olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-129">You can declare `out` values inline as arguments to the method where they're used.</span></span>
- [<span data-ttu-id="50017-130">Girintili olmayan adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="50017-130">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="50017-131">Adlandırılmış bağımsız değişkenlerin ardından konumsal bağımsız değişkenler gelebilir.</span><span class="sxs-lookup"><span data-stu-id="50017-131">Named arguments can be followed by positional arguments.</span></span>
- [<span data-ttu-id="50017-132">`private protected` erişim değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="50017-132">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="50017-133">`private protected`Erişim değiştiricisi aynı derlemede türetilmiş sınıflar için erişim imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="50017-133">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>
- [<span data-ttu-id="50017-134">Geliştirilmiş aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="50017-134">Improved overload resolution</span></span>](#improved-overload-candidates)
  - <span data-ttu-id="50017-135">Aşırı yükleme çözümleme belirsizliğe çözüm için yeni kurallar.</span><span class="sxs-lookup"><span data-stu-id="50017-135">New rules to resolve overload resolution ambiguity.</span></span>
- [<span data-ttu-id="50017-136">Güvenli verimli kod yazma teknikleri</span><span class="sxs-lookup"><span data-stu-id="50017-136">Techniques for writing safe efficient code</span></span>](#enabling-more-efficient-safe-code)
  - <span data-ttu-id="50017-137">Başvuru semantiğinin kullanıldığı değer türleriyle çalışmayı sağlayan sözdizimi geliştirmelerinden oluşan bir bileşim.</span><span class="sxs-lookup"><span data-stu-id="50017-137">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>

<span data-ttu-id="50017-138">Son olarak, derleyici yeni seçeneklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="50017-138">Finally, the compiler has new options:</span></span>

- <span data-ttu-id="50017-139">`-refout` ve `-refonly` Bu denetim [Başvuru derleme oluşturma](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="50017-139">`-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>
- <span data-ttu-id="50017-140">`-publicsign` Açık kaynak yazılım (OSS) derlemelerinin imzalanmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="50017-140">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="50017-141">`-pathmap` Kaynak dizinlere eşleme sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="50017-141">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="50017-142">Bu makalenin geri kalanında her özelliğe bir genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="50017-142">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="50017-143">Her özellik için, arkasındaki ve söz dizimi hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-143">For each feature, you'll learn the reasoning behind it and the syntax.</span></span> <span data-ttu-id="50017-144">Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz `dotnet try` :</span><span class="sxs-lookup"><span data-stu-id="50017-144">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="50017-145">[DotNet-TRY](https://github.com/dotnet/try/blob/main/DotNetTryLocal.md) küresel aracını yükler.</span><span class="sxs-lookup"><span data-stu-id="50017-145">Install the [dotnet-try](https://github.com/dotnet/try/blob/main/DotNetTryLocal.md) global tool.</span></span>
1. <span data-ttu-id="50017-146">[DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="50017-146">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="50017-147">*TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="50017-147">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="50017-148">`dotnet try` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="50017-148">Run `dotnet try`.</span></span>

## <a name="tuples-and-discards"></a><span data-ttu-id="50017-149">Tanımlama grupları ve atma</span><span class="sxs-lookup"><span data-stu-id="50017-149">Tuples and discards</span></span>

<span data-ttu-id="50017-150">C#, tasarım amacını açıklamak için kullanılan sınıflar ve yapılar için zengin bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="50017-150">C# provides a rich syntax for classes and structs that is used to explain your design intent.</span></span> <span data-ttu-id="50017-151">Ancak bazen zengin söz dizimi çok az avantajlı ek iş gerektirir.</span><span class="sxs-lookup"><span data-stu-id="50017-151">But sometimes that rich syntax requires extra work with minimal benefit.</span></span> <span data-ttu-id="50017-152">Genellikle birden fazla veri öğesi içeren basit bir yapıya ihtiyacı olan Yöntemler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-152">You may often write methods that need a simple structure containing more than one data element.</span></span> <span data-ttu-id="50017-153">Bu *senaryoları desteklemek* için C# ' ye eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="50017-153">To support these scenarios *tuples* were added to C#.</span></span> <span data-ttu-id="50017-154">Tanımlama grupları, veri üyelerini temsil etmek için birden çok alan içeren hafif veri yapılarıdır.</span><span class="sxs-lookup"><span data-stu-id="50017-154">Tuples are lightweight data structures that contain multiple fields to represent the data members.</span></span> <span data-ttu-id="50017-155">Alanlar doğrulanmaz ve kendi yöntemlerinizi tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="50017-155">The fields aren't validated, and you can't define your own methods.</span></span> <span data-ttu-id="50017-156">C# demet türleri destekler `==` `!=` .</span><span class="sxs-lookup"><span data-stu-id="50017-156">C# tuple types support `==` and `!=`.</span></span> <span data-ttu-id="50017-157">Daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="50017-157">For more information.</span></span>

> [!NOTE]
> <span data-ttu-id="50017-158">Tanımlama grupları C# 7,0 ' den önce kullanılabilir, ancak verimsiz ve dil desteği yoktu.</span><span class="sxs-lookup"><span data-stu-id="50017-158">Tuples were available before C# 7.0, but they were inefficient and had no language support.</span></span> <span data-ttu-id="50017-159">Bu, demet öğelerine yalnızca olarak başvurulabilir `Item1` , `Item2` vb. anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="50017-159">This meant that tuple elements could only be referenced as `Item1`, `Item2` and so on.</span></span> <span data-ttu-id="50017-160">C# 7,0, tanımlama grupları için dil desteğini tanıtır ve bu, yeni, daha verimli demet türleri kullanarak bir kayıt düzeni alanları için anlamsal adlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="50017-160">C# 7.0 introduces language support for tuples, which enables semantic names for the fields of a tuple using new, more efficient tuple types.</span></span>

<span data-ttu-id="50017-161">Her üyeye bir değer atayarak ve isteğe bağlı olarak tanımlama grubu üyelerinin her birine anlamsal adlar sağlayarak bir tanımlama grubu oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50017-161">You can create a tuple by assigning a value to each member, and optionally providing semantic names to each of the members of the tuple:</span></span>

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

<span data-ttu-id="50017-162">`namedLetters`Kayıt düzeni ve olarak adlandırılan alanları içerir `Alpha` `Beta` .</span><span class="sxs-lookup"><span data-stu-id="50017-162">The `namedLetters` tuple contains fields referred to as `Alpha` and `Beta`.</span></span> <span data-ttu-id="50017-163">Bu adlar yalnızca derleme sırasında bulunur ve korunmaz, örneğin, çalışma zamanında yansıma kullanarak tanımlama grubu incelenirken.</span><span class="sxs-lookup"><span data-stu-id="50017-163">Those names exist only at compile time and aren't preserved, for example when inspecting the tuple using reflection at run time.</span></span>

<span data-ttu-id="50017-164">Tanımlama grubu atamasında, atamanın sağ tarafındaki alanların adlarını da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50017-164">In a tuple assignment, you can also specify the names of the fields on the right-hand side of the assignment:</span></span>

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

<span data-ttu-id="50017-165">Bir yöntemden döndürülen bir tanımlama grubunun üyelerinin paketini kaldırmak istediğiniz zamanlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-165">There may be times when you want to unpackage the members of a tuple that were returned from a method.</span></span>  <span data-ttu-id="50017-166">Bu, kayıt grubundaki her bir değer için ayrı değişkenler bildirerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-166">You can do that by declaring separate variables for each of the values in the tuple.</span></span> <span data-ttu-id="50017-167">Bu paketten *çıkarılması* , kayıt düzeninin kaldırılması olarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="50017-167">This unpackaging is called *deconstructing* the tuple:</span></span>

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

<span data-ttu-id="50017-168">Ayrıca, .NET 'teki herhangi bir tür için benzer bir deme sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-168">You can also provide a similar deconstruction for any type in .NET.</span></span> <span data-ttu-id="50017-169">Bir `Deconstruct` yöntemi sınıfının bir üyesi olarak yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="50017-169">You write a `Deconstruct` method as a member of the class.</span></span> <span data-ttu-id="50017-170">Bu `Deconstruct` Yöntem `out` , ayıklamak istediğiniz her bir özellik için bir dizi bağımsız değişken sağlar.</span><span class="sxs-lookup"><span data-stu-id="50017-170">That `Deconstruct` method provides a set of `out` arguments for each of the properties you want to extract.</span></span> <span data-ttu-id="50017-171">`Point`Ve koordinatlarını çıkaran bir Deconstructor yöntemi sağlayan bu sınıfı göz önünde `X` bulundurun `Y` :</span><span class="sxs-lookup"><span data-stu-id="50017-171">Consider this `Point` class that provides a deconstructor method that extracts the `X` and `Y` coordinates:</span></span>

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

<span data-ttu-id="50017-172">Bir tanımlama grubu 'na atayarak tek tek alanları ayıklayabilirsiniz `Point` :</span><span class="sxs-lookup"><span data-stu-id="50017-172">You can extract the individual fields by assigning a `Point` to a tuple:</span></span>

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

<span data-ttu-id="50017-173">Bir tanımlama grubu başlattığınızda, atamanın sağ tarafında kullanılan değişkenler demet öğeleri için istediğiniz adlarla aynı olur: demet öğelerinin adları, kayıt kümesini başlatmak için kullanılan değişkenlerden çıkarsanamıyor:</span><span class="sxs-lookup"><span data-stu-id="50017-173">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements: The names of tuple elements can be inferred from the variables used to initialize the tuple:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="50017-174">[Demet türleri](../language-reference/builtin-types/value-tuples.md) makalesinde bu özellik hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-174">You can learn more about this feature in the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

<span data-ttu-id="50017-175">Genellikle, bir tanımlama grubu oluştururken veya parametreler ile bir yöntemi çağırırken `out` , değeri ilgilenmediğiniz ve kullanmayı planlamadığınız bir değişken tanımlamaya zorlanır.</span><span class="sxs-lookup"><span data-stu-id="50017-175">Often when deconstructing a tuple or calling a method with `out` parameters, you're forced to define a variable whose value you don't care about and don't intend to use.</span></span> <span data-ttu-id="50017-176">C#, bu senaryoyu işlemek için *atma* desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="50017-176">C# adds support for *discards* to handle this scenario.</span></span> <span data-ttu-id="50017-177">Bir atma, adı `_` (alt çizgi karakteri) olan salt yazılır bir değişkendir; atmayı planladığınız tüm değerleri tek bir değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-177">A discard is a write-only variable whose name is `_` (the underscore character); you can assign all of the values that you intend to discard to the single variable.</span></span> <span data-ttu-id="50017-178">Bir atma atanmamış değişken gibidir; atama ifadesinden ayrı olarak, atma kodda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="50017-178">A discard is like an unassigned variable; apart from the assignment statement, the discard can't be used in code.</span></span>

<span data-ttu-id="50017-179">Atma, aşağıdaki senaryolarda desteklenir:</span><span class="sxs-lookup"><span data-stu-id="50017-179">Discards are supported in the following scenarios:</span></span>

- <span data-ttu-id="50017-180">Tanımlama grupları veya Kullanıcı tanımlı türler kaldırılıyor.</span><span class="sxs-lookup"><span data-stu-id="50017-180">When deconstructing tuples or user-defined types.</span></span>
- <span data-ttu-id="50017-181">[Out](../language-reference/keywords/out-parameter-modifier.md) parametreleri ile Yöntemler çağrılırken.</span><span class="sxs-lookup"><span data-stu-id="50017-181">When calling methods with [out](../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>
- <span data-ttu-id="50017-182">WITH ve [Switch](../language-reference/keywords/switch.md) deyimleriyle bir kalıp [](../language-reference/keywords/is.md) eşleştirme işleminde.</span><span class="sxs-lookup"><span data-stu-id="50017-182">In a pattern matching operation with the [is](../language-reference/keywords/is.md) and [switch](../language-reference/keywords/switch.md) statements.</span></span>
- <span data-ttu-id="50017-183">Bir atamanın değerini bir atma olarak açıkça tanımlamak istediğinizde tek başına tanımlayıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="50017-183">As a standalone identifier when you want to explicitly identify the value of an assignment as a discard.</span></span>

<span data-ttu-id="50017-184">Aşağıdaki örnek, `QueryCityDataForYears` iki farklı yıl için şehir için veri içeren 6 demet döndüren bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="50017-184">The following example defines a `QueryCityDataForYears` method that returns a 6-tuple that contains data for a city for two different years.</span></span> <span data-ttu-id="50017-185">Örnekteki yöntem çağrısı yalnızca yöntemi tarafından döndürülen iki popülasyon değeriyle ilgilidir ve bu nedenle, kayıt düzeni oluşturulduğunda, kayıt düzeninde kalan değerleri atma olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="50017-185">The method call in the example is concerned only with the two population values returned by the method and so treats the remaining values in the tuple as discards when it deconstructs the tuple.</span></span>

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="50017-186">Daha fazla bilgi için bkz. [atma](../discards.md).</span><span class="sxs-lookup"><span data-stu-id="50017-186">For more information, see [Discards](../discards.md).</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="50017-187">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="50017-187">Pattern matching</span></span>

<span data-ttu-id="50017-188">*Model eşleştirme* , kodunuzda hızlı denetim akışını sağlayan yeni yollar sağlayan bir özellikler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="50017-188">*Pattern matching* is a set of features that enable new ways to express control flow in your code.</span></span> <span data-ttu-id="50017-189">Değişkenlerini türlerine, değerlerine veya özelliklerinin değerlerine göre test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-189">You can test variables for their type, values or the values of their properties.</span></span> <span data-ttu-id="50017-190">Bu teknikler daha okunabilir kod akışı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50017-190">These techniques create more readable code flow.</span></span>

<span data-ttu-id="50017-191">Model eşleştirme `is` , ifadeleri ve `switch` ifadeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="50017-191">Pattern matching supports `is` expressions and `switch` expressions.</span></span> <span data-ttu-id="50017-192">Her biri, nesnenin aranan düzene karşılayıp karşılamadığını tespit etmek için bir nesne ve özelliklerini inceleyerek sağlar.</span><span class="sxs-lookup"><span data-stu-id="50017-192">Each enables inspecting an object and its properties to determine if that object satisfies the sought pattern.</span></span> <span data-ttu-id="50017-193">`when`Modele ek kurallar belirtmek için anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="50017-193">You use the `when` keyword to specify additional rules to the pattern.</span></span>

<span data-ttu-id="50017-194">`is`Model ifadesi, bir nesneyi türü hakkında sorgulamak ve sonucu bir yönergede atamak için tanıdık [ `is` işleci](../language-reference/keywords/is.md#pattern-matching-with-is) genişletir.</span><span class="sxs-lookup"><span data-stu-id="50017-194">The `is` pattern expression extends the familiar [`is` operator](../language-reference/keywords/is.md#pattern-matching-with-is) to query an object about its type and assign the result in one instruction.</span></span> <span data-ttu-id="50017-195">Aşağıdaki kod, bir değişkenin bir olduğunu denetler `int` ve varsa, geçerli Sum 'a ekler:</span><span class="sxs-lookup"><span data-stu-id="50017-195">The following code checks if a variable is an `int`, and if so, adds it to the current sum:</span></span>

```csharp
if (input is int count)
    sum += count;
```

<span data-ttu-id="50017-196">Önceki küçük örnek, ifadeye yönelik geliştirmeleri gösterir `is` .</span><span class="sxs-lookup"><span data-stu-id="50017-196">The preceding small example demonstrates the enhancements to the `is` expression.</span></span> <span data-ttu-id="50017-197">Aynı zamanda değer türlerine ve başvuru türlerine karşı test edebilirsiniz ve başarılı sonucu doğru türdeki yeni bir değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-197">You can test against value types as well as reference types, and you can assign the successful result to a new variable of the correct type.</span></span>

<span data-ttu-id="50017-198">Anahtar eşleşme ifadesi, `switch` C# dilinin zaten bir parçası olan bildirime göre tanıdık bir sözdizimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="50017-198">The switch match expression has a familiar syntax, based on the `switch` statement already part of the C# language.</span></span> <span data-ttu-id="50017-199">Güncelleştirilmiş switch ifadesinin çeşitli yeni yapıları vardır:</span><span class="sxs-lookup"><span data-stu-id="50017-199">The updated switch statement has several new constructs:</span></span>

- <span data-ttu-id="50017-200">Bir ifadenin yöneten türü `switch` artık, `Enum` `string` Bu türlerden birine karşılık gelen tamsayı türleri, türleri veya null olabilen bir türle sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="50017-200">The governing type of a `switch` expression is no longer restricted to integral types, `Enum` types, `string`, or a nullable type corresponding to one of those types.</span></span> <span data-ttu-id="50017-201">Herhangi bir tür kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-201">Any type may be used.</span></span>
- <span data-ttu-id="50017-202">`switch`Her etikette ifadenin türünü test edebilirsiniz `case` .</span><span class="sxs-lookup"><span data-stu-id="50017-202">You can test the type of the `switch` expression in each `case` label.</span></span> <span data-ttu-id="50017-203">İfadesinde olduğu gibi `is` , bu türe yeni bir değişken atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-203">As with the `is` expression, you may assign a new variable to that type.</span></span>
- <span data-ttu-id="50017-204">`when`O değişkende daha fazla test koşullarına bir yan tümce ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-204">You may add a `when` clause to further test conditions on that variable.</span></span>
- <span data-ttu-id="50017-205">`case`Etiketlerin sırası artık önemlidir.</span><span class="sxs-lookup"><span data-stu-id="50017-205">The order of `case` labels is now important.</span></span> <span data-ttu-id="50017-206">Eşleştirilecek ilk dal yürütülür; diğerleri atlanır.</span><span class="sxs-lookup"><span data-stu-id="50017-206">The first branch to match is executed; others are skipped.</span></span>

<span data-ttu-id="50017-207">Aşağıdaki kod bu yeni özellikleri göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="50017-207">The following code demonstrates these new features:</span></span>

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

- <span data-ttu-id="50017-208">`case 0:` sabit bir [örüntü](../language-reference/operators/patterns.md#constant-pattern).</span><span class="sxs-lookup"><span data-stu-id="50017-208">`case 0:` is a [constant pattern](../language-reference/operators/patterns.md#constant-pattern).</span></span>
- <span data-ttu-id="50017-209">`case IEnumerable<int> childSequence:` bir [bildirim deseninin](../language-reference/operators/patterns.md#declaration-and-type-patterns).</span><span class="sxs-lookup"><span data-stu-id="50017-209">`case IEnumerable<int> childSequence:` is a [declaration pattern](../language-reference/operators/patterns.md#declaration-and-type-patterns).</span></span>
- <span data-ttu-id="50017-210">`case int n when n > 0:` , ek bir koşula sahip bir bildirim modelidir `when` .</span><span class="sxs-lookup"><span data-stu-id="50017-210">`case int n when n > 0:` is a declaration pattern with an additional `when` condition.</span></span>
- <span data-ttu-id="50017-211">`case null:` sabit bir modeldir `null` .</span><span class="sxs-lookup"><span data-stu-id="50017-211">`case null:` is the `null` constant pattern.</span></span>
- <span data-ttu-id="50017-212">`default:` tanıdık varsayılan durumdur.</span><span class="sxs-lookup"><span data-stu-id="50017-212">`default:` is the familiar default case.</span></span>

<span data-ttu-id="50017-213">C# 7,1 ile başlayarak, `is` ve `switch` tür deseninin model ifadesi bir genel tür parametresinin türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-213">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="50017-214">Bu, ya da türünde olabilecek türler denetlenirken `struct` `class` ve kutulamayı önlemek istediğiniz durumlarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-214">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

<span data-ttu-id="50017-215">[C# ' de model eşleştirme](../pattern-matching.md)ile model eşleştirme hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-215">You can learn more about pattern matching in [Pattern Matching in C#](../pattern-matching.md).</span></span>

## <a name="async-main"></a><span data-ttu-id="50017-216">Zaman uyumsuz ana</span><span class="sxs-lookup"><span data-stu-id="50017-216">Async main</span></span>

<span data-ttu-id="50017-217">*Zaman uyumsuz Main* yöntemi, `await` yöntekinizdeki kullanmanıza olanak sağlar `Main` .</span><span class="sxs-lookup"><span data-stu-id="50017-217">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="50017-218">Daha önce yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="50017-218">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="50017-219">Artık şunu yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50017-219">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="50017-220">Programınız çıkış kodu döndürmezse, şunu `Main` döndüren bir yöntem bildirebilirsiniz <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="50017-220">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="50017-221">Programlama kılavuzundaki [zaman uyumsuz ana](../programming-guide/main-and-command-args/index.md) makaledeki ayrıntılar hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-221">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="local-functions"></a><span data-ttu-id="50017-222">Yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="50017-222">Local functions</span></span>

<span data-ttu-id="50017-223">Sınıfların pek çok tasarımı yalnızca bir konumdan çağrılan yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="50017-223">Many designs for classes include methods that are called from only one location.</span></span> <span data-ttu-id="50017-224">Bu ek özel yöntemler her bir yöntemi küçük ve odaklanmış olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="50017-224">These additional private methods keep each method small and focused.</span></span> <span data-ttu-id="50017-225">*Yerel işlevler* , yöntemleri başka bir yöntem bağlamı içinde bildirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="50017-225">*Local functions* enable you to declare methods inside the context of another method.</span></span> <span data-ttu-id="50017-226">Yerel işlevler, sınıfının okuyucularının, yerel yöntemin yalnızca bildirildiği bağlamdan çağrıldığını görmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="50017-226">Local functions make it easier for readers of the class to see that the local method is only called from the context in which it is declared.</span></span>

<span data-ttu-id="50017-227">Yerel işlevler için iki yaygın kullanım durumu vardır: genel Yineleyici yöntemleri ve genel zaman uyumsuz yöntemler.</span><span class="sxs-lookup"><span data-stu-id="50017-227">There are two common use cases for local functions: public iterator methods and public async methods.</span></span> <span data-ttu-id="50017-228">Her iki yöntem türü, programcılar tarafından daha sonra oluşabilecek hataları raporlayan kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50017-228">Both types of methods generate code that reports errors later than programmers might expect.</span></span> <span data-ttu-id="50017-229">Yineleyici metotlarda, tüm özel durumlar yalnızca döndürülen sırayı belirten kod çağrılırken izlenir.</span><span class="sxs-lookup"><span data-stu-id="50017-229">In iterator methods, any exceptions are observed only when calling code that enumerates the returned sequence.</span></span> <span data-ttu-id="50017-230">Zaman uyumsuz metotlarda, tüm özel durumlar yalnızca döndürülen geri beklendiğinde gözlemlenir `Task` .</span><span class="sxs-lookup"><span data-stu-id="50017-230">In async methods, any exceptions are only observed when the returned `Task` is awaited.</span></span> <span data-ttu-id="50017-231">Aşağıdaki örnek, yerel bir işlev kullanarak Yineleyici uygulamasından parametre doğrulamayı ayırmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="50017-231">The following example demonstrates separating parameter validation from the iterator implementation using a local function:</span></span>

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

<span data-ttu-id="50017-232">`async`Bağımsız değişken doğrulamasından doğan özel durumların, zaman uyumsuz iş başlamadan önce oluşturulması için yöntemler ile aynı yöntem kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="50017-232">The same technique can be employed with `async` methods to ensure that exceptions arising from argument validation are thrown before the asynchronous work begins:</span></span>

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

<span data-ttu-id="50017-233">Bu sözdizimi artık desteklenmektedir:</span><span class="sxs-lookup"><span data-stu-id="50017-233">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="50017-234">Özniteliği, `SomeThingAboutFieldAttribute` için derleyicinin oluşturduğu yedekleme alanına uygulanır `SomeProperty` .</span><span class="sxs-lookup"><span data-stu-id="50017-234">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="50017-235">Daha fazla bilgi için bkz. C# programlama kılavuzundaki [öznitelikler](../programming-guide/concepts/attributes/index.md) .</span><span class="sxs-lookup"><span data-stu-id="50017-235">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

> [!NOTE]
> <span data-ttu-id="50017-236">Yerel işlevler tarafından desteklenen tasarımlardan bazıları *lambda ifadeleri* kullanılarak da gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="50017-236">Some of the designs that are supported by local functions can also be accomplished using *lambda expressions*.</span></span> <span data-ttu-id="50017-237">Daha fazla bilgi için bkz [. yerel işlevler ve lambda ifadeleri](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).</span><span class="sxs-lookup"><span data-stu-id="50017-237">For more information, see [Local functions vs. lambda expressions](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).</span></span>

## <a name="more-expression-bodied-members"></a><span data-ttu-id="50017-238">Daha fazla ifade-Bodied Üyeler</span><span class="sxs-lookup"><span data-stu-id="50017-238">More expression-bodied members</span></span>

<span data-ttu-id="50017-239">C# 6 ifadesi-üye işlevleri ve salt okunurdur özellikler için Bodied eklenen üyeler.</span><span class="sxs-lookup"><span data-stu-id="50017-239">C# 6 introduced expression-bodied members for member functions and read-only properties.</span></span> <span data-ttu-id="50017-240">C# 7,0, ifade olarak uygulanabilecek izin verilen üyeleri genişletir.</span><span class="sxs-lookup"><span data-stu-id="50017-240">C# 7.0 expands the allowed members that can be implemented as expressions.</span></span> <span data-ttu-id="50017-241">C# 7,0 ' de,   `get` `set` *Özellikler* ve *Dizin oluşturucular* üzerinde oluşturucular, sonlandırıcılar ve erişimciler uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-241">In C# 7.0, you can implement *constructors*, *finalizers*, and `get` and `set` accessors on *properties* and *indexers*.</span></span> <span data-ttu-id="50017-242">Aşağıdaki kod, her birinin örneklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="50017-242">The following code shows examples of each:</span></span>

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> <span data-ttu-id="50017-243">Bu örnekte sonlandırıcısı gerekmez, ancak söz dizimini göstermek için gösterilir.</span><span class="sxs-lookup"><span data-stu-id="50017-243">This example does not need a finalizer, but it is shown to demonstrate the syntax.</span></span> <span data-ttu-id="50017-244">Yönetilmeyen kaynakları serbest bırakmak gerekmedikçe, sınıfınıza sonlandırıcıyı uygulamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="50017-244">You should not implement a finalizer in your class unless it is necessary to  release unmanaged resources.</span></span> <span data-ttu-id="50017-245">Ayrıca, <xref:System.Runtime.InteropServices.SafeHandle> yönetilmeyen kaynakları doğrudan yönetmek yerine sınıfını kullanmayı göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="50017-245">You should also consider using the <xref:System.Runtime.InteropServices.SafeHandle> class instead of managing unmanaged resources directly.</span></span>

<span data-ttu-id="50017-246">İfade için bu yeni konumlar C# dili için önemli bir kilometre taşını temsil eder: Bu özellikler, açık kaynaklı [Roslyn](https://github.com/dotnet/Roslyn) projesinde çalışan topluluk üyeleri tarafından uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="50017-246">These new locations for expression-bodied members represent an important milestone for the C# language: These features were implemented by community members working on the open-source [Roslyn](https://github.com/dotnet/Roslyn) project.</span></span>

<span data-ttu-id="50017-247">Bir yöntemi bir ifade ile değiştirmek, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)olur.</span><span class="sxs-lookup"><span data-stu-id="50017-247">Changing a method to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="throw-expressions"></a><span data-ttu-id="50017-248">Throw ifadeleri</span><span class="sxs-lookup"><span data-stu-id="50017-248">Throw expressions</span></span>

<span data-ttu-id="50017-249">C# ' de `throw` her zaman bir ifade olmuştur.</span><span class="sxs-lookup"><span data-stu-id="50017-249">In C#, `throw` has always been a statement.</span></span> <span data-ttu-id="50017-250">Bir `throw` ifade değil, bir deyim olduğundan, bunu kullanamadığı Için C# yapıları vardı.</span><span class="sxs-lookup"><span data-stu-id="50017-250">Because `throw` is a statement, not an expression, there were C# constructs where you couldn't use it.</span></span> <span data-ttu-id="50017-251">Bu dahil edilen Koşullu ifadeler, null birleştirme ifadeleri ve bazı lambda ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="50017-251">These included conditional expressions, null coalescing expressions, and some lambda expressions.</span></span> <span data-ttu-id="50017-252">İfade bululmuş üyelerin eklenmesi, ifadelerin yararlı olacağı daha fazla konum ekler `throw` .</span><span class="sxs-lookup"><span data-stu-id="50017-252">The addition of expression-bodied members adds more locations where `throw` expressions would be useful.</span></span> <span data-ttu-id="50017-253">Bu yapıların herhangi birini yazmak için C# 7,0, [*throw ifadelerini*](../language-reference/keywords/throw.md#the-throw-expression)tanıtır.</span><span class="sxs-lookup"><span data-stu-id="50017-253">So that you can write any of these constructs, C# 7.0 introduces [*throw expressions*](../language-reference/keywords/throw.md#the-throw-expression).</span></span>

<span data-ttu-id="50017-254">Bu ek, daha fazla ifade tabanlı kod yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="50017-254">This addition makes it easier to write more expression-based code.</span></span> <span data-ttu-id="50017-255">Hata denetimi için ek deyimlere ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="50017-255">You don't need additional statements for error checking.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="50017-256">Varsayılan değişmez değer ifadeleri</span><span class="sxs-lookup"><span data-stu-id="50017-256">Default literal expressions</span></span>

<span data-ttu-id="50017-257">Varsayılan değişmez değer ifadeleri varsayılan değer ifadelerine yönelik bir geliştirmedir.</span><span class="sxs-lookup"><span data-stu-id="50017-257">Default literal expressions are an enhancement to default value expressions.</span></span> <span data-ttu-id="50017-258">Bu ifadeler varsayılan değere bir değişken başlatır.</span><span class="sxs-lookup"><span data-stu-id="50017-258">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="50017-259">Daha önce yazdığınız yer:</span><span class="sxs-lookup"><span data-stu-id="50017-259">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="50017-260">Artık başlatmanın sağ tarafındaki türü atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50017-260">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="50017-261">Daha fazla bilgi için [varsayılan işleç](../language-reference/operators/default.md) makalesinin [varsayılan değişmez değeri](../language-reference/operators/default.md#default-literal) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="50017-261">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="numeric-literal-syntax-improvements"></a><span data-ttu-id="50017-262">Sayısal sabit değer sözdizimi geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="50017-262">Numeric literal syntax improvements</span></span>

<span data-ttu-id="50017-263">Hatalı okuma sayısal sabitleri, ilk kez okurken kodu daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="50017-263">Misreading numeric constants can make it harder to understand code when reading it for the first time.</span></span> <span data-ttu-id="50017-264">Bit maskeleri veya diğer sembolik değerler yanlış anlama eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="50017-264">Bit masks or other symbolic values are prone to misunderstanding.</span></span> <span data-ttu-id="50017-265">C# 7,0, tasarlanan kullanım için en okunabilir şekilde sayı yazmak üzere iki yeni özellik içerir: *ikili sabit değerler* ve *basamak ayırıcıları*.</span><span class="sxs-lookup"><span data-stu-id="50017-265">C# 7.0 includes two new features to write numbers in the most readable fashion for the intended use: *binary literals*, and *digit separators*.</span></span>

<span data-ttu-id="50017-266">Bit maskeleri oluştururken veya bir sayının ikili gösteriminin en çok okunabilen kodu yaptığı durumlarda bu süreler için bu sayıyı binary olarak yazın:</span><span class="sxs-lookup"><span data-stu-id="50017-266">For those times when you're creating bit masks, or whenever a binary representation of a number makes the most readable code, write that number in binary:</span></span>

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

<span data-ttu-id="50017-267">`0b`Sabitin başlangıcında, sayının bir ikili sayı olarak yazıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50017-267">The `0b` at the beginning of the constant indicates that the number is written as a binary number.</span></span> <span data-ttu-id="50017-268">İkili sayılar uzun sürebilir, bu nedenle, `_` önceki örnekteki ikili Sabitte gösterildiği gibi, bir rakam ayırıcısı olarak girerek bit desenlerini görmeniz genellikle daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="50017-268">Binary numbers can get long, so it's often easier to see the bit patterns by introducing the `_` as a digit separator, as shown in the binary constant in the preceding example.</span></span> <span data-ttu-id="50017-269">Sayı ayırıcısı, sabit içinde herhangi bir yerde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="50017-269">The digit separator can appear anywhere in the constant.</span></span> <span data-ttu-id="50017-270">10 tabanında sayı için bu, binlerce ayırıcı olarak kullanılması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="50017-270">For base 10 numbers, it is common to use it as a thousands separator.</span></span> <span data-ttu-id="50017-271">Onaltılı ve ikili sayısal değişmez değerler bir ile başlayabilir `_` :</span><span class="sxs-lookup"><span data-stu-id="50017-271">Hex and binary numeric literals may begin with an `_`:</span></span>

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

<span data-ttu-id="50017-272">Rakam ayırıcısı,, ve türleri ile birlikte kullanılabilir `decimal` `float` `double` :</span><span class="sxs-lookup"><span data-stu-id="50017-272">The digit separator can be used with `decimal`, `float`, and `double` types as well:</span></span>

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

<span data-ttu-id="50017-273">Birlikte çalışarak, sayısal sabitleri çok daha okunaklı bir şekilde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-273">Taken together, you can declare numeric constants with much more readability.</span></span>

## <a name="out-variables"></a><span data-ttu-id="50017-274">`out` değişkenlerinin</span><span class="sxs-lookup"><span data-stu-id="50017-274">`out` variables</span></span>

<span data-ttu-id="50017-275">Parametreleri destekleyen mevcut sözdizimi `out` C# 7 ' de geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="50017-275">The existing syntax that supports `out` parameters has been improved in C# 7.</span></span> <span data-ttu-id="50017-276">Artık `out` değişkenleri, ayrı bir bildirim bildirimi yazmak yerine bir yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50017-276">You can now declare `out` variables in the argument list of a method call, rather than writing a separate declaration statement:</span></span>

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

<span data-ttu-id="50017-277">`out`Yukarıdaki örnekte gösterildiği gibi, açıklık için değişkenin türünü belirtmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-277">You may want to specify the type of the `out` variable for clarity, as shown in the preceding example.</span></span> <span data-ttu-id="50017-278">Ancak, dil örtük olarak yazılmış bir yerel değişken kullanmayı destekler:</span><span class="sxs-lookup"><span data-stu-id="50017-278">However, the language does support using an implicitly typed local variable:</span></span>

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- <span data-ttu-id="50017-279">Kodu daha kolay okunabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-279">The code is easier to read.</span></span>
  - <span data-ttu-id="50017-280">Yukarıdaki kod satırında değil, kullandığınız yerde çıkış değişkenini bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-280">You declare the out variable where you use it, not on a preceding line of code.</span></span>
- <span data-ttu-id="50017-281">İlk değer atamaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="50017-281">No need to assign an initial value.</span></span>
  - <span data-ttu-id="50017-282">`out`Yöntemi bir yöntem çağrısında kullanıldığı yerde bildirerek, yanlışlıkla onu atanmadan kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="50017-282">By declaring the `out` variable where it's used in a method call, you can't accidentally use it before it is assigned.</span></span>

<span data-ttu-id="50017-283">Değişken bildirimlerine izin vermek için C# 7,0 ' ye eklenen söz dizimi, `out` alan başlatıcıları, özellik başlatıcıları, Oluşturucu başlatıcıları ve sorgu yan tümcelerini kapsayacak şekilde genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="50017-283">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="50017-284">Aşağıdaki örnek gibi kodu sunar:</span><span class="sxs-lookup"><span data-stu-id="50017-284">It enables code such as the following example:</span></span>

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

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="50017-285">Girintili olmayan adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="50017-285">Non-trailing named arguments</span></span>

<span data-ttu-id="50017-286">Yöntem çağrıları artık, adlandırılmış bağımsız değişkenler doğru konumlarda olduğunda Konumsal bağımsız değişkenlerden önce gelen adlandırılmış bağımsız değişkenleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-286">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="50017-287">Daha fazla bilgi için bkz. [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="50017-287">For more information, see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="private-protected-access-modifier"></a><span data-ttu-id="50017-288">*özel korumalı* erişim değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="50017-288">*private protected* access modifier</span></span>

<span data-ttu-id="50017-289">Yeni bir bileşik erişim değiştiricisi: `private protected` bir üyeye, aynı derlemede belirtilen sınıf veya türetilmiş sınıfları içeren bir üyeye erişilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="50017-289">A new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="50017-290">`protected internal`Aynı derlemede bulunan türetilmiş sınıfların veya sınıfların erişimine izin verdiğinden, `private protected` aynı derlemede belirtilen türetilmiş türlere erişimi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="50017-290">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="50017-291">Daha fazla bilgi için bkz. dil başvurusunda [erişim değiştiriciler](../language-reference/keywords/access-modifiers.md) .</span><span class="sxs-lookup"><span data-stu-id="50017-291">For more information, see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

## <a name="improved-overload-candidates"></a><span data-ttu-id="50017-292">Geliştirilmiş aşırı yükleme adayları</span><span class="sxs-lookup"><span data-stu-id="50017-292">Improved overload candidates</span></span>

<span data-ttu-id="50017-293">Her sürümde, aşırı yükleme çözümleme kuralları belirsiz Yöntem etkinleştirmeleri "belirgin" bir seçeneğe sahip olduğu durumlara göre güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="50017-293">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="50017-294">Bu sürüm, derleyicinin açık seçimi seçmesini sağlamaya yardımcı olmak için üç yeni kural ekler:</span><span class="sxs-lookup"><span data-stu-id="50017-294">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="50017-295">Bir yöntem grubu hem örnek hem de statik üye içerdiğinde, yöntem bir örnek alıcısı veya bağlamı olmadan çağrılırsa, derleyici örnek üyelerini atar.</span><span class="sxs-lookup"><span data-stu-id="50017-295">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="50017-296">Yöntem bir örnek alıcısıyla çağrılırsa derleyici statik üyeleri atar.</span><span class="sxs-lookup"><span data-stu-id="50017-296">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="50017-297">Alıcı olmadığında, derleyici statik bir bağlamda yalnızca statik üyeleri ve statik ve örnek üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="50017-297">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="50017-298">Alıcı bir örnek veya tür ındexattributes, derleyici her ikisini de içerir.</span><span class="sxs-lookup"><span data-stu-id="50017-298">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="50017-299">Örtük bir örnek alıcısının kullanıldığı statik bir bağlam, statik üyeler gibi, hiçbir üyenin, örneğin, `this` `this` `this` alan başlatıcıları ve Oluşturucu başlatıcıları gibi kullanılamayan yerleri de içerir.</span><span class="sxs-lookup"><span data-stu-id="50017-299">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="50017-300">Bir yöntem grubu, tür bağımsız değişkenleri kısıtlamalarını karşılamadığı bazı genel yöntemler içerdiğinde, bu üyeler aday kümesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="50017-300">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="50017-301">Bir yöntem grubu dönüştürmesi için, dönüş türü, temsilcinin dönüş türüyle eşleşmeyen aday Yöntemler kümeden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="50017-301">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="50017-302">Bu değişikliği yalnızca, hangi yöntemin daha iyi olduğundan emin olduğunuzda belirsiz yöntem aşırı yüklemeleri için daha az derleyici hatası bulacağınız için fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-302">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="50017-303">Daha verimli güvenli kod etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="50017-303">Enabling more efficient safe code</span></span>

<span data-ttu-id="50017-304">Güvenli olmayan kodun yanı sıra, güvenli bir şekilde C# kodu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="50017-304">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="50017-305">Güvenli kod, arabellek taşmaları, başıya işaretçileri ve diğer bellek erişim hataları gibi hata sınıflarını önler.</span><span class="sxs-lookup"><span data-stu-id="50017-305">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="50017-306">Bu yeni özellikler, doğrulanabilir güvenli kod yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="50017-306">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="50017-307">Güvenli yapılar kullanarak kodunuzun daha fazlasını yazmak için çaba harcar.</span><span class="sxs-lookup"><span data-stu-id="50017-307">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="50017-308">Bu özellikler daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="50017-308">These features make that easier.</span></span>

<span data-ttu-id="50017-309">Aşağıdaki yeni özellikler, güvenli kod için daha iyi performans temasını destekler:</span><span class="sxs-lookup"><span data-stu-id="50017-309">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="50017-310">Sabitlemeden sabit alanlara erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-310">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="50017-311">`ref`Yerel değişkenleri yeniden atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-311">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="50017-312">Dizilerde başlatıcıları kullanabilirsiniz `stackalloc` .</span><span class="sxs-lookup"><span data-stu-id="50017-312">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="50017-313">`fixed`Deyimlerini, bir kalıbı destekleyen herhangi bir türle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-313">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="50017-314">Ek genel kısıtlamalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-314">You can use additional generic constraints.</span></span>
- <span data-ttu-id="50017-315">`in`Bir bağımsız değişkenin başvuruya göre geçirilmesini, ancak çağrılan yöntem tarafından değiştirilmediğinden emin olmak için parametrelerde değiştirici.</span><span class="sxs-lookup"><span data-stu-id="50017-315">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span> <span data-ttu-id="50017-316">`in`Bir bağımsız değişkene değiştirici eklemek, kaynak ile [uyumlu bir değişiklik](version-update-considerations.md#source-compatible-changes)olur.</span><span class="sxs-lookup"><span data-stu-id="50017-316">Adding the `in` modifier to an argument is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span>
- <span data-ttu-id="50017-317">Yöntem `ref readonly` üzerinde değiştirici, bir yöntemin değerini başvuruya göre döndürdüğünü ancak bu nesneye yazma izni olmadığını belirtmek için döndürür.</span><span class="sxs-lookup"><span data-stu-id="50017-317">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span> <span data-ttu-id="50017-318">Değiştirici eklemek `ref readonly` , döndürme bir değere atanmışsa, [kaynak ile uyumlu bir değişiklik](version-update-considerations.md#source-compatible-changes)olur.</span><span class="sxs-lookup"><span data-stu-id="50017-318">Adding the `ref readonly` modifier is a [source compatible change](version-update-considerations.md#source-compatible-changes), if the return is assigned to a value.</span></span> <span data-ttu-id="50017-319">`readonly`Değiştirici varolan bir `ref` Return ifadesine eklendiğinde [uyumsuz bir değişiklik](version-update-considerations.md#incompatible-changes)vardır.</span><span class="sxs-lookup"><span data-stu-id="50017-319">Adding the `readonly` modifier to an existing `ref` return statement is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="50017-320">Çağrıcıların `ref` , değiştiricisini içermesi için yerel değişkenlerin bildirimini güncelleştirmesi gerekir `readonly` .</span><span class="sxs-lookup"><span data-stu-id="50017-320">It requires callers to update the declaration of `ref` local variables to include the `readonly` modifier.</span></span>
- <span data-ttu-id="50017-321">`readonly struct`Bir yapının sabit olduğunu ve onun üye yöntemlerine bir parametre olarak geçirilmesi gerektiğini göstermek için bildirimi `in` .</span><span class="sxs-lookup"><span data-stu-id="50017-321">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span> <span data-ttu-id="50017-322">Değiştirici, `readonly` var olan bir struct bildirimine eklendiğinde, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)bulunur.</span><span class="sxs-lookup"><span data-stu-id="50017-322">Adding the `readonly` modifier to an existing struct declaration is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>
- <span data-ttu-id="50017-323">`ref struct`Bir yapı türünün doğrudan yönetilen belleğe eriştiğini ve her zaman yığın ayrılması gerektiğini göstermek için bildirimi.</span><span class="sxs-lookup"><span data-stu-id="50017-323">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span> <span data-ttu-id="50017-324">`ref`Değiştirici varolan bir `struct` bildirime eklendiğinde [uyumsuz bir değişiklik](version-update-considerations.md#incompatible-changes)vardır.</span><span class="sxs-lookup"><span data-stu-id="50017-324">Adding the `ref` modifier to an existing `struct` declaration is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="50017-325">Bir `ref struct` sınıfın üyesi olamaz veya yığın üzerinde ayrılabileceği diğer konumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-325">A `ref struct` cannot be a member of a class or used in other locations where it may be allocated on the heap.</span></span>

<span data-ttu-id="50017-326">Bu değişiklikler hakkında daha fazla bilgi için [yazma güvenli verimli kod](../write-safe-efficient-code.md)' a erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-326">You can read more about all these changes in [Write safe efficient code](../write-safe-efficient-code.md).</span></span>

### <a name="ref-locals-and-returns"></a><span data-ttu-id="50017-327">Ref Yereller ve geri dönüşler</span><span class="sxs-lookup"><span data-stu-id="50017-327">Ref locals and returns</span></span>

<span data-ttu-id="50017-328">Bu özellik, tarafından kullanılan ve başka bir yerde tanımlanan değişkenlere başvuru döndüren algoritmaların yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="50017-328">This feature enables algorithms that use and return references to variables defined elsewhere.</span></span> <span data-ttu-id="50017-329">Bir örnek büyük matrislerle çalışıyor ve belirli özelliklere sahip tek bir konum buluyor.</span><span class="sxs-lookup"><span data-stu-id="50017-329">One example is working with large matrices, and finding a single location with certain characteristics.</span></span> <span data-ttu-id="50017-330">Aşağıdaki yöntem, matriste bu depolama için bir **başvuru** döndürür:</span><span class="sxs-lookup"><span data-stu-id="50017-330">The following method returns a **reference** to that storage in the matrix:</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="50017-331">`ref`Aşağıdaki kodda gösterildiği gibi, dönüş değerini bir olarak bildirebilir ve matriste bu değeri değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50017-331">You can declare the return value as a `ref` and modify that value in the matrix, as shown in the following code:</span></span>

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

<span data-ttu-id="50017-332">C# dili, yerelleri yanlış kullanmanızı ve şunu döndürdüğünü koruyan çeşitli kurallara sahiptir `ref` :</span><span class="sxs-lookup"><span data-stu-id="50017-332">The C# language has several rules that protect you from misusing the `ref` locals and returns:</span></span>

- <span data-ttu-id="50017-333">`ref`Anahtar sözcüğünü Yöntem imzasına ve `return` bir yöntemindeki tüm deyimlere eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="50017-333">You must add the `ref` keyword to the method signature and to all `return` statements in a method.</span></span>
  - <span data-ttu-id="50017-334">Bu, yöntem boyunca başvuruya göre döndürülen yöntemi temizler.</span><span class="sxs-lookup"><span data-stu-id="50017-334">That makes it clear the method returns by reference throughout the method.</span></span>
- <span data-ttu-id="50017-335">Bir `ref return` değer değişkenine veya bir `ref` değişkene atanabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-335">A `ref return` may be assigned to a value variable, or a `ref` variable.</span></span>
  - <span data-ttu-id="50017-336">Çağıran, dönüş değerinin kopyalanıp kopyalanmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="50017-336">The caller controls whether the return value is copied or not.</span></span> <span data-ttu-id="50017-337">`ref`Dönüş değerini atarken değiştiricinin atlanması, çağıranın depolama için bir başvuru değil, değer kopyasının istediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="50017-337">Omitting the `ref` modifier when assigning the return value indicates that the caller wants a copy of the value, not a reference to the storage.</span></span>
- <span data-ttu-id="50017-338">Bir yerel değişkene standart bir yöntem dönüş değeri atayamazsınız `ref` .</span><span class="sxs-lookup"><span data-stu-id="50017-338">You can't assign a standard method return value to a `ref` local variable.</span></span>
  - <span data-ttu-id="50017-339">Şunun gibi deyimler izin vermez `ref int i = sequence.Count();`</span><span class="sxs-lookup"><span data-stu-id="50017-339">That disallows statements like `ref int i = sequence.Count();`</span></span>
- <span data-ttu-id="50017-340">`ref`Ömrü, yönteminin yürütülmesinden daha fazla genişlemeyen bir değişkene geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="50017-340">You can't return a `ref` to a variable whose lifetime doesn't extend beyond the execution of the method.</span></span>
  - <span data-ttu-id="50017-341">Bu, yerel bir değişkene veya benzer kapsama sahip bir değişkene bir başvuru döndüremeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="50017-341">That means you can't return a reference to a local variable or a variable with a similar scope.</span></span>
- <span data-ttu-id="50017-342">`ref` Yereller ve geri dönüş, zaman uyumsuz yöntemlerle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="50017-342">`ref` locals and returns can't be used with async methods.</span></span>
  - <span data-ttu-id="50017-343">Zaman uyumsuz yöntem döndürüldüğünde, derleyici başvurulan değişkenin son değerine ayarlandığını bilemez.</span><span class="sxs-lookup"><span data-stu-id="50017-343">The compiler can't know if the referenced variable has been set to its final value when the async method returns.</span></span>

<span data-ttu-id="50017-344">Ref Yereller ve ref işlevinin eklenmesi, değerleri kopyalamayı önleyerek veya birden çok kez başvuru işlemleri gerçekleştirerek daha etkili olan algoritmaların kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="50017-344">The addition of ref locals and ref returns enables algorithms that are more efficient by avoiding copying values, or performing dereferencing operations multiple times.</span></span>

<span data-ttu-id="50017-345">`ref`Dönüş değerine ekleme, [kaynak ile uyumlu bir değişikdir](version-update-considerations.md#source-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="50017-345">Adding `ref` to the return value is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span> <span data-ttu-id="50017-346">Varolan kod derlenir, ancak ref dönüş değeri atandığında kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="50017-346">Existing code compiles, but the ref return value is copied when assigned.</span></span> <span data-ttu-id="50017-347">Çağıranlar, döndürmeyi `ref` bir başvuru olarak depolamak için dönüş değeri için depolamayı yerel bir değişkene güncelleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="50017-347">Callers must update the storage for the return value to a `ref` local variable to store the return as a reference.</span></span>

<span data-ttu-id="50017-348">Şimdi `ref` Yereller, başlatıldıktan sonra farklı örneklere başvuracak şekilde yeniden atanabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-348">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="50017-349">Aşağıdaki kod artık derlenir:</span><span class="sxs-lookup"><span data-stu-id="50017-349">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="50017-350">Daha fazla bilgi için bkz. [ `ref` `ref` dönüşler ve yerel öğeler](../programming-guide/classes-and-structs/ref-returns.md)ve hakkındaki makale [`foreach`](../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="50017-350">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

<span data-ttu-id="50017-351">Daha fazla bilgi için bkz. [ref anahtar sözcüğü](../language-reference/keywords/ref.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="50017-351">For more information, see the [ref keyword](../language-reference/keywords/ref.md) article.</span></span>

### <a name="conditional-ref-expressions"></a><span data-ttu-id="50017-352">Koşullu `ref` ifadeler</span><span class="sxs-lookup"><span data-stu-id="50017-352">Conditional `ref` expressions</span></span>

<span data-ttu-id="50017-353">Son olarak, koşullu ifade bir değer sonucu yerine bir başvuru sonucu üretebilir.</span><span class="sxs-lookup"><span data-stu-id="50017-353">Finally, the conditional expression may produce a ref result instead of a value result.</span></span> <span data-ttu-id="50017-354">Örneğin, iki diziden birindeki ilk öğeye başvuru almak için aşağıdakini yazın:</span><span class="sxs-lookup"><span data-stu-id="50017-354">For example, you would write the following to retrieve a reference to the first element in one of two arrays:</span></span>

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

<span data-ttu-id="50017-355">Değişken, `r` veya içindeki ilk değere bir başvurudur `arr` `otherArr` .</span><span class="sxs-lookup"><span data-stu-id="50017-355">The variable `r` is a reference to the first value in either `arr` or `otherArr`.</span></span>

<span data-ttu-id="50017-356">Daha fazla bilgi için bkz. dil başvurusunda [koşullu işleç (?:)](../language-reference/operators/conditional-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="50017-356">For more information, see [conditional operator (?:)](../language-reference/operators/conditional-operator.md) in the language reference.</span></span>

### <a name="in-parameter-modifier"></a><span data-ttu-id="50017-357">`in` parametre değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="50017-357">`in` parameter modifier</span></span>

<span data-ttu-id="50017-358">`in`Anahtar sözcüğü, bağımsız değişkenleri başvuruya göre geçirmek için mevcut ref ve out anahtar sözcüklerini tamamlar.</span><span class="sxs-lookup"><span data-stu-id="50017-358">The `in` keyword complements the existing ref and out keywords to pass arguments by reference.</span></span> <span data-ttu-id="50017-359">`in`Anahtar sözcüğü, bağımsız değişkeni başvuruya göre geçirmeyi belirtir, ancak çağrılan yöntem değeri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="50017-359">The `in` keyword specifies passing the argument by reference, but the called method doesn't modify the value.</span></span>

<span data-ttu-id="50017-360">Aşağıdaki kodda gösterildiği gibi, değere göre veya ReadOnly başvuruya göre geçen aşırı yüklemeleri bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50017-360">You may declare overloads that pass by value or by readonly reference, as shown in the following code:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="50017-361">By değeri (önceki örnekte ilk) aşırı yükleme, salt okunur başvuru sürümünden daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="50017-361">The by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="50017-362">Salt okunur başvuru bağımsız değişkeniyle sürümü çağırmak için, `in` yöntemini çağırırken değiştiricisini dahil etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="50017-362">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

<span data-ttu-id="50017-363">Daha fazla bilgi için, [ `in` parametre değiştiricisiyle](../language-reference/keywords/in-parameter-modifier.md)ilgili makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="50017-363">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="50017-364">Daha fazla tür, `fixed` ifadeyi destekler</span><span class="sxs-lookup"><span data-stu-id="50017-364">More types support the `fixed` statement</span></span>

<span data-ttu-id="50017-365">`fixed`İfade sınırlı bir tür kümesi destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="50017-365">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="50017-366">C# 7,3 ' den başlayarak, veya döndüren bir yöntemi içeren herhangi bir tür olabilir `GetPinnableReference()` `ref T` `ref readonly T` `fixed` .</span><span class="sxs-lookup"><span data-stu-id="50017-366">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="50017-367">Bu özelliği eklemek, `fixed` ve ilgili türlerle birlikte kullanılabilecek anlamına gelir <xref:System.Span%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="50017-367">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="50017-368">Daha fazla bilgi için bkz. dil başvurusu içindeki [ `fixed` ifade](../language-reference/keywords/fixed-statement.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="50017-368">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="50017-369">Dizin oluşturma `fixed` alanları sabitleme gerektirmez</span><span class="sxs-lookup"><span data-stu-id="50017-369">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="50017-370">Bu yapıyı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="50017-370">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="50017-371">C# ' nin önceki sürümlerinde, öğesinin parçası olan tamsayıların birine erişmek için bir değişkeni sabitlemeyi gerekiyordu `myFixedField` .</span><span class="sxs-lookup"><span data-stu-id="50017-371">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="50017-372">Şimdi, aşağıdaki kod değişkeni `p` ayrı bir ifadeye sabitlemeden derler `fixed` :</span><span class="sxs-lookup"><span data-stu-id="50017-372">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="50017-373">Değişkeni `p` içindeki bir öğeye erişir `myFixedField` .</span><span class="sxs-lookup"><span data-stu-id="50017-373">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="50017-374">Ayrı bir değişken bildirmeniz gerekmez `int*` .</span><span class="sxs-lookup"><span data-stu-id="50017-374">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="50017-375">Yine de bir `unsafe` bağlam gerekir.</span><span class="sxs-lookup"><span data-stu-id="50017-375">You still need an `unsafe` context.</span></span> <span data-ttu-id="50017-376">C# ' nin önceki sürümlerinde ikinci bir sabit işaretçi bildirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="50017-376">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="50017-377">Daha fazla bilgi için, [ `fixed` deyimindeki](../language-reference/keywords/fixed-statement.md)makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="50017-377">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="50017-378">`stackalloc` diziler, başlatıcıları destekler</span><span class="sxs-lookup"><span data-stu-id="50017-378">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="50017-379">Bir dizideki öğeler için değerleri, başlatma sırasında belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50017-379">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="50017-380">Artık, ile belirtilen dizilere aynı söz dizimi uygulanabilir `stackalloc` :</span><span class="sxs-lookup"><span data-stu-id="50017-380">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="50017-381">Daha fazla bilgi için bkz. [ `stackalloc` operatör](../language-reference/operators/stackalloc.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="50017-381">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="50017-382">Gelişmiş genel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="50017-382">Enhanced generic constraints</span></span>

<span data-ttu-id="50017-383">Artık tür <xref:System.Enum?displayProperty=nameWithType> <xref:System.Delegate?displayProperty=nameWithType> parametresi için türü veya temel sınıf kısıtlamalarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-383">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="50017-384">Yeni `unmanaged` kısıtlamayı, bir tür parametresinin null yapılamayan [yönetilmeyen bir tür](../language-reference/builtin-types/unmanaged-types.md)olması gerektiğini belirtmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50017-384">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="50017-385">Daha fazla bilgi için bkz. tür parametrelerinde [ `where` genel kısıtlamalar](../language-reference/keywords/where-generic-type-constraint.md) ve [kısıtlamalar](../programming-guide/generics/constraints-on-type-parameters.md)hakkında makaleler.</span><span class="sxs-lookup"><span data-stu-id="50017-385">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="50017-386">Bu kısıtlamaları var olan türlere eklemek uyumsuz bir [değişiklik](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="50017-386">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="50017-387">Kapalı genel türler artık bu yeni kısıtlamaları karşılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-387">Closed generic types may no longer meet these new constraints.</span></span>

### <a name="generalized-async-return-types"></a><span data-ttu-id="50017-388">Genelleştirilmiş zaman uyumsuz dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="50017-388">Generalized async return types</span></span>

<span data-ttu-id="50017-389">`Task`Zaman uyumsuz metotlardan bir nesne döndürmek, belirli yollarda performans sorunlarını ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-389">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="50017-390">`Task` bir başvuru türüdür, bu nedenle bu bir nesne ayırma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="50017-390">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="50017-391">Değiştirici ile belirtilen bir yöntemin `async` önbelleğe alınmış bir sonuç döndürdüğü veya zaman uyumlu olarak tamamladığı durumlarda, ek ayırmalar kodun performans açısından kritik bölümlerinde önemli bir zaman maliyeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="50017-391">In cases where a method declared with the `async` modifier returns a cached result, or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="50017-392">Bu ayırmalar sıkı Döngülerde gerçekleşirse maliyetli hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="50017-392">It can become costly if those allocations occur in tight loops.</span></span>

<span data-ttu-id="50017-393">Yeni dil özelliği, zaman uyumsuz yöntem dönüş türlerinin `Task` , ve ile sınırlı olmadığı anlamına gelir `Task<T>` `void` .</span><span class="sxs-lookup"><span data-stu-id="50017-393">The new language feature means that async method return types aren't limited to `Task`, `Task<T>`, and `void`.</span></span> <span data-ttu-id="50017-394">Döndürülen türün zaman uyumsuz düzene uygun olması gerekir, yani bir `GetAwaiter` yönteme erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="50017-394">The returned type must still satisfy the async pattern, meaning a `GetAwaiter` method must be accessible.</span></span> <span data-ttu-id="50017-395">Tek bir somut örnek olarak, `ValueTask` Bu yeni dil özelliğinin kullanılması için tür .net 'e eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="50017-395">As one concrete example, the `ValueTask` type has been added to .NET to make use of this new language feature:</span></span>

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> <span data-ttu-id="50017-396">[`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/)Türünü kullanmak Için NuGet paketini > eklemeniz gerekir <xref:System.Threading.Tasks.ValueTask%601> .</span><span class="sxs-lookup"><span data-stu-id="50017-396">You need to add the NuGet package [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) > in order to use the <xref:System.Threading.Tasks.ValueTask%601> type.</span></span>

<span data-ttu-id="50017-397">Bu geliştirme, en çok bir performans kritik kodunda ayırmayı önlemek için kitaplık yazarları için yararlıdır `Task` .</span><span class="sxs-lookup"><span data-stu-id="50017-397">This enhancement is most useful for library authors to avoid allocating a `Task` in performance critical code.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="50017-398">Yeni derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="50017-398">New compiler options</span></span>

<span data-ttu-id="50017-399">Yeni derleyici seçenekleri C# programları için yeni derleme ve DevOps senaryolarını destekler.</span><span class="sxs-lookup"><span data-stu-id="50017-399">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="reference-assembly-generation"></a><span data-ttu-id="50017-400">Başvuru derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="50017-400">Reference assembly generation</span></span>

<span data-ttu-id="50017-401">*Yalnızca başvuru derlemeler* üreten iki yeni derleyici seçeneği vardır: [**ProduceReferenceAssembly**](../language-reference/compiler-options/output.md#producereferenceassembly) ve [**ProduceOnlyReferenceAssembly**](../language-reference/compiler-options/code-generation.md#produceonlyreferenceassembly).</span><span class="sxs-lookup"><span data-stu-id="50017-401">There are two new compiler options that generate *reference-only assemblies*: [**ProduceReferenceAssembly**](../language-reference/compiler-options/output.md#producereferenceassembly) and [**ProduceOnlyReferenceAssembly**](../language-reference/compiler-options/code-generation.md#produceonlyreferenceassembly).</span></span>
<span data-ttu-id="50017-402">Bağlantılı makaleler, bu seçenekleri ve başvuru derlemelerini daha ayrıntılı bir şekilde açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="50017-402">The linked articles explain these options and reference assemblies in more detail.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="50017-403">Ortak veya açık kaynak imzalama</span><span class="sxs-lookup"><span data-stu-id="50017-403">Public or Open Source signing</span></span>

<span data-ttu-id="50017-404">**Publicsign** derleyici seçeneği derleyicinin bir ortak anahtar kullanarak derlemeyi imzalamasını ister.</span><span class="sxs-lookup"><span data-stu-id="50017-404">The **PublicSign** compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="50017-405">Derleme imzalanmış olarak işaretlenir, ancak imza ortak anahtardan alınır.</span><span class="sxs-lookup"><span data-stu-id="50017-405">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="50017-406">Bu seçenek, açık kaynaklı projelerden ortak anahtar kullanarak imzalı derlemeler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="50017-406">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="50017-407">Daha fazla bilgi için bkz. [ **publicsign** derleyici seçeneği](../language-reference/compiler-options/security.md#publicsign) makalesi.</span><span class="sxs-lookup"><span data-stu-id="50017-407">For more information, see the [**PublicSign** compiler option](../language-reference/compiler-options/security.md#publicsign) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="50017-408">pathmap</span><span class="sxs-lookup"><span data-stu-id="50017-408">pathmap</span></span>

<span data-ttu-id="50017-409">**Pathmap** derleyici seçeneği, derleyicinin kaynak yollarını, derleme ortamından eşlenen kaynak yollarıyla değiştirmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="50017-409">The **PathMap** compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="50017-410">**Pathmap** seçeneği, DERLEYICI tarafından pdb dosyalarına veya için yazılan kaynak yolunu denetler <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> .</span><span class="sxs-lookup"><span data-stu-id="50017-410">The **PathMap** option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="50017-411">Daha fazla bilgi için bkz. [ **pathmap** derleyici seçeneği](../language-reference/compiler-options/advanced.md#pathmap) makalesi.</span><span class="sxs-lookup"><span data-stu-id="50017-411">For more information, see the [**PathMap** compiler option](../language-reference/compiler-options/advanced.md#pathmap) article.</span></span>
