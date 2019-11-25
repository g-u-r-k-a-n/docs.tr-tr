---
title: Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: afd7dda4e876b7faa54ae4a8e62d640d2b9aaf07
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970028"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme

Zaman uyumsuz çözümün performansını şu şekilde artırabilirsiniz: <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi kullanılarak [, Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md) . Bu yöntem, bir görev koleksiyonu olarak temsil edilen birden çok zaman uyumsuz işlemi zaman uyumsuz olarak bekler.

Gözden geçirmede, Web sitelerinin farklı oranlarda indirdiğini fark etmiş olabilirsiniz. Bazen Web sitelerinden biri çok yavaş olduğundan, kalan tüm indirmeleri gecikmekte. Yönergede oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, beklemek istemiyorsanız programı kolayca sonlandırabilir, ancak daha iyi bir seçenek, tüm indirmeleri aynı anda başlatıp daha hızlı karşıdan yüklemelerin devam etmesini sağlamak zorunda kalmadan devam edebilir.  gerekebilecek.

`Task.WhenAll` yöntemini bir görev koleksiyonuna uygularsınız. `WhenAll` uygulaması, koleksiyondaki her görev tamamlanana kadar tamamlanmamış tek bir görev döndürür. Görevler paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz. Görevler herhangi bir sırada tamamlanabilir.

> [!IMPORTANT]
> Aşağıdaki yordamlar [Izlenecek yol: Async ve await (C#) kullanılarak Web 'e erişim](./walkthrough-accessing-the-web-by-using-async-and-await.md)için geliştirilmiş zaman uyumsuz uygulamalara yönelik uzantıları anlatmaktadır. Uygulamayı, izlenecek yolu tamamlayarak veya kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirerek geliştirebilirsiniz.
>
> Örneği çalıştırmak için bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümünün yüklü olması gerekir.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>GetURLContentsAsync çözümünüze Task. WhenAll eklemek için

1. `ProcessURLAsync` yöntemini, [Izlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ilk uygulamaya ekleyin.

    - Kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)Indirdiyseniz asyncwalkthrough projesini açın ve ardından `ProcessURLAsync` MainWindow.xaml.cs dosyasına ekleyin.

    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `GetURLContentsAsync` yöntemini içeren uygulamaya `ProcessURLAsync` ekleyin. Bu uygulama için MainWindow.xaml.cs dosyası, "Izlenecek yol içindeki tüm kod örnekleri" bölümünde yer aldığı ilk örnektir.

    `ProcessURLAsync` yöntemi, özgün izlenecek yolda `SumPageSizesAsync` `foreach` döngüsünün gövdesinde eylemleri birleştirir. Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Aşağıdaki kodun gösterdiği gibi, `SumPageSizesAsync``foreach` döngüsünü açıklama veya silme.

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    byte[] urlContents = await GetURLContentsAsync(url);

    //    // The previous line abbreviates the following two assignment statements.
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //    //byte[] urlContents = await getContentsTask;

    //    DisplayResults(url, urlContents);

    //    // Update the total.
    //    total += urlContents.Length;
    //}
    ```

3. Bir görev koleksiyonu oluşturun. Aşağıdaki kod, <xref:System.Linq.Enumerable.ToArray%2A> yöntemi tarafından yürütüldüğünde, her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir [sorgu](../linq/index.md) tanımlar. Sorgu değerlendirildiğinde görevler başlatılır.

    `urlList`bildiriminden sonra `SumPageSizesAsync` aşağıdaki kodu yöntemine ekleyin.

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. `Task.WhenAll`, `downloadTasks`görevleri koleksiyonuna uygulayın. `Task.WhenAll`, görevler koleksiyonundaki tüm görevler tamamlandığında tamamlanmış tek bir görev döndürür.

    Aşağıdaki örnekte `await` ifadesi, `WhenAll` döndüren tek görevin tamamlanmasını bekler. İfade, her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. Önceki adımda eklediğiniz koddan hemen sonra `SumPageSizesAsync` aşağıdaki kodu ekleyin.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Son olarak, tüm Web sitelerinin uzunluklarının toplamını hesaplamak için <xref:System.Linq.Enumerable.Sum%2A> yöntemini kullanın. `SumPageSizesAsync`için aşağıdaki satırı ekleyin.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>HttpClient. GetByteArrayAsync çözümüne Task. WhenAll eklemek için

1. Aşağıdaki `ProcessURLAsync` sürümünü, [Izlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ikinci uygulamaya ekleyin.

    - Kodu [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)' nden indirdiyseniz, AsyncWalkthrough_HttpClient projesini açın ve sonra MainWindow.xaml.cs dosyasına `ProcessURLAsync` ekleyin.

    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `HttpClient.GetByteArrayAsync` yöntemini kullanan uygulamaya `ProcessURLAsync` ekleyin. Bu uygulama için MainWindow.xaml.cs dosyası, "Izlenecek yol ile ilgili tüm kod örnekleri" bölümünde yer aldığı ikinci örnektir.

    `ProcessURLAsync` yöntemi, özgün izlenecek yolda `SumPageSizesAsync` `foreach` döngüsünün gövdesinde eylemleri birleştirir. Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.

    Önceki yordamdaki `ProcessURLAsync` yönteminin tek farkı, `client` <xref:System.Net.Http.HttpClient> örneğinin kullanımı.

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Aşağıdaki kodun gösterdiği gibi `SumPageSizesAsync``For Each` veya `foreach` döngüsünü açıklama veya silme.

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    byte[] urlContent = await client.GetByteArrayAsync(url);

    //    // The previous line abbreviates the following two assignment
    //    // statements.
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
    //    byte[] urlContent = await getContentTask;

    //    DisplayResults(url, urlContent);

    //    // Update the total.
    //    total += urlContent.Length;
    //}
    ```

3. <xref:System.Linq.Enumerable.ToArray%2A> yöntemi tarafından yürütüldüğünde, her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir [sorgu](../linq/index.md) tanımlayın. Sorgu değerlendirildiğinde görevler başlatılır.

    `client` ve `urlList`bildiriminin ardından aşağıdaki kodu yöntemine ekleyin `SumPageSizesAsync`.

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Sonra, `downloadTasks` görevleri koleksiyonuna `Task.WhenAll` uygulayın. `Task.WhenAll`, görevler koleksiyonundaki tüm görevler tamamlandığında tamamlanmış tek bir görev döndürür.

    Aşağıdaki örnekte `await` ifadesi, `WhenAll` döndüren tek görevin tamamlanmasını bekler. İşlem tamamlandığında, `await` ifade, her tamsayı indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. Önceki adımda eklediğiniz koddan hemen sonra `SumPageSizesAsync` aşağıdaki kodu ekleyin.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Son olarak, tüm Web sitelerinin uzunluklarının toplamını almak için <xref:System.Linq.Enumerable.Sum%2A> yöntemini kullanın. `SumPageSizesAsync`için aşağıdaki satırı ekleyin.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Task. WhenAll çözümlerini test etmek için

- İki çözüm için, programı çalıştırmak için F5 tuşunu seçin ve ardından **Başlat** düğmesini seçin. Çıktı, [Izlenecek yol: AsyncC#ve await () kullanarak Web 'e erişmek](./walkthrough-accessing-the-web-by-using-async-and-await.md)için zaman uyumsuz çözümlerin çıktısına benzer olmalıdır. Ancak, Web sitelerinin her seferinde farklı bir sırada görünmediğine dikkat edin.

## <a name="example"></a>Örnek

Aşağıdaki kod, Web 'den içerik indirmek için `GetURLContentsAsync` yöntemini kullanan projenin uzantılarını gösterir.

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_WhenAll
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

            // Two-step async call.
            Task sumTask = SumPageSizesAsync();
            await sumTask;

            // One-step async call.
            //await SumPageSizesAsync();

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    byte[] urlContents = await GetURLContentsAsync(url);

            //    // The previous line abbreviates the following two assignment statements.
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
            //    //byte[] urlContents = await getContentsTask;

            //    DisplayResults(url, urlContents);

            //    // Update the total.
            //    total += urlContents.Length;
            //}

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

        // The actions from the foreach loop are moved to this async method.
        private async Task<int> ProcessURLAsync(string url)
        {
            var byteArray = await GetURLContentsAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
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
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    await responseStream.CopyToAsync(content);
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

## <a name="example"></a>Örnek

Aşağıdaki kod, Web 'den içerik indirmek için `HttpClient.GetByteArrayAsync` yöntemi kullanan projenin uzantılarını gösterir.

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_HttpClient_WhenAll
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

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url, client);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    byte[] urlContent = await client.GetByteArrayAsync(url);

            //    // The previous line abbreviates the following two assignment
            //    // statements.
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
            //    byte[] urlContent = await getContentTask;

            //    DisplayResults(url, urlContent);

            //    // Update the total.
            //    total += urlContent.Length;
            //}

            // Display the total count for all of the web addresses.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
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

        // The actions from the foreach loop are moved to this async method.
        async Task<int> ProcessURLAsync(string url, HttpClient client)
        {
            byte[] byteArray = await client.GetByteArrayAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each web site. The string format
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

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)
