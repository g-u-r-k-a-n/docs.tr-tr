---
title: Performans konuları (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 2b116a22c0f422377246d8cc0b2d647fd78a289b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039853"
---
# <a name="performance-considerations-entity-framework"></a>Performans konuları (Entity Framework)
Bu konu, ADO.NET Entity Framework performans özelliklerini açıklar ve Entity Framework uygulamaların performansını artırmaya yardımcı olmak için bazı hususlar sağlar.  
  
## <a name="stages-of-query-execution"></a>Sorgu yürütme aşamaları  
 Entity Framework sorguların performansını daha iyi anlamak için, bir sorgu kavramsal bir modelde yürütüldüğünde oluşan işlemleri anlamak ve verileri nesne olarak döndürmek yararlı olur. Aşağıdaki tabloda bu işlem dizisi açıklanmaktadır.  
  
|Çalışma|Göreli maliyet|Sıklık|Açıklamalar|  
|---------------|-------------------|---------------|--------------|  
|Meta veriler yükleniyor|Düzey|Her uygulama etki alanında bir kez.|Entity Framework tarafından kullanılan model ve eşleme meta verileri bir <xref:System.Data.Metadata.Edm.MetadataWorkspace>yüklenir. Bu meta veriler genel olarak önbelleğe alınır ve aynı uygulama etki alanındaki diğer <xref:System.Data.Objects.ObjectContext> örnekleri için kullanılabilir.|  
|Veritabanı bağlantısı açılıyor|Orta<sup>1</sup>|Gerektiğinde.|Veritabanına açık bir bağlantı değerli bir kaynak kullandığından, Entity Framework açılır ve veritabanı bağlantısını yalnızca gerektiğinde kapatır. Ayrıca bağlantıyı açık bir şekilde açabilirsiniz. Daha fazla bilgi için bkz. [bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).|  
|Görünümler üretiliyor|Yüksek|Her uygulama etki alanında bir kez. (Önceden oluşturulmuş olabilir.)|Entity Framework, kavramsal bir modelde sorgu yürütebilmesi veya veri kaynağına değişiklikleri kaydedebilmek için, veritabanına erişmek üzere bir yerel sorgu görünümleri kümesi oluşturması gerekir. Bu görünümlerin oluşturulması için yüksek maliyetli olduğundan, görünümleri önceden oluşturabilir ve tasarım zamanında projeye ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: sorgu performansını artırmak Için görünümleri önceden oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).|  
|Sorgu hazırlanıyor|Orta<sup>2</sup>|Her benzersiz sorgu için bir kez.|Sorgu komutunu oluşturma, model ve eşleme meta verilerini temel alan bir komut ağacı oluşturma ve döndürülen verilerin şeklini tanımlama maliyetlerini içerir. Artık hem Entity SQL sorgu komutları hem de LINQ sorguları önbelleğe alındığından, aynı sorgunun sonraki yürütmeleri daha az zaman alır. Daha sonraki yürütmeler ve derlenmiş sorgularda bu maliyeti azaltmak için derlenen LINQ sorgularını kullanmaya devam edebilirsiniz ve derlenen sorgular otomatik olarak önbelleğe alınan LINQ sorgularından daha verimli olabilir. Daha fazla bilgi için bkz. [derlenmiş sorgular (LINQ to Entities)](./language-reference/compiled-queries-linq-to-entities.md). LINQ sorgu yürütmesi hakkında genel bilgi için bkz. [LINQ to Entities](./language-reference/linq-to-entities.md). **Note:**  `Enumerable.Contains` işlecini bellek içi koleksiyonlara uygulayan LINQ to Entities sorguları otomatik olarak önbelleğe alınmaz. Ayrıca, derlenen LINQ sorgularında bellek içi koleksiyonlara parametreleştirmeye izin verilmez.|  
|Sorgu Yürütülüyor|Düşük<sup>2</sup>|Her sorgu için bir kez.|ADO.NET veri sağlayıcısı kullanılarak, komutu veri kaynağında yürütme maliyeti. Çoğu veri kaynağı sorgu planlarını aştığından, aynı sorgunun daha sonraki yürütmeleri daha da az zaman alabilir.|  
|Türleri yükleme ve doğrulama|Düşük<sup>3</sup>|Her <xref:System.Data.Objects.ObjectContext> örneği için.|Türler, kavramsal modelin tanımladığı türlere göre yüklenir ve onaylanır.|  
|İzleme|Düşük<sup>3</sup>|Bir sorgunun döndürdüğü her nesne için bir kez. <sup>4</sup>|Bir sorgu <xref:System.Data.Objects.MergeOption.NoTracking> birleştirme seçeneğini kullanıyorsa, bu aşama performansı etkilemez.<br /><br /> Sorgu <xref:System.Data.Objects.MergeOption.AppendOnly>, <xref:System.Data.Objects.MergeOption.PreserveChanges>veya <xref:System.Data.Objects.MergeOption.OverwriteChanges> birleştirme seçeneğini kullanıyorsa sorgu sonuçları <xref:System.Data.Objects.ObjectStateManager>izlenir. Sorgunun döndürdüğü ve <xref:System.Data.Objects.ObjectStateManager><xref:System.Data.Objects.ObjectStateEntry> oluşturmak için kullanılan her izlenen nesne için bir <xref:System.Data.EntityKey> oluşturulur. <xref:System.Data.EntityKey>için mevcut bir <xref:System.Data.Objects.ObjectStateEntry> bulunursa, varolan nesne döndürülür. <xref:System.Data.Objects.MergeOption.PreserveChanges>veya <xref:System.Data.Objects.MergeOption.OverwriteChanges> seçeneği kullanılırsa, nesne döndürülmeden önce güncelleştirilir.<br /><br /> Daha fazla bilgi için bkz. [kimlik çözümleme, durum yönetimi ve değişiklik izleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
|Nesneleri görselleştirme|Orta<sup>3</sup>|Bir sorgunun döndürdüğü her nesne için bir kez. <sup>4</sup>|Döndürülen <xref:System.Data.Common.DbDataReader> nesnesini okuma ve nesne oluşturma ve <xref:System.Data.Common.DbDataRecord> sınıfının her örneğindeki değerleri temel alan özellik değerlerini ayarlama işlemi. Nesne <xref:System.Data.Objects.ObjectContext> zaten varsa ve sorgu <xref:System.Data.Objects.MergeOption.AppendOnly> veya <xref:System.Data.Objects.MergeOption.PreserveChanges> birleştirme seçeneklerini kullanıyorsa, bu aşama performansı etkilemez. Daha fazla bilgi için bkz. [kimlik çözümleme, durum yönetimi ve değişiklik izleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
  
 <sup>1</sup> bir veri kaynağı sağlayıcısı bağlantı havuzunu uygularsa, bir bağlantı açma maliyeti havuza dağıtılır. SQL Server için .NET sağlayıcısı bağlantı kuyruğunu destekler.  
  
 artan sorgu karmaşıklığı sayesinde <sup>2</sup> maliyet artar.  
  
 <sup>3</sup> toplam maliyet, sorgu tarafından döndürülen nesne sayısıyla orantılı olarak artar.  
  
 <sup>4</sup> EntityClient sorguları nesneler yerine bir <xref:System.Data.EntityClient.EntityDataReader> döndürdüğü için bu ek yük, EntityClient sorguları için gerekli değildir. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Ek konular  
 Aşağıda Entity Framework uygulamaların performansını etkileyebilecek diğer noktalar verilmiştir.  
  
### <a name="query-execution"></a>Sorgu Yürütme  
 Sorgular kaynak kullanımı yoğun olabileceğinden, kodunuzun hangi noktada ve bir sorgunun yürütülebileceğini göz önünde bulundurun.  
  
#### <a name="deferred-versus-immediate-execution"></a>Ertelenmiş ve anında yürütme  
 <xref:System.Data.Objects.ObjectQuery%601> veya LINQ sorgusu oluşturduğunuzda sorgu hemen yürütülemeyebilir. Sorgu yürütme, `foreach` (C#) veya`For Each`(Visual Basic) numaralandırması sırasında veya bir<xref:System.Collections.Generic.List%601>koleksiyonunu dolduracak şekilde atandığında, sonuçlar gerekene kadar ertelenir. Sorgu yürütme, bir <xref:System.Data.Objects.ObjectQuery%601> <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> yöntemini çağırdığınızda veya <xref:System.Linq.Enumerable.First%2A> ya da <xref:System.Linq.Enumerable.Any%2A>gibi tek bir sorgu döndüren LINQ metodunu çağırdığınızda hemen başlar. Daha fazla bilgi için bkz. [nesne sorguları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)) ve [sorgu yürütme (LINQ to Entities)](./language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>LINQ sorgularının istemci tarafı yürütmesi  
 Bir LINQ sorgusunun yürütülmesi, veri kaynağını barındıran bilgisayarda gerçekleşse de, bir LINQ sorgusunun bazı kısımları istemci bilgisayarda değerlendirilemeyebilir. Daha fazla bilgi için, [sorgu yürütme (LINQ to Entities)](./language-reference/query-execution.md)konusunun mağaza yürütme bölümüne bakın.  
  
### <a name="query-and-mapping-complexity"></a>Sorgu ve eşleme karmaşıklığı  
 Tek tek sorguların ve varlık modelindeki eşlemenin karmaşıklığı, sorgu performansı üzerinde önemli bir etkiye sahip olacaktır.  
  
#### <a name="mapping-complexity"></a>Eşleme karmaşıklığı  
 Kavramsal modeldeki ve depolama modelindeki tablolardaki varlıklar arasında basit bir bire bir eşleştirmenin daha karmaşık olduğu modeller, bire bir eşlemeye sahip modellerden daha karmaşık komutlar oluşturur.  
  
#### <a name="query-complexity"></a>Sorgu karmaşıklığı  
 Veri kaynağına karşı yürütülen veya büyük miktarda veri döndüren komutlarda çok sayıda birleşim gerektiren sorgular aşağıdaki yollarla performansı etkileyebilir:  
  
- Basit görünen kavramsal bir modele yönelik sorgular, veri kaynağında daha karmaşık sorguların yürütülmesine neden olabilir. Bu durum, Entity Framework bir sorguyu kavramsal bir modelde veri kaynağına karşı eşdeğer bir sorguya çevirdiğinde ortaya çıkabilir. Kavramsal modelde ayarlanan tek bir varlık veri kaynağında birden fazla tabloya eşleniyorsa veya varlıklar arasındaki ilişki bir birleştirme tablosuna eşlendiğinde, veri kaynağı sorgusuna karşı yürütülen sorgu komutu bir veya daha fazla birleşim gerektirebilir.  
  
    > [!NOTE]
    > Belirli bir sorgu için veri kaynağına karşı yürütülen komutları görüntülemek için <xref:System.Data.Objects.ObjectQuery%601> veya <xref:System.Data.EntityClient.EntityCommand> sınıflarının <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> yöntemini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: mağaza komutlarını görüntüleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
- İç içe Entity SQL sorguları sunucuda birleşimler oluşturabilir ve çok sayıda satır döndürebilir.  
  
     Aşağıda, bir izdüşüm yan tümcesindeki iç içe sorgu örneği verilmiştir:  
  
    ```sql  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Bunlara ek olarak, bu tür sorgular sorgu işlem hattının iç içe sorgularda nesneleri çoğaltmasıyla tek bir sorgu oluşturmasına neden olur. Bu nedenle, tek bir sütun birden çok kez yinelenebilir. SQL Server dahil bazı veritabanlarında, bu, TempDB tablosunun çok büyük büyümesine neden olabilir ve bu da sunucu performansını düşürebilir. İç içe sorguları yürüttüğünüzde dikkatli olunmalıdır.  
  
- İstemci, kaynakları sonuç kümesinin boyutuyla orantılı bir şekilde kullanan işlemler yapıyorsa, büyük miktarda veri döndüren sorgular performansın düşmesine neden olabilir. Bu gibi durumlarda, sorgu tarafından döndürülen veri miktarını sınırlandırmaya dikkat etmelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: sorgu sonuçları aracılığıyla sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
 Entity Framework tarafından otomatik olarak oluşturulan komutlar, bir veritabanı geliştiricisi tarafından açıkça yazılmış benzer komutlardan daha karmaşık olabilir. Veri kaynağınıza karşı yürütülen komutlar üzerinde açık denetime ihtiyacınız varsa, tablo değerli bir işlev veya saklı yordam için bir eşleme tanımlamayı düşünün.  
  
#### <a name="relationships"></a>İlişkiler  
 En iyi sorgu performansı için, varlıklar arasındaki ilişkiyi varlık modelinde ilişkiler olarak ve veri kaynağında mantıksal ilişkiler olarak tanımlamanız gerekir.  
  
### <a name="query-paths"></a>Sorgu yolları  
 Varsayılan olarak, bir <xref:System.Data.Objects.ObjectQuery%601>yürüttüğünüzde ilgili nesneler döndürülmez (ancak ilişkilerin kendileri temsil eden nesneler). İlgili nesneleri üç şekilde yükleyebilirsiniz:  
  
1. <xref:System.Data.Objects.ObjectQuery%601> yürütülmeden önce sorgu yolunu ayarlayın.  
  
2. Nesnenin sunduğu gezinti özelliğinde `Load` yöntemini çağırın.  
  
3. <xref:System.Data.Objects.ObjectContext> <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> seçeneğini `true`olarak ayarlayın. [Varlık veri modeli Tasarımcısı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100))ile nesne katmanı kodu oluşturduğunuzda bu otomatik olarak yapılır. Daha fazla bilgi için bkz. [oluşturulan koda genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100)).  
  
 Hangi seçeneği kullanacağınızı göz önünde bulundurdığınızda, veritabanının istek sayısı ile tek bir sorguda döndürülen veri miktarı arasında bir zorunluluğunu getirir olduğunu unutmayın. Daha fazla bilgi için bkz. [Ilgili nesneleri yükleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
#### <a name="using-query-paths"></a>Sorgu yollarını kullanma  
 Sorgu yolları, bir sorgunun döndürdüğü nesnelerin grafiğini tanımlar. Bir sorgu yolu tanımladığınızda, yolun tanımladığı tüm nesneleri döndürmek için yalnızca veritabanına yönelik tek bir istek gereklidir. Sorgu yollarının kullanılması, karmaşık komutların basit nesne sorgularının veri kaynağında yürütülmesine neden olabilir. Bu durum, ilişkili nesneleri tek bir sorguda döndürmek için bir veya daha fazla birleşim gerektiğinden oluşur. Bu karmaşıklık, devralma içeren bir varlık veya çoktan çoğa ilişkiler içeren bir yol gibi karmaşık bir varlık modeline karşı sorgularda daha büyüktür.  
  
> [!NOTE]
> Bir <xref:System.Data.Objects.ObjectQuery%601>tarafından oluşturulacak komutu görmek için <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> yöntemini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: mağaza komutlarını görüntüleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
 Bir sorgu yolu çok fazla ilgili nesne içerdiğinde veya nesneler çok fazla satır verisi içerdiğinde, veri kaynağı sorguyu tamamlayamayabilir. Bu, sorgu, veri kaynağının yeteneklerini aşan ara geçici depolama gerektiriyorsa oluşur. Bu gerçekleştiğinde, ilgili nesneleri açıkça yükleyerek veri kaynağı sorgusunun karmaşıklığını azaltabilirsiniz.  
  
#### <a name="explicitly-loading-related-objects"></a>İlgili nesneleri açıkça yükleme  
 <xref:System.Data.Objects.DataClasses.EntityCollection%601> veya <xref:System.Data.Objects.DataClasses.EntityReference%601>döndüren bir gezinti özelliğinde `Load` yöntemini çağırarak ilgili nesneleri açıkça yükleyebilirsiniz. Nesneleri açıkça yüklemek, `Load` her çağrıldığında veritabanına gidiş dönüş gerektirir.  
  
> [!NOTE]
> döndürülen nesneler koleksiyonu aracılığıyla döngüsü sırasında `Load` çağırırsanız`For Each` (Visual Basic içinde `foreach` ifadesini kullandığınızda), veri kaynağına özgü sağlayıcı tek bir bağlantıda birden çok etkin sonuç kümesini desteklemelidir. SQL Server veritabanı için, sağlayıcı bağlantı dizesinde bir `MultipleActiveResultSets = true` değeri belirtmeniz gerekir.  
  
 Varlıklarda <xref:System.Data.Objects.DataClasses.EntityCollection%601> veya <xref:System.Data.Objects.DataClasses.EntityReference%601> özellikleri yoksa <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> yöntemi de kullanabilirsiniz. Bu, POCO varlıklarını kullanırken faydalıdır.  
  
 İlişkili nesneleri açıkça yükleme, birleştirme sayısını azaltmasını ve gereksiz veri miktarını azaltmasına karşın, `Load` veritabanına yinelenen bir bağlantı gerektirir ve bu da çok sayıda nesne açıkça yüklenirken maliyetli hale gelebilir.  
  
### <a name="saving-changes"></a>Değişiklikler kaydediliyor  
 Bir <xref:System.Data.Objects.ObjectContext><xref:System.Data.Objects.ObjectContext.SaveChanges%2A> yöntemini çağırdığınızda, bağlamdaki her eklenen, güncellenen veya silinen nesne için ayrı bir oluşturma, güncelleştirme veya silme komutu oluşturulur. Bu komutlar veri kaynağında tek bir işlemde yürütülür. Sorgularda olduğu gibi, oluşturma, güncelleştirme ve silme işlemlerinin performansı kavramsal modeldeki eşlemenin karmaşıklığına bağlıdır.  
  
### <a name="distributed-transactions"></a>Dağıtılmış İşlemler  
 Dağıtılmış işlem Düzenleyicisi (DTC) tarafından yönetilen kaynakları gerektiren açık bir işlemdeki işlemler, DTC gerektirmeyen benzer bir işlemden çok daha pahalı olacaktır. DTC 'ye yükseltme aşağıdaki durumlarda meydana gelir:  
  
- SQL Server 2000 veritabanına veya açık işlemleri her zaman DTC 'ye yükseltebileceğiniz diğer veri kaynaklarına karşı bir işlem içeren açık bir işlem.  
  
- Bağlantı Entity Framework tarafından yönetildiğinde 2005 SQL Server karşı bir işlem içeren açık bir işlem. Bu durum SQL Server 2005 bir bağlantı her kapatıldığında bir DTC 'ye ve Entity Framework varsayılan davranış olan tek bir işlem içinde yeniden açıldığı zaman oluşur. SQL Server 2008 kullanılırken bu DTC yükseltmesi gerçekleşmez. SQL Server 2005 kullanırken bu yükseltmeyi önlemek için, işlem içindeki bağlantıyı açıkça açıp kapatmanız gerekir. Daha fazla bilgi için bkz. [bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
 Bir veya daha fazla işlem <xref:System.Transactions> işlem içinde yürütüldüğünde açık bir işlem kullanılır. Daha fazla bilgi için bkz. [bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="strategies-for-improving-performance"></a>Performansı geliştirme stratejileri  
 Aşağıdaki stratejileri kullanarak Entity Framework sorguların genel performansını geliştirebilirsiniz.  
  
#### <a name="pre-generate-views"></a>Görünümleri önceden oluştur  
 Bir uygulama bir sorguyu ilk kez yürüttüğünde, bir varlık modelini temel alan görünümler oluşturmak önemli bir maliyettir. Tasarım sırasında projeye eklenebilen bir Visual Basic veya C# kod dosyası olarak görünümleri önceden oluşturmak Için EdmGen. exe yardımcı programını kullanın. Önceden derlenmiş görünümler oluşturmak için metin şablonu dönüştürme araç takımını da kullanabilirsiniz. Önceden oluşturulan görünümler, belirtilen varlık modelinin geçerli sürümüyle tutarlı olduklarından emin olmak için çalışma zamanında onaylanır. Daha fazla bilgi için bkz. [nasıl yapılır: sorgu performansını artırmak Için görünümleri önceden oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).
  
 Çok büyük modellerle çalışırken aşağıdaki düşünce geçerlidir:  
  
 .NET meta veri biçimi, belirli bir ikilide bulunan Kullanıcı dizesi karakterlerinin sayısını 16.777.215 (0xFFFFFF) olarak sınırlar. Çok büyük bir model için görünümler oluşturuyorsanız ve görünüm dosyası bu boyut sınırına ulaşırsa, "daha fazla kullanıcı dizesi oluşturmak için mantıksal alan kalmadı." ifadesini görürsünüz. derleme hatası. Bu boyut sınırlaması tüm yönetilen ikililer için geçerlidir. Daha fazla bilgi için, büyük ve karmaşık modellerle çalışırken hatanın nasıl önleneceğini gösteren [bloga](https://go.microsoft.com/fwlink/?LinkId=201476) bakın.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Sorgular için NoTracking birleştirme seçeneğini kullanmayı düşünün  
 Nesne bağlamındaki döndürülen nesneleri izlemek için gereken bir maliyet vardır. Nesnelerde yapılan değişiklikler algılanıyor ve aynı mantıksal varlık için birden çok isteğin aynı nesne örneğini döndürmesini sağlamak, nesnelerin bir <xref:System.Data.Objects.ObjectContext> örneğine eklenmesini gerektirir. Nesneler üzerinde güncelleştirme veya silme yapmayı planlamıyorsanız ve kimlik yönetimi gerektirmiyorsa, sorguları yürüttüğünüzde <xref:System.Data.Objects.MergeOption.NoTracking> birleştirme seçeneklerini kullanmayı düşünün.  
  
#### <a name="return-the-correct-amount-of-data"></a>Doğru miktarda veriyi döndür  
 Bazı senaryolarda, veritabanına daha fazla gidiş dönüş gerektirdiğinden <xref:System.Data.Objects.ObjectQuery%601.Include%2A> yöntemi kullanılarak bir sorgu yolu belirtilmesi çok daha hızlıdır. Ancak, diğer senaryolarda, daha az birleştirme içeren daha basit sorgular verilerin artıklığına neden olduğu için ilgili nesneleri yüklemek üzere veritabanına yapılan diğer gidiş dönüş daha hızlı olabilir. Bu nedenle, ilgili nesneleri almak için çeşitli yolların performansını sınamanızı öneririz. Daha fazla bilgi için bkz. [Ilgili nesneleri yükleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
 Tek bir sorguda çok fazla veri döndürmeyi önlemek için sorgunun sonuçlarını daha yönetilebilir gruplar halinde sayfalamayı göz önünde bulundurun. Daha fazla bilgi için bkz. [nasıl yapılır: sorgu sonuçları aracılığıyla sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>ObjectContext kapsamını sınırlandırma  
 Çoğu durumda, bir `using` bildiriminde (`Using…End Using` Visual Basic) <xref:System.Data.Objects.ObjectContext> bir örnek oluşturmalısınız. Bu, kod deyimin bloğundan çıkıldığında nesne bağlamıyla ilişkili kaynakların otomatik olarak atılmasını sağlayarak performansı artırabilir. Ancak, denetimler nesne bağlamı tarafından yönetilen nesnelere bağlandığında, bağlamanın gerekli olduğu ve el ile bırakıldığı sürece <xref:System.Data.Objects.ObjectContext> örneği korunur. Daha fazla bilgi için bkz. [bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Veritabanı bağlantısını el ile açmayı düşünün  
 Uygulamanız, veri kaynağında oluşturma, güncelleştirme ve silme işlemlerini kalıcı hale getirmek için <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> bir dizi sorgu veya sıklıkla çağrı yürüttüğünde, Entity Framework sürekli olarak açılmaları ve veri kaynağına bağlantıyı kapatması gerekir. Bu durumlarda, bu işlemlerin başlangıcında bağlantıyı el ile açmayı ve işlemler tamamlandığında bağlantıyı kapatmayı ya da elden kaldırmayı düşünün. Daha fazla bilgi için bkz. [bağlantıları ve Işlemleri yönetme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="performance-data"></a>Performans Verileri  
 Entity Framework ilişkin bazı performans verileri [ADO.NET ekip blogundan](https://go.microsoft.com/fwlink/?LinkId=91905)aşağıdaki gönderilerde yayımlanır:  
  
- [ADO.NET Entity Framework performansını keşfetme-Bölüm 1](https://go.microsoft.com/fwlink/?LinkId=123907)  
  
- [ADO.NET Entity Framework performansını keşfetme – Bölüm 2](https://go.microsoft.com/fwlink/?LinkId=123909)  
  
- [ADO.NET Entity Framework performans karşılaştırması](https://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme ve Dağıtım Konuları](development-and-deployment-considerations.md)
