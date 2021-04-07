---
title: Zaman uyumsuz akışlar oluşturma ve kullanma
description: Bu gelişmiş öğreticide, zaman uyumsuz akışlar oluşturma ve kullanma işlemlerinin nasıl yapılacağı gösterilmektedir. Zaman uyumsuz akışlar, zaman uyumsuz olarak oluşturulabilecek veri dizileri ile çalışmanın daha doğal bir yolunu sağlar.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: 4e2264e88b0df9fe8c4e1ebf9bd154dddb390e4e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497430"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Öğretici: C# 8,0 ve .NET Core 3,0 kullanarak zaman uyumsuz akışlar oluşturma ve kullanma

C# 8,0, akış veri kaynağını modelleyebilir ve **zaman uyumsuz akışları** tanıtır. Veri akışları genellikle zaman uyumsuz olarak öğeleri alır veya oluşturur. Zaman uyumsuz akışlar .NET Standard 2,1 ' de tanıtılan yeni arabirimleri kullanır. Bu arabirimler .NET Core 3,0 ve üzeri sürümlerde desteklenir. Bunlar, zaman uyumsuz akış veri kaynakları için doğal bir programlama modeli sağlar.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:

> [!div class="checklist"]
>
> - Zaman uyumsuz bir veri öğeleri dizisi üreten bir veri kaynağı oluşturun.
> - Bu veri kaynağını zaman uyumsuz olarak tükettin.
> - Zaman uyumsuz akışlar için iptal ve yakalanan bağlamlara destek.
> - Yeni arabirim ve veri kaynağı daha önceki zaman uyumlu veri dizileri için tercih edildiği zaman tanıyın.

## <a name="prerequisites"></a>Önkoşullar

C# 8,0 derleyicisi dahil olmak üzere makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. C# 8 derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

GitHub GraphQL uç noktasına erişebilmek için bir [GitHub erişim belirteci](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) oluşturmanız gerekir. GitHub erişim belirteciniz için aşağıdaki izinleri seçin:

- Depo: durum
- public_repo

Erişim belirtecini, GitHub API uç noktasına erişim kazanmak için kullanabilmeniz için güvenli bir yere kaydedin.

> [!WARNING]
> Kişisel erişim belirtecinizi güvende tutun. Kişisel erişim belirtecinize sahip tüm yazılımlar, erişim haklarınızı kullanarak GitHub API çağrıları yapabilir.

Bu öğreticide, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="run-the-starter-application"></a>Başlangıç uygulamasını çalıştırma

Bu öğreticide kullanılan başlangıç uygulamasının kodunu [CSharp/yenilikleri-New/öğreticiler](https://github.com/dotnet/docs/tree/main/docs/csharp/whats-new/tutorials/snippets/generate-consume-asynchronous-streams/start) klasöründeki [DotNet/docs](https://github.com/dotnet/docs) deposundan alabilirsiniz.

Başlangıç uygulaması, [DotNet/docs](https://github.com/dotnet/docs) deposunda yazılan son sorunları almak Için [GitHub graphql](https://developer.github.com/v4/) arabirimini kullanan bir konsol uygulamasıdır. Başlangıç uygulaması yöntemi için aşağıdaki koda bakarak başlayın `Main` :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetStarterAppMain" :::

`GitHubKey`Kişisel erişim belirtecinize bir ortam değişkeni ayarlayabilir veya çağrısındaki son bağımsız değişkeni `GetEnvVariable` kişisel erişim belirtecinizle değiştirebilirsiniz. Kaynağı başkalarıyla paylaşacaksanız, erişim kodunuzu kaynak koda yerleştirmeyin. Erişim kodlarını bir paylaşılan kaynak deposuna hiçbir daha yükleme.

GitHub istemcisini oluşturduktan sonra, içindeki kod `Main` bir ilerleme raporlama nesnesi ve bir iptal belirteci oluşturur. Bu nesneler oluşturulduktan sonra, `Main` `runPagedQueryAsync` en son 250 oluşturulan sorunları almak için çağırır. Bu görev bittikten sonra sonuçlar görüntülenir.

Başlangıç uygulamasını çalıştırdığınızda, bu uygulamanın nasıl çalıştığı hakkında bazı önemli gözlemlerinizi yapabilirsiniz.  GitHub 'dan döndürülen her sayfa için ilerleme durumunu görürsünüz. GitHub her yeni sorun sayfasını geri döndürdüğünden, dikkat çekici bir duraklama gözlemleyebilirsiniz. Son olarak, sorunlar yalnızca GitHub 'dan 10 sayfa alındıktan sonra görüntülenir.

## <a name="examine-the-implementation"></a>Uygulamayı İnceleme

Uygulama, önceki bölümde ele alınan davranışı neden gözlemlediğinizi ortaya çıkarır. Kodu inceleyin `runPagedQueryAsync` :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetRunPagedQuery" :::

Yukarıdaki kodun disk belleği algoritmasına ve zaman uyumsuz yapısına odaklanalım. (GitHub GraphQL API 'SI ile ilgili ayrıntılar için [GitHub graphql belgelerine](https://developer.github.com/v4/guides/) başvurabilirsiniz.) `runPagedQueryAsync` Yöntemi en sonuncudan en eskiye doğru olan sorunları numaralandırır. Sayfa başına 25 sorun ister ve `pageInfo` önceki sayfaya devam etmek için yanıtın yapısını inceler. Bu, çok sayfalı yanıtlar için GraphQL 'in standart disk belleği desteğini izler. Yanıt, `pageInfo` bir `hasPreviousPages` değeri ve `startCursor` önceki sayfayı istemek için kullanılan bir değeri içeren bir nesnesi içerir. Sorunlar `nodes` dizide bulunur. `runPagedQueryAsync`Yöntemi, tüm sayfalardaki sonuçları içeren bir diziye bu düğümleri ekler.

Bir sonuç sayfasını aldıktan ve geri yükledikten sonra, `runPagedQueryAsync` ilerlemeyi raporlar ve iptal olup olmadığını denetler. İptal isteniyorsa, `runPagedQueryAsync` bir oluşturur <xref:System.OperationCanceledException> .

Bu kodda iyileştirilen birkaç öğe vardır. En önemlisi, `runPagedQueryAsync` döndürülen tüm sorunlar için depolama alanı ayırmalıdır. Tüm açık sorunların alınması, alınan tüm sorunları depolamak için çok daha fazla bellek gerektirdiğinden, bu örnek 250 sorunlarını durduruyor. İlerleme raporlarını ve iptali destekleme protokolleri, ilk okuma sırasında algoritmayı daha zor hale getirir. Diğer türler ve API 'Ler dahil değildir. <xref:System.Threading.CancellationTokenSource> <xref:System.Threading.CancellationToken> İptalin istendiği ve nerede verildiğini anlamak için, ve arasındaki iletişimleri takip etmeniz gerekir.

## <a name="async-streams-provide-a-better-way"></a>Zaman uyumsuz akışlar daha iyi bir yol sağlar

Zaman uyumsuz akışlar ve ilişkili dil desteği Bu kaygıların tümünü ele. Diziyi oluşturan kod artık `yield return` değiştiriciyle tanımlanmış bir yöntemde öğe döndürmek için kullanabilir `async` . Döngü kullanarak bir zaman uyumsuz akışı, bir `await foreach` döngüyü kullanarak herhangi bir diziyi tüketiğinizde kullanabilirsiniz `foreach` .

Bu yeni dil özellikleri, 2,1 .NET Standard eklenen ve .NET Core 3,0 ' de uygulanan üç yeni arabirime bağımlıdır:

- <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>
- <xref:System.IAsyncDisposable?displayProperty=nameWithType>

Bu üç arabirim çoğu C# geliştiricisi için tanıdık olmalıdır. Zaman uyumlu ortaklarınıza benzer bir şekilde davranır:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Alışkın olabilecek bir tür <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType> . `ValueTask`Struct, sınıfa benzer BIR API sağlar <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> . `ValueTask` performans nedenleriyle bu arabirimlerde kullanılır.

## <a name="convert-to-async-streams"></a>Zaman uyumsuz akışlara Dönüştür

Sonra, `runPagedQueryAsync` zaman uyumsuz akış oluşturmak için yöntemini dönüştürün. İlk olarak, `runPagedQueryAsync` öğesini döndürmek için imzasını değiştirin `IAsyncEnumerable<JToken>` ve aşağıdaki kodda gösterildiği gibi parametre listesinden iptal belirtecini ve ilerleme nesnelerini kaldırın:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetUpdateSignature" :::

Başlangıç kodu, aşağıdaki kodda gösterildiği gibi her sayfayı sayfa alındığından işler:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetProcessPage" :::

Bu üç satırı aşağıdaki kodla değiştirin:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetYieldReturnPage" :::

Ayrıca, `finalResults` Bu yöntemin önceki bildirimini ve `return` değiştirdiğiniz döngüyü izleyen ifadeyi de kaldırabilirsiniz.

Zaman uyumsuz akış oluşturma değişikliklerini tamamladınız. Tamamlanan yöntem aşağıdaki koda benzemelidir:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateAsyncStream" :::

Daha sonra, zaman uyumsuz akışı kullanmak için koleksiyonu tüketen kodu değiştirirsiniz. Sorun koleksiyonunu işleyen ' de aşağıdaki kodu bulun `Main` :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetEnumerateOldStyle" :::

Bu kodu aşağıdaki `await foreach` döngüyle değiştirin:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateAsyncStream" :::

Yeni arabirim <xref:System.Collections.Generic.IAsyncEnumerator%601> öğesinden türetilir <xref:System.IAsyncDisposable> . Diğer bir deyişle, döngü tamamlandığında önceki döngünün akışı zaman uyumsuz olarak elden atacaktır. Döngünün aşağıdaki kod gibi göründüğünü hayal edebilirsiniz:

```csharp
int num = 0;
var enumerator = runPagedQueryAsync(client, PagedIssueQuery, "docs").GetEnumeratorAsync();
try
{
    while (await enumerator.MoveNextAsync())
    {
        var issue = enumerator.Current;
        Console.WriteLine(issue);
        Console.WriteLine($"Received {++num} issues in total");
    }
} finally
{
    if (enumerator != null)
        await enumerator.DisposeAsync();
}
```

Akış öğeleri varsayılan olarak yakalanan bağlamda işlenir. Bağlam yakalamayı devre dışı bırakmak istiyorsanız, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> genişletme yöntemini kullanın. Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz model](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)kullanma başlıklı makaleye bakın.

Zaman uyumsuz akışlar, diğer yöntemlerle aynı protokolü kullanarak iptali destekler `async` . İptali desteklemek için zaman uyumsuz Yineleyici yönteminin imzasını aşağıdaki şekilde değiştirirsiniz:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateWithCancellation" :::

<xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType>Özniteliği, derleyicinin, <xref:System.Collections.Generic.IAsyncEnumerator%601> belirtecin `GetAsyncEnumerator` zaman uyumsuz yineleyicinin gövdesine bu bağımsız değişken olarak geçirilmesini sağlayan kod oluşturmasını sağlar. İçinde `runQueryAsync` , belirtecin durumunu inceleyebilir ve istenirse daha fazla çalışmayı iptal edebilirsiniz.

<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A>İptal belirtecini zaman uyumsuz akışa geçirmek için başka bir genişletme yöntemi kullanın. Sorunları şu şekilde numaralandırarak aşağıdaki gibi düzenleyin:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateWithCancellation" :::

[CSharp/yenilikleri-New/öğreticiler](https://github.com/dotnet/docs/tree/main/docs/csharp/whats-new/tutorials/snippets/generate-consume-asynchronous-streams/finished) klasöründeki [DotNet/docs](https://github.com/dotnet/docs) deposundan tamamlanan öğreticinin kodunu alabilirsiniz.

## <a name="run-the-finished-application"></a>Tamamlanmış uygulamayı çalıştırma

Uygulamayı yeniden çalıştırın. Davranışını, başlangıç uygulamasının davranışıyla kontrast. Sonuçların ilk sayfası, kullanılabilir duruma geldiğinde numaralandırılır. Her yeni sayfa istendiği ve alındığı için bir observable durakladıkça, sonraki sayfanın sonuçları hızla numaralandırılır. `try`  /  `catch` İptali işlemek için blok gerekmez: çağıran, koleksiyonu listemeyi durdurabilir. Zaman uyumsuz akış, her sayfa indirildiğinden sonuçlar oluşturduğundan, ilerleme durumu açıkça raporlanır. Döndürülen her bir sorunun durumu, döngüye sorunsuz bir şekilde dahildir `await foreach` . İlerlemeyi izlemek için bir geri çağırma nesnesine gerek yoktur.

Kodu inceleyerek, bellek kullanımıyla iyileştirmeleri görebilirsiniz. Artık tüm sonuçları numaralandırılmadan önce depolamak için bir koleksiyon ayırmanız gerekmez. Çağıran, sonuçların nasıl kullanıldığını ve bir depolama koleksiyonu gerekip gerekmediğini belirleyebilir.

Hem Başlatıcı hem de tamamlanmış uygulamaları çalıştırın ve uygulamalar arasındaki farklılıkları gözlemleyebilirsiniz. İşiniz bittiğinde, bu öğreticiyi başlattığınızda oluşturduğunuz GitHub erişim belirtecini silebilirsiniz. Bir saldırgan bu belirtece erişim kazanırsa, kimlik bilgilerinizi kullanarak GitHub API 'Lerine erişebilirler.
