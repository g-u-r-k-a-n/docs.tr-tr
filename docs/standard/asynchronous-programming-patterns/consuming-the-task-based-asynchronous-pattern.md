---
title: Görev Tabanlı Zaman Uyumsuz Desen Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73cf0c09ab41fa7b1e4ee974d62ff8cbee59653b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038127"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Görev Tabanlı Zaman Uyumsuz Desen Kullanma

Zaman uyumsuz işlemlerle çalışmak için görev tabanlı zaman uyumsuz model (TAP) kullandığınızda geri çağırmaları kullanarak, engellemeden beklemeyi elde edebilirsiniz.  Görevler için, bu <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>gibi yöntemlerle elde edilir. Dil tabanlı zaman uyumsuz destek, zaman uyumsuz işlemlerin normal Denetim akışında beklemesine izin vererek geri çağırmaları gizler ve derleyicinin ürettiği kod aynı API düzeyi desteğini sağlar.

## <a name="suspending-execution-with-await"></a>Await ile yürütmeyi askıya alma
 .NET Framework 4,5 ' den başlayarak, zaman uyumsuz olarak<xref:System.Threading.Tasks.Task>[](../../csharp/language-reference/operators/await.md) ve<xref:System.Threading.Tasks.Task%601>nesneleri C# için ' de await anahtar sözcüğünü ve Visual Basic [await işlecini](../../visual-basic/language-reference/operators/await-operator.md) kullanabilirsiniz. Bir <xref:System.Threading.Tasks.Task>beklerken, `await` ifadesi `void`türündedir. Bir <xref:System.Threading.Tasks.Task%601>beklerken, `await` ifadesi `TResult`türündedir. Bir `await` ifadesi bir zaman uyumsuz yöntemin gövdesinde gerçekleşmelidir. .NET Framework 4,5 Visual Basic dil C# desteği hakkında daha fazla bilgi için bkz. C# ve Visual Basic dil belirtimleri.

 Kapakların altında, await işlevi bir devamlılık kullanarak göreve bir geri çağırma işlemini kurar.  Bu geri çağırma, askıya alma noktasındaki zaman uyumsuz yöntemi sürdürür. Zaman uyumsuz yöntem devam ettirildiğinde, abeklelen işlem başarıyla tamamlanırsa ve bir <xref:System.Threading.Tasks.Task%601>, `TResult` döndürülür.  Beklenen <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda sonlandıysa, bir <xref:System.OperationCanceledException> özel durumu oluşturulur.  Beklenen <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda sonlandırılması durumunda hataya neden olan özel durum oluşturulur. `Task` birden çok özel durumun sonucu olarak hata verebilir, ancak bu özel durumların yalnızca biri yayılır. Ancak <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği, tüm hataları içeren bir <xref:System.AggregateException> özel durumu döndürür.

 Bir eşitleme bağlamı (<xref:System.Threading.SynchronizationContext> nesnesi) askıya alma sırasında zaman uyumsuz yöntemi yürüten iş parçacığıyla ilişkiliyse (örneğin, <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> özelliği `null`), zaman uyumsuz yöntem aynı zamanda devam eder bağlam <xref:System.Threading.SynchronizationContext.Post%2A> yöntemi kullanılarak eşitleme bağlamı. Aksi takdirde, askıya alma sırasında geçerli olan görev zamanlayıcısını (<xref:System.Threading.Tasks.TaskScheduler> nesnesi) kullanır. Genellikle, bu, iş parçacığı havuzunu hedefleyen varsayılan görev zamanlayıcısıdır (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>). Bu görev zamanlayıcı, beklenen zaman uyumsuz işlemin tamamlandığında veya sürdürme zamanlanıp zamanlanmayacağını belirler. Varsayılan Zamanlayıcı genellikle devamlılığın tamamlanan işlemin tamamlandığı iş parçacığında çalışmasına izin verir.

 Zaman uyumsuz bir yöntem çağrıldığında, henüz tamamlanmamış olan bir awasever örneğine ilk await ifadesi kadar zaman uyumlu olarak çalışır; bu noktada çağrı çağırana döner. Zaman uyumsuz yöntem `void`döndürmezse, devam eden hesaplamayı temsil eden bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesnesi döndürülür. Void olmayan bir zaman uyumsuz yöntemde, bir return ifadesine karşılaşılırsa veya Yöntem gövdesinin sonuna ulaşıldığında, görev <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> son durumunda tamamlanır. İşlenmeyen bir özel durum denetimin zaman uyumsuz yöntemin gövdesinden ayrılmasına neden oluyorsa, görev <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda sona erer. Bu özel durum bir <xref:System.OperationCanceledException>ise, görev <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda sona erer. Bu şekilde, sonuç veya özel durum sonunda yayımlanmıştır.

 Bu davranışın çeşitli önemli çeşitlemeleri vardır.  Performans nedenleriyle, görev beklenerek görevin zaten tamamlanmışsa, denetim bir şekilde uygulanmaz ve işlev yürütülmeye devam eder.  Ayrıca, özgün bağlamına dönmek her zaman istenen davranış değildir ve değiştirilebilir; Bu, sonraki bölümde daha ayrıntılı olarak açıklanmıştır.

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Yield ve ConfigureAwait ile askıya alma ve sürdürme yapılandırma
 Çeşitli yöntemler zaman uyumsuz yöntemin yürütülmesi üzerinde daha fazla denetim sağlar. Örneğin, zaman uyumsuz metoda bir yield noktası tanıtmak için <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz:

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 Bu, zaman uyumsuz naklin veya geçerli bağlamına yeniden zamanlama ile eşdeğerdir.

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 Zaman uyumsuz bir yöntemde askıya alma ve sürdürme üzerinde daha iyi denetim için <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> yöntemini de kullanabilirsiniz.  Daha önce belirtildiği gibi, varsayılan olarak, geçerli bağlam zaman uyumsuz bir yöntem askıya alındığında yakalanır ve sürdürme üzerinde zaman uyumsuz yöntemin devamlılığını çağırmak için yakalanan bağlam kullanılır.  Çoğu durumda bu, istediğiniz tam davranışdır.  Diğer durumlarda, devamlılık bağlamıyla ilgilenmeyebilirsiniz ve bu gibi gönderilerin özgün bağlamına geri giderek daha iyi performans elde edebilirsiniz.  Bunu etkinleştirmek için, await işleminin bağlam üzerinde yakalanıp sürdürülmeyeceğini bilgilendirmek için <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> yöntemini kullanın, ancak beklenen zaman uyumsuz işlemin tamamlandığı her yerde yürütmeye devam etmek için:

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a>Zaman uyumsuz bir Işlem iptal ediliyor
 .NET Framework 4 ' ten başlayarak, iptali destekleyen yöntemler ' e dokunarak iptal belirtecini kabul eden en az bir aşırı yükleme sağlayın (<xref:System.Threading.CancellationToken> nesnesi).

 İptal belirteci, bir iptal belirteci kaynağı (<xref:System.Threading.CancellationTokenSource> nesnesi) ile oluşturulur.  Kaynağın <xref:System.Threading.CancellationTokenSource.Token%2A> özelliği, kaynağın <xref:System.Threading.CancellationTokenSource.Cancel%2A> yöntemi çağrıldığında sinyal verilecek iptal belirtecini döndürür.  Örneğin, tek bir Web sayfasını indirmek isterseniz ve işlemi iptal etmek istiyorsanız, bir <xref:System.Threading.CancellationTokenSource> nesnesi oluşturur, belirtecini TAP yöntemine geçitirsiniz ve ardından işlemi iptal etmeye hazırsanız kaynağın <xref:System.Threading.CancellationTokenSource.Cancel%2A> metodunu çağırın :

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 Birden çok zaman uyumsuz çağırma işlemini iptal etmek için, tüm etkinleştirmeleri için aynı belirteci geçirebilirsiniz:

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 Ya da aynı belirteci bir işlem seçmeli alt kümesine geçirebilirsiniz:

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 İptal istekleri herhangi bir iş parçacığından başlatılabilir.

 <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> değerini, İptalin hiçbir şekilde istenmeyeceğini göstermek için iptal belirteci kabul eden herhangi bir yönteme geçirebilirsiniz.  Bu, <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> özelliğinin `false`döndürmesini sağlar ve çağrılan yöntem buna göre iyileştirebilirler.  Sınama amacıyla, belirtecin zaten iptal edilmiş veya iptal edilemez durumunda başlaması gerekip gerekmediğini belirtmek için bir Boole değeri kabul eden oluşturucuyu kullanarak, önceden iptal edilmiş bir iptal belirteci de geçirebilirsiniz.

 Bu iptale yönelik bu yaklaşım birkaç avantaj sağlar:

- Aynı iptal belirtecini herhangi bir sayıda zaman uyumsuz ve zaman uyumlu işleme geçirebilirsiniz.

- Aynı iptal isteği herhangi bir sayıda dinleyiciyle aynı olabilir.

- Zaman uyumsuz API 'nin geliştiricisi, İptalin istenip istenmeyeceğini ve ne zaman etkili olabileceğini kontrol ediyor.

- API 'YI tüketen kod, iptal isteklerinin yayılacağı zaman uyumsuz çağırmaları seçmeli olarak belirleyebilir.

## <a name="monitoring-progress"></a>İlerlemeyi İzleme
 Bazı zaman uyumsuz yöntemler, zaman uyumsuz metoda geçirilen bir ilerleme arabirimiyle ilerlemeyi açığa çıkarır.  Örneğin, bir metin dizesini zaman uyumsuz olarak indiren bir işlevi düşünün ve bu nedenle, şu ana kadar tamamlanan indirme yüzdesini içeren ilerleme güncellemeleri yayınlar.  Böyle bir yöntem, aşağıdaki gibi bir Windows Presentation Foundation (WPF) uygulamasında tüketilebilir:

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a>Yerleşik görev tabanlı kombinatör kullanma
 <xref:System.Threading.Tasks> ad alanı, görevleri oluşturmak ve bunlarla çalışmak için birkaç yöntem içerir.

### <a name="taskrun"></a>Task. Run
 <xref:System.Threading.Tasks.Task> sınıfı, iş parçacığı havuzuna bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> olarak çalışmayı kolayca boşaltmasını sağlayan birkaç <xref:System.Threading.Tasks.Task.Run%2A> yöntemi içerir, örneğin:

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> aşırı yüklemesi gibi bu <xref:System.Threading.Tasks.Task.Run%2A> yöntemlerinden bazıları <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi için toplu olarak mevcuttur.  <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>gibi diğer aşırı yüklemeler, boşaltılan iş içinde await kullanmanıza olanak sağlar, örneğin:

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 Bu tür aşırı yüklemeler, görev paralel kitaplığındaki <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> uzantısı yöntemiyle birlikte <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yönteminin kullanılmasına mantıksal olarak eşdeğerdir.

### <a name="taskfromresult"></a>Task. FromResult
 Verilerin kullanılabildiği senaryolarda <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemini kullanın ve yalnızca bir <xref:System.Threading.Tasks.Task%601>görev döndüren yöntem içinden döndürülmesi gerekir:

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a>Task.WhenAll
 Görev olarak temsil edilen birden çok zaman uyumsuz işlemde zaman uyumsuz olarak beklemek için <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemini kullanın.  Yönteminde, genel olmayan bir görev kümesini veya tek biçimli genel görevler kümesini destekleyen birden çok aşırı yükleme vardır (örneğin, zaman uyumsuz birden fazla void işlem için bekliyor veya birden çok değer döndüren yöntemler için zaman uyumsuz olarak bekleniyor) Her bir değer farklı bir türde olabilir) ve tek bir genel görev kümesini destekler (örneğin, birden çok `TResult`döndüren yöntemler için bekleyen zaman uyumsuz).

 Birkaç müşteriye e-posta iletileri göndermek istediğinizi varsayalım. Bir sonraki göndermeden önce bir iletinin tamamlanmasını beklemmeniz için iletilerin gönderilmesini örtüştürüyorsunuz. Gönderme işlemlerinin ne zaman tamamlandığını ve herhangi bir hata oluşup oluşmadığını da öğrenebilirsiniz:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 Bu kod, oluşabilecek özel durumları açıkça işlemez, ancak <xref:System.Threading.Tasks.Task.WhenAll%2A>' dan elde edilen görevde `await` özel durumlara yaymasına olanak tanır.  Özel durumları işlemek için aşağıdakiler gibi bir kod kullanabilirsiniz:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 Bu durumda, herhangi bir zaman uyumsuz işlem başarısız olursa, tüm özel durumlar <xref:System.Threading.Tasks.Task.WhenAll%2A> yönteminden döndürülen <xref:System.Threading.Tasks.Task> depolanan <xref:System.AggregateException> özel durumunda birleştirilir.  Ancak, bu özel durumlardan yalnızca biri `await` anahtar sözcüğüyle yayılır.  Tüm özel durumları incelemek istiyorsanız, önceki kodu aşağıdaki gibi yeniden yazabilirsiniz:

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 Web 'den zaman uyumsuz olarak birden çok dosya indirme örneği ele alalım.  Bu durumda, tüm zaman uyumsuz işlemlerin homojen sonuç türleri vardır ve sonuçlara erişmek kolaydır:

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 Önceki void döndüren senaryoda açıklandığımız aynı özel durum işleme tekniklerini kullanabilirsiniz:

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a>Task.WhenAny
 Görevler tamamlanana kadar temsil edilen birden çok zaman uyumsuz işlemden yalnızca birini zaman uyumsuz olarak beklemek için <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemini kullanabilirsiniz.  Bu yöntem dört birincil kullanım durumu sunar:

- Yedeklilik: bir işlemi birden çok kez gerçekleştirme ve ilk olarak tamamlanan birini seçme (örneğin, tek bir sonuç üreten ve en hızlı şekilde tamamlanarak birden çok hisse senedi teklifiyle Web hizmetine bağlantı kurma).

- Araya ekleme: birden çok işlem başlatma ve tümünün tamamlanmasını bekleme, ancak tamamlandıkları gibi işleme.

- Daraltma: diğer işlemlerin, diğerleri tamamlanana kadar başlaması sağlanır.  Bu, araya ekleme senaryosunun bir uzantısıdır.

- Erken baılout: Örneğin, Task T1 tarafından temsil edilen bir işlem, başka bir görev T2 ile <xref:System.Threading.Tasks.Task.WhenAny%2A> bir görevde gruplandırılabilir ve <xref:System.Threading.Tasks.Task.WhenAny%2A> görevini bekleyebilir. Görev T2, bir zaman aşımını veya iptali veya <xref:System.Threading.Tasks.Task.WhenAny%2A> görevinin, T1 tamamlanmadan önce tamamlanmasını sağlayan başka bir sinyali temsil ediyor.

#### <a name="redundancy"></a>Yedeklilik
 Bir stok satın alıp almayacağı konusunda bir karar vermek istediğiniz bir durum düşünün.  Güvendiğiniz birkaç hisse senedi önerisi Web hizmeti bulunur, ancak günlük yüküne bağlı olarak her hizmet farklı zamanlarda yavaş yavaş çalışabilir.  Herhangi bir işlem tamamlandığında bildirim almak için <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemini kullanabilirsiniz:

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 Başarıyla tamamlanan tüm görevlerin sarmalanmamış sonuçlarını döndüren <xref:System.Threading.Tasks.Task.WhenAll%2A>aksine <xref:System.Threading.Tasks.Task.WhenAny%2A>, tamamlanan görevi döndürür. Bir görev başarısız olursa, başarısız olması ve bir görevin başarılı olması durumunda, döndürülen değerin hangi görevi ilişkilendirildiğini bilmemiz önemlidir.  Bu nedenle, döndürülen görevin sonucuna erişmeniz veya bu örnekte gösterildiği gibi daha fazla beklemek gerekir.

 <xref:System.Threading.Tasks.Task.WhenAll%2A>olduğu gibi, özel durumlara uyum sağlayabilmeniz gerekir.  Tamamlanan görevi geri aldığınız için döndürülen görevi, hata yayılmasını beklemek ve uygun şekilde `try/catch` için kullanabilirsiniz; Örneğin:

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 Ayrıca, bir ilk görev başarıyla tamamlanırsa bile sonraki görevler başarısız olabilir.  Bu noktada, özel durumlarla uğraşmaya yönelik çeşitli seçenekleriniz vardır: tüm başlatılan görevler tamamlanana kadar bekleyebilirsiniz, bu durumda <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemini kullanabilir veya tüm özel durumların önemli ve günlüğe kaydedilecek şekilde emin olabilirsiniz.  Bu şekilde, görevler zaman uyumsuz olarak tamamlandığında bir bildirim almak için devamlılıkları kullanabilirsiniz:

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 veya:

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 Hatta:

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 Son olarak, kalan tüm işlemleri iptal etmek isteyebilirsiniz:

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a>Araya
 Web 'den görüntü indirirken ve her görüntüyü işlerken (örneğin, bir kullanıcı arabirimi denetimine görüntü ekleme) bir durum düşünün.  İşlem arabirimini Kullanıcı arabirimi iş parçacığında sırayla yapmanız gerekir, ancak görüntüleri mümkün olduğunca eşzamanlı olarak indirmek istersiniz. Ayrıca, tümünün indirilene kadar Kullanıcı arabirimine eklemek istemezsiniz, ancak bunları tamamlandığı gibi eklemek istersiniz:

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 Ayrıca, indirilen görüntülerin <xref:System.Threading.ThreadPool> yoğun işlem gücü içeren bir senaryoya ekleme işlemi uygulayabilirsiniz; Örneğin:

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a>Sınırlama
 Kullanıcının indirdiği, indirmelerin kısıtlanacak birçok görüntünün olması dışında, araya ekleme örneğini düşünün; Örneğin, aynı anda yalnızca belirli sayıda indirmelerin gerçekleşmesini istiyorsunuz. Bunu başarmak için, zaman uyumsuz işlemlerin bir alt kümesini başlatabilirsiniz.  İşlemler tamamlandıktan sonra, bunların yerini almak için ek işlemler başlatabilirsiniz:

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a>Erken Baılout
 Bir işlemin tamamlanması için zaman uyumsuz olarak bir kullanıcının iptal isteğine (örneğin, Kullanıcı bir iptal düğmesine tıkladığını) göz önünde bulundurdığınızı düşünün. Aşağıdaki kod bu senaryoyu göstermektedir:

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 Bu uygulama, zaman aşımına uğrar, ancak temeldeki zaman uyumsuz işlemleri iptal etmez, Kullanıcı arabirimini yeniden sağlar.  Diğer bir seçenek de, iptal etme isteği nedeniyle erken bitebileceği için, işlem gerçekten tamamlanana kadar Kullanıcı arabirimini yeniden kurmamaya kadar bekleyen işlemleri iptal etmek olacaktır:

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 Erken bailout 'ın başka bir örneği, sonraki bölümde anlatıldığı gibi <xref:System.Threading.Tasks.Task.WhenAny%2A> yönteminin <xref:System.Threading.Tasks.Task.Delay%2A> yöntemiyle birlikte kullanılmasını içerir.

### <a name="taskdelay"></a>Task.Delay
 Bir zaman uyumsuz metodun yürütülmesine duraklamalar tanıtmak için <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.  Bu, yoklama döngüleri oluşturma ve önceden belirlenmiş bir süre için Kullanıcı girişinin işlenmesini erteleme dahil olmak üzere çok sayıda işlevsellik için yararlıdır.  <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> yöntemi, await üzerinde zaman aşımlarını uygulamak için <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> birlikte da yararlı olabilir.

 Daha büyük bir zaman uyumsuz işlemin (örneğin, bir ASP.NET Web hizmeti) parçası olan bir görevin tamamlanabilmesi çok uzun sürerse, bu durum özellikle tamamlanamazsa, genel işlem zarar verebilir.  Bu nedenle, zaman uyumsuz bir işlem beklerken zaman aşımına uğrar.  Zaman uyumlu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemleri zaman aşımı değerlerini kabul eder, ancak karşılık gelen <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ve yukarıda bahsedilen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/yöntemleri değildir.  Bunun yerine, zaman aşımı uygulamak için <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> birlikte kullanabilirsiniz.

 Örneğin, Kullanıcı arabirimi uygulamanızda bir görüntü indirmek ve görüntü indirilirken Kullanıcı arabirimini devre dışı bırakmak istediğinizi varsayalım. Ancak indirme çok uzun sürerse, Kullanıcı arabirimini yeniden etkinleştirmek ve indirmeyi atmak istersiniz:

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <xref:System.Threading.Tasks.Task.WhenAll%2A> bir görev döndürdüğünden, aynı durum birden çok indirme için geçerlidir:

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a>Görev tabanlı kombinatör oluşturma
 Bir görev, zaman uyumsuz bir işlemi tamamen temsil edebildiğinden ve işlemle birleştirmek için zaman uyumlu ve zaman uyumsuz yetenekler sağladığından, sonuçlarını almakla ve bu şekilde devam ediyorsa, görevleri oluşturan daha büyük desenler oluşturun.  Önceki bölümde anlatıldığı gibi .NET Framework çeşitli yerleşik kombinatör içerir, ancak kendi kodunuzu da oluşturabilirsiniz. Aşağıdaki bölümlerde olası Combinator yöntemlerine ve türlerine birkaç örnek verilmiştir.

### <a name="retryonfault"></a>RetryOnFault
 Birçok durumda, önceki bir deneme başarısız olursa bir işlemi yeniden denemek isteyebilirsiniz.  Zaman uyumlu kod için, bunu gerçekleştirmek için aşağıdaki örnekte `RetryOnFault` gibi bir yardımcı yöntem oluşturabilirsiniz:

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 DOKUNARAK uygulanan ve bu nedenle görevleri döndüren zaman uyumsuz işlemler için neredeyse özdeş bir yardımcı yöntem oluşturabilirsiniz:

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 Daha sonra bu Combinator kullanarak yeniden denemeleri uygulamanın mantığına dönüştürebilirsiniz; Örneğin:

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 `RetryOnFault` işlevini daha fazla genişletebilirsiniz. Örneğin, işlev işlemin ne zaman denenmesini anlamak için yeniden denemeler arasında çağrılacak başka bir `Func<Task>` kabul edebilir; Örneğin:

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 Ardından, işlemi yeniden denemeden önce bir saniye beklemek için işlevini aşağıdaki şekilde kullanabilirsiniz:

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a>Gereksiz bir
 Bazen bir işlemin gecikme süresini ve başarılı olma olasılığını artırmak için yedekliliğe sahip olabilirsiniz.  Hisse senedi fiyatları sağlayan birden çok Web hizmeti düşünün, ancak günün çeşitli saatlerinde her hizmet farklı düzeylerde kalite ve yanıt süreleri sağlayabilir.  Bu dalgalanmalara ulaşmak için tüm Web hizmetlerine istek verebilir ve birinden yanıt aldığınızda, kalan istekleri iptal edebilirsiniz.  Birden çok işlem başlatmanın bu ortak deseninin uygulanmasını kolaylaştırmak için bir yardımcı işlevi uygulayabilir, herhangi bir bekliyor ve geri kalanını iptal edebilirsiniz. Aşağıdaki örnekteki `NeedOnlyOne` işlevi bu senaryoyu göstermektedir:

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 Daha sonra bu işlevi aşağıdaki şekilde kullanabilirsiniz:

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a>Araya eklemeli Işlemler
 Çok büyük görev kümeleriyle çalışırken bir araya ekleme senaryosunu desteklemek için <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemi kullanımıyla ilgili olası bir performans sorunu vardır. Her <xref:System.Threading.Tasks.Task.WhenAny%2A> çağrısı, her görevle birlikte kaydedilmesiyle sonuçlanır. N sayıda görev için, bu, araya ekleme işleminin ömrü boyunca oluşturulan (N<sup>2</sup>) devamlılıklar ile sonuçlanır. Büyük bir görev kümesiyle çalışıyorsanız, performans sorununu gidermek için bir Combinator (aşağıdaki örnekte`Interleaved`) kullanabilirsiniz:

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 Daha sonra, görevlerin sonuçlarını tamamlarsa işlemek için Combinator kullanabilirsiniz; Örneğin:

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a>WhenAllOrFirstException
 Belirli dağılım/toplama senaryolarında, bir küme içindeki tüm görevleri beklemek isteyebilirsiniz, bu durumda, özel durum meydana geldiğinde beklemeyi durdurmak isteyebilirsiniz.  Bunu, aşağıdaki örnekte `WhenAllOrFirstException` gibi bir Combinator yöntemi ile gerçekleştirebilirsiniz:

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a>Görev tabanlı veri yapıları oluşturma
 Özel görev tabanlı kombinatör oluşturma özelliğine ek olarak, <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> ' de bir veri yapısına sahip olma ve hem zaman uyumsuz bir işlemin sonuçlarını hem de bununla birleştirmek için gereken eşitleme, üzerinde çok güçlü bir tür yapar. zaman uyumsuz senaryolarda kullanılacak özel veri yapılarını derlemek.

### <a name="asynccache"></a>AsyncCache
 Bir görevin önemli bir yönü, birden fazla tüketiciye, hepsi tarafından bekleme, devamlılık veya özel durumları (<xref:System.Threading.Tasks.Task%601>durumunda) elde ettirebilir.  Bu, <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> zaman uyumsuz bir önbelleğe alma altyapısında kullanılmak üzere uygun hale getirir.  Aşağıda, <xref:System.Threading.Tasks.Task%601>üzerine inşa eden küçük ancak güçlü bir zaman uyumsuz önbellek örneği verilmiştir:

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 [AsyncCache\<TKey, TValue > sınıfı,](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) oluşturucusu bir `TKey` alan ve <xref:System.Threading.Tasks.Task%601>döndüren bir işlev için bir temsilci olarak kabul eder.  Ön belleğe daha önce erişilen tüm değerler iç sözlükte depolanır ve `AsyncCache`, önbelleğe eşzamanlı olarak erişilse bile, her anahtar için yalnızca bir görevin oluşturulmasını sağlar.

 Örneğin, indirilen Web sayfaları için bir önbellek oluşturabilirsiniz:

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 Böylece, bir Web sayfasının içeriğine ihtiyacınız olduğunda bu önbelleği zaman uyumsuz metotlarda kullanabilirsiniz. `AsyncCache` sınıfı mümkün olduğunca az sayfa indirmenizi ve sonuçları önbelleğe almanızı sağlar.

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection
 Ayrıca, zaman uyumsuz etkinlikleri koordine etmek üzere veri yapıları oluşturmak için görevleri de kullanabilirsiniz.  Klasik paralel tasarım desenlerinden birini göz önünde bulundurun: Producer/Consumer.  Bu düzende, üreticileri tüketiciler tarafından tüketilen verileri oluşturur ve üreticileri ve tüketiciler paralel olarak çalışabilir. Örneğin, tüketici daha önce öğe 2 ' yi üreten bir üretici tarafından oluşturulan öğe 1 ' i işler.  Üretici/tüketici düzeninde, müşteriler yeni veriler hakkında bildirim almak ve kullanılabilir olduğunda bulmak için üreticileri tarafından oluşturulan işi depolamak üzere bazı veri yapısına ihtiyacınız vardır.

 Aşağıda, zaman uyumsuz yöntemlerin üreticileri ve tüketiciler olarak kullanılmasını sağlayan görevlerin üzerine oluşturulmuş basit bir veri yapısı verilmiştir:

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 Bu veri yapısıyla birlikte, aşağıdaki gibi bir kod yazabilirsiniz:

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<xref:System.Threading.Tasks.Dataflow> ad alanı, benzer bir şekilde kullanabileceğiniz, ancak özel bir koleksiyon türü oluşturmaya gerek kalmadan <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> türünü içerir:

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <xref:System.Threading.Tasks.Dataflow> ad alanı, **NuGet**aracılığıyla .NET Framework 4,5 ' de kullanılabilir. <xref:System.Threading.Tasks.Dataflow> ad alanını içeren derlemeyi yüklemek için projenizi Visual Studio 'da açın, proje menüsünden **NuGet Paketlerini Yönet** ' i seçin ve Microsoft. tpl. Dataflow paketini çevrimiçi olarak arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
