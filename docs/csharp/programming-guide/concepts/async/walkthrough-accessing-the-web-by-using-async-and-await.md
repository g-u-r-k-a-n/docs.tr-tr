---
title: "İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)"
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: edc45f252b75c742afe4f073ca7dd92d9784d2c4
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240648"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)

Zaman uyumsuz programları, zaman uyumsuz/await özelliklerini kullanarak daha kolay ve daha canlı bir şekilde yazabilirsiniz. Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve derleyicinin zaman uyumsuz kodun genellikle sahip olduğu zor geri çağırma işlevlerini ve devamlılığını işlemesini sağlayabilirsiniz.

Zaman uyumsuz özellik hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama (C#)](./index.md).

Bu izlenecek yol, bir Web sitesi listesindeki bayt sayısını toplayan bir zaman uyumlu Windows Presentation Foundation (WPF) uygulamasıyla başlar. İzlenecek yol, yeni özellikleri kullanarak uygulamayı zaman uyumsuz bir çözüme dönüştürür.

Uygulamaları kendiniz derlemek istemiyorsanız, [zaman uyumsuz örneği indirebilirsiniz: Web 'e (C# ve Visual Basic) erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

## <a name="create-a-wpf-application"></a>WPF uygulaması oluşturma

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde, Visual C# ' ı seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.

4. **Ad** metin kutusuna girin `AsyncExampleWPF` ve sonra **Tamam** düğmesini seçin.

     Yeni proje **Çözüm Gezgini**görüntülenir.

## <a name="design-a-simple-wpf-mainwindow"></a>Basit bir WPF MainWindow tasarımı

1. Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.

2. **Araç kutusu** penceresi görünür değilse, **Görünüm** menüsünü açın ve ardından **araç kutusu**' nu seçin.

3. **MainWindow** penceresine bir **Button** denetimi ve **TextBox** denetimi ekleyin.

4. **TextBox** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

    - **Name** özelliğini olarak ayarlayın `resultsTextBox` .

    - **Height** özelliğini 250 olarak ayarlayın.

    - **Width** özelliğini 500 olarak ayarlayın.

    - **Metin** sekmesinde, Lucida Console veya Global tek boşluk gibi tek boşluklu bir yazı tipi belirtin.

5. **Düğme** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

    - **Name** özelliğini olarak ayarlayın `startButton` .

    - **İçerik** özelliğinin değerini **düğmeden** **başla**olarak değiştirin.

6. Metin kutusunu ve düğmeyi her ikisinin de **MainWindow** penceresinde görünmesi için konumlandırın.

     WPF XAML Tasarımcısı hakkında daha fazla bilgi için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).

## <a name="add-a-reference"></a>Başvuru ekleme

1. **Çözüm Gezgini**, projenizin adını vurgulayın.

2. Menü çubuğunda **Proje**  >  **Başvuru Ekle**' yi seçin.

     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.

3. İletişim kutusunun üst kısmında, projenizin .NET Framework 4,5 veya üstünü hedeflediğinden emin olun.

4. **Derlemeler** kategorisinde, zaten seçili değilse **Framework** ' ü seçin.

5. Ad listesinde, **System .net. http** onay kutusunu seçin.

6. İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="add-necessary-using-directives"></a>Gerekli yönergeleri kullanarak ekleme

1. **Çözüm Gezgini**' de, MainWindow.xaml.cs için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

2. `using`Zaten mevcut değilse, kod dosyasının en üstüne aşağıdaki yönergeleri ekleyin.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Zaman uyumlu uygulama oluşturma

1. Tasarım penceresinde, MainWindow. xaml, **Start** `startButton_Click` MainWindow.xaml.cs içinde olay Işleyicisini oluşturmak için Başlat düğmesine çift tıklayın.

2. MainWindow.xaml.cs içinde aşağıdaki kodu ' ın gövdesine kopyalayın `startButton_Click` :

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Kod, uygulamayı yönlendiren yöntemini çağırır `SumPageSizes` ve denetim ' e döndüğünde bir ileti görüntüler `startButton_Click` .

3. Zaman uyumlu çözüm kodu aşağıdaki dört yöntemi içerir:

    - `SumPageSizes`, ' den Web sayfası URL 'Lerinin bir listesini alır ve `SetUpURLList` ardından `GetURLContents` `DisplayResults` her URL 'yi çağırır ve işler.

    - `SetUpURLList`, bir Web adresleri listesi oluşturur ve döndürür.

    - `GetURLContents`, her bir Web sitesinin içeriğini indirir ve bir bayt dizisi olarak içeriğini döndürür.

    - `DisplayResults`, her bir URL için bayt dizisindeki bayt sayısını görüntüler.

    Aşağıdaki dört yöntemi kopyalayın ve sonra `startButton_Click` MainWindow.xaml.cs içindeki olay işleyicisinin altına yapıştırın:

    ```csharp
    private void SumPageSizes()
    {
        // Make a list of web addresses.
        List<string> urlList = SetUpURLList();

        var total = 0;
        foreach (var url in urlList)
        {
            // GetURLContents returns the contents of url as a byte array.
            byte[] urlContents = GetURLContents(url);

            DisplayResults(url, urlContents);

            // Update the total.
            total += urlContents.Length;
        }

        // Display the total count for all of the web addresses.
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
        {
            "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290136.aspx",
            "https://msdn.microsoft.com/library/ee256749.aspx",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }

    private byte[] GetURLContents(string url)
    {
        // The downloaded resource ends up in the variable named content.
        var content = new MemoryStream();

        // Initialize an HttpWebRequest for the current URL.
        var webReq = (HttpWebRequest)WebRequest.Create(url);

        // Send the request to the Internet resource and wait for
        // the response.
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        using (WebResponse response = webReq.GetResponse())
        {
            // Get the data stream that is associated with the specified URL.
            using (Stream responseStream = response.GetResponseStream())
            {
                // Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content);
            }
        }

        // Return the result as a byte array.
        return content.ToArray();
    }

    private void DisplayResults(string url, byte[] content)
    {
        // Display the length of each website. The string format
        // is designed to be used with a monospaced font, such as
        // Lucida Console or Global Monospace.
        var bytes = content.Length;
        // Strip off the "https://".
        var displayURL = url.Replace("https://", "");
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }
    ```

## <a name="test-the-synchronous-solution"></a>Zaman uyumlu çözümü test etme

Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.

Aşağıdaki listeye benzer bir çıktı görünmelidir:

```text
msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
msdn.microsoft.com                                            33964
msdn.microsoft.com/library/hh290136.aspx               225793
msdn.microsoft.com/library/ee256749.aspx               143577
msdn.microsoft.com/library/hh290138.aspx               237372
msdn.microsoft.com/library/hh290140.aspx               128279
msdn.microsoft.com/library/dd470362.aspx               157649
msdn.microsoft.com/library/aa578028.aspx               204457
msdn.microsoft.com/library/ms404677.aspx               176405
msdn.microsoft.com/library/ff730837.aspx               143474

Total bytes returned:  1834802

Control returned to startButton_Click.
```

Sayıları görüntülemenin birkaç saniye sürdiğine dikkat edin. Bu süre boyunca, Kullanıcı arabirimi iş parçacığı istenen kaynakların indirilmesini beklerken engellenir. Sonuç olarak, **Başlat** düğmesini seçtikten sonra görüntü penceresini taşıyamaz, ekranı kaplamaz, simge durumuna küçültebilir ya da kapatabilirsiniz. Bu çalışmalar, bayt sayıları görünene kadar başarısız olur. Bir Web sitesi yanıt vermiyorsa, hangi sitenin başarısız olduğunun belirtii olmaz. Beklemeyi durdurup programı kapatmanız zordur.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür

1. Zaman uyumlu çözümü zaman uyumsuz bir çözüme dönüştürmek için, `GetURLContents` <xref:System.Net.HttpWebRequest> yönteme <xref:System.Net.HttpWebRequest.GetResponse%2A> ve yöntemine yapılan çağrılar <xref:System.IO.Stream> <xref:System.IO.Stream.CopyTo%2A> uygulamanın Web 'e eriştiği yerdir. .NET Framework, her iki yöntemin de zaman uyumsuz sürümlerini sağlayarak dönüştürmeyi kolaylaştırır.

     İçinde kullanılan yöntemler hakkında daha fazla bilgi için `GetURLContents` bkz <xref:System.Net.WebRequest> ..

    > [!NOTE]
    > Bu izlenecek yolda bulunan adımları izleyerek bazı derleyici hataları görüntülenir. Bunları yoksayabilir ve İzlenecek yol ile devam edebilirsiniz.

     ' In üçüncü satırında çağrılan yöntemi, `GetURLContents` `GetResponse` zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda değiştirin.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. `GetResponseAsync`döndürür <xref:System.Threading.Tasks.Task%601> . Bu durumda, *görev dönüş değişkeni*, `TResult` türündedir <xref:System.Net.WebResponse> . Görev, `WebResponse` istenen veriler indirildikten ve görevin tamamlanmasını çalıştırdıktan sonra gerçek bir nesne oluşturmak için bir taahhüddir.

     `WebResponse`Görevden değeri almak için, aşağıdaki kodda gösterildiği gibi çağrısına bir [await](../../../language-reference/operators/await.md) işleci uygulayın `GetResponseAsync` .

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     `await`İşleç, beklenen görev tamamlanana kadar geçerli yöntemin yürütülmesini askıya alır `GetURLContents` . Bu arada, Denetim geçerli yöntemi çağırana döner. Bu örnekte, geçerli yöntem `GetURLContents` ve arayan ' dır `SumPageSizes` . Görev tamamlandığında, taahhüt edilen `WebResponse` nesne, beklenen görevin değeri olarak üretilir ve değişkenine atanır `response` .

     Önceki deyim, ne olacağını açıklamak için aşağıdaki iki ifadeye ayrılabilir.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     Çağrısı `webReq.GetResponseAsync` bir `Task(Of WebResponse)` veya döndürür `Task<WebResponse>` . Sonra değeri almak için göreve bir Await işleci uygulanır `WebResponse` .

     Zaman uyumsuz yönteminiz görevin tamamlanmasına bağlı değilse, bu iki deyim arasında, zaman uyumsuz metoda yapılan çağrıdan sonra ve işleç uygulanmadan önce, yöntemi bu iş ile devam edebilir `await` . Örnekler için bkz. [Async ve await (c#) kullanarak birden çok web isteğini paralel hale getirme](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [Task. WhenAll (c#) kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. `await`Önceki adımda işleci eklediğiniz için bir derleyici hatası oluşur. İşleci yalnızca [zaman uyumsuz](../../../language-reference/keywords/async.md) değiştiriciyle işaretlenen yöntemlerde kullanılabilir. Çağrısını ' a ' çağrısı ile değiştirmek için dönüştürme adımlarını tekrarlarken hatayı yoksayın `CopyTo` `CopyToAsync` .

    - Olarak çağrılan metodun adını değiştirin <xref:System.IO.Stream.CopyToAsync%2A> .

    - `CopyTo`Ya da `CopyToAsync` yöntemi, bayt bağımsız değişkenine bayt kopyalar, `content` ve anlamlı bir değer döndürmez. Zaman uyumlu sürümde, çağrısı `CopyTo` bir değer döndürmeyen basit bir ifadedir. Zaman uyumsuz sürüm, `CopyToAsync` bir döndürür <xref:System.Threading.Tasks.Task> . Görev, "Task (void)" gibi çalışır ve yöntemin beklenmesine olanak sağlar. `Await` `await` `CopyToAsync` Aşağıdaki kodda gösterildiği gibi, çağrısına yönelik veya çağrısı yapın.

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         Önceki ifade aşağıdaki iki kod satırını abbreviates.

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. Tüm bunlar ' de yapılacak şekilde, `GetURLContents` yöntem imzasını ayarlamasıdır. `await`İşlecini yalnızca [zaman uyumsuz](../../../language-reference/keywords/async.md) değiştiriciyle işaretlenen yöntemlerde kullanabilirsiniz. Aşağıdaki kodun gösterdiği gibi, yöntemi *zaman uyumsuz bir yöntem*olarak işaretlemek için değiştirici ekleyin.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. Zaman uyumsuz bir yöntemin dönüş türü yalnızca <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> veya `void` C# olabilir. Genellikle, bir dönüş türü `void` yalnızca zaman uyumsuz olay işleyicide kullanılır, burada `void` gereklidir. Diğer durumlarda, `Task(T)` Tamamlanan yöntemin T türünde bir değer döndüren bir [Return](../../../language-reference/keywords/return.md) ifadesine sahip olması ve `Task` Tamamlanan yöntemin anlamlı bir değer döndürmemesi durumunda kullanmanız gerekir. `Task`Dönüş türünü anlamı "görev (void)" olarak düşünebilirsiniz.

     Daha fazla bilgi için bkz. [Async Return Types (C#)](./async-return-types.md).

     Yöntem `GetURLContents` bir return ifadesine sahiptir ve ifade bir bayt dizisi döndürür. Bu nedenle, zaman uyumsuz sürümün dönüş türü görev (T), burada T bir bayt dizisidir. Yöntem imzasında aşağıdaki değişiklikleri yapın:

    - Dönüş türünü olarak değiştirin `Task<byte[]>` .

    - Kurala göre, zaman uyumsuz metotların "Async" ile biten adları vardır. bu nedenle, yöntemi yeniden adlandırın `GetURLContentsAsync` .

     Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     Bu az değişiklikle, `GetURLContents` zaman uyumsuz bir metoda dönüştürme işlemi tamamlanmıştır.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Sumpageslikleri zaman uyumsuz bir metoda Dönüştür

1. İçin önceki yordamdaki adımları tekrarlayın `SumPageSizes` . İlk olarak, çağrısını `GetURLContents` zaman uyumsuz bir çağrıya değiştirin.

    - `GetURLContents` `GetURLContentsAsync` Daha önce yapmadıysanız, ' dan ' a çağrılan metodun adını değiştirin.

    - `await` `GetURLContentsAsync` Bayt dizi değerini almak için döndüren göreve uygulanır.

     Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     Önceki atama, aşağıdaki iki kod satırını abbreviates.

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. Yöntemin imzasında aşağıdaki değişiklikleri yapın:

    - Yöntemi `async` değiştiriciyle işaretleyin.

    - Yöntem adına "Async" ekleyin.

    - Bir görev dönüş değişkeni yok, T, bu kez `SumPageSizesAsync` t için bir değer döndürmüyor. (yöntemin hiçbir yöntemi yoktur `return` .) Ancak, yöntemi bir `Task` olarak bir olarak döndürmelidir. Bu nedenle, yönteminin dönüş türünü ' den ' `void` e değiştirin `Task` .

    Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     ' A dönüştürme `SumPageSizes` `SumPageSizesAsync` işlemi tamamlanmıştır.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>StartButton_Click zaman uyumsuz bir metoda Dönüştür

1. Daha önce yapmadıysanız, olay işleyicisinde, çağrılan yöntemin adını `SumPageSizes` olarak olarak değiştirin `SumPageSizesAsync` .

2. `SumPageSizesAsync`Zaman uyumsuz bir yöntem olduğundan, olay işleyicisindeki kodu, sonucu bekleme olarak değiştirin.

     `SumPageSizesAsync`İçindeki çağrısını yansıtan çağrı `CopyToAsync` `GetURLContentsAsync` . Çağrı `Task` a değil, döndürür `Task(T)` .

     Önceki yordamlarda olduğu gibi, çağrıyı tek bir deyim veya iki deyim kullanarak dönüştürebilirsiniz. Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. İşlemi yanlışlıkla yeniden girmeye engel olmak için, `startButton_Click` **Başlangıç** düğmesini devre dışı bırakmak için aşağıdaki ifadeyi ' ın üst kısmına ekleyin.

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Yeniden giriş hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)](./handling-reentrancy-in-async-apps.md).

4. Son olarak, `async` olay işleyicisinin beklebilmesi için değiştiricisini bildirime ekleyin `SumPagSizesAsync` .

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     Genellikle, olay işleyicilerinin adları değiştirilmez. Olay işleyicilerinin dönmesi gereken için dönüş türü olarak değiştirilmez `Task` `void` .

     Projenin zaman uyumlu olarak zaman uyumsuz işlemeye dönüştürülmesi işlemi tamamlanır.

## <a name="test-the-asynchronous-solution"></a>Zaman uyumsuz çözümü test etme

1. Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.

2. Zaman uyumlu çözümün çıktısına benzeyen çıkış görünmelidir. Ancak, aşağıdaki farklılıklara dikkat edin.

    - İşlem tamamlandıktan sonra sonuçların hepsi aynı anda gerçekleşmiyor. Örneğin, her iki program içinde `startButton_Click` metin kutusunu temizleyen bir satır içerir. Tek bir sonuç kümesi görüntülendikten sonra **Başlat** düğmesini ikinci bir kez seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemek amaç. Zaman uyumlu sürümde, metin kutusu yalnızca sayımlar ikinci kez görüntülenmeden önce temizlenir, İndirmeler tamamlandığında ve Kullanıcı arabirimi iş parçacığı başka iş yapmak için ücretsizdir. Zaman uyumsuz sürümde, **Başlat** düğmesini seçtikten sonra metin kutusu hemen temizlenir.

    - En önemlisi, indirme sırasında UI iş parçacığı engellenmiyor. Web kaynakları indirilirken, sayıldıkça ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz. Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alanda bulunan x) seçerek işlemi iptal edebilirsiniz.

## <a name="replace-method-geturlcontentsasync-with-a-net-method"></a>GetURLContentsAsync yöntemini bir .NET yöntemiyle Değiştir

1. .NET Framework 4,5 ve sonraki sürümler, kullanabileceğiniz birçok zaman uyumsuz yöntem sağlar. Bunlardan biri, <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> Bu izlenecek yol için yalnızca ihtiyacınız olanları yapar. `GetURLContentsAsync`Daha önceki bir yordamda oluşturduğunuz yöntemi yerine kullanabilirsiniz.

     İlk adım, yönteminde bir nesne oluşturmaktır `HttpClient` `SumPageSizesAsync` . Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. İçinde, yöntemine yapılan çağrıyı yöntemine `SumPageSizesAsync,` `GetURLContentsAsync` bir çağrı ile değiştirin `HttpClient` .

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. Yazdığınız yöntemi kaldırın veya not edin `GetURLContentsAsync` .

4. Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.

     Projenin bu sürümünün davranışı, "zaman uyumsuz çözümü test etmek Için" yordamının açıklandığı, ancak sizin de daha az çaba gösteren davranışla eşleşmelidir.

## <a name="example-code"></a>Örnek kod

Aşağıdaki kod, yazdığınız zaman uyumsuz yöntemi kullanarak zaman uyumsuz bir çözüme dönüştürme işleminin tam örneğini içerir `GetURLContentsAsync` . Özgün, zaman uyumlu çözüme kesinlikle benzediğine dikkat edin.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                byte[] urlContents = await GetURLContentsAsync(url);

                // The previous line abbreviates the following two assignment statements.

                // GetURLContentsAsync returns a Task<T>. At completion, the task
                // produces a byte array.
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }
            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())

            // The previous statement abbreviates the following two statements.

            //Task<WebResponse> responseTask = webReq.GetResponseAsync();
            //using (WebResponse response = await responseTask)
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    // Read the bytes in responseStream and copy them to content.
                    await responseStream.CopyToAsync(content);

                    // The previous statement abbreviates the following two statements.

                    // CopyToAsync returns a Task, not a Task<T>.
                    //Task copyTask = responseStream.CopyToAsync(content);

                    // When copyTask is completed, content contains a copy of
                    // responseStream.
                    //await copyTask;
                }
            }
            // Return the result as a byte array.
            return content.ToArray();
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

Aşağıdaki kod, yöntemini kullanan çözümün tam örneğini içerir `HttpClient` `GetByteArrayAsync` .

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            // One-step async call.
            await SumPageSizesAsync();

            //// Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client =
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                // GetByteArrayAsync returns a task. At completion, the task
                // produces a byte array.
                byte[] urlContents = await client.GetByteArrayAsync(url);

                // The following two lines can replace the previous assignment statement.
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz örnek: Web 'e yönelik Izlenecek yol (C# ve Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Async ve await ile zaman uyumsuz programlama (C#)](./index.md)
- [Zaman uyumsuz dönüş türleri (C#)](./async-return-types.md)
- [Görev tabanlı zaman uyumsuz programlama (TAP)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Task. WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Async ve await kullanarak birden çok web isteğini paralel hale getirme (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
