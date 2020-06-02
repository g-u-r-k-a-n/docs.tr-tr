---
title: Çöp Toplama ve Performans
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 1d9c72a64d172dcadf1bff1b1edf3050ca5f7d05
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287629"
---
# <a name="garbage-collection-and-performance"></a>Çöp Toplama ve Performans

Bu konuda çöp toplama ve bellek kullanımı ile ilgili sorunlar açıklanmaktadır. Yönetilen yığınla ilgili sorunları ele alır ve çöp toplamanın uygulamalarınız üzerindeki etkisinin nasıl en aza indirgenebileceğini açıklar. Her başlıkta, problemleri araştırmak için kullanabileceğiniz prosedürlerin bağlantıları yer alır.

## <a name="performance-analysis-tools"></a>Performans Analiz Araçları

Aşağıdaki bölümlerde, bellek kullanımı ve çöp toplama sorunlarını araştırmak için kullanılabilen araçlar açıklanmaktadır. Bu konunun ilerleyen kısımlarında sunulan [yordamlar](#performance-check-procedures) Bu araçlara başvurur.

### <a name="memory-performance-counters"></a>Bellek Performans Sayaçları

Performans verilerini toplamak için performans sayaçlarını kullanabilirsiniz. Yönergeler için bkz. [çalışma zamanı profili oluşturma](../../framework/debug-trace-profile/runtime-profiling.md). Performans sayaçlarının .NET CLR bellek kategorisi, [.NET Framework performans sayaçları](../../framework/debug-trace-profile/performance-counters.md)bölümünde açıklandığı gibi, çöp toplayıcı hakkında bilgi sağlar.

### <a name="debugging-with-sos"></a>SOS ile hata ayıklama

Yönetilen yığında nesneleri incelemek için [Windows hata ayıklayıcı (WinDbg)](/windows-hardware/drivers/debugger/index) kullanabilirsiniz.

WinDbg 'yi yüklemek için, [Windows Için hata ayıklama araçları 'Nı karşıdan yükle](/windows-hardware/drivers/debugger/debugger-download-tools) sayfasından Windows Için hata ayıklama araçları 'nı yükleyin.

### <a name="garbage-collection-etw-events"></a>Çöp Toplama ETW Olayları

Windows için olay izleme (ETW), .NET Framework tarafından sağlanan ve profil oluşturma ile hata ayıklama desteğini tamamlayan bir izleme sistemidir. .NET Framework 4 ' ten başlayarak, [atık toplama ETW olayları](../../framework/performance/garbage-collection-etw-events.md) , yönetilen yığının istatistiksel bir görünüm noktasından çözümlenmesi için yararlı bilgiler yakalar. Örneğin, çöp toplama olayı gerçekleşmek üzereyken oluşturulan `GCStart_V1` olayı, aşağıdaki bilgileri sağlar:

- Hangi nesne neslinin toplandığı.

- Çöp toplama işlemini neyin tetiklediği.

- Çöp toplama işleminin türü (eşzamanlı veya eşzamansız).

ETW olay günlüğü verimlidir ve çöp toplamayla ilgili hiçbir performans sorununu gizlemez. Bir işlem, ETW olaylarıyla birlikte kendi olaylarını sağlayabilir. Günlüğe kaydedildiğinde, yığın problemlerinin nasıl ve ne zaman oluştuğunu belirlemek için hem uygulamanın olayları hem de çöp toplama olayları eşleştirilebilir. Örneğin bir sunucu uygulaması, olayları bir istemci isteğinin başında ve sonunda sağlayabilir.

### <a name="the-profiling-api"></a>Profil oluşturma API 'SI

Ortak dil çalışma zamanı (CLR) profil oluşturma arabirimleri, çöp toplama işlemi sırasında etkilenen nesneler hakkında detaylı bilgi sağlar. Bir çöp toplama işlemi başladığında ve bittiğinde bir profil oluşturucu bildirim alabilir. Her nesildeki nesnelerin bir tanımlaması dahil olmak üzere yönetilen yığındaki nesneler hakkında raporlar sağlayabilir. Daha fazla bilgi için bkz. [profil oluşturma genel bakış](../../framework/unmanaged-api/profiling/profiling-overview.md).

Profil oluşturucular kapsamlı bilgi sağlayabilir. Ancak karmaşık profil oluşturucular, bir uygulamanın davranışını değiştirebilir.

### <a name="application-domain-resource-monitoring"></a>Uygulama Etki Alanı Kaynak İzleme

.NET Framework 4 ' te başlayarak, uygulama etki alanı kaynak izleme (ARM), ana bilgisayarların uygulama etki alanı tarafından CPU ve bellek kullanımını izlemesini sağlar. Daha fazla bilgi için bkz. [uygulama etki alanı kaynak izleme](app-domain-resource-monitoring.md).

## <a name="troubleshooting-performance-issues"></a>Performans Sorunlarını Giderme

İlk adım, [sorunun gerçekten çöp toplama olup olmadığını belirlemektir](#IsGC). Eğer sorunun bu olduğunu belirlerseniz, aşağıdaki listeden sorunu gidermeyi seçin.

- [Yetersiz bellek özel durumu oluşturuldu](#Issue_OOM)

- [İşlem çok fazla bellek kullanıyor](#Issue_TooMuchMemory)

- [Çöp toplayıcı nesneleri yeterince hızlı geri kazanmıyor](#Issue_NotFastEnough)

- [Yönetilen yığın çok parçalanmış](#Issue_Fragmentation)

- [Çöp toplama duraklamaları çok uzun](#Issue_LongPauses)

- [Nesil 0 çok büyük](#Issue_Gen0)

- [Çöp toplama sırasında CPU kullanımı çok yüksek](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Sorun: Bir Yetersiz Bellek Özel Durumu Oluşturuldu

Yönetilen bir <xref:System.OutOfMemoryException> oluşturulması için iki meşru durum vardır:

- Sanal bellek tükeniyor.

  Çöp toplayıcısı önceden belirlenmiş bir boyutun segmentlerindeki sistemden bellek ayırır. Eğer bir ayırma işlemi için ek bir segment gerekirse, ancak işlemin sanal bellek alanının bitişiğinde boş bir blok kalmamışsa, yönetilen yığın için ayırma başarısız olur.

- Ayrılacak yeterli fiziksel belleğe sahip olmama.

|Performans denetimleri|
|------------------------|
|[Yetersiz bellek özel durumunun yönetilip yönetilmediğini belirleme.](#OOMIsManaged)<br /><br /> [Ne kadar sanal bellek ayrılacağını belirleme.](#GetVM)<br /><br /> [Yeterli fiziksel bellek olup olmadığını belirleme.](#Physical)|

Özel durumun meşru olmadığını belirlerseniz, aşağıdaki bilgilerle Microsoft Müşteri Hizmetleri ve Destek birimiyle iletişime geçin:

- Yönetilen yetersiz bellek özel durumu olan yığın.

- Tam bellek dökümü.

- Sanal veya fiziksel belleğin bir sorun olmadığını gösteren veriler dahil olmak üzere, meşru bir yetersiz bellek özel durumu olmadığını kanıtlayan veriler.

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a>Sorun: İşlem Çok Fazla Bellek Kullanıyor

Yaygın bir varsayım, Windows Görev Yöneticisi 'nin **performans** sekmesindeki bellek kullanımının çok fazla bellek kullanıldığını gösterebilir. Ancak, bu ekran çalışan kümeyle ilgilidir; sanal bellek kullanımı hakkında bilgi sağlamaz.

Eğer sorunun yönetilen yığından kaynaklı olduğunu belirlerseniz, herhangi bir düzen olup olmadığını belirlemek için yönetilen yığını zamanla ölçmeniz gerekir.

Eğer problemin yönetilen yığından kaynaklanmadığını belirlerseniz, yerel hata ayıklama kullanmanız gerekir.

|Performans denetimleri|
|------------------------|
|[Ne kadar sanal bellek ayrılacağını belirleme.](#GetVM)<br /><br /> [Yönetilen yığının ne kadar bellek kullandığını saptayın.](#ManagedHeapCommit)<br /><br /> [Yönetilen yığının ne kadar bellek ayırdığını belirleme.](#ManagedHeapReserve)<br /><br /> [2. nesil büyük nesneleri belirleme.](#ExamineGen2)<br /><br /> [Nesnelere başvuruları belirleme.](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Sorun: Atık Toplayıcısı Nesneleri Yeterince Hızlı Geri Kazanmıyor

Çöp toplama işlemi için nesnelerin beklendiği kadar hızlı geri kazanılmadığı anlaşıldığında, bu nesnelere yapılan güçlü atıflar olup olmadığını belirlemeniz gerekir.

Etkin olmayan nesneye ait sonlandırıcının çalıştırılmadığını gösteren etkin olmayan bir nesne içeren nesilde hiç çöp toplama olmaması durumunda da bu sorunla karşılaşabilirsiniz. Örneğin, bir tek iş parçacıklı bölme (STA) uygulamasını çalıştırdığınızda ve sonlandırıcı sıraya hizmet veren iş parçacığı bu uygulamaya çağrılamadığında mümkün olur.

|Performans denetimleri|
|------------------------|
|[Nesnelere başvuruları denetleyin.](#ObjRef)<br /><br /> [Sonlandırıcının çalıştırılıp çalıştırılmadığını belirleme.](#Induce)<br /><br /> [Sonlandırılmayı bekleyen nesneler olup olmadığını belirleme.](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a>Sorun: Yönetilen Yığın Çok Parçalanmış

Parçalanma düzeyi, boş alanın nesil için ayrılan toplam belleğe oranı olarak hesaplanır. Nesil 2 için, kabul edilebilir parçalanma düzeyi %20'den fazla değildir. Nesil 2 çok fazla büyüyebildiğinden, parçalanma oranı mutlak değerden daha önemlidir.

Nesil 0, yeni nesnelerin ayrıldığı nesil olduğundan, içerisinde fazla boş alan olması problem değildir.

Parçalanma, sıkıştırılmış olmadığından her zaman büyük nesne yığınında oluşur. Bitişik olan boş nesneler, büyük nesne ayırma isteklerini karşılamak için doğal olarak tek bir boşluk içine daraltılır.

Nesil 1 ve nesil 2'de parçalanma bir sorun olabilir. Eğer bu nesiller çöp toplama sonrasında büyük bir boş alana sahipse, uygulamanın nesne kullanımının değiştirilmesi gerekebilir ve uzun zamanlı nesnelerin kullanım sürelerini yeniden değerlendirmeyi göz önünde bulundurmanız gerekir.

Aşırı nesne sabitlenmesi parçalanmayı arttırabilir. Parçalama yüksekse çok fazla nesne sabitlenmiş olabilir.

Sanal belleğin parçalanması toplamanın segment eklemesini engelliyorsa, bunun sebebi aşağıdakilerden biri olabilir:

- Birçok küçük derlemenin sık sık yüklenmesi ve kaldırılması.

- Yönetilemeyen kodla karşılıklı çalışılırken COM nesnelerinde çok fazla atıf tutulması.

- Büyük nesne yığınının sık sık yığın segmentlerinin ayrılmasına ve boşaltılmasına neden olan büyük geçici nesnelerin oluşturulması.

  Bir uygulama CLR'yi barındırdığı sırada çöp toplayıcıdan segmentlerini tutmasını isteyebilir. Bu, segment ayırma sıklığını azaltır. Bu, [startup_flags numaralandırmasında](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md)STARTUP_HOARD_GC_VM bayrağı kullanılarak gerçekleştirilir.

|Performans denetimleri|
|------------------------|
|[Yönetilen yığında boş alan miktarını belirleme.](#Fragmented)<br /><br /> [Sabitlenmiş nesne sayısını belirleme.](#Pinned)|

Eğer parçalanma için meşru bir neden olmadığını düşünüyorsanız, Microsoft Müşteri Hizmetleri ve Destek'le iletişime geçin.

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a>Sorun: Atık Toplama Duraksamaları Çok Uzun

Çöp toplama gerçek zamanlı olarak çalıştığından, bir uygulamanın bazı duraklamalara izin vermesi gerekir. Yazılımsal olarak gerçek zamanlı çalışmanın bir kriteri, işlemlerin %95'inin zamanında bitmesi gerektiğidir.

Eşzamanlı çöp toplamada, bir toplama işlemi sırasında yönetilen iş parçacıklarının çalışmasına izin verilir, bu ise çok az duraklama olacağı anlamına gelir.

Kısa ömürlü çöp toplama işlemleri (nesil 0 ve 1) yalnızca birkaç milisaniye sürdüğünden, duraksamaların azaltılması genellikle mantıklı değildir. Ancak, bir uygulama tarafından yapılan ayırma isteklerinin düzenini değiştirerek nesil 2 koleksiyonlarındaki duraksamaları azaltabilirsiniz.

Diğer bir, daha doğru yöntem ise [çöp toplama ETW olaylarını](../../framework/performance/garbage-collection-etw-events.md)kullanmaktır. Bir olay dizisine ait zaman damgalarının farklarını ekleyerek koleksiyonlar için zamanlamaları bulabilirsiniz. Tüm koleksiyon dizisi, yürütme altyapısının askıya alınmasını, çöp toplamanın kendisini ve yürütme altyapısının sürdürülmesini içerir.

Bir sunucunun bir nesil 2 koleksiyonuna sahip olup olmadığını ve başka bir sunucuya yeniden yönlendirme isteklerinin duraklamalar ile ilgili sorunları kolayca yapıp yapmadığını anlamak için [çöp toplama bildirimlerini](notifications.md) kullanabilirsiniz.

|Performans denetimleri|
|------------------------|
|[Çöp koleksiyonundaki sürenin uzunluğunu belirleme.](#TimeInGC)<br /><br /> [Çöp toplamaya neyin neden olduğunu belirleme.](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a>Sorun: Nesil 0 Çok Büyük

Özellikle iş istasyonu çöp toplama yerine sunucu çöp toplamayı kullandığınızda, nesil 0, 64 bit bir sistem üzerinde genellikle çok sayıda nesneye sahip olur. Bunun sebebi, bir nesil 0 atık temizleme işlemini tetikleme eşiğinin bu ortamlarda daha yüksek olması ve nesil 0 toplama işlemlerinin çok daha fazla büyüyebilecek olmasıdır. Bir çöp toplama tetiklenmeden önce bir uygulama daha fazla bellek ayırırsa performans artar.

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Sorun: Bir Atık Toplama İşlemi Sırasında CPU Kullanımı Çok Yüksek

Çöp toplama sırasında CPU kullanımı yüksek olacaktır. Eğer bir çöp toplama işlemi sırasında önemli miktarda işlem süresi harcanırsa, toplama işlemi çok sık gerçekleşiyordur veya çok uzun sürüyordur. Yönetilen yığındaki nesnelerin arttırılmış ayırma oranı, çöp toplamanın daha sık gerçekleşmesine neden olur. Ayırma oranının azaltılması çöp toplamaların sıklığını azaltır.

`Allocated Bytes/second` performans sayacını kullanarak ayırma oranlarını izleyebilirsiniz. Daha fazla bilgi için [.NET Framework performans sayaçları](../../framework/debug-trace-profile/performance-counters.md)bölümüne bakın.

Bir koleksiyonun süresi, öncelikle ayırma sonrası varlığını sürdüren nesnelerin sayısında bir etmendir. Toplanacak çok nesne kaldıysa çöp toplayıcının büyük miktarda belleği gözden geçirmesi gerekir. Dışarıda kalanların sıkıştırılması, zaman alan bir işlemdir. Bir toplama sırasında kaç nesnenin işlendiğini belirlemek için belirli bir nesle yönelik bir çöp toplamanın sonundaki hata ayıklayıcıda bir kesme noktası ayarlayın.

|Performans denetimleri|
|------------------------|
|[Yüksek CPU kullanımının çöp toplamadan kaynaklanıp kaynaklanmadığını belirleme.](#HighCPU)<br /><br /> [Çöp toplamanın sonunda bir kesme noktası ayarlayın.](#GenBreak)|

## <a name="troubleshooting-guidelines"></a>Sorun Giderme Kılavuzları

Bu bölümde, araştırmalarınıza başlamadan önce göz önünde bulundurmanız gereken yönergeler açıklanmaktadır.

### <a name="workstation-or-server-garbage-collection"></a>İş İstasyonu veya Sunucu Atık Toplama

Doğru çöp toplama türünü kullanıp kullanmadığınızı belirleyin. Uygulamanız birden çok iş parçacığı ve nesne örneği kullanıyorsa, iş istasyonu çöp toplama yerine sunucu çöp toplama kullanın. İş istasyonu çöp toplama, bir uygulamanın birden çok örneğinin kendi çöp toplama iş parçacıklarını çalıştırmasını ve CPU süresi için birbirleriyle yarışmasını gerektirirken sunucu çöp toplama, birden çok iş parçacığında çalışır.

Bir hizmet gibi düşük yüke sahip ve arka planda seyrek olarak çalışan bir uygulama, eşzamanlı çöp toplama özelliği devre dışı bırakılmış iş istasyonu çöp toplamayı kullanabilir.

### <a name="when-to-measure-the-managed-heap-size"></a>Yönetilen Yığın Boyutu Ne Zaman Ölçülmeli

Bir profil oluşturucu kullanmıyorsanız, performans sorunlarını etkili bir biçimde tanılamak için tutarlı bir ölçüm düzeni oluşturmanız gerekecektir. Bir zamanlama oluşturmak için aşağıdaki noktaları göz önünde bulundurun:

- Bir nesil 2 çöp toplamanın ardından ölçerseniz, yönetilen bütün yığın atıktan arınmış olacaktır (etkin olmayan nesneler).

- Bir nesil 0 çöp toplamanın hemen ardından ölçerseniz nesil 1 ve 2'deki nesneler henüz toplanmamış olacaktır.

- Bir çöp toplamadan hemen önce ölçerseniz, çöp toplama başlamadan önce mümkün olduğunca fazla ayırmayı ölçersiniz.

- Çöp toplama veri yapıları gezinme için geçerli bir durumda olmadığından ve size tam sonuçlar vermeyebileceğinden çöp toplama sırasında ölçüm yapmak çeşitli sorunlara yol açar. Bu tasarım gereğidir.

- Eşzamanlı çöp toplama özellikli iş istasyonu çöp toplama kullandığınızda, geri kazanılan nesneler sıkıştırılmayacağından, yığın boyutu aynı veya daha büyük olabilir (parçalanma boyutu daha büyük gösterebilir).

- Nesil 2'deki eşzamanlı çöp toplama, fiziksel bellek yükü çok fazla olduğunda geciktirilir.

Aşağıdaki yordam, yönetilen yığını ölçmek için nasıl bir kesme noktası ayarlayacağınızı açıklar.

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Çöp toplamanın sonunda bir kesme noktası ayarlamak için

- SOS hata ayıklama uzantısı yüklü olan WinDbg'lerde aşağıdaki komutu yazın:

  **BP mscorwks! WKS:: GCHeap:: Restart "j (DWO) (mscorwks! WKS:: GCHeap:: GcCondemnedGeneration) = = 2) ' KB '; ' g ' "**

  Burada **GcCondemnedGeneration** , istenen nesil olarak ayarlanmıştır. Bu komut özel simgeler gerektirir.

  Bu komut, derleme 2 nesneleri atık toplama için geri alındıktan sonra, **restart** yürütüldüğünde kesmeyi zorlar.

  Sunucu çöp toplama işleminde, yalnızca bir iş parçacığı **yeniden**çağırır. bu nedenle kesme noktası yalnızca 2. nesil atık toplama sırasında gerçekleşir.

## <a name="performance-check-procedures"></a>Performans Denetim Prosedürleri

Bu bölümde, performans sorunlarınızın sebeplerini ortadan kaldırmak için aşağıdaki yordamlar açıklanmaktadır:

- [Sorunun çöp toplamadan kaynaklanıp kaynaklanmadığını belirleme.](#IsGC)

- [Yetersiz bellek özel durumunun yönetilip yönetilmediğini belirleme.](#OOMIsManaged)

- [Ne kadar sanal bellek ayrılacağını belirleme.](#GetVM)

- [Yeterli fiziksel bellek olup olmadığını belirleme.](#Physical)

- [Yönetilen yığının ne kadar bellek kullandığını saptayın.](#ManagedHeapCommit)

- [Yönetilen yığının ne kadar bellek ayırdığını belirleme.](#ManagedHeapReserve)

- [2. nesil büyük nesneleri belirleme.](#ExamineGen2)

- [Nesnelere başvuruları belirleme.](#ObjRef)

- [Sonlandırıcının çalıştırılıp çalıştırılmadığını belirleme.](#Induce)

- [Sonlandırılmayı bekleyen nesneler olup olmadığını belirleme.](#Finalize)

- [Yönetilen yığında boş alan miktarını belirleme.](#Fragmented)

- [Sabitlenmiş nesne sayısını belirleme.](#Pinned)

- [Çöp koleksiyonundaki sürenin uzunluğunu belirleme.](#TimeInGC)

- [Ne bir çöp toplama tetikleyeceğini belirleme.](#Triggered)

- [Yüksek CPU kullanımının çöp toplamadan kaynaklanıp kaynaklanmadığını belirleme.](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Sorunun çöp toplamadan kaynaklanıp kaynaklanmadığını belirlemek için

- Şu iki bellek performans sayacını inceleyin:

  - **GC 'de% Time**. Son çöp toplama döngüsünden sonra gerçekleşen bir çöp toplamaya harcanan süresinin yüzdesini gösterir. Bu sayacı kullanarak çöp toplayıcısının yönetilen yığın alanı açmak için ne kadar süre harcadığını belirleyebilirsiniz. Eğer çöp toplamaya harcanan süre göreceli olarak düşükse, bu, yönetilen yığın dışında bir kaynak problemi olduğunu gösteriyor olabilir. Bu sayaç, süreçte eş zamanlı veya arka plan çöp toplama işlemleri varsa düzgün olmayabilir.

  - **Toplam kaydedilmiş bayt**sayısı. Çöp toplayıcısı tarafından o an yürütülen sanal bellek miktarını gösterir. Bu sayacı kullanarak çöp toplayıcı tarafından uygulamanızın kullandığı belleğin aşırı bir kısmının kullanılıp kullanılmadığını belirleyebilirsiniz.

  Çoğu bellek performans sayacı her çöp toplamanın sonunda güncelleştirilir. Bu nedenle, hakkında bilgi almak istediğiniz geçerli koşulları yansıtmayabilir.

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Yetersiz bellek özel durumunun yönetilip yönetilmediğini belirlemek için

1. SOS hata ayıklayıcı uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında, yazdırma özel durumu (**PE**) komutunu yazın:

    **! PE**

    Eğer özel durum yönetiliyorsa, aşağıdaki örnekte gösterildiği gibi, istisna türü <xref:System.OutOfMemoryException> olarak gösterilir.

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. Eğer çıktıda bir özel durum belirtilmezse, bellek yetmezliği özel durumunun hangi iş parçacığından kaynaklandığını belirlemeniz gerekir. Bütün iş parçacıklarını çağrı yığınlarıyla birlikte göstermek için hata ayıklayıcısına aşağıdaki komutu yazın:

    **~\*makalesinin**

    Özel durum çağrısı yapan yığınlı iş parçacığı, `RaiseTheException` bağımsız değişkeni tarafından belirtilir. Bu yönetilen özel durum nesnesidir.

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. İç içe özel durumların dökümünü almak için aşağıdaki komutu kullanabilirsiniz.

    **! PE-iç içe**

    Eğer herhangi bir özel durum bulamazsanız, bellek yetmezliği özel durumu, yönetilmeyen koddan kaynaklanmıştır.

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Ne kadar sanal belleğin ayrılabileceğini belirlemek için

- SOS hata ayıklama uzantısı yüklenmiş WinDbg'de, en büyük boş bölgeyi almak için şu komutu yazın:

  **! Adres-Özet**

  En büyük boş bölge aşağıdaki çıktıda gösterildiği gibi görüntülenir.

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  Bu örnekte, en büyük boş bölge yaklaşık olarak 24000 KB büyüklüğündedir (onaltılık sistemde 3A980). Bu bölgenin boyutu, çöp toplayıcının bir segment için ihtiyaç duyduğu boyuttan daha küçüktür.

  -veya-

- **Vmstat** komutunu kullanın:

  **! vmstat**

  En büyük boş bölge, aşağıdaki çıktıda görüldüğü üzere, MAXIMUM sütunundaki en büyük değerdir.

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a>Yeterli fiziksel bellek olup olmadığını belirlemek için

1. Windows Görev Yöneticisi'ni başlatın.

2. **Performans** sekmesinde, taahhüt edilen değere bakın. (Windows 7 ' de **sistem grubundaki** **işlemeye (KB)** bakın.)

    **Toplam** **sınıra**yakınsa fiziksel belleği azalmış olursunuz.

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Yönetilen yığının ne kadar bellek kullandığını belirlemek için

- Yönetilen yığının kullandığı bayt sayısını elde etmek için `# Total committed bytes` bellek performans sayacını kullanın. Çöp toplayıcı yığınların hepsini aynı zamanda değil, ihtiyaç duyulan bir segmentte yürütür.

  > [!NOTE]
  > `# Bytes in all Heaps` performans sayacı yönetilen yığın tarafından kullanılan gerçek bellek kullanımını göstermediğinden, bu sayacı kullanmayın. Bu değere bir neslin boyutu dahildir ve aslında onun eşik sınırı, yani, eğer nesil nesnelerle doluysa bir çöp toplama işlemini başlatan boyutu gösterir. Bu nedenle, bu değer genellikle sıfırdır.

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Yönetilen yığının ne kadar bellek ayırdığını belirlemek için

- `# Total reserved bytes` bellek performans sayacını kullanın.

  Çöp toplayıcı bu belleği kesimlerde ayırır ve bir segmentin **eeheap** komutunu kullanarak nereden başlayacağını belirleyebilirsiniz.

  > [!IMPORTANT]
  > Çöp toplayıcı 'nın her segment için ayırdığı bellek miktarını belirleyebilseniz de, kesim boyutu uygulamaya özgüdür ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabidir. Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.

- SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:

  **! eeheap-GC**

  Sonuç aşağıdaki gibidir.

  ```console
  Number of GC Heaps: 2
  ------------------------------
  Heap 0 (002db550)
  generation 0 starts at 0x02abe29c
  generation 1 starts at 0x02abdd08
  generation 2 starts at 0x02ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  02ab0000 02ab0038  02aceff4 0x0001efbc(126908)
  Large object heap starts at 0x0aab0038
    segment    begin allocated     size
  0aab0000 0aab0038  0aab2278 0x00002240(8768)
  Heap Size   0x211fc(135676)
  ------------------------------
  Heap 1 (002dc958)
  generation 0 starts at 0x06ab1bd8
  generation 1 starts at 0x06ab1bcc
  generation 2 starts at 0x06ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  06ab0000 06ab0038  06ab3be4 0x00003bac(15276)
  Large object heap starts at 0x0cab0038
    segment    begin allocated     size
  0cab0000 0cab0038  0cab0048 0x00000010(16)
  Heap Size    0x3bbc(15292)
  ------------------------------
  GC Heap Size   0x24db8(150968)
  ```

  "Segment" ifadesiyle gösterilen adresler, segmentlerin başlangıç adresleridir.

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a>Nesil 2'deki büyük nesneleri belirlemek için

- SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:

  **! dumpheap – stat**

  Yönetilen yığın büyükse, **dumpheap** işleminin tamamlanması biraz zaman alabilir.

  Analize çıktının son satırlarından başlayabilirsiniz çünkü en çok alan kullanan nesneler burada listelenmektedir. Örneğin:

  ```console
  2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo
  00155f80      533     15216804      Free
  7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary
  2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo
  79124228   121143     29064120 System.Object[]
  035f0ee4    81626     35588936 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    40182     90664128 System.Collections.Hashtable+bucket[]
  790fa3e0  3154024    137881448 System.String
  Total 8454945 objects
  ```

  En son listelenen nesne bir dizedir ve en çok yeri o kaplar. Dize nesnelerinin nasıl optimize edilebileceğini görmek için uygulamanızı inceleyebilirsiniz. 150-200 bayt arasındaki dizeleri görmek için, aşağıdakini yazın:

  **! dumpheap-tür System. String-min 150-max 200**

  Sonuçların bir örneği aşağıdaki gibidir.

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  ID için dize yerine tamsayı kullanmak daha verimli olabilir. Aynı dize binlerce kez yineleniyorsa, dize kopyasını kullanmayı düşünün. Dize kopyası kullanımı hakkında daha fazla bilgi edinmek için, <xref:System.String.Intern%2A?displayProperty=nameWithType> yöntemine yönelik referans konusuna bakın.

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a>Nesnelere olan atıfları belirlemek için

- SOS hata ayıklama uzantısı yüklenmiş WinDbg'de, nesnelere yapılan atıfları listelemek için aşağıdaki komutu yazın:

  **! gcroot**

  `-or-`

- Belirli bir nesneye yapılan atıfları belirlemek için, şu adresleri ekleyin:

  **! gcroot 1c37b2ac**

  Yığınlar üzerinde bulunan kökler yanlış pozitif olabilir. Daha fazla bilgi edinmek için `!help gcroot` komutunu kullanın.

  ```console
  ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->
  19010b78(DemoApp.FormDemoApp)->
  19011158(System.Windows.Forms.PropertyStore)->
  … [omitted]
  1c3745ec(System.Data.DataTable)->
  1c3747a8(System.Data.DataColumnCollection)->
  1c3747f8(System.Collections.Hashtable)->
  1c376590(System.Collections.Hashtable+bucket[])->
  1c376c98(System.Data.DataColumn)->
  1c37b270(System.Data.Common.DoubleStorage)->
  1c37b2ac(System.Double[])
  Scan Thread 0 OSTHread 99c
  Scan Thread 6 OSTHread 484
  ```

  **Gcroot** komutunun tamamlanması uzun zaman alabilir. Çöp toplama tarafından iade alınmayan her nesne yaşayan bir nesnedir. Bu, bazı kökin doğrudan veya dolaylı olarak nesneye tutulduğu anlamına gelir, bu nedenle, **gcroot** nesne için yol bilgilerini döndürmelidir. Döndürülen grafikleri ve bu nesnelere neden hala atıf yapıldığını incelemeniz gerekir.

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Bir sonlandırıcının çalıştırılıp çalıştırılmadığını belirlemek için

- Aşağıdaki kodu içeren bir test programı çalıştırın:

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  Test işleminin sorunu çözmesi, sorunun, o nesnelere yönelik sonlandırıcılar askıya alındığı için çöp toplayıcının nesneleri iade almamasından kaynaklandığı anlamına gelir. <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> yöntemi, işlemlerini tamamlaması ve problemi gidermesi için sonlandırıcıları etkinleştirir.

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Sonlandırılmayı bekleyen nesneler olup olmadığını belirlemek için

1. SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:

    **! finalizequeue**

    Sonlandırılmaya hazır olan nesnelerinin sayısına bakın Eğer sayı yüksekse, o sonlandırıcıların niye ilerlemediğini veya yeterince hızlı olmadığını incelemeniz gerekir.

2. İş parçacıklarının bir çıktısını almak için, aşağıdaki komutu yazın:

    **iş parçacıkları-özel**

    Bu komut aşağıdaki gibi bir çıktı sağlar.

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    Sonlandırıcı iş parçacığı, varsa, o an çalışmakta olan sonlandırıcıyı gösterir. Bir sonlandırıcı iş parçacığı herhangi bir sonlandırıcı çalıştırmıyorsa, ona işini söyleyecek bir olay bekliyordur. Çoğu zaman sonlandırıcı iş parçacığını bu durumda görürsünüz çünkü THREAD_HIGHEST_PRIORITY'de çalışır ve varsa çalışan sonlandırıcıları çok hızlı sonlandırması gerekir.

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Yönetilen yığında ne kadar boş alan olduğunu belirlemek için

- SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:

  **! dumpheap-tür serbest stat**

  Bu komut, aşağıdaki örnekte de gösterildiği gibi, yönetilen yığındaki tüm boş nesnelerin toplam boyutunu görüntüler.

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- Nesil 0'daki boş alanı belirlemek için, nesle göre bellek tüketimi bilgilerini öğrenmek için aşağıdaki komutu yazın:

  **! eeheap-GC**

  Bu komut, aşağıdakine benzer bir çıktı gösterir. Son satır kısa ömürlü segmenti gösterir.

  ```console
  Heap 0 (0015ad08)
  generation 0 starts at 0x49521f8c
  generation 1 starts at 0x494d7f64
  generation 2 starts at 0x007f0038
  ephemeral segment allocation context: none
  segment  begin     allocated  size
  00178250 7a80d84c  7a82f1cc   0x00021980(137600)
  00161918 78c50e40  78c7056c   0x0001f72c(128812)
  007f0000 007f0038  047eed28   0x03ffecf0(67103984)
  3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)
  46120000 46120038  49e05d04   0x03ce5ccc(63855820)
  ```

- Nesil 0 tarafından kullanılan alanı hesaplayın:

  **? 49e05d04-0x49521f8c**

  Sonuç aşağıdaki gibidir. Nesil 0 yaklaşık olarak 9 MB.

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- Aşağıdaki komut, nesil 0 aralığındaki boş alanların dökümünü verir:

  **! dumpheap-tür ücretsiz-stat 0x49521f8c 49e05d04**

  Sonuç aşağıdaki gibidir.

  ```console
  ------------------------------
  Heap 0
  total 409 objects
  ------------------------------
  Heap 1
  total 0 objects
  ------------------------------
  Heap 2
  total 0 objects
  ------------------------------
  Heap 3
  total 0 objects
  ------------------------------
  total 409 objects
  Statistics:
        MT    Count TotalSize Class Name
  0015a498      409   7296540      Free
  Total 409 objects
  ```

  Bu çıktı, yığının nesil 0 bölümünün nesneler için 9 MB alan kullandığını 7 MB boş alana sahip olduğunu göstermektedir. Bu çözümleme nesil 0'ın parçalanmaya ne kadar katkıda bulunduğunu gösterir. Bu yığın kullanımının miktarı, uzun zamanlı nesnelerden kaynaklanan parçalanma nedenlerinin toplam miktarından çıkarılmalıdır.

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a>Sabitlenen nesne sayısını belirlemek için

- SOS hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında şu komutu yazın:

  **! GCHandles**

  Görüntülenen istatistikler, aşağıdaki örnekte gösterildiği gibi, sabitlenen işleyicilerin sayısını içerir.

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>Bir çöp toplama işleminde sürenin uzunluğunu belirlemek için

- `% Time in GC` bellek performans sayacını inceleyin.

  Değer, örnek bir zaman aralığı kullanılarak hesaplanır. Her çöp toplama işlemi sonrası sayaçlar güncellendiğinden, ikisi arasında bir toplama işlemi gerçekleşmediyse geçerli örnek öncekiyle aynı değere sahip olacaktır.

  Toplama süresi, örnek zaman aralığının yüzde değeri ile çarpılarak elde edilir.

  Aşağıdaki veriler, 8 saniyelik bir çalışma için ikişer saniyelik dört örnek aralığını göstermektedir. `Gen0`, `Gen1`, ve `Gen2` sütunları, o nesil için bu aralıkta kaç çöp toplama işlemi gerçekleştirildiğini gösterir.

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  Çöp toplama işleminin ne zaman gerçekleştiği bu bilgilerde yer almaz, ancak belirli bir zaman aralığında gerçekleşen çöp toplama işlemi sayısını belirleyebilirsiniz. En kötü durumu varsayarak, onuncu nesil 0 çöp toplama ikinci aralığının başlangıcında, on birinci nesil 0 çöp toplama ise beşinci aralığın sonunda bitmiştir. Onuncu çöp toplama işleminin sonuyla on birinci işlemin sonu arasında geçen süre, yaklaşık 2 saniyedir ve performans sayacı %3'ü gösterdiğinden, on birinci nesil 0 çöp toplamanın süresi (2 saniye * 3% = 60 ms)'dir.

  Bu örnekte 5 periyot vardır.

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  İkinci nesil 2 çöp toplama, üçüncü aralık sırasında başlamış ve beşinci aralıkta bitmiştir. En kötü durumu varsayarak, son çöp toplama işlemi, ikinci aralığın başlangıcında biten bir nesil 0 toplama işlemine aittir ve nesil 2 çöp toplama, beşinci aralığın sonunda bitmiştir. Bu nedenle, nesil 0 çöp toplamanın sonu ile nesil 2 çöp toplamanın sonu arasında geçen süre 4 saniyedir. `% Time in GC` sayacı %20 olduğundan, nesil 2 çöp toplama en fazla (4 saniye * 20% = 800 ms) sürmüş olabilir.

- Alternatif olarak, çöp toplama [ETW olaylarını](../../framework/performance/garbage-collection-etw-events.md)kullanarak bir çöp toplamanın uzunluğunu belirleyebilir ve çöp toplama süresini anlamak için bilgileri çözümleyebilirsiniz.

  Örneğin, aşağıdaki veriler, eş zamanlı olmayan bir çöp toplama işlemi sırasında meydana gelen bir olay dizisini gösterir.

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  Yönetilen iş parçacığını askıya almak 26 us sürüyor (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).

  Çöp toplama işleminin kendisi 4,8 ms sürmüş (`GCEnd_V1` – `GCStart_V1`).

  Yönetilen parçacığını devam ettirmek 21 us sürüyor (`GCRestartEEEnd` – `GCRestartEEBegin`).

  Aşağıdaki çıktıda bir arkaplan çöp toplama örneği verilmiştir ve işlem, iş parçacığı ve olay alanlarını içerir. (Tüm veriler gösterilmemektedir.)

  ```console
  timestamp(us)    event name            process    thread    event field
  42504385        GCSuspendEEBegin_V1    Test.exe    4372             1
  42504648        GCSuspendEEEnd         Test.exe    4372
  42504816        GCStart_V1             Test.exe    4372        102019
  42504907        GCStart_V1             Test.exe    4372        102020
  42514170        GCEnd_V1               Test.exe    4372
  42514204        GCHeapStats            Test.exe    4372        102020
  42832052        GCRestartEEBegin       Test.exe    4372
  42832136        GCRestartEEEnd         Test.exe    4372
  63685394        GCSuspendEEBegin_V1    Test.exe    4744             6
  63686347        GCSuspendEEEnd         Test.exe    4744
  63784294        GCRestartEEBegin       Test.exe    4744
  63784407        GCRestartEEEnd         Test.exe    4744
  89931423        GCEnd_V1               Test.exe    4372        102019
  89931464        GCHeapStats            Test.exe    4372
  ```

  Son alan `GCStart_V1` olduğundan, 42504816'daki `1` olayı, bunun bir arkaplan çöp toplama olduğunu gösterir. Bu çöp toplama Hayır olur. 102019.

  `GCStart` olayı, bir arkaplan çöp toplama işlemi başlamadan önce geçici bir çöp toplama işlemine ihtiyaç duyulduğu için gerçekleşir. Bu çöp toplama Hayır olur. 102020.

  42514170 konumunda çöp toplama No. 102020 bitiyor. Yönetilen iş parçacıkları bu noktada yeniden başlatılır. Bu, arkaplan çöp toplama işlemini tetikleyen 4372 numaralı iş parçacığı üzerinde tamamlanır.

  4744 numaralı iş parçacığında bir askıya alma meydana gelir. Bu, arkaplan çöp toplamanın yönetilen iş parçacıklarını askıya almasının gerektiği tek zamandır. Bu süre yaklaşık olarak 99 ms'dir ((63784407-63685394)/1000).

  Arkaplan çöp toplama için `GCEnd` olayı 89931423'tedir. Bu, arkaplan çöp toplamanın yaklaşık 47 saniye sürdüğü anlamına gelir ((89931423-42504816)/1000).

  Yönetilen iş parçacıkları çalışırken, belirli bir sayıda geçici çöp toplama işleminin gerçekleştiğini görebilirsiniz.

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a>Bir çöp toplama işlemini neyin tetiklediğini belirlemek için

- Hata ayıklama uzantısının yüklendiği WinDbg veya Visual Studio hata ayıklayıcısında, bütün iş parçacıklarını çağrı yığınlarıyla birlikte görmek için aşağıdaki komutu yazın:

  **~\*makalesinin**

  Bu komut, aşağıdakine benzer bir çıktı gösterir.

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  Çöp toplama işlemine işletim sisteminden kaynaklanan bir düşük bellek bildirimi yol açmışsa, çağrı yığını benzerdir ama iş parçacığı sonlandırıcı iş parçacığıdır. Sonlandırıcı iş parçacığı zaman uyumsuz bir düşük bellek bildirimi alır ve çöp toplama işlemini başlatır.

  Çöp toplama işlemine bellek ayırma yol açtıysa, yığın aşağıdaki gibi görünür:

  ```console
  0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration
  0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1
  0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18
  0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b
  0012f310 7a02ae4c mscorwks!Alloc+0x60
  0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd
  0012f424 300027f4 mscorwks!JIT_NewArr1+0x148
  000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c
  0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153
  ```

  Bir tam zamanında yardımcı olan (`JIT_New*`), sonunda `GCHeap::GarbageCollectGeneration` komutuna çağrı yapar. Eğer nesil 2 çöp toplamaya ayırmaların neden olduğunu belirlerseniz, nesil 2 bir çöp toplama işlemi tarafından hangi nesnelerin toplandığını ve bunlardan nasıl kaçınabileceğinizi belirlemeniz gerekir. Yani, nesil 2 bir çöp toplama işleminin başıyla ve sonu arasındaki farkı ve nesil 2'ye ait bir toplama işlemine neden olan nesneleri belirlemeniz faydalı olur.

  Örneğin, nesil 2'ye ait bir toplama işleminin başlangıcını görmek için hata ayıklayıcıya aşağıdaki komutu yazın:

  **! dumpheap – stat**

  Örnek çıktı (en çok alan kullanan nesneleri göstermek için kısaltılmıştır):

  ```console
  79124228    31857      9862328 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  00155f80    21248     12256296      Free
  79103b6c   297003     13068132 System.Threading.ReaderWriterLock
  7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary
  7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  035f0ee4    89192     38887712 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  7912c444    91616     71887080 System.Double[]
  791242ec    32451     82462728 System.Collections.Hashtable+bucket[]
  790fa3e0  2459154    112128436 System.String
  Total 6471774 objects
  ```

  Nesil 2 sonunda komutu yineleyin:

  **! dumpheap – stat**

  Örnek çıktı (en çok alan kullanan nesneleri göstermek için kısaltılmıştır):

  ```console
  79124228    26648      9314256 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  79103b6c   296770     13057880 System.Threading.ReaderWriterLock
  7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary
  7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  00155f80    13806     34007212      Free
  035f0ee4    89187     38885532 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    32370     82359768 System.Collections.Hashtable+bucket[]
  790fa3e0  2440020    111341808 System.String
  Total 6417525 objects
  ```

  Çıktının sonunda `double[]` nesneleri kaybolduğundan, bunların toplandığını anlayabiliriz. Bu nesneler yaklaşık olarak 70 MB. Geri kalan nesneler pek değişmemiş. Bu nedenle, bu nesil 2 çöp toplama işleminin meydana gelmesinin nedeni, bu `double[]` nesneleridir. Bir sonraki adımınız, `double[]` nesnelerinin neden orada olduğu ve neden öldüğünü belirlemek olacaktır. Kod geliştiricisinden bu nesnelerin nereden geldiğini sorabilir veya **gcroot** komutunu kullanabilirsiniz.

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Yüksek CPU kullanımına çöp toplamanın sebep olup olmadığını belirlemek için

- `% Time in GC` bellek performans sayaç değeriyle işlem süresini karşılaştırın.

  `% Time in GC` değeri işlem süresiyle aynı anda artıyorsa, yüksek CPU kullanımına çöp toplama işlemi neden oluyor demektir. Böyle olmuyorsa, yüksek kullanımın nerede meydana geldiğini bulmak için uygulamayı profilleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Çöp toplama](index.md)
