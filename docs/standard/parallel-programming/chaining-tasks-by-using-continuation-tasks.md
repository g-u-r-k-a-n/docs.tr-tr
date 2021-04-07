---
title: Devamlılık görevlerini kullanarak görevleri zincirleme
description: .NET 'teki devamlılık görevlerini kullanarak görev zincirini öğrenin. Devamlılık görevi, başka bir görev tarafından çağrılan zaman uyumsuz bir görevdir.
ms.date: 01/06/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
ms.openlocfilehash: e261674a38f250f667df5298fc1a80b75596c4c5
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498509"
---
# <a name="chaining-tasks-using-continuation-tasks"></a>Devamlılık görevlerini kullanarak görevleri zincirleme

Zaman uyumsuz programlamada, tamamlandığında bir zaman uyumsuz işlem, ikinci bir işlemi çağırmak için ortaktır. Devamlılıklar, alt işlemlerin ilk işlemin sonuçlarını kullanmasına izin verir. Geleneksel olarak, devamlılıklar geri çağırma yöntemleri kullanılarak yapılır. Görev paralel kitaplığında, aynı işlevler _devamlılık görevleri_ tarafından sağlanır. Bir devamlılık görevi (sadece devamlılık olarak da bilinir _), öncül_ olarak bilinen başka bir görev tarafından çağrılan zaman uyumsuz bir görevdir.

Devamlılıkların kullanımı nispeten kolaydır, ancak bu, güçlü ve esnektir. Örneğin, şunları yapabilirsiniz:

- Verileri öncül bilgisayardan devamlıya geçirin.
- Devamlılığın çağrılacağını veya çağrılmaması gereken kesin koşulları belirtin.
- Çalışmaya başlamadan önce veya çalışmaya devam etmeden önce bir devamlılığın iptal edildiğini yapın.
- Devamlılığın nasıl zamanlanması gerektiği hakkında ipuçları sağlayın.
- Aynı öncül öğesinden birden çok devamlılık çağırın.
- Bir veya birden çok öncüllerin tamamlandıktan sonra bir devamlılık çağırın.
- Zincirden sonra herhangi bir rastgele uzunluğa kadar zincir devamlılıkları.
- Öncül tarafından oluşturulan özel durumları işlemek için devamlılık kullanın.

## <a name="about-continuations"></a>Devamlılıklar hakkında

Devamlılık, durumunda oluşturulan bir görevdir <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> . Öncül görevi veya görevleri tamamlandığında otomatik olarak etkinleştirilir. <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType>Kullanıcı kodunda devamlılığın çağrılması bir <xref:System.InvalidOperationException?displayProperty=nameWithType> özel durum oluşturur.

Devamlılık kendi kendisidir <xref:System.Threading.Tasks.Task> ve başlatıldığı iş parçacığını engellemez. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>Devamlılık görevi bitene kadar engellemek için yöntemini çağırın.

## <a name="create-a-continuation-for-a-single-antecedent"></a>Tek bir öncül için devamlılık oluşturma

Yöntemini çağırarak, öncül öğesinin tamamlandığında yürütülen bir devamlılık oluşturursunuz <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> . Aşağıdaki örnekte temel desenler gösterilmektedir (açıklık için özel durum işleme atlanır). Bu, `taskA` <xref:System.DayOfWeek> haftanın geçerli gününün adını belirten bir nesne döndüren bir öncül görevini yürütür. Öncül tamamlandığında, devamlılık görevi, öncül öğesini `continuation` geçirdiğini ve sonucunu içeren bir dize görüntüler.

> [!NOTE]
> Bu makaledeki C# örnekleri, `async` yöntemi üzerindeki değiştiriciyi kullanır `Main` . Bu özellik C# 7,1 ve üzeri sürümlerde kullanılabilir. Önceki sürümler [`CS5001`](../../csharp/misc/cs5001.md) Bu örnek kodu derlerken oluşturulur. Dil sürümünü C# 7,1 veya daha yeni bir sürüme ayarlamanız gerekir. Dil sürümünü [yapılandırma sürümünü yapılandırma](../../csharp/language-reference/configure-language-version.md)makalesindeki makaleyi yapılandırma hakkında bilgi edinebilirsiniz.

:::code language="csharp" source="snippets/cs/simple1.cs":::

[!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]

## <a name="create-a-continuation-for-multiple-antecedents"></a>Birden çok öncüllerin için devamlılık oluşturma

Ayrıca, bir görev grubunun herhangi biri veya tümü tamamlandığında çalıştırılacak bir devamlılık oluşturabilirsiniz. Tüm öncül görevler tamamlandığında bir devamlılık yürütmek için statik ( `Shared` Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi veya örnek <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> yöntemi çağırın. Öncül görevlerden herhangi biri tamamlandığında bir devamlılık yürütmek için statik ( `Shared` Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemi veya örnek <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> yöntemi çağırın.

Ve aşırı yüklerine yapılan çağrılar <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> çağıran iş parçacığını engellemez. Ancak, <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> çağıran iş parçacığını engelleyen döndürülen özelliği almak için ve yöntemleri hariç tüm ve yöntemlerini çağırabilirsiniz.

Aşağıdaki örnek, <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> 10 öncül görevlerinin sonuçlarını yansıtan bir devamlılık görevi oluşturmak için yöntemini çağırır. Her öncül görev, birinden 10 ' a değişen bir dizin değeri sağlar. Öncüllerin başarıyla tamamlandıysanız ( <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> özelliği ise <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> ), <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Devamlılık özelliği <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> her öncül tarafından döndürülen değerlerin bir dizisidir. Örnek, bir ve 10 arasındaki tüm sayıların karelerinin toplamını hesaplamak için bunları ekler.

:::code language="csharp" source="snippets/cs/whenall1.cs":::

[!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]

## <a name="continuation-options"></a>Devamlılık seçenekleri

Tek bir görev devamlılığı oluşturduğunuzda, <xref:System.Threading.Tasks.Task.ContinueWith%2A> <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> devamlılığın başladığı koşulları belirtmek için bir sabit listesi değeri alan aşırı yüklemeyi kullanabilirsiniz. Örneğin, Devamlılığın yalnızca öncül işlemi başarıyla tamamlandığında veya hatalı bir durumda tamamlanırsa çalıştırılacağını belirtebilirsiniz. Öncül, devamlılık çağırmaya hazırlandığında koşul doğru değilse, devamlılık doğrudan <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> duruma geçer ve daha sonra başlatılamaz.

Yöntemin aşırı yüklemeleri gibi çok sayıda çoklu görev devamlılık yöntemi <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> de bir <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parametre içerir. Ancak, tüm numaralandırma üyelerinin yalnızca bir alt kümesi <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> geçerlidir. <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType>Numaralandırmada,, ve gibi karşılıkları olan değerleri belirtebilirsiniz <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType> . `NotOn` `OnlyOn` Çoklu görev devamlılığı olan veya seçeneklerden herhangi birini belirtirseniz, çalışma zamanında bir <xref:System.ArgumentOutOfRangeException> özel durum oluşturulur.

Görev devamlılık seçenekleri hakkında daha fazla bilgi için konusuna bakın <xref:System.Threading.Tasks.TaskContinuationOptions> .

## <a name="pass-data-to-a-continuation"></a>Verileri bir devamlıya geçirme

<xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>Yöntemi, öncül öğesine bir başvuruyu bir bağımsız değişken olarak devamlılık Kullanıcı temsilcisine geçirir. Öncül bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesneysa ve görev tamamlanana kadar çalışırsa, devamlılık <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> görevin özelliğine erişebilir.

<xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>Özellik, görev tamamlanana kadar engeller. Ancak, görev iptal edildiyse veya hata olduysa, özelliğe erişmeye çalışmak <xref:System.Threading.Tasks.Task%601.Result%2A> bir <xref:System.AggregateException> özel durum oluşturur. <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion>Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak bu sorundan kaçınabilirsiniz.

:::code language="csharp" source="snippets/cs/result1.cs":::

[!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]

Öncül başarıyla tamamlanmayı çalıştırmadığından bile devamlılığın çalıştırılmasını istiyorsanız özel duruma karşı koruma gerekir. Bir yaklaşım, <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> öncül öğesinin özelliğini test etmek ve yalnızca <xref:System.Threading.Tasks.Task%601.Result%2A> durum veya değilse özelliğe erişmeyi dener <xref:System.Threading.Tasks.TaskStatus.Faulted> <xref:System.Threading.Tasks.TaskStatus.Canceled> . <xref:System.Threading.Tasks.Task.Exception%2A>Öncül öğesinin özelliğini de inceleyebilirsiniz. Daha fazla bilgi için bkz. [özel durum işleme](exception-handling-task-parallel-library.md). Aşağıdaki örnek, önceki örneği yalnızca durumu ise öncül öğesinin özelliğine erişmek için değiştirir <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> .

:::code language="csharp" source="snippets/cs/result2.cs":::

[!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]

## <a name="cancel-a-continuation"></a>Devamlılığını iptal et

<xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType>Devamlılık özelliği <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> aşağıdaki durumlarda olarak ayarlanır:

- <xref:System.OperationCanceledException>İptal isteğine yanıt olarak bir özel durum oluşturur. Herhangi bir görevde olduğu gibi, özel durum devamlılığın geçirildiği aynı belirteci içeriyorsa, birlikte iptalin iptali bildirimi olarak değerlendirilir.
- Devamlılık bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType> <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği olan `true` . Bu durumda, devamlılık başlamaz ve durumuna geçiş yapar <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> .
- Bağımsız değişkeni tarafından ayarlanan koşul karşılanmadığından devamlılık hiçbir şekilde <xref:System.Threading.Tasks.TaskContinuationOptions> çalışmaz. Örneğin, bir öncül bir <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> duruma gittiyse, bu, bu, bu, bu, bu <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> işlem çalışır ancak <xref:System.Threading.Tasks.TaskStatus.Canceled> duruma geçer.

Bir görev ve devamlılık aynı mantıksal işlemin iki parçasını temsil ediyorsa, aşağıdaki örnekte gösterildiği gibi aynı iptal belirtecini her iki göreve da geçirebilirsiniz. Bu, 33 ile bölünebilen tamsayıların bir listesini üreten bir öncül öğesinden oluşur ve bu da devamlıya geçirilir. Devam eden devamlılık listeyi görüntüler. Hem öncül hem de devamlılık rastgele aralıklarla düzenli olarak duraklatılır. Ayrıca, bir <xref:System.Threading.Timer?displayProperty=nameWithType> nesnesi, `Elapsed` beş saniyelik bir zaman aşımı aralığından sonra yöntemi yürütmek için kullanılır. Bu örnek <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> , şu anda yürütülmekte olan görevin yöntemi aramasına neden olan yöntemini çağırır <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> . <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>Öncül veya devamlılık yürütüldüğü zaman yöntemin çağrılmayacağı, rastgele oluşturulan duraklamalar süresine bağlıdır. Öncül iptal edilirse, devamlılık başlamacaktır. Öncül iptal edilmediğinde, belirteç devam etmek için hala kullanılabilir.

:::code language="csharp" source="snippets/cs/cancellation1.cs":::

[!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]

Devamlılığın, devamlılığı oluştururken seçeneği belirtilerek devam eden bir iptal belirteci vermeden iptal edilse de devamlılığın yürütülmesini engelleyebilirsiniz <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> . Aşağıda basit bir örnek verilmiştir.

:::code language="csharp" source="snippets/cs/cancellation2.cs":::

[!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]

Bir devamlılık duruma geçtikten sonra, <xref:System.Threading.Tasks.TaskStatus.Canceled> <xref:System.Threading.Tasks.TaskContinuationOptions> Bu devamlılıklar için belirtilen değere bağlı olarak, izleyen devamlılıkları etkileyebilir.

Bırakılan devamlılık başlamaz.

## <a name="continuations-and-child-tasks"></a>Devamlılıklar ve alt görevler

Bir devamlılık, eklenen alt görevlerinin tümü tamamlanana kadar çalışmaz. Devamlılık, ayrılmış alt görevlerin bitmesini beklemez. Aşağıdaki iki örnek, bir devamlılık oluşturan bir öncül öğesine iliştirilmiş ve bu gruptan ayrılan alt görevleri gösterir. Aşağıdaki örnekte, devamlılık yalnızca tüm alt görevler tamamlandıktan sonra çalışır ve örneği birden çok kez çalıştırarak her seferinde aynı çıktıyı üretir. Bu örnek, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> Varsayılan olarak <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi, varsayılan görevi oluşturma seçeneği olan bir üst görev oluşturduğunda, yöntemi çağırarak öncül öğesini başlatır <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> .

:::code language="csharp" source="snippets/cs/attached1.cs":::

[!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]

Ancak alt görevler öncül öğesinden ayrılımışsa, alt görevlerin durumundan bağımsız olarak öncül sona erer tamamlanmaz devamlılık çalışır. Sonuç olarak, aşağıdaki örnekte birden çok çalıştırma, görev zamanlayıcının her bir alt görevi nasıl ele dığına bağlı olarak değişken çıktı üretebilir.

:::code language="csharp" source="snippets/cs/detached1.cs":::

[!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]

Öncül görevin son durumu, bağlı olan tüm alt görevlerin son durumuna bağlıdır. Ayrılmış alt görevlerin durumu üst öğeyi etkilemez. Daha fazla bilgi için bkz. [ekli ve ayrılmış alt görevler](attached-and-detached-child-tasks.md).

## <a name="associate-state-with-continuations"></a>Durumu Devamlılıklarla ilişkilendir

Rastgele durumu, bir görev devamlılığı ile ilişkilendirebilirsiniz. <xref:System.Threading.Tasks.Task.ContinueWith%2A>Yöntemi, her birinin <xref:System.Object> devamlılık durumunu temsil eden bir değer alan aşırı yüklenmiş sürümler sağlar. Daha sonra özelliği kullanarak bu durum nesnesine erişebilirsiniz <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> . Bu durum nesnesi `null` bir değer sağlamazsanız olur.

Devamlılık durumu, [zaman uyumsuz programlama modeli (APM)](../asynchronous-programming-patterns/asynchronous-programming-model-apm.md) kullanan mevcut kodu tpl 'yi kullanacak şekilde dönüştürdüğünüzde faydalıdır. APM 'de, genellikle **BEGIN**_Method_ yönteminde nesne durumu sağlarsınız ve daha sonra özelliği kullanarak bu duruma erişebilirsiniz <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> . <xref:System.Threading.Tasks.Task.ContinueWith%2A>Yöntemini kullanarak, TPL 'yi kullanmak IÇIN APM kullanan kodu dönüştürürken bu durumu koruyabilirsiniz.

Devamlılık durumu <xref:System.Threading.Tasks.Task> , Visual Studio hata ayıklayıcısındaki nesnelerle çalışırken da yararlı olabilir. Örneğin, **paralel görevler** penceresinde, **görev** sütunu her görev için durum nesnesinin dize gösterimini görüntüler. **Paralel görevler** penceresi hakkında daha fazla bilgi için, bkz. [Görevler penceresini kullanma](/visualstudio/debugger/using-the-tasks-window).

Aşağıdaki örnek, devamlılık durumunun nasıl kullanılacağını göstermektedir. Bir devamlılık görevleri zinciri oluşturur. Her görev, <xref:System.DateTime> yönteminin parametresi için geçerli zamanı (bir nesnesi) sağlar `state` <xref:System.Threading.Tasks.Task.ContinueWith%2A> . Her <xref:System.DateTime> nesne, devamlılık görevinin oluşturulduğu saati temsil eder. Her görev, sonucu <xref:System.DateTime> görevin bittiği süreyi temsil eden ikinci bir nesne olarak üretir. Tüm görevler bittikten sonra bu örnek, oluşturma zamanını ve her devamlılık görevinin bittiği saati görüntüler.

:::code language="csharp" source="snippets/cs/continuationstate.cs":::

[!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]

## <a name="continuations-that-return-task-types"></a>Görev türlerini döndüren devamlılıklar

Bazen bir tür döndüren devamlılık zincirlemesi gerekebilir <xref:System.Threading.Tasks.Task> . Bunlar iç içe geçmiş görevler olarak adlandırılır ve bunlar ortaktır. Bir üst görev çağırdığında <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> , `continuationFunction` <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> `<Task<Task<T>>>` veya `Task(Of Task(Of T))` (Visual Basic) zaman uyumsuz işlemini temsil eden bir ara sunucu görevi oluşturma çağrısını döndüren bir görev sağlar.

Aşağıdaki örnek, ek görevi döndüren işlevleri sarmanın nasıl kullanıldığını gösterir. Her devamlılık, Sarmalanan iç görevi ortaya çıkarmış olabilir.

:::code language="csharp" source="snippets/cs/unwrap.cs":::
:::code language="vb" source="snippets/vb/unwrap.vb":::

Kullanma hakkında daha fazla bilgi için <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> bkz. [nasıl yapılır: iç içe geçmiş bir görevi sarmalama](how-to-unwrap-a-nested-task.md).

## <a name="handle-exceptions-thrown-from-continuations"></a>Devamlılıklardan oluşan özel durumları işle

Öncül-devamlılık ilişkisi üst-alt ilişkisi değildir. Devamlılıklar tarafından oluşturulan özel durumlar, öncül öğesine yayılmaz. Bu nedenle, devamlılıklar tarafından oluşturulan özel durumları aşağıdaki gibi başka bir görevde idare ettiğiniz şekilde işleyin:

- <xref:System.Threading.Tasks.Task.Wait%2A> <xref:System.Threading.Tasks.Task.WaitAll%2A> <xref:System.Threading.Tasks.Task.WaitAny%2A> Devamlılığın bekleneceği,, veya yöntemini ya da genel karşılığına sahip olabilirsiniz. Aşağıdaki örnekte gösterildiği gibi, bir öncül ve devamlılığını aynı `try` deyimde bekleyebilirsiniz.

:::code language="csharp" source="snippets/cs/exception1.cs":::

[!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]

- İlk devamlılık özelliğini gözlemlemek için ikinci devamlılık kullanabilirsiniz <xref:System.Threading.Tasks.Task.Exception%2A> . Aşağıdaki örnekte, bir görev var olmayan bir dosyadan okumaya çalışır. Devamlılık daha sonra, öncül görevde özel durumla ilgili bilgileri görüntüler.

:::code language="csharp" source="snippets/cs/exception2.cs" id="example":::

[!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]

Seçeneğiyle çalıştırıldığı için, <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> devamlılık yalnızca öncül içinde bir özel durum oluşursa ve bu nedenle, öncül özelliğinin özelliğin olmadığını varsayabilir <xref:System.Threading.Tasks.Task.Exception%2A> `null` . Devamlılığın, öncül içinde bir özel durum oluşturulup oluşturulmayacağını yürüttüğünde, <xref:System.Threading.Tasks.Task.Exception%2A> `null` Aşağıdaki kod parçasının gösterdiği gibi, öncül özelliğinin özel durumu işlemeye çalışmadan önce olmadığını denetlemesi gerekir.

:::code language="csharp" source="snippets/cs/exception2.cs" id="exception":::

[!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]

Daha fazla bilgi için bkz. [özel durum işleme](exception-handling-task-parallel-library.md).

- Devamlılık, seçeneği kullanılarak oluşturulan iliştirilmiş bir alt görev ise <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> , diğer tüm bağlı alt bir örnekte olduğu gibi, özel durumları üst öğe tarafından çağıran iş parçacığına yayılır. Daha fazla bilgi için bkz. [ekli ve ayrılmış alt görevler](attached-and-detached-child-tasks.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](task-parallel-library-tpl.md)
