---
description: 'Hakkında daha fazla bilgi edinin: zaman uyumsuz görevleri bir süre sonra Iptal etme (Visual Basic)'
title: Zaman Uyumsuz Görevleri Belirli Bir Süre Sonunda İptal Etme
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: fa1711017128dd32f29adfd87a540676371d02cf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431639"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="932f5-103">Zaman uyumsuz görevleri bir süre sonra iptal et (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="932f5-103">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>

<span data-ttu-id="932f5-104">İşlemin bitmesini beklemek istemiyorsanız yöntemini kullanarak bir süre sonra zaman uyumsuz bir işlemi iptal edebilirsiniz  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="932f5-104">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="932f5-105">Bu yöntem, ifadesi tarafından belirlenen süre içinde tamamlanmamış olan ilişkili görevlerin iptalini zamanlar `CancelAfter` .</span><span class="sxs-lookup"><span data-stu-id="932f5-105">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="932f5-106">Bu örnek, bir Web sitesi listesini indirmek ve her birinin içindekilerin uzunluğunu göstermek için [zaman uyumsuz bir görevi veya görev listesini (Visual Basic) iptal](cancel-an-async-task-or-a-list-of-tasks.md) etmek üzere geliştirilmiş koda ekler.</span><span class="sxs-lookup"><span data-stu-id="932f5-106">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="932f5-107">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümü ve .NET Framework 4,5 veya üzeri bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="932f5-107">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="932f5-108">Örnek indiriliyor</span><span class="sxs-lookup"><span data-stu-id="932f5-108">Downloading the Example</span></span>

<span data-ttu-id="932f5-109">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı Ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="932f5-109">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="932f5-110">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="932f5-110">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="932f5-111">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="932f5-111">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="932f5-112">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="932f5-112">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="932f5-113">**Çözüm Gezgini**, **zaman** hatası ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="932f5-113">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="932f5-114">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="932f5-114">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="932f5-115">Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="932f5-115">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="932f5-116">Çıktının tüm Web siteleri, Web sitesi veya bazı Web siteleri için çıktıyı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="932f5-116">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

 <span data-ttu-id="932f5-117">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyasını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="932f5-117">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="932f5-118">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="932f5-118">Building the Example</span></span>

<span data-ttu-id="932f5-119">Bu konudaki örnek, bir görev listesini iptal etmek için [zaman uyumsuz bir görevi veya görev listesini iptal etmek (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) için geliştirilmiş projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="932f5-119">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="932f5-120">Örnek, aynı kullanıcı arabirimini kullanır, ancak **iptal** düğmesi açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="932f5-120">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="932f5-121">Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi** olarak iptal eden **ınlıftasks** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="932f5-121">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="932f5-122">Bu konudaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="932f5-122">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="932f5-123">Görevler iptal edildi olarak işaretlenmeden önce en uzun süreyi belirtmek için, `CancelAfter` `startButton_Click` Aşağıdaki örnekte gösterildiği gibi öğesine bir çağrı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="932f5-123">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="932f5-124">Toplama, yıldız işareti ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="932f5-124">The addition is marked with asterisks.</span></span>

```vb
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

    ' Instantiate the CancellationTokenSource.
    cts = New CancellationTokenSource()

    resultsTextBox.Clear()

    Try
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        ' can adjust the time.)
        cts.CancelAfter(2500)

        Await AccessTheWebAsync(cts.Token)
        resultsTextBox.Text &= vbCrLf & "Downloads complete."

    Catch ex As OperationCanceledException
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

    Catch ex As Exception
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
    End Try

    ' Set the CancellationTokenSource to Nothing when the download is complete.
    cts = Nothing
End Sub
```

<span data-ttu-id="932f5-125">Çıktının tüm Web siteleri, Web sitesi veya bazı Web siteleri için çıktıyı gösterebileceğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="932f5-125">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="932f5-126">Aşağıdaki çıktı bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="932f5-126">The following output is a sample:</span></span>

```console
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="932f5-127">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="932f5-127">Complete Example</span></span>

<span data-ttu-id="932f5-128">Aşağıdaki kod, örnek için MainWindow. xaml. vb dosyasının tüm metinkodudur.</span><span class="sxs-lookup"><span data-stu-id="932f5-128">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="932f5-129">Yıldız işaretleri bu örnek için eklenen öğeleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="932f5-129">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="932f5-130">İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="932f5-130">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="932f5-131">Projeyi [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="932f5-131">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
            ' can adjust the time.)
            cts.CancelAfter(2500)

            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Process each element in the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' Add a method that creates a list of web addresses.
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

' Sample output:

' Length of the downloaded string: 35990.

' Length of the downloaded string: 407399.

' Length of the downloaded string: 226091.

' Downloads canceled.
```

## <a name="see-also"></a><span data-ttu-id="932f5-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="932f5-132">See also</span></span>

- [<span data-ttu-id="932f5-133">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="932f5-133">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="932f5-134">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="932f5-134">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="932f5-135">Zaman uyumsuz bir görevi veya görev listesini iptal etme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="932f5-135">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="932f5-136">Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="932f5-136">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="932f5-137">Zaman uyumsuz örnek: uygulamanıza Ince ayar yapma</span><span class="sxs-lookup"><span data-stu-id="932f5-137">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
