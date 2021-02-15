---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)'
title: 'Nasıl yapılır: Async ve Await Kullanarak Birden Çok Web İsteğini Paralel Hale Getirme'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: e1137424911b77ba94a760a4b4b034e45ef83462
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474349"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="ac6b9-103">Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac6b9-103">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="ac6b9-104">Zaman uyumsuz bir yöntemde görevler oluşturulduğunda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-104">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="ac6b9-105">[Await](../../../language-reference/operators/await-operator.md) işleci, görev bitene kadar işlemin devam edemediği yöntemdeki noktada göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-105">The [Await](../../../language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="ac6b9-106">Aşağıdaki örnekte gösterildiği gibi, genellikle bir görev, oluşturulduktan hemen sonra beklediğinde.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-106">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

<span data-ttu-id="ac6b9-107">Ancak, programın gerçekleştirmeye yönelik başka bir işi olması durumunda görevin tamamlanmasına bağlı olmaması durumunda görevi bekleyen görev oluşturmayı ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-107">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>

```vb
' The following line creates and starts the task.
Dim myTask = someWebAccessMethodAsync(url)

' While the task is running, you can do other work that does not depend
' on the results of the task.
' . . . . .

' The application of Await suspends the rest of this method until the task is
' complete.
Dim result = Await myTask
```

<span data-ttu-id="ac6b9-108">Bir görevi başlatma ve bekleme arasında başka görevler de başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-108">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="ac6b9-109">Ek görevler dolaylı olarak paralel olarak çalışır, ancak ek iş parçacığı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-109">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>

<span data-ttu-id="ac6b9-110">Aşağıdaki program, üç zaman uyumsuz Web yüklemesi başlatır ve ardından bunların çağrıldıkları sırayla bekler.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-110">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="ac6b9-111">Programı çalıştırdığınızda, görevlerin Oluşturulma sırasında ve bekledikleri sırada her zaman bitmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-111">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="ac6b9-112">Bunlar oluşturulduğunda çalışmaya başlar ve Yöntem await ifadelerine ulaşmadan önce bir veya daha fazla görev bitebilirler.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-112">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="ac6b9-113">Bu projeyi tamamlayabilmeniz için, bilgisayarınızda Visual Studio 2012 veya üzeri ve .NET Framework 4,5 veya üzeri yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-113">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>

<span data-ttu-id="ac6b9-114">Aynı anda birden çok görevi Başlatan başka bir örnek için, bkz. [nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="ac6b9-114">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

<span data-ttu-id="ac6b9-115">Bu örnek için kodu [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-115">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>

### <a name="to-set-up-the-project"></a><span data-ttu-id="ac6b9-116">Projeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ac6b9-116">To set up the project</span></span>

1. <span data-ttu-id="ac6b9-117">WPF uygulaması ayarlamak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-117">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="ac6b9-118">[Izlenecek yol: Async ve await (Visual Basic) kullanarak Web 'e erişmek](walkthrough-accessing-the-web-by-using-async-and-await.md)için bu adımlarla ilgili ayrıntılı yönergeleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-118">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="ac6b9-119">Metin kutusu ve düğme içeren bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-119">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="ac6b9-120">Düğmeyi adlandırın `startButton` ve metin kutusunu adlandırın `resultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="ac6b9-120">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>

    - <span data-ttu-id="ac6b9-121">İçin bir başvuru ekleyin <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="ac6b9-121">Add a reference for <xref:System.Net.Http>.</span></span>

    - <span data-ttu-id="ac6b9-122">MainWindow. xaml. vb dosyasında `Imports` için bir ifade ekleyin `System.Net.Http` .</span><span class="sxs-lookup"><span data-stu-id="ac6b9-122">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>

### <a name="to-add-the-code"></a><span data-ttu-id="ac6b9-123">Kodu eklemek için</span><span class="sxs-lookup"><span data-stu-id="ac6b9-123">To add the code</span></span>

1. <span data-ttu-id="ac6b9-124">MainWindow. xaml tasarım penceresinde, `startButton_Click` MainWindow. xaml. vb ' de olay işleyicisini oluşturmak için düğmeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-124">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="ac6b9-125">Aşağıdaki kodu kopyalayın ve `startButton_Click` MainWindow. xaml. vb içindeki gövdesine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-125">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     <span data-ttu-id="ac6b9-126">Kod, uygulamayı yönlendiren bir zaman uyumsuz yöntemini çağırır `CreateMultipleTasksAsync` .</span><span class="sxs-lookup"><span data-stu-id="ac6b9-126">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>

3. <span data-ttu-id="ac6b9-127">Aşağıdaki destek yöntemlerini projeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ac6b9-127">Add the following support methods to the project:</span></span>

    - <span data-ttu-id="ac6b9-128">`ProcessURLAsync`<xref:System.Net.Http.HttpClient>bir Web sitesinin içeriğini bayt dizisi olarak indirmek için bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-128">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="ac6b9-129">Destek yöntemi, `ProcessURLAsync` ardından dizinin uzunluğunu görüntüler ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-129">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>

    - <span data-ttu-id="ac6b9-130">`DisplayResults` her URL için bayt dizisindeki bayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-130">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="ac6b9-131">Bu ekranda, her görevin indirilmesi tamamlandığında gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-131">This display shows when each task has finished downloading.</span></span>

     <span data-ttu-id="ac6b9-132">Aşağıdaki yöntemleri kopyalayın ve `startButton_Click` MainWindow. xaml. vb içindeki olay işleyicisinden sonra yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-132">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

4. <span data-ttu-id="ac6b9-133">Son olarak, `CreateMultipleTasksAsync` aşağıdaki adımları gerçekleştiren yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-133">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>

    - <span data-ttu-id="ac6b9-134">Yöntemi `HttpClient` , içindeki yöntemine erişmeniz gereken bir nesne bildirir <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="ac6b9-134">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>

    - <span data-ttu-id="ac6b9-135">Yöntemi, türünde üç görev oluşturur ve başlatır <xref:System.Threading.Tasks.Task%601> , burada `TResult` bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-135">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="ac6b9-136">Her görev bittiğinde, `DisplayResults` görevin URL 'sini ve indirilen içeriklerin uzunluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-136">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="ac6b9-137">Görevler zaman uyumsuz olarak çalıştığından, sonuçların göründüğü sıra, bildirildiği sırayla farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-137">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>

    - <span data-ttu-id="ac6b9-138">Yöntemi her görevin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-138">The method awaits the completion of each task.</span></span> <span data-ttu-id="ac6b9-139">Her `Await` operatör, `CreateMultipleTasksAsync` beklelen görev tamamlanana kadar yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-139">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="ac6b9-140">İşleci, her tamamlanan görevden öğesine yapılan çağrıdan döndürülen değeri de alır `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="ac6b9-140">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>

    - <span data-ttu-id="ac6b9-141">Görevler tamamlandığında ve tamsayı değerleri alınırsa, yöntemi web sitelerinin uzunluklarını toplar ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-141">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>

     <span data-ttu-id="ac6b9-142">Aşağıdaki yöntemi kopyalayın ve çözümünüze yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-142">Copy the following method, and paste it into your solution.</span></span>

    ```vb
    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function
    ```

5. <span data-ttu-id="ac6b9-143">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-143">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="ac6b9-144">Üç görevin her zaman aynı sırada bitmeyeceğini ve bunların tamamların oluşturulma sırası ve bekledikleri sıra olması gerektiğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-144">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>

## <a name="example"></a><span data-ttu-id="ac6b9-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac6b9-145">Example</span></span>

<span data-ttu-id="ac6b9-146">Aşağıdaki kod tam örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-146">The following code contains the full example.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
        resultsTextBox.Clear()
        Await CreateMultipleTasksAsync()
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="ac6b9-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac6b9-147">See also</span></span>

- [<span data-ttu-id="ac6b9-148">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac6b9-148">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="ac6b9-149">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac6b9-149">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="ac6b9-150">Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac6b9-150">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
