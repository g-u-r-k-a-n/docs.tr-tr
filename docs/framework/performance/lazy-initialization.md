---
title: Yavaş Başlatma
description: Nesne oluşturmanın, nesne ilk kez kullanılana kadar ertelenmesi anlamına gelen bir performans geliştirmesi olan .NET ' te yavaş başlatmayı keşfet.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
ms.openlocfilehash: 6cbda2bd45f2cdc5085ca30af878824069fb019a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242181"
---
# <a name="lazy-initialization"></a>Yavaş Başlatma

Bir nesnenin *geç başlatılması* , oluşturulması ilk kullanılana kadar ertelenmesi anlamına gelir. (Bu konu için, *yavaş başlatma* ve *yavaş örnekleme* terimleri eş anlamlı.) Yavaş başlatma öncelikle performansı artırmak, gereksiz hesaplama önlemek ve program belleği gereksinimlerini azaltmak için kullanılır. Bunlar en yaygın senaryolardır:  
  
- Oluşturmakta maliyetli bir nesneniz varsa ve program bunu kullanmayabilir. Örneğin, bir `Customer` nesne içinde, başlatılacak olan büyük bir nesne dizisi içeren bir özelliği olan bir nesnesi olduğunu varsayalım `Orders` `Order` , bir veritabanı bağlantısı gerektirir. Kullanıcı hiçbir şekilde siparişleri görüntülemeyi veya verileri bir hesaplamada kullanmayı istemez, bu durumda sistem belleğini veya bilgi işlem döngülerini oluşturmak için bir neden yoktur. `Lazy<Orders>` `Orders` Yavaş başlatma için nesneyi bildirmek üzere kullanarak, nesne kullanılmazsa sistem kaynaklarının geri harcanmasını engelleyebilirsiniz.  
  
- Oluşturma maliyetli bir nesneniz varsa ve diğer maliyetli İşlemler tamamlanana kadar oluşturmayı erteleyin. Örneğin, programınızın başladığında birkaç nesne örneği yüklediğini varsayın, ancak yalnızca bir kısmı hemen gereklidir. Gerekli nesneler oluşturuluncaya kadar gerekli olmayan nesneleri başlatmayı erteleyerek programın başlangıç performansını artırabilirsiniz.  
  
 Yavaş başlatma gerçekleştirmek için kendi kodunuzu yazabilseniz de, <xref:System.Lazy%601> bunun yerine kullanmanızı öneririz. <xref:System.Lazy%601> Ayrıca, ilgili türleri iş parçacığı güvenliğini destekler ve tutarlı bir özel durum yayma ilkesi sağlar.  
  
 Aşağıdaki tabloda, farklı senaryolarda yavaş başlatmayı etkinleştirmek için .NET Framework sürüm 4 ' ün sağladığı türler listelenmektedir.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Herhangi bir sınıf kitaplığı veya Kullanıcı tanımlı tür için yavaş başlatma semantiğini sağlayan sarmalayıcı sınıf.|  
|<xref:System.Threading.ThreadLocal%601>|<xref:System.Lazy%601>Buna benzer şekilde, iş parçacığı yerel temelinde yavaş başlatma semantiği sağlar. Her iş parçacığının kendi benzersiz değerine erişimi vardır.|  
|<xref:System.Threading.LazyInitializer>|`static` `Shared` Bir sınıfın ek yükü olmadan nesnelerin yavaş başlatılmasına yönelik gelişmiş (Visual Basic) yöntemler sağlar.|  
  
## <a name="basic-lazy-initialization"></a>Temel yavaş başlatma  

 Geç başlatılmış bir tür tanımlamak için, örneğin, `MyType` `Lazy<MyType>` `Lazy(Of MyType)` Aşağıdaki örnekte gösterildiği gibi (Visual Basic) kullanın. Oluşturucuya hiçbir temsilci geçirilmemişse <xref:System.Lazy%601> , sarmalanmış tür, <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> Value özelliğine ilk erişildiğinde kullanılarak oluşturulur. Türün parametresiz bir Oluşturucusu yoksa, bir çalışma zamanı özel durumu oluşturulur.  
  
 Aşağıdaki örnekte, `Orders` `Order` bir veritabanından alınan nesne dizisini içeren bir sınıf olduğunu varsayalım. Bir `Customer` nesnesi bir örneği içerir `Orders` , ancak kullanıcı eylemlerine bağlı olarak, `Orders` nesnedeki veriler gerekli olmayabilir.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Ayrıca, <xref:System.Lazy%601> oluşturma zamanında sarmalanmış tür üzerinde belirli bir Oluşturucu aşırı yüklemesini çağıran oluşturucuya bir temsilci geçirebilir ve aşağıdaki örnekte gösterildiği gibi gereken diğer başlatma adımlarını gerçekleştirebilirsiniz.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Lazy nesnesi oluşturulduktan sonra, `Orders` <xref:System.Lazy%601.Value%2A> geç değişkeninin özelliğine ilk kez erişilene kadar bir örneği oluşturulmaz. İlk erişimde, Sarmalanan tür oluşturulur ve döndürülür ve gelecekte herhangi bir erişim için depolanır.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 Bir <xref:System.Lazy%601> nesne her zaman ile başlatıldığı nesne veya değeri döndürür. Bu nedenle, <xref:System.Lazy%601.Value%2A> özelliği salt okunurdur. <xref:System.Lazy%601.Value%2A>Bir başvuru türü depoluyorsa, buna yeni bir nesne atayamazsınız. (Ancak, ayarlanabilir ortak alanları ve özellikleri değerini değiştirebilirsiniz.) <xref:System.Lazy%601.Value%2A> Değer türünü saklarsa, değerini değiştiremezsiniz. Bununla birlikte, yeni bağımsız değişkenler kullanarak değişken oluşturucuyu yeniden çağırarak yeni bir değişken oluşturabilirsiniz.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Daha önceki bir gibi yeni bir geç örnek, `Orders` <xref:System.Lazy%601.Value%2A> özelliği ilk kez erişilene kadar örneklemez.  
  
### <a name="thread-safe-initialization"></a>Thread-Safe başlatma  

 Varsayılan olarak, <xref:System.Lazy%601> nesneler iş parçacığı güvenlidir. Diğer bir deyişle, Oluşturucu iş parçacığı güvenliği türünü belirtmezse, <xref:System.Lazy%601> oluşturduğu nesneler iş parçacığı güvenlidir. Çok iş parçacıklı senaryolarda, <xref:System.Lazy%601.Value%2A> iş parçacığı açısından güvenli bir nesnenin özelliğine erişmek için ilk iş parçacığı, <xref:System.Lazy%601> tüm iş parçacıklarında sonraki tüm erişimler için onu başlatır ve tüm iş parçacıkları aynı verileri paylaşır. Bu nedenle, hangi iş parçacığının nesneyi başlattığında ve yarış durumlarının zararsız olması önemlidir.  
  
> [!NOTE]
> Özel durum önbelleğe alma özelliğini kullanarak bu tutarlılığı hata koşullarına genişletebilirsiniz. Daha fazla bilgi için, [yavaş nesnelerdeki özel durumlar](lazy-initialization.md#ExceptionsInLazyObjects)başlıklı sonraki bölüme bakın.  
  
 Aşağıdaki örnek, aynı `Lazy<int>` Örneğin üç ayrı iş parçacığı için aynı değere sahip olduğunu gösterir.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Her iş parçacığında ayrı veriye ihtiyacınız varsa, <xref:System.Threading.ThreadLocal%601> Bu konunun ilerleyen kısımlarında açıklandığı gibi türü kullanın.  
  
 Bazı <xref:System.Lazy%601> oluşturucuların `isThreadSafe` , <xref:System.Lazy%601.Value%2A> özelliğe birden çok iş parçacığından erişip erişmeyeceğini belirtmek için kullanılan adlı bir Boolean parametresi vardır. Özelliğe yalnızca bir iş parçacığından erişmeyi planlıyorsanız, `false` bir ila büyüklükteki performans avantajı elde etmek için geçirin. Özelliğe birden çok iş parçacığından erişmeyi planlıyorsanız, `true` <xref:System.Lazy%601> bir iş parçacığının başlatma zamanında bir özel durum oluşturan yarış koşullarını doğru şekilde işlemesini bildirmek için geçirin.  
  
 Bazı <xref:System.Lazy%601> oluşturucuların adlı bir <xref:System.Threading.LazyThreadSafetyMode> parametresi vardır `mode` . Bu oluşturucular ek bir iş parçacığı güvenliği modu sağlar. Aşağıdaki tabloda, bir nesnenin iş parçacığı güvenliği, <xref:System.Lazy%601> iş parçacığı güvenliğini belirten Oluşturucu parametrelerinden nasıl etkileneceği gösterilmektedir. Her oluşturucunun bu tür bir parametresi vardır.  
  
|Nesnenin iş parçacığı güvenliği|`LazyThreadSafetyMode``mode`parametre|Boolean `isThreadSafe` parametresi|İş parçacığı güvenlik parametresi yok|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Tam iş parçacığı güvenli; tek seferde yalnızca bir iş parçacığı değeri başlatmaya çalışır.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Evet.|  
|İş parçacığı açısından güvenli değildir.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Geçerli değildir.|  
|Tam iş parçacığı güvenli; değeri başlatmak için iş parçacıkları Race.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Geçerli değildir.|Geçerli değildir.|  
  
 Tabloda gösterildiği gibi, <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> parametresi için belirtmek `mode` parametresi için belirtmeyle aynıdır ve belirtme, `true` `isThreadSafe` <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> belirtilerek aynı olur `false` .  
  
 Belirtme <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> , örneği başlatmayı denemek için birden çok iş parçacığının kullanılmasına izin verir <xref:System.Lazy%601> . Bu yarış 'i yalnızca bir iş parçacığı alabilir ve diğer tüm iş parçacıkları başarılı iş parçacığı tarafından başlatılan değeri alır. Başlatma sırasında bir iş parçacığında bir özel durum oluşturulursa, bu iş parçacığı başarılı iş parçacığı tarafından ayarlanan değeri almaz. Özel durumlar önbelleğe alınmaz, bu nedenle özelliğe daha sonra erişme girişimi <xref:System.Lazy%601.Value%2A> başarıyla başlatılmasına neden olabilir. Bu, özel durumların aşağıdaki bölümde açıklanan diğer modlarda ele alındığı yollardan farklıdır. Daha fazla bilgi için bkz <xref:System.Threading.LazyThreadSafetyMode> . sabit listesi.  
  
<a name="ExceptionsInLazyObjects"></a>

## <a name="exceptions-in-lazy-objects"></a>Yavaş nesnelerde özel durumlar  

 Daha önce belirtildiği gibi, bir <xref:System.Lazy%601> nesne her zaman ile başlatıldığı aynı nesne veya değeri döndürür ve bu nedenle <xref:System.Lazy%601.Value%2A> özellik salt okunurdur. Özel durum önbelleğe almayı etkinleştirirseniz bu yaklaşım, özel durum davranışına de genişletilir. Geç başlatılmış bir nesnenin özel durum önbelleğe alma özelliği varsa ve özellik ilk kez erişildiğinde başlatma yönteminden bir özel durum oluşturursa <xref:System.Lazy%601.Value%2A> , bu özelliğe erişmek için sonraki her denemede aynı özel durum oluşturulur <xref:System.Lazy%601.Value%2A> . Diğer bir deyişle, kaydırılmış türdeki Oluşturucu, çok iş parçacıklı senaryolarda bile hiçbir şekilde yeniden çağrılmaz. Bu nedenle, <xref:System.Lazy%601> nesne tek bir erişim üzerinde bir özel durum oluşturmaz ve sonraki erişimde bir değer döndürmez.  
  
 <xref:System.Lazy%601?displayProperty=nameWithType>Bir başlatma yöntemi (parametre) alan herhangi bir Oluşturucu kullandığınızda özel durum önbelleğe alma etkinleştirilir `valueFactory` ; Örneğin, oluşturucuyu kullandığınızda etkinleştirilir `Lazy(T)(Func(T))` . Oluşturucu aynı zamanda bir <xref:System.Threading.LazyThreadSafetyMode> değer ( `mode` parametre) alırsa, veya belirtin <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> . Bir başlatma yöntemi belirtildiğinde, bu iki mod için özel durum önbelleğe alma etkinleştirilir. Başlatma yöntemi çok basit olabilir. Örneğin, `T` `new Lazy<Contents>(() => new Contents(), mode)` C# ' ta veya Visual Basic içinde parametresiz oluşturucuyu çağırabilir `New Lazy(Of Contents)(Function() New Contents())` . <xref:System.Lazy%601?displayProperty=nameWithType>Bir başlatma yöntemi belirtmeyen bir Oluşturucu kullanırsanız, için parametresiz Oluşturucu tarafından oluşturulan özel durumlar `T` önbelleğe alınmaz. Daha fazla bilgi için bkz <xref:System.Threading.LazyThreadSafetyMode> . sabit listesi.  
  
> [!NOTE]
> Oluşturucu parametresi olarak ayarlanmış bir <xref:System.Lazy%601> nesne `isThreadSafe` `false` veya `mode` olarak ayarlanmış Oluşturucu parametresi oluşturursanız <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> , <xref:System.Lazy%601> nesneye tek bir iş parçacığından erişmeniz veya kendi eşitlemesini sağlamanız gerekir. Bu, özel durum önbelleğe alma da dahil olmak üzere nesnenin tüm yönleri için geçerlidir.  
  
 Önceki bölümde belirtildiği gibi, <xref:System.Lazy%601> <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> özel durumları farklı değerlendir belirterek oluşturulan nesneler. İle <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly> , birden çok iş parçacığı örneği başlatmak için rekabet edebilir <xref:System.Lazy%601> . Bu durumda, özel durumlar önbelleğe alınmaz ve <xref:System.Lazy%601.Value%2A> başlatma başarılı olana kadar özelliğe erişim girişimleri devam edebilir.  
  
 Aşağıdaki tabloda, <xref:System.Lazy%601> oluşturucuların özel durum önbelleğe alma yöntemi özetlenmektedir.  
  
|Oluşturucu|İş parçacığı güvenlik modu|Başlatma yöntemini kullanır|Özel durumlar önbelleğe alındı|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Geç (T) ()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Hayır|Hayır|  
|Geç (T) (Func (T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Evet|Evet|  
|Geç (T) (Boole)|`True` ( <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication> ) veya `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Hayır|Hayır|  
|Geç (T) (Func (T), Boolean)|`True` ( <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication> ) veya `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Evet|Evet|  
|Geç (T) (LazyThreadSafetyMode)|Kullanıcı tarafından belirtilen|Hayır|Hayır|  
|Geç (T) (Func (T), LazyThreadSafetyMode)|Kullanıcı tarafından belirtilen|Evet|Kullanıcı belirttiğinde Hayır <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly> ; Aksi takdirde, evet.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Lazy-Initialized özelliği uygulama  

 Yavaş başlatma kullanarak ortak bir özellik uygulamak için, özelliğinin yedekleme alanını bir olarak tanımlayın <xref:System.Lazy%601> ve özelliği <xref:System.Lazy%601.Value%2A> `get` özelliğin erişimcisinde döndürün.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A>Özelliği salt okunurdur; bu nedenle, onu ortaya çıkaran özelliğin `set` erişimcisi yoktur. Bir nesne tarafından desteklenen bir okuma/yazma özelliğine ihtiyacınız varsa <xref:System.Lazy%601> , `set` erişimci yeni bir <xref:System.Lazy%601> nesne oluşturmalı ve bunu yedekleme deposuna atamalıdır. `set`Erişimci, erişimciye geçirilen yeni özellik değerini döndüren bir lambda ifadesi oluşturmalı `set` ve bu lambda ifadesini yeni nesnenin oluşturucusuna geçitirsiniz <xref:System.Lazy%601> . Özelliğin sonraki erişimi, <xref:System.Lazy%601.Value%2A> Yeni ' nin başlatılmasına neden olur <xref:System.Lazy%601> ve <xref:System.Lazy%601.Value%2A> özelliği daha sonra özelliğe atanan yeni değeri döndürür. Bu, bu düzenlemenin nedeni, yerleşik olarak bulunan çok iş parçacıklı korumaların korunmasının nedenidir <xref:System.Lazy%601> . Aksi halde, özellik erişimcileri, özelliği tarafından döndürülen ilk değeri önbelleğe almak <xref:System.Lazy%601.Value%2A> ve yalnızca önbelleğe alınmış değeri değiştirmek ve bunu yapmak için kendi iş parçacığı güvenli kodunuzu yazmanız gerekir. Bir nesne tarafından desteklenen bir okuma/yazma özelliği için gereken ek başlatmalar nedeniyle <xref:System.Lazy%601> , performans kabul edilebilir olmayabilir. Ayrıca, belirli senaryoya bağlı olarak, ayarlayıcılar ve alıcılar arasında yarış durumlarının önüne geçmek için ek koordinasyon gerekebilir.  
  
## <a name="thread-local-lazy-initialization"></a>Thread-Local yavaş başlatma  

 Bazı çok iş parçacıklı senaryolarda, her iş parçacığına kendi özel verilerini vermek isteyebilirsiniz. Bu tür veriler, *iş parçacığı yerel verileri* olarak adlandırılır. .NET Framework sürüm 3,5 ve önceki sürümlerde, `ThreadStatic` özniteliği bir statik değişkene uygulayabilir ve bunu iş parçacığı yerel hale getirebilirsiniz. Ancak, özniteliğini kullanmak, `ThreadStatic` hafif hatalara neden olabilir. Örneğin, temel başlatma deyimleri bile, aşağıdaki örnekte gösterildiği gibi, değişkenin yalnızca ona erişen ilk iş parçacığında başlatılmasına neden olur.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Diğer tüm iş parçacıklarında, değişken varsayılan değeri (sıfır) kullanılarak başlatılır. .NET Framework sürüm 4 ' te bir alternatif olarak, <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> sağladığınız temsilci tarafından tüm iş parçacıklarında başlatılan örnek tabanlı, iş parçacığı yerel bir değişken oluşturmak için türünü de kullanabilirsiniz <xref:System.Action%601> . Aşağıdaki örnekte, erişen tüm iş parçacıkları `counter` başlangıç değerini 1 olarak görür.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> nesnesini <xref:System.Lazy%601> , bu temel farklılıklarla çok benzer şekilde sarmalar:  
  
- Her iş parçacığı, iş parçacığı yerel değişkenini diğer iş parçacıklarından erişilemeyen kendi özel verilerini kullanarak başlatır.  
  
- <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType>Özellik okuma-yazma ' dır ve herhangi bir sayıda değişiklik yapılabilir. Bu, özel durum yaymayı etkileyebilir, örneğin, bir `get` işlem özel durum oluşturabilir, ancak bir sonraki değer değeri başarıyla başlatabilir.  
  
- Başlatma temsilcisi sağlanmazsa, <xref:System.Threading.ThreadLocal%601> türün varsayılan değerini kullanarak sarmalanmış türünü başlatır. Bu şekilde, <xref:System.Threading.ThreadLocal%601> <xref:System.ThreadStaticAttribute> özniteliğiyle tutarlıdır.  
  
 Aşağıdaki örnek, örneğine erişen her iş parçacığının, `ThreadLocal<int>` verilerin kendine ait benzersiz bir kopyasını aldığı gösterilmektedir.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Thread-Local değişkenleri Parallel. for ve ForEach  

 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Veri kaynaklarını paralel olarak yinelemek için yöntemini veya yöntemini kullandığınızda, iş parçacığı yerel verileri için yerleşik desteğe sahip olan aşırı yüklemeleri kullanabilirsiniz. Bu yöntemlerde, iş parçacığı konum oluşturma, verileri oluşturmak, erişmek ve temizlemek için yerel temsilciler kullanılarak elde edilir. Daha fazla bilgi için bkz. [nasıl yapılır: Thread-Local değişkenleriyle paralel. for döngüsü yazma](../../standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) ve [nasıl yapılır: Partition-Local değişkenlerle bir Parallel. foreach döngüsü yazma](../../standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Low-Overhead senaryolar için yavaş başlatma kullanma  

 Çok sayıda nesneyi yavaş başlatmak zorunda olduğunuz senaryolarda, bir içindeki her bir nesnenin <xref:System.Lazy%601> çok fazla bellek veya çok fazla bilgi işlem kaynağı gerektirip gerektirdiğine karar verebilirsiniz. Ya da, yavaş başlatmanın nasıl açığa çıkmasıyla ilgili sıkı gereksinimlere sahip olabilirsiniz. Bu gibi durumlarda, `static` `Shared` <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> sınıfının bir örneğine sarmalamadan her bir nesneyi geç başlatmak için sınıfının (Visual Basic) yöntemlerini kullanabilirsiniz <xref:System.Lazy%601> .  
  
 Aşağıdaki örnekte, tek bir nesnede bir nesnenin tamamını sarmalama yerine `Orders` <xref:System.Lazy%601> `Order` yalnızca gerekli olmaları durumunda ayrı ayrı başlatılan nesneler olduğunu varsayalım.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 Bu örnekte, başlatma yordamının döngünün her tekrarında çağrıldığına dikkat edin. Çok iş parçacıklı senaryolarda, başlatma yordamını çağırmak için ilk iş parçacığı değeri tüm iş parçacıkları tarafından görülen bir alandır. Sonraki iş parçacıkları da başlatma yordamını çağırır, ancak sonuçları kullanılmaz. Bu tür bir olası yarış durumu kabul edilemez ise, ' nin <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> bir Boole bağımsız değişkeni ve bir eşitleme nesnesi alan aşırı yüklemesini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](../../standard/threading/managed-threading-basics.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../standard/threading/threads-and-threading.md)
- [Görev Paralel Kitaplığı (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Nasıl yapılır: Nesnelerin Yavaş Başlatılmasını Gerçekleştirme](how-to-perform-lazy-initialization-of-objects.md)
