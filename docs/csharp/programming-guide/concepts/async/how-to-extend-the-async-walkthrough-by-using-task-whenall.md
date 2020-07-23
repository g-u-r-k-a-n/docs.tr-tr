---
title: Task. WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme (C#)
description: Task. WhenAll kullanarak C# ' de zaman uyumsuz çözüm performansını geliştirmeyi öğrenin. Bu yöntem, birden çok zaman uyumsuz işlemi zaman uyumsuz olarak bekler.
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 275f4aeca854f8938642dbea40bf7fd9dc5362d9
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925221"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Task. WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme (C#)

Zaman uyumsuz çözümün performansını şu şekilde artırabilirsiniz: yöntemini kullanarak [, Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Bu yöntem, bir görev koleksiyonu olarak temsil edilen birden çok zaman uyumsuz işlemi zaman uyumsuz olarak bekler.

Gözden geçirmede, Web sitelerinin farklı oranlarda indirdiğini fark etmiş olabilirsiniz. Bazen Web sitelerinden biri çok yavaş olduğundan, kalan tüm indirmeleri gecikmekte. Yönergede oluşturduğunuz zaman uyumsuz çözümleri çalıştırdığınızda, beklemek istemiyorsanız programı kolayca sonlandırabilir, ancak daha iyi bir seçenek, tüm indirmeleri aynı anda başlatmak ve geciktirilen bir süre beklemeden daha hızlı karşıdan yüklemelerin devam etmesini sağlamak olacaktır.

`Task.WhenAll`Yöntemi bir görev koleksiyonuna uygularsınız. Uygulaması, `WhenAll` koleksiyondaki her görev tamamlanana kadar tamamlanmamış tek bir görev döndürür. Görevler paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz. Görevler herhangi bir sırada tamamlanabilir.

> [!IMPORTANT]
> Aşağıdaki yordamlar, [Izlenecek yol: Async ve await (C#) kullanılarak Web 'e erişim](./walkthrough-accessing-the-web-by-using-async-and-await.md)için geliştirilmiş, zaman uyumsuz uygulamalara yönelik uzantıları anlatmaktadır. Uygulamayı, izlenecek yolu tamamlayarak veya kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirerek geliştirebilirsiniz.
>
> Örneği çalıştırmak için bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümünün yüklü olması gerekir.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>GetURLContentsAsync çözümünüze Task. WhenAll eklemek için

1. Yöntemi, `ProcessURLAsync` [izlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ilk uygulamaya ekleyin.

    - Kodu [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)' nden Indirdiyseniz asyncwalkthrough projesini açın ve `ProcessURLAsync` MainWindow.xaml.cs dosyasına ekleyin.

    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` yöntemini içeren uygulamaya ekleyin `GetURLContentsAsync` . Bu uygulama için MainWindow.xaml.cs dosyası, "Izlenecek yol içindeki tüm kod örnekleri" bölümünde yer aldığı ilk örnektir.

    `ProcessURLAsync`Yöntemi, `foreach` ilk izlenecek yolda içindeki döngüsünün gövdesinde bulunan eylemleri birleştirir `SumPageSizesAsync` . Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. `foreach` `SumPageSizesAsync` Aşağıdaki kodun gösterdiği gibi, içindeki döngüyü not edin veya silin.

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

3. Bir görev koleksiyonu oluşturun. Aşağıdaki kod, yöntemi tarafından [query](../linq/index.md) yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> , her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir sorgu tanımlar. Sorgu değerlendirildiğinde görevler başlatılır.

    Bildirimi sonrasında yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` `urlList` .

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. `Task.WhenAll`Görev koleksiyonu için geçerlidir `downloadTasks` . `Task.WhenAll`görev koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.

    Aşağıdaki örnekte, `await` ifadesi döndüren tek görevin tamamlanmasını bekler `WhenAll` . İfade, her tamsayının indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. `SumPageSizesAsync`Önceki adımda eklediğiniz koddan hemen sonra aşağıdaki kodu ekleyin.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını hesaplamak için yöntemini kullanın. Aşağıdaki satırı öğesine ekleyin `SumPageSizesAsync` .

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>HttpClient. GetByteArrayAsync çözümüne Task. WhenAll eklemek için

1. Aşağıdaki sürümünü, `ProcessURLAsync` [izlenecek yol: Async ve await (C#) kullanarak Web 'e erişme](./walkthrough-accessing-the-web-by-using-async-and-await.md)bölümünde geliştirilen ikinci uygulamaya ekleyin.

    - Kodu [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)' nden indirdiyseniz, AsyncWalkthrough_HttpClient projesini açın ve sonra `ProcessURLAsync` MainWindow.xaml.cs dosyasına ekleyin.

    - İzlenecek yolu tamamlayarak kodu geliştirdiyseniz, `ProcessURLAsync` yöntemini kullanan uygulamaya ekleyin `HttpClient.GetByteArrayAsync` . Bu uygulama için MainWindow.xaml.cs dosyası, "Izlenecek yol ile ilgili tüm kod örnekleri" bölümünde yer aldığı ikinci örnektir.

    `ProcessURLAsync`Yöntemi, `foreach` ilk izlenecek yolda içindeki döngüsünün gövdesinde bulunan eylemleri birleştirir `SumPageSizesAsync` . Yöntemi, belirtilen bir Web sitesinin içeriğini bir bayt dizisi olarak zaman uyumsuz olarak indirir ve bayt dizisinin uzunluğunu görüntüler ve döndürür.

    `ProcessURLAsync`Önceki yordamdaki yöntemden tek fark <xref:System.Net.Http.HttpClient> , örneği kullanmaktır `client` .

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. `For Each` `foreach` Aşağıdaki kodun gösterdiği gibi, içindeki veya döngüsünü açıklama veya silme `SumPageSizesAsync` .

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

3. Yöntemi tarafından [query](../linq/index.md) yürütüldüğünde <xref:System.Linq.Enumerable.ToArray%2A> , her bir Web sitesinin içeriğini yükleyen bir görev koleksiyonu oluşturan bir sorgu tanımlayın. Sorgu değerlendirildiğinde görevler başlatılır.

    Ve bildiriminden sonra yöntemine aşağıdaki kodu ekleyin `SumPageSizesAsync` `client` `urlList` .

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Sonra, `Task.WhenAll` görev koleksiyonu için geçerlidir `downloadTasks` . `Task.WhenAll`görev koleksiyonundaki tüm görevler tamamlandığında tamamlanan tek bir görev döndürür.

    Aşağıdaki örnekte, `await` ifadesi döndüren tek görevin tamamlanmasını bekler `WhenAll` . İşlem tamamlandığında, `await` ifade, her tamsayı indirilen bir Web sitesinin uzunluğu olduğu bir tamsayılar dizisi olarak değerlendirilir. `SumPageSizesAsync`Önceki adımda eklediğiniz koddan hemen sonra aşağıdaki kodu ekleyin.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Son olarak, <xref:System.Linq.Enumerable.Sum%2A> tüm Web sitelerinin uzunluklarının toplamını almak için yöntemini kullanın. Aşağıdaki satırı öğesine ekleyin `SumPageSizesAsync` .

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Task. WhenAll çözümlerini test etmek için

- İki çözüm için, programı çalıştırmak için F5 tuşunu seçin ve ardından **Başlat** düğmesini seçin. Çıktı, [Izlenecek yol: Async ve await (C#) kullanarak Web 'e erişmek](./walkthrough-accessing-the-web-by-using-async-and-await.md)için zaman uyumsuz çözümlerin çıktısına benzer olmalıdır. Ancak, Web sitelerinin her seferinde farklı bir sırada görünmediğine dikkat edin.

## <a name="example"></a>Örnek

Aşağıdaki kod, `GetURLContentsAsync` Web 'den içerik indirmek için yöntemini kullanan projenin uzantılarını gösterir.

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

Aşağıdaki kod, `HttpClient.GetByteArrayAsync` Web 'den içerik indirmek için yöntemini kullanan projenin uzantılarını gösterir.

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
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
