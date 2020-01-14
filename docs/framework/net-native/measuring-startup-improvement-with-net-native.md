---
title: .NET Yerel ile Başlangıç İyileştirmesini Hesaplama
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
ms.openlocfilehash: 453159c3fd0590a1ed549bb7e6f8c171aac7d064
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937747"
---
# <a name="measuring-startup-improvement-with-net-native"></a>.NET Yerel ile Başlangıç İyileştirmesini Hesaplama
.NET Native uygulamaların başlatma süresini önemli ölçüde geliştirir. Bu geliştirme, özellikle taşınabilir, düşük güç destekli cihazlarda ve karmaşık uygulamalarla görülür. Bu konu, bu başlangıç geliştirmesini ölçmek için gereken temel araçları kullanmaya başlamanıza yardımcı olur.  
  
 .NET Framework ve Windows, performans araştırmamasını kolaylaştırmak için, uygulamanızın olaylar gerçekleştiğinde araçları bilgilendirmek için olay Izleme (ETW) adlı bir olay çerçevesi kullanır. Daha sonra, ETW olaylarını kolayca görüntülemek ve analiz etmek için PerfView adlı bir araç kullanabilirsiniz. Bu konuda aşağıdakiler açıklanmaktadır:  
  
- Olayları göstermek için <xref:System.Diagnostics.Tracing.EventSource> sınıfını kullanın.  
  
- Bu olayları toplamak için PerfView kullanın.  
  
- Bu olayları görüntülemek için PerfView kullanın.  
  
## <a name="using-eventsource-to-emit-events"></a>Olayları yayma için EventSource kullanma  
 <xref:System.Diagnostics.Tracing.EventSource>, özel olay sağlayıcısı oluşturmak için bir temel sınıf sağlar. Genellikle <xref:System.Diagnostics.Tracing.EventSource> bir alt sınıfı oluşturur ve `Write*` yöntemlerini kendi olay yöntemlerinize sarırsınız. Tek bir model genellikle her bir <xref:System.Diagnostics.Tracing.EventSource>için kullanılır.  
  
 Örneğin, aşağıdaki örnekteki sınıf iki performans özelliğini ölçmek için kullanılabilir:  
  
- `App` sınıf oluşturucusu çağrılana kadar geçen süre.  
  
- `MainPage` Oluşturucu çağrılana kadar geçen süre.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Burada dikkat etmeniz gereken birkaç nokta vardır. İlk olarak, `AppEventSource.Log`içinde tek bir oluşturulur. Bu örnek, tüm günlük kaydı için kullanılacaktır. İkincisi, her olay yönteminin bir <xref:System.Diagnostics.Tracing.EventAttribute>vardır. Bu, <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> yönteminin dizinini `AppEventSource`çağrılan yöntemle ilişkilendirmenize yardımcı olur.  
  
 Bu olayların yalnızca tanım olduğunu unutmayın. Çoğu uygulama kodu, bu olaylardan sonra çalışacaktır. Koddaki hangi olayların kullanıcı etkileşimlerine karşılık geldiğini anlamanız, bunları ölçmenizi ve bu değerlendirmeleri iyileştirmelisiniz. Ayrıca, olaylar zaman içinde yalnızca tek bir örneği günlüğe kaydeder. Her işlem için aynı zamanda başlangıç ve durdurma olaylarını eşleştirmek genellikle yararlıdır. Uygulama başlatma işlemi incelenirken, başlangıç olayı genellikle işletim sisteminin yaydığı "Işlem/başlatma" olayıdır.  
  
 Örneğin, bir RSS okuyucusu oluşturduğunuzu varsayalım. Bir olayı günlüğe kaydetmek için birkaç ilginç konum şunlardır:  
  
- Ana sayfa ilk işlendiğinde.  
  
- Eski RSS hikayeleri yerel depolamadan seri durumdan çıkarılacağından.  
  
- Uygulamanız yeni hikayeleri eşitlemeye başladığında.  
  
- Uygulamanız yeni hikayeleri eşitlemeyi tamamladığında.  
  
 Bir uygulamanın kullanımı basittir: yalnızca türetilmiş sınıfta uygun yöntemi çağırın. Önceki örnekte `AppEventSource` kullanarak bir uygulamayı aşağıdaki şekilde kullanabilirsiniz:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Uygulama görüntülendiğinde, olayları toplamaya hazırsınız demektir.  
  
## <a name="gathering-events-with-perfview"></a>PerfView ile olayları toplama  
 PerfView, uygulamanızdaki tüm performans araştırmaları türlerini yapmanıza yardımcı olması için ETW olaylarını kullanır. Ayrıca, farklı olay türleri için günlüğe kaydetmeyi açmanıza veya kapatmaya olanak sağlayan bir yapılandırma GUI 'si de içerir. PerfView ücretsiz bir araçtır ve [Microsoft Indirme merkezi](https://www.microsoft.com/download/details.aspx?id=28567)' nden indirilebilir. Daha fazla bilgi için [PerfView öğretici videolarını](https://channel9.msdn.com/Series/PerfView-Tutorial)izleyin.  
  
> [!NOTE]
> , ARM sistemlerinde olayları toplamak için PerfView kullanılamaz. ARM sistemlerinde olayları toplamak için Windows performans Kaydedicisi 'Ni (WPR) kullanın. Daha fazla bilgi için bkz. [Vance Morrison 'un blog gönderisi](https://docs.microsoft.com/archive/blogs/vancem/collecting-etwperfview-data-on-an-windows-rt-winrt-arm-surface-device).  
  
 Ayrıca, komut satırından PerfView öğesini çağırabilirsiniz. Yalnızca sağlayıcınızdaki olayları günlüğe kaydetmek için komut Istemi penceresini açın ve şu komutu girin:  
  
```console
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 burada:  
  
 `-KernelEvents:Process`  
 İşlemin ne zaman başlayacağını ve durdurduğunu bilmesini istediğinizi belirtir. Uygulamanız için Işlem/başlangıç olayına gerek duyarsınız, bu nedenle diğer olay sürelerinin üzerinden çıkarılabilir.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 PerfView 'ın varsayılan olarak açtığı diğer sağlayıcıları kapatır ve MyCompany-MyApp sağlayıcısını açar.  (Yıldız işareti bir <xref:System.Diagnostics.Tracing.EventSource>olduğunu gösterir.)  
  
 `collect outputFile`  
 Koleksiyonu başlatmak ve verileri ÇıktıDosyası. etl. zip ' e kaydetmek istediğinizi belirtir.  
  
 PerfView 'ı başlattıktan sonra uygulamanızı çalıştırın. Uygulamanızı çalıştırırken dikkat etmeniz gereken birkaç nokta vardır:  
  
- Hata ayıklama derlemesi değil, yayın derlemesi kullanın. Hata ayıklama derlemeleri genellikle uygulamanızın beklenenden daha yavaş çalışmasına neden olabilecek ek hata denetimi ve hata işleme kodu içerir.  
  
- Uygulamanızı bir hata ayıklayıcı ekli olarak çalıştırmak uygulamanızın performansını etkiler.  
  
- Windows, uygulama başlatma sürelerini hızlandırmak için birden çok önbelleğe alma stratejisi kullanır. Uygulamanız Şu anda bellekte önbelleğe alınmışsa ve diskten yüklenmesi gerekiyorsa daha hızlı başlayacaktır. Tutarlılığı sağlamak için uygulamanızı ölçmeye başlamadan birkaç kez başlatın ve kapatın.  
  
 PerfView 'un yayınlanan olayları toplayabilmesi için uygulamanızı çalıştırdığınızda, **toplamayı durdur** düğmesini seçin. Genellikle, gereksiz olayları almadan uygulamanızı kapatmadan önce toplamayı durdurmanız gerekir. Ancak, kapalı veya askıya alma performansını ölçyorsanız, koleksiyona devam etmek isteyeceksiniz.  
  
## <a name="displaying-the-events"></a>Olayları görüntüleme  
 Zaten toplanmış olan olayları görüntülemek için PerfView komutunu kullanarak oluşturduğunuz. etl veya. etl. zip dosyasını açın ve **Olaylar**' ı seçin. ETW, diğer süreçlerdeki olaylar da dahil olmak üzere çok sayıda olay hakkında bilgi toplamıştır. Araştırmanızı odaklamak için Olaylar görünümünde aşağıdaki metin kutularını doldurun:  
  
- **Işlem filtresi** kutusunda uygulamanızın adını (". exe" olmadan) belirtin.  
  
- **Olay türleri filtre** kutusunda, `Process/Start | MyCompany-MyApp`belirtin. Bu, MyCompany-MyApp ve Windows Kernel/Process/start olaylarından olaylar için bir filtre ayarlar.  
  
 Sol bölmede listelenen tüm olayları seçin (CTRL-A) ve **ENTER** tuşunu seçin. Şimdi, her bir olaydan gelen zaman damgalarını görebilmeniz gerekir. Bu zaman damgaları izlemenin başlangıcına göre yapılır, bu nedenle başlangıçtan itibaren geçen süreyi belirlemek için her bir olayın süresini işlemin başlangıç zamanından çıkarabilirsiniz. İki zaman damgasını seçmek için CTRL + tıklama kullanırsanız, sayfanın altındaki durum çubuğunda görüntülenmeleri arasındaki farkı görürsünüz. Bu, ekranda iki olay arasında geçen süreyi görmeyi kolaylaştırır (işlem başlangıcı dahil). Görünümün kısayol menüsünü açabilir ve verileri kaydetmek veya işlemek üzere CSV dosyalarına dışarı aktarma veya Microsoft Excel 'i açma gibi faydalı seçeneklerden seçim yapabilirsiniz.  
  
 Hem özgün uygulamanız hem de .NET Native araç zinciri kullanarak oluşturduğunuz sürüm için yordamı tekrarlayarak, performans farkını karşılaştırabilirsiniz.   .NET Native uygulamalar genellikle non-.NET Native uygulamalardan daha hızlı başlar. Daha ayrıntılı bir şekilde ilgileniyorsanız, PerfView kodunuzun en çok geçen kısmını da tanımlayabilir. Daha fazla bilgi için [PerfView öğreticileri](https://channel9.msdn.com/Series/PerfView-Tutorial) Izleyin veya [Vance Morrison 'un blog girişini](https://docs.microsoft.com/archive/blogs/vancem/publication-of-the-perfview-performance-analysis-tool)okuyun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Tracing.EventSource>
