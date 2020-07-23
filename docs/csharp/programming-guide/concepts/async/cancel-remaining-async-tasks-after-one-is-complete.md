---
title: Kalan zaman uyumsuz görevleri bir tane tamamlandıktan sonra iptal etme (C#)
description: Bu örnekte bir görev tamamlandığında kalan tüm görevleri iptal etmek Için, Task. WhenAny yöntemini C# içindeki CancellationToken ile birlikte kullanın.
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 6de60c8faa93752961e3703a042885a71972cc4a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925298"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="07856-103">Kalan zaman uyumsuz görevleri bir tane tamamlandıktan sonra iptal etme (C#)</span><span class="sxs-lookup"><span data-stu-id="07856-103">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="07856-104"><xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>Yöntemini bir ile birlikte kullanarak, bir <xref:System.Threading.CancellationToken> görev tamamlandığında kalan tüm görevleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07856-104">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="07856-105">`WhenAny`Yöntemi, bir görev koleksiyonu olan bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="07856-105">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="07856-106">Yöntemi tüm görevleri başlatır ve tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="07856-106">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="07856-107">Koleksiyondaki herhangi bir görev tamamlandığında tek görev tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="07856-107">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="07856-108">Bu örnek, bir iptal belirtecinin `WhenAny` , görev koleksiyonundan sona ermesini ve kalan görevleri iptal etmek için ilk görevi tutmak üzere ile birlikte nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="07856-108">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="07856-109">Her görev bir Web sitesinin içeriğini indirir.</span><span class="sxs-lookup"><span data-stu-id="07856-109">Each task downloads the contents of a website.</span></span> <span data-ttu-id="07856-110">Örnek, tamamlanacak ilk indirmenin içeriklerinin uzunluğunu görüntüler ve diğer indirmeleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="07856-110">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07856-111">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07856-111">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="07856-112">Örnek indiriliyor</span><span class="sxs-lookup"><span data-stu-id="07856-112">Downloading the Example</span></span>  
 <span data-ttu-id="07856-113">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="07856-113">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="07856-114">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="07856-114">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="07856-115">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="07856-115">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="07856-116">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="07856-116">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="07856-117">**Çözüm Gezgini**' de, **ınkıfteronetask** projesinin kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="07856-117">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="07856-118">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="07856-118">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="07856-119">Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="07856-119">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="07856-120">İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="07856-120">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="07856-121">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07856-121">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="07856-122">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="07856-122">Building the Example</span></span>  
 <span data-ttu-id="07856-123">Bu konudaki örnek, bir görev listesini iptal etmek için [zaman uyumsuz bir görevi veya bir görev listesini (C#) Iptal etme](./cancel-an-async-task-or-a-list-of-tasks.md) bölümünde geliştirilen projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="07856-123">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="07856-124">Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="07856-124">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="07856-125">Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi**olarak iptal eden **ınlıftasks** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="07856-125">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="07856-126">Bu konudaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="07856-126">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="07856-127">"MainWindow.xaml.cs & lt; & lt; & lt; & lt; & lt; 3} dosya **dosyasında, içindeki** her bir Web sitesi için işleme adımlarını `AccessTheWebAsync` aşağıdaki zaman uyumsuz metoda taşıyarak geçişi başlatın.</span><span class="sxs-lookup"><span data-stu-id="07856-127">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
// ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="07856-128">`AccessTheWebAsync`' De, bu örnek bir sorgu, <xref:System.Linq.Enumerable.ToArray%2A> Yöntem ve bir `WhenAny` dizi görev oluşturmak ve başlatmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="07856-128">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="07856-129">Dizi için olan uygulaması, `WhenAny` bir görev dizisinde tamamlamaya ulaşmak üzere ilk görevi değerlendiren tek bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="07856-129">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="07856-130">İçinde aşağıdaki değişiklikleri yapın `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="07856-130">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="07856-131">Yıldız işaretleri kod dosyasındaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="07856-131">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="07856-132">Döngüyü not edin veya silin.</span><span class="sxs-lookup"><span data-stu-id="07856-132">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="07856-133">Yürütüldüğünde, genel görevlerden oluşan bir koleksiyon üreten bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="07856-133">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="07856-134">Her çağrısı `ProcessURLAsync` <xref:System.Threading.Tasks.Task%601> , bir, bir `TResult` tamsayı olan bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="07856-134">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="07856-135">`ToArray`Sorguyu yürütmek ve görevleri başlatmak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="07856-135">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="07856-136">Bir `WhenAny` sonraki adımda yönteminin uygulaması sorguyu yürütür ve görevleri kullanmadan başlatır `ToArray` , ancak diğer yöntemler de çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="07856-136">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="07856-137">En güvenli yöntem, sorgunun yürütülmesini açıkça zorlamaktır.</span><span class="sxs-lookup"><span data-stu-id="07856-137">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="07856-138">`WhenAny`Görevler koleksiyonunda çağırın.</span><span class="sxs-lookup"><span data-stu-id="07856-138">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="07856-139">`WhenAny`bir `Task(Of Task(Of Integer))` veya döndürür `Task<Task<int>>` .</span><span class="sxs-lookup"><span data-stu-id="07856-139">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="07856-140">Diğer bir deyişle, `WhenAny` tek veya bekleniyor bir görevi döndürür `Task(Of Integer)` `Task<int>` .</span><span class="sxs-lookup"><span data-stu-id="07856-140">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="07856-141">Bu tek görev, koleksiyondaki ilk görevin sona ermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="07856-141">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="07856-142">Önce tamamlanan görev öğesine atanır `firstFinishedTask` .</span><span class="sxs-lookup"><span data-stu-id="07856-142">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="07856-143">Türü, öğesinin `firstFinishedTask` <xref:System.Threading.Tasks.Task%601> `TResult` dönüş türü olduğu için bir tamsayıdır `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="07856-143">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="07856-144">Bu örnekte, yalnızca ilk olarak sona erki görevi ilgileniyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="07856-144">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="07856-145">Bu nedenle, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> kalan görevleri iptal etmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="07856-145">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="07856-146">Son olarak, `firstFinishedTask` indirilen içeriğin uzunluğunu almak için Await.</span><span class="sxs-lookup"><span data-stu-id="07856-146">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="07856-147">İlk olarak farklı indirmelerin bitmesini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="07856-147">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="07856-148">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="07856-148">Complete Example</span></span>  
 <span data-ttu-id="07856-149">Aşağıdaki kod, örnek için tüm MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="07856-149">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="07856-150">Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="07856-150">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="07856-151">İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="07856-151">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="07856-152">Projeyi [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="07856-152">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
namespace CancelAfterOneTask  
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
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.
            //    // Argument ct carries the message if the Cancel button is chosen.
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="07856-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07856-153">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="07856-154">Zaman uyumsuz uygulamanızda ince ayar yapma (C#)</span><span class="sxs-lookup"><span data-stu-id="07856-154">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="07856-155">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="07856-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="07856-156">Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma</span><span class="sxs-lookup"><span data-stu-id="07856-156">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
