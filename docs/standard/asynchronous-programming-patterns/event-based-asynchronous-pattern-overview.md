---
title: Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 792aa8da-918b-458e-b154-9836b97735f3
ms.openlocfilehash: cce01a7c87f6f20b5e6c46881b8c863bb5a72a88
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160078"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış
Aynı anda pek çok görevi gerçekleştiren ve kullanıcı etkileşimine yanıt veren uygulamalar, genellikle birden çok iş parçacığı kullanan bir tasarım gerektirir. <xref:System.Threading> ad alanı, yüksek performanslı çok iş parçacıklı uygulamalar oluşturmak için gereken tüm araçları sağlar, ancak bu araçların kullanılması çok iş parçacıklı yazılım mühendisliğinde önemli bir deneyim gerektirir. Oldukça basit çok iş parçacıklı uygulamalar için <xref:System.ComponentModel.BackgroundWorker> bileşen basit bir çözüm sağlar. Daha karmaşık zaman uyumsuz uygulamalarda, olay tabanlı zaman uyumsuz düzene uygun bir sınıf uygulamayı düşünün.  
  
 Olay tabanlı zaman uyumsuz model, çok iş parçacıklı uygulamaların avantajlarından yararlanır ve çok iş parçacıklı tasarımda bulunan karmaşık sorunların çoğunu gizler. Bu kalıbı destekleyen bir sınıf kullanmak şunları yapmanıza izin verebilir:  
  
- Yüklemeler ve veritabanı işlemleri gibi zaman alan görevleri, "arka planda", uygulamanızı kesintiye uğramadan gerçekleştirin.  
  
- Birden çok işlemi aynı anda yürütün, her tamamlandığında bildirim alma.  
  
- Uygulamanızı durdurmadan ("engellenmeden") kaynakların kullanılabilir olmasını bekleyin.  
  
- Tanıdık olayları ve temsilciler modelini kullanarak bekleyen zaman uyumsuz işlemlerle iletişim kurun. Olay işleyicilerini ve temsilcileri kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../docs/standard/events/index.md).  
  
 Olay tabanlı zaman uyumsuz deseninin desteklendiği bir sınıf, _MethodName_**zaman uyumsuz**adlı bir veya daha fazla yöntemlere sahip olur. Bu yöntemler, geçerli iş parçacığında aynı işlemi gerçekleştiren zaman uyumlu sürümleri yansıtabilir. Sınıfta bir _MethodName_**tamamlandı** olayı olabilir ve bir _MethodName_**Asynccancel** (veya yalnızca bir algıladığında **lasync**) yöntemi olabilir.  
  
 <xref:System.Windows.Forms.PictureBox>, olay tabanlı zaman uyumsuz stili destekleyen tipik bir bileşendir. <xref:System.Windows.Forms.PictureBox.Load%2A> yöntemini çağırarak bir görüntüyü zaman uyumlu olarak indirebilirsiniz, ancak görüntü büyükse veya ağ bağlantısı yavaşsa, yükleme işlemi tamamlanana ve <xref:System.Windows.Forms.PictureBox.Load%2A> çağrısı geri alınana kadar uygulamanız yanıt vermeyi durdurur.  
  
 Görüntü yüklenirken uygulamanızın çalışmaya devam etmesini istiyorsanız, diğer tüm olayları idare ettiğiniz gibi, <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> yöntemini çağırabilir ve <xref:System.Windows.Forms.PictureBox.LoadCompleted> olayını işleyebilirsiniz. <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> yöntemini çağırdığınızda, yükleme işlemi ayrı bir iş parçacığına ("arka planda") devam ederken uygulamanız çalışmaya devam edecektir. Olay işleyiciniz, görüntü yükleme işlemi tamamlandığında çağrılır ve olay işleyiciniz, indirme işleminin başarıyla tamamlanıp tamamlanmadığını anlamak için <xref:System.ComponentModel.AsyncCompletedEventArgs> parametresini inceleyebilir.  
  
 Olay tabanlı zaman uyumsuz model, zaman uyumsuz bir işlemin iptal edilmesine ve <xref:System.Windows.Forms.PictureBox> denetiminin bu gereksinimi <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> yöntemiyle desteklemesini gerektirir. <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> çağırmak bekleyen indirmeyi durdurma isteği gönderir ve görev iptal edildiğinde, <xref:System.Windows.Forms.PictureBox.LoadCompleted> olay tetiklenir.  
  
> [!CAUTION]
> İndirme işlemi <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> isteği yaptığı gibi bitecektir, bu nedenle <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> iptal etme isteğini yansıtmayabilir. Bu, *yarış durumu* olarak adlandırılır ve çok iş parçacıklı programlamada yaygın bir sorundur. Çoklu iş parçacıklı programlamada sorunlar hakkında daha fazla bilgi için bkz. [yönetilen Iş parçacığı En Iyi yöntemleri](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz düzenin özellikleri  
 Olay tabanlı zaman uyumsuz model, belirli bir sınıf tarafından desteklenen işlemlerin karmaşıklığına bağlı olarak birkaç form alabilir. En basit sınıflarda tek bir _MethodName_**zaman uyumsuz** yöntemi ve karşılık gelen bir _MethodName_**tamamlandı** olayı olabilir. Daha karmaşık sınıfların, her biri karşılık gelen _MethodName_**tamamlandı** olayına ve bu yöntemlerin eşzamanlı sürümlerine sahip birkaç _MethodName_**zaman uyumsuz** yöntemi olabilir. Sınıflar, her zaman uyumsuz yöntem için, isteğe bağlı olarak iptali, ilerleme raporlaması ve artımlı sonuçları destekleyebilir.  
  
 Zaman uyumsuz bir yöntem aynı zamanda birden fazla bekleyen çağrıyı destekleyebilir (birden çok eşzamanlı çağırma), kodunuzun diğer bekleyen işlemleri tamamlamadan önce herhangi bir sayıda çağrı yapmasına izin verir. Bu durumu doğru şekilde işlemek, uygulamanızın her bir işlemin tamamlanmasını izlemesini gerektirebilir.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz model örnekleri  
 <xref:System.Media.SoundPlayer> ve <xref:System.Windows.Forms.PictureBox> bileşenleri, olay tabanlı zaman uyumsuz düzenin basit uygulamalarını temsil eder. <xref:System.Net.WebClient> ve <xref:System.ComponentModel.BackgroundWorker> bileşenleri, olay tabanlı zaman uyumsuz düzenin daha karmaşık uygulamalarını temsil eder.  
  
 Aşağıda, düzene uyan örnek bir sınıf bildirimi verilmiştir:  
  
```vb  
Public Class AsyncExample  
    ' Synchronous methods.  
    Public Function Method1(ByVal param As String) As Integer
    Public Sub Method2(ByVal param As Double)
  
    ' Asynchronous methods.  
    Overloads Public Sub Method1Async(ByVal param As String)
    Overloads Public Sub Method1Async(ByVal param As String, ByVal userState As Object)
    Public Event Method1Completed As Method1CompletedEventHandler  
  
    Overloads Public Sub Method2Async(ByVal param As Double)
    Overloads Public Sub Method2Async(ByVal param As Double, ByVal userState As Object)
    Public Event Method2Completed As Method2CompletedEventHandler  
  
    Public Sub CancelAsync(ByVal userState As Object)
  
    Public ReadOnly Property IsBusy () As Boolean  
  
    ' Class implementation not shown.  
End Class  
```  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 Kurgusal `AsyncExample` sınıfında, her ikisi de zaman uyumlu ve zaman uyumsuz çağırmaları destekleyen iki yöntem vardır. Zaman uyumlu aşırı yüklemeler herhangi bir yöntem çağrısı gibi davranır ve işlemi çağıran iş parçacığında yürütür; işlem zaman alıyorsa, çağrı dönüşmeden önce dikkat çekici bir gecikme olabilir. Zaman uyumsuz aşırı yüklemeler işlemi başka bir iş parçacığında başlatır ve ardından hemen geri döner ve bu işlem, çağıran iş parçacığının işlem "arka planda" yürütüldüğü sırada devam etmesine izin verir.  
  
### <a name="asynchronous-method-overloads"></a>Zaman uyumsuz yöntem aşırı yüklemeleri  
 Zaman uyumsuz işlemler için olası iki aşırı yükleme vardır: tek çağrı ve Çoklu çağrı. Bu iki formu Yöntem imzalarına göre ayırabilirsiniz: Çoklu çağrı formunda `userState`adlı ek bir parametre vardır. Bu form, kodunuzun bekleyen zaman uyumsuz işlemlerin bitmesini beklemeden birden çok kez `Method1Async(string param, object userState)` çağırabilmesini sağlar. Diğer taraftan, önceki bir çağrı tamamlanmadan önce `Method1Async(string param)` çağırmayı denerseniz, yöntem bir <xref:System.InvalidOperationException>oluşturur.  
  
 Çoklu çağrı aşırı yüklemelerinin `userState` parametresi, zaman uyumsuz işlemler arasında ayrım yapmanıza olanak tanır. Her bir `Method1Async(string param, object userState)`çağrısı için benzersiz bir değer (örneğin, bir GUID veya karma kod) sağlarsınız ve her işlem tamamlandığında, olay işleyiciniz işlemin hangi örneğinin tamamlanma olayını gerçekleştirdiğini belirleyebilir.  
  
### <a name="tracking-pending-operations"></a>Bekleyen Işlemleri izleme  
 Çoklu çağrı yüklerini kullanırsanız, kodunuzun bekleyen görevler için `userState` nesneleri (görev kimlikleri) izlemesi gerekir. Her `Method1Async(string param, object userState)`çağrısı için genellikle yeni, benzersiz bir `userState` nesnesi oluşturup bir koleksiyona ekleyebilirsiniz. Bu `userState` nesnesine karşılık gelen görev tamamlanma olayını harekete geçirirse, tamamlama yöntemi uygulamanız <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> inceler ve koleksiyonunuzdan kaldırır. Bu şekilde kullanılırsa, `userState` parametresi bir görev KIMLIĞI rolünü alır.  
  
> [!NOTE]
> Birden çok çağırma aşırı yüküne yönelik çağrılarınızın `userState` için benzersiz bir değer sağlamanız gerekir. Benzersiz olmayan görev kimlikleri, zaman uyumsuz sınıfın bir <xref:System.ArgumentException>oluşturmasına neden olur.  
  
### <a name="canceling-pending-operations"></a>Bekleyen Işlemleri iptal etme  
 Her zaman zaman uyumsuz işlemleri tamamlanmadan önce iptal edebilmek önemlidir. Olay tabanlı zaman uyumsuz model uygulayan sınıfların bir `CancelAsync` yöntemi vardır (yalnızca bir zaman uyumsuz yöntem varsa) veya _MethodName_**asynccancel** yöntemi (birden çok zaman uyumsuz yöntem varsa) olur.  
  
 Birden çok yüklemeye izin veren Yöntemler, her görevin ömrünü izlemek için kullanılabilecek bir `userState` parametresi alır. `CancelAsync`, özel bekleyen görevleri iptal etmenizi sağlayan bir `userState` parametresi alır.  
  
 `Method1Async(string param)`gibi yalnızca tek bir bekleyen işlemi destekleyen yöntemler iptal edilemez.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Ilerleme güncellemeleri ve artımlı sonuçlar alınıyor  
 Olay tabanlı zaman uyumsuz düzene uygun bir sınıf, isteğe bağlı olarak ilerleme durumunu ve artımlı sonuçları izlemek için bir olay sağlayabilir. Bu, genellikle `ProgressChanged` veya _MethodName_**ProgressChanged & lt**olarak adlandırılır ve buna karşılık gelen olay işleyicisi <xref:System.ComponentModel.ProgressChangedEventArgs> bir parametre alır.  
  
 `ProgressChanged` olayının olay işleyicisi, zaman uyumsuz bir görevin tamamlanan yüzdesini belirlemek için <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> özelliğini inceleyebilir. Bu özellik 0 ile 100 arasında değişir ve bir <xref:System.Windows.Forms.ProgressBar><xref:System.Windows.Forms.ProgressBar.Value%2A> özelliğini güncelleştirmek için kullanılabilir. Birden çok zaman uyumsuz işlem beklendiğinde, hangi işlemin ilerleme durumunu ayırt etmek için <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> özelliğini kullanabilirsiniz.  
  
 Bazı sınıflar, zaman uyumsuz işlemler devam edecek şekilde artımlı sonuçlar bildirebilir. Bu sonuçlar, <xref:System.ComponentModel.ProgressChangedEventArgs> türetilen bir sınıfta saklanır ve türetilmiş sınıfta özellikler olarak görünürler. Bu sonuçlara, `ProgressChanged` olayına yönelik olay İşleyicide, <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> özelliğine erişirken olduğu gibi erişebilirsiniz. Birden çok zaman uyumsuz işlem beklendiğinde, hangi işlemin artımlı sonuçlar raporlanmasını ayırt etmek için <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> özelliğini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
