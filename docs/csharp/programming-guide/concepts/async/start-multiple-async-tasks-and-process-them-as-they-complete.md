---
title: Zaman uyumsuz görevleri tamamlarlar işleme
description: Bu örnek, birden çok görevi başlatmak ve sonuçlarını tamamlandığında işlem sırasında işlemek yerine sonuçları işlemek Için C# ' de Task. WhenAny 'ın nasıl kullanılacağını gösterir.
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: a7cfa0bdf783fe9bb735241ca398fde7895f1493
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925156"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Birden çok zaman uyumsuz görev başlatma ve bunları tamamlarsa Işleme (C#)

Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , aynı anda birden çok görev başlatabilir ve bunları, başlatıldıkları sırada işlemek yerine, bir kez işlem tamamlanır.

Aşağıdaki örnek, bir görev koleksiyonu oluşturmak için bir sorgu kullanır. Her görev belirtilen bir Web sitesinin içeriğini indirir. Bir while döngüsünün her yinelemesinde, geri beklenmiş bir çağrı, `WhenAny` önce indirmeyi izleyen görevler koleksiyonundaki görevi döndürür. Bu görev koleksiyondan kaldırılır ve işlenir. Döngü, koleksiyon daha fazla görev içerene kadar yinelenir.

> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio (2012 veya üzeri) ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

## <a name="download-an-example-solution"></a>Örnek çözüm indirin

Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.

> [!TIP]
> Projeyi indirmek istemiyorsanız, bunun yerine bu konunun sonundaki *MainWindow.xaml.cs* dosyasını gözden geçirebilirsiniz.

1. İndirdiğiniz dosyaları *. zip* dosyasından ayıklayın ve ardından Visual Studio 'yu başlatın.

2. Menü çubuğunda **Dosya**  >  **Aç**  >  **Proje/çözüm**' ı seçin.

3. **Proje Aç** iletişim kutusunda, indirdiğiniz örnek kodu tutan klasörü açın ve ardından *AsyncFineTuningCS**.sln* / *AsyncFineTuningVB*için çözüm (. sln) dosyasını açın.

4. **Çözüm Gezgini**' de, **Processtasksastheyıfinish** projesinin kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.

5. Programı hata ayıklamayla çalıştırmak için <kbd>F5</kbd> tuşunu seçin veya <kbd>Ctrl</kbd> + programı hata ayıklamadan çalıştırmak için CTRL<kbd>F5</kbd> tuşlarına basın.

6. İndirilen uzunluklarının her zaman aynı sırada görünmediğini doğrulamak için projeyi birkaç kez çalıştırın.

## <a name="create-the-program-yourself"></a>Programı kendiniz oluşturun

Bu örnek, [bir tane tamamlandıktan sonra kalan zaman uyumsuz görevleri Iptal etme](cancel-remaining-async-tasks-after-one-is-complete.md)bölümünde geliştirilen koda ekler (C#) ve aynı kullanıcı arabirimini kullanır.

Örneği kendiniz oluşturmak için, örnek ' i [karşıdan yükleme](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) bölümündeki yönergeleri izleyin, ancak başlangıç projesi olarak, bir **erteleme görevi** ayarlayın. Bu konudaki değişiklikleri bu `AccessTheWebAsync` projedeki yöntemine ekleyin. Değişiklikler yıldız işaretiyle işaretlenir.

Bu **görev** projesi, yürütüldüğünde bir görev koleksiyonu oluşturduğunda zaten bir sorgu içeriyor. Aşağıdaki kodda öğesine yapılan her çağrı `ProcessURLAsync` <xref:System.Threading.Tasks.Task%601> , bir `TResult` tam sayı olan bir döndürür:

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

Projenin *MainWindow.xaml.cs* dosyasında, yönteminde aşağıdaki değişiklikleri yapın `AccessTheWebAsync` :

- Yerine uygulayarak sorguyu yürütün <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToArray%2A> .

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- `while`Koleksiyondaki her görev için aşağıdaki adımları gerçekleştiren bir döngü ekleyin:

    1. Bu, `WhenAny` indirme işleminin sona ermesi için koleksiyondaki ilk görevi tanımlamak üzere öğesine bir çağrıyı bekler.

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. Bu görevi koleksiyondan kaldırır.

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. `firstFinishedTask`Bir çağrısıyla döndürülen await `ProcessURLAsync` . `firstFinishedTask`Değişkeni bir <xref:System.Threading.Tasks.Task%601> WHERE `TReturn` tamsayıdır. Görev zaten tamamlanmış, ancak aşağıdaki örnekte gösterildiği gibi, indirilen Web sitesinin uzunluğunu almak için bu işlemi beklediniz. Görev hata verdiyse, ' `await` de bulunan `AggregateException` özelliği okumaktan farklı olarak, içinde depolanan ilk alt özel durumu oluşturur `Result` `AggregateException` .

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

İndirilen uzunluklarının her zaman aynı sırada görünmediğini doğrulamak için programı birkaç kez çalıştırın.

> [!CAUTION]
> `WhenAny`Az sayıda görevle ilgili sorunları gidermek için örnekte açıklandığı gibi bir döngüde kullanabilirsiniz. Ancak, işlemek için çok sayıda göreviniz varsa diğer yaklaşımlar daha etkilidir. Daha fazla bilgi ve örnek için bkz. [görevleri tamamladıklarında işleme](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).

## <a name="complete-example"></a>Örnek Tamam

Aşağıdaki kod, örnek için *MainWindow.xaml.cs* dosyasının tüm metinkodudur. Yıldız işaretleri bu örnek için eklenen öğeleri işaretler. Ayrıca, için bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http> .

Projeyi [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive.
using System.Threading;

namespace ProcessTasksAsTheyFinish
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            try
            {
                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Create a query that, when executed, returns a collection of tasks.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURL(url, client, ct);

            // ***Use ToList to execute the query and start the tasks.
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

            // ***Add a loop to process the tasks one at a time until none remain.
            while (downloadTasks.Count > 0)
            {
                    // Identify the first task that completes.
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);

                    // ***Remove the selected task from the list so that you don't
                    // process it more than once.
                    downloadTasks.Remove(firstFinishedTask);

                    // Await the completed task.
                    int length = await firstFinishedTask;
                    resultsTextBox.Text += $"\r\nLength of the download:  {length}";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)
        {
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            return urlContents.Length;
        }
    }
}

// Sample Output:

// Length of the download:  226093
// Length of the download:  412588
// Length of the download:  175490
// Length of the download:  204890
// Length of the download:  158855
// Length of the download:  145790
// Length of the download:  44908
// Downloads complete.
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Zaman uyumsuz uygulamanızda ince ayar yapma (C#)](fine-tuning-your-async-application.md)
- [Async ve await ile zaman uyumsuz programlama (C#)](index.md)
- [Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
