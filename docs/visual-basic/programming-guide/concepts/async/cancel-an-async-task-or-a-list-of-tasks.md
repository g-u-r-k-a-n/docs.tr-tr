---
description: 'Hakkında daha fazla bilgi edinin: zaman uyumsuz bir görevi veya görev listesini Iptal etme (Visual Basic)'
title: Zaman Uyumsuz bir Görevi veya Görev Listesini İptal Etme
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: d61db65db62c62e93abf0a5036533dd2967fe917
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467088"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="20938-103">Zaman uyumsuz bir görevi veya görev listesini iptal etme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20938-103">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>

<span data-ttu-id="20938-104">Bir zaman uyumsuz uygulamayı, bitmesini beklemek istemiyorsanız iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20938-104">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="20938-105">Bu konudaki örnekleri izleyerek, bir Web sitesinin veya Web sitesi listesinin içeriğini yükleyen bir uygulamaya iptal düğmesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20938-105">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="20938-106">Örnekler, [zaman uyumsuz uygulamanızı (Visual Basic) ayrıntılı olarak ayarlamaya](fine-tuning-your-async-application.md) yönelik kullanıcı arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="20938-106">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="20938-107">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20938-107">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><a name="BKMK_CancelaTask"></a> <span data-ttu-id="20938-108">Bir görevi iptal etme</span><span class="sxs-lookup"><span data-stu-id="20938-108">Cancel a Task</span></span>

<span data-ttu-id="20938-109">İlk örnek, **iptal** düğmesini tek bir indirme göreviyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="20938-109">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="20938-110">Uygulama içerik indirirken düğmeyi seçerseniz, indirme iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="20938-110">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="downloading-the-example"></a><span data-ttu-id="20938-111">Örnek indiriliyor</span><span class="sxs-lookup"><span data-stu-id="20938-111">Downloading the Example</span></span>

<span data-ttu-id="20938-112">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="20938-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="20938-113">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="20938-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="20938-114">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="20938-115">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="20938-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="20938-116">**Çözüm Gezgini**' de,,,, Iptal eden **görev** projesi için kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-116">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="20938-117">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-117">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="20938-118">Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

 <span data-ttu-id="20938-119">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20938-119">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>

### <a name="building-the-example"></a><span data-ttu-id="20938-120">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="20938-120">Building the Example</span></span>

<span data-ttu-id="20938-121">Aşağıdaki değişiklikler bir Web sitesini indiren uygulamaya bir **iptal** düğmesi ekler.</span><span class="sxs-lookup"><span data-stu-id="20938-121">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="20938-122">Örneği indirmek veya derlemek istemiyorsanız, bu konunun sonundaki "tüm örnekler" bölümünde son ürünü gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20938-122">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="20938-123">Yıldız işaretleri koddaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="20938-123">Asterisks mark the changes in the code.</span></span>

<span data-ttu-id="20938-124">Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi** olarak, **1. aşama yerine** **startercode** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

<span data-ttu-id="20938-125">Ardından, bu projenin MainWindow. xaml. vb dosyasına aşağıdaki değişiklikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20938-125">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>

1. <span data-ttu-id="20938-126">`CancellationTokenSource` `cts` Kendisine erişen tüm yöntemler için kapsam içinde olan bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="20938-126">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```vb
    Class MainWindow

        ' ***Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="20938-127">**İptal** düğmesi için aşağıdaki olay işleyicisini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20938-127">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="20938-128">Olay işleyicisi, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> Kullanıcı iptali istediğinde bildirimde bulunan yöntemini kullanır `cts` .</span><span class="sxs-lookup"><span data-stu-id="20938-128">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

    ```vb
    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub
    ```

3. <span data-ttu-id="20938-129">**Başlat** düğmesi için olay işleyicisinde aşağıdaki değişiklikleri yapın `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="20938-129">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="20938-130">, İçin örneğini oluşturun `CancellationTokenSource` `cts` .</span><span class="sxs-lookup"><span data-stu-id="20938-130">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

      ```vb
      ' ***Instantiate the CancellationTokenSource.
      cts = New CancellationTokenSource()
      ```

    - <span data-ttu-id="20938-131">`AccessTheWebAsync`Belirtilen bir Web sitesinin içeriğini yükleyen çağrısında, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliğini `cts` bağımsız değişken olarak gönderin.</span><span class="sxs-lookup"><span data-stu-id="20938-131">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="20938-132">`Token`Özelliği, iptal isteniyorsa iletiyi yayar.</span><span class="sxs-lookup"><span data-stu-id="20938-132">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="20938-133">Kullanıcı indirme işlemini iptal etmeyi seçerse bir ileti görüntüleyen bir catch bloğu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20938-133">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="20938-134">Aşağıdaki kod değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="20938-134">The following code shows the changes.</span></span>

      ```vb
      Try
          ' ***Send a token to carry the message if cancellation is requested.
          Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

          resultsTextBox.Text &=
              vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

          ' *** If cancellation is requested, an OperationCanceledException results.
      Catch ex As OperationCanceledException
          resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

      Catch ex As Exception
          resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
      End Try
      ```

4. <span data-ttu-id="20938-135">İçinde `AccessTheWebAsync` ,  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> `GetAsync` <xref:System.Net.Http.HttpClient> bir Web sitesinin içeriğini indirmek için türünde yönteminin aşırı yüklemesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="20938-135">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="20938-136">`ct` <xref:System.Threading.CancellationToken> `AccessTheWebAsync` İkinci bağımsız değişken olarak, parametresini geçirin.</span><span class="sxs-lookup"><span data-stu-id="20938-136">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="20938-137">Kullanıcı **iptal** düğmesini seçerse, belirteç iletiyi taşır.</span><span class="sxs-lookup"><span data-stu-id="20938-137">The token carries the message if the user chooses the **Cancel** button.</span></span>

    <span data-ttu-id="20938-138">Aşağıdaki kod, içindeki değişiklikleri gösterir `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="20938-138">The following code shows the changes in `AccessTheWebAsync`.</span></span>

    ```vb
    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &= vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
    ```

5. <span data-ttu-id="20938-139">Programı iptal ederseniz aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="20938-139">If you don’t cancel the program, it produces the following output:</span></span>

    ```console
    Ready to download.
    Length of the downloaded string: 158125.
    ```

    <span data-ttu-id="20938-140">Program içeriği indirmeyi bitirmeden **iptal** düğmesini seçerseniz, program aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="20938-140">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output:</span></span>

    ```console
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><a name="BKMK_CancelaListofTasks"></a> <span data-ttu-id="20938-141">Görev listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="20938-141">Cancel a List of Tasks</span></span>

<span data-ttu-id="20938-142">Aynı örneği her görevle ilişkilendirerek, daha fazla görevi iptal etmek için önceki örneği genişletebilirsiniz `CancellationTokenSource` .</span><span class="sxs-lookup"><span data-stu-id="20938-142">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="20938-143">**İptal** düğmesini seçerseniz, henüz tamamlanmamış tüm görevleri iptal edersiniz.</span><span class="sxs-lookup"><span data-stu-id="20938-143">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="downloading-the-example"></a><span data-ttu-id="20938-144">Örnek indiriliyor</span><span class="sxs-lookup"><span data-stu-id="20938-144">Downloading the Example</span></span>

<span data-ttu-id="20938-145">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="20938-145">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="20938-146">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="20938-146">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="20938-147">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-147">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="20938-148">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="20938-148">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="20938-149">**Çözüm Gezgini**' de,,,,,,,, iptal eden bir **Proje projesi için** kısayol menüsünü açın ve **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-149">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="20938-150">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-150">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="20938-151">Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-151">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

 <span data-ttu-id="20938-152">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20938-152">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>

### <a name="building-the-example"></a><span data-ttu-id="20938-153">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="20938-153">Building the Example</span></span>

<span data-ttu-id="20938-154">Örneği kendiniz genişletmek için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi** **olarak iptal** eden ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="20938-154">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="20938-155">Aşağıdaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20938-155">Add the following changes to that project.</span></span> <span data-ttu-id="20938-156">Yıldız işaretleri programdaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="20938-156">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="20938-157">Web adreslerinin bir listesini oluşturmak için bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20938-157">Add a method to create a list of web addresses.</span></span>

    ```vb
    ' ***Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function
    ```

2. <span data-ttu-id="20938-158">İçindeki yöntemi çağırın `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="20938-158">Call the method in `AccessTheWebAsync`.</span></span>

    ```vb
    ' ***Call SetUpURLList to make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()
    ```

3. <span data-ttu-id="20938-159">`AccessTheWebAsync`Listesindeki her bir Web adresini işlemek için aşağıdaki döngüsünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20938-159">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

    ```vb
    ' ***Add a loop to process the list of web addresses.
    For Each url In urlList
        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' Argument ct carries the message if the Cancel button is chosen.
        ' ***Note that the Cancel button can cancel all remaining downloads.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        resultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
    Next
    ```

4. <span data-ttu-id="20938-160">`AccessTheWebAsync`, Uzunlukları gösterdiği için yöntemin herhangi bir şey döndürmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="20938-160">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="20938-161">Return ifadesini kaldırın ve yöntemin dönüş türünü yerine olarak değiştirin <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="20938-161">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```vb
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task
    ```

    <span data-ttu-id="20938-162">Bir `startButton_Click` ifadesi yerine deyimi kullanarak yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="20938-162">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```vb
    Await AccessTheWebAsync(cts.Token)
    ```

5. <span data-ttu-id="20938-163">Programı iptal ederseniz aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="20938-163">If you don’t cancel the program, it produces the following output:</span></span>

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

    <span data-ttu-id="20938-164">İndirmeler tamamlanmadan önce **iptal** düğmesini seçerseniz, çıkış, iptalden önce tamamlanan indirmelerin uzunluklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="20938-164">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><a name="BKMK_CompleteExamples"></a> <span data-ttu-id="20938-165">Tüm örnekler</span><span class="sxs-lookup"><span data-stu-id="20938-165">Complete Examples</span></span>

<span data-ttu-id="20938-166">Aşağıdaki bölümler, önceki örneklerin her birine ilişkin kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="20938-166">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="20938-167">İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="20938-167">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="20938-168">Projeleri [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="20938-168">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="cancel-a-task-example"></a><span data-ttu-id="20938-169">Bir görev örneğini iptal etme</span><span class="sxs-lookup"><span data-stu-id="20938-169">Cancel a Task Example</span></span>

<span data-ttu-id="20938-170">Aşağıdaki kod, tek bir görevi iptal eden örnek için tüm MainWindow. xaml. vb dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="20938-170">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' ***Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)
        ' ***Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***Send a token to carry the message if cancellation is requested.
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

            ' *** If cancellation is requested, an OperationCanceledException results.
        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' ***Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &=
            vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
End Class

' Output for a successful download:

' Ready to download.

' Length of the downloaded string: 158125.

' Or, if you cancel:

' Ready to download.

' Download canceled.
```

### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="20938-171">Görev listesini iptal etme örneği</span><span class="sxs-lookup"><span data-stu-id="20938-171">Cancel a List of Tasks Example</span></span>

<span data-ttu-id="20938-172">Aşağıdaki kod, bir görev listesini iptal eden örnek için tüm MainWindow. xaml. vb dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="20938-172">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).
            Await AccessTheWebAsync(cts.Token)
            '  ***Small change in the display lines.
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' ***Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' ***Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' ***Add a loop to process the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' ***Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' ***Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Output if you do not choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Length of the downloaded string: 158124.

' Length of the downloaded string: 204890.

' Length of the downloaded string: 175488.

' Length of the downloaded string: 145790.

' Downloads complete.

'  Sample output if you choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Downloads canceled.
```

## <a name="see-also"></a><span data-ttu-id="20938-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20938-173">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="20938-174">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20938-174">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="20938-175">Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20938-175">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="20938-176">Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma</span><span class="sxs-lookup"><span data-stu-id="20938-176">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
