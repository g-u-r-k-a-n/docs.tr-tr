---
title: "İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)"
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: feaa1e298cda852492e020a5fa81845fb887f102
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197019"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="6f54b-102">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f54b-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="6f54b-103">Zaman uyumsuz programları, zaman uyumsuz/await özelliklerini kullanarak daha kolay ve daha canlı bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="6f54b-104">Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve derleyicinin zaman uyumsuz kodun genellikle sahip olduğu zor geri çağırma işlevlerini ve devamlılığını işlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="6f54b-105">Async özelliği hakkında daha fazla bilgi için bkz. zaman uyumsuz [programlama, Async ve await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="6f54b-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="6f54b-106">Bu izlenecek yol, bir Web sitesi listesindeki bayt sayısını toplayan bir zaman uyumlu Windows Presentation Foundation (WPF) uygulamasıyla başlar.</span><span class="sxs-lookup"><span data-stu-id="6f54b-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="6f54b-107">İzlenecek yol, yeni özellikleri kullanarak uygulamayı zaman uyumsuz bir çözüme dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6f54b-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="6f54b-108">Uygulamaları kendiniz derlemek istemiyorsanız,C# [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)"zaman uyumsuz örnek: Web 'e (ve Visual Basic) erişme" ' ya erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="6f54b-109">Bu kılavuzda, aşağıdaki görevleri tamamlayadınız:</span><span class="sxs-lookup"><span data-stu-id="6f54b-109">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="6f54b-110">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f54b-110">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="6f54b-111">Basit bir WPF MainWindow tasarımı</span><span class="sxs-lookup"><span data-stu-id="6f54b-111">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="6f54b-112">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="6f54b-112">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="6f54b-113">Gerekli Imports deyimlerini Ekle</span><span class="sxs-lookup"><span data-stu-id="6f54b-113">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="6f54b-114">Zaman uyumlu uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f54b-114">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="6f54b-115">Zaman uyumlu çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="6f54b-115">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="6f54b-116">GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6f54b-116">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="6f54b-117">Sumpageslikleri zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6f54b-117">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="6f54b-118">StartButton_Click öğesini zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6f54b-118">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="6f54b-119">Zaman uyumsuz çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="6f54b-119">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="6f54b-120">GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin</span><span class="sxs-lookup"><span data-stu-id="6f54b-120">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="6f54b-121">Tüm zaman uyumsuz örnek için [örnek](#example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-121">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f54b-122">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="6f54b-122">Prerequisites</span></span>

<span data-ttu-id="6f54b-123">Bilgisayarınızda Visual Studio 2012 veya üzeri yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="6f54b-124">Daha fazla bilgi için bkz. Visual Studio [İndirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) sayfası.</span><span class="sxs-lookup"><span data-stu-id="6f54b-124">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="6f54b-125">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f54b-125">Create a WPF application</span></span>

1. <span data-ttu-id="6f54b-126">Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-126">Start Visual Studio.</span></span>

2. <span data-ttu-id="6f54b-127">Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="6f54b-128">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-128">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="6f54b-129">**Yüklü şablonlar** bölmesinde Visual Basic öğesini seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="6f54b-130">**Ad** metin kutusuna `AsyncExampleWPF`girin ve sonra **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="6f54b-131">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-131">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="6f54b-132">Basit bir WPF MainWindow tasarımı</span><span class="sxs-lookup"><span data-stu-id="6f54b-132">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="6f54b-133">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="6f54b-134">**Araç kutusu** penceresi görünür değilse, **Görünüm** menüsünü açın ve ardından **araç kutusu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="6f54b-135">**MainWindow** penceresine bir **Button** denetimi ve **TextBox** denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="6f54b-136">**TextBox** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6f54b-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="6f54b-137">**Name** özelliğini `resultsTextBox`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-137">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="6f54b-138">**Height** özelliğini 250 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-138">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="6f54b-139">**Width** özelliğini 500 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-139">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="6f54b-140">**Metin** sekmesinde, Lucida Console veya Global tek boşluk gibi tek boşluklu bir yazı tipi belirtin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="6f54b-141">**Düğme** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6f54b-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="6f54b-142">**Name** özelliğini `startButton`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-142">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="6f54b-143">**İçerik** özelliğinin değerini **düğmeden** **başla**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="6f54b-144">Metin kutusunu ve düğmeyi her ikisinin de **MainWindow** penceresinde görünmesi için konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="6f54b-145">WPF XAML Tasarımcısı hakkında daha fazla bilgi için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6f54b-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="6f54b-146">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="6f54b-146">Add a reference</span></span>

1. <span data-ttu-id="6f54b-147">**Çözüm Gezgini**, projenizin adını vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-147">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="6f54b-148">Menü çubuğunda **Proje**, **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="6f54b-149">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-149">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="6f54b-150">İletişim kutusunun üst kısmında, projenizin .NET Framework 4,5 veya üstünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6f54b-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="6f54b-151">**Derlemeler** alanında, zaten seçili değilse **Framework** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="6f54b-152">Ad listesinde, **System .net. http** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-152">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="6f54b-153">İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-153">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="6f54b-154">Gerekli Imports deyimlerini Ekle</span><span class="sxs-lookup"><span data-stu-id="6f54b-154">Add necessary Imports statements</span></span>

1. <span data-ttu-id="6f54b-155">**Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="6f54b-156">Zaten mevcut değilse, kod dosyasının en üstüne aşağıdaki `Imports` deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="6f54b-157">Zaman uyumlu uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f54b-157">Create a synchronous application</span></span>

1. <span data-ttu-id="6f54b-158">MainWindow. xaml tasarım penceresinde, MainWindow. xaml. vb ' de `startButton_Click` olay işleyicisini oluşturmak için **Başlat** düğmesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="6f54b-159">MainWindow. xaml. vb dosyasında aşağıdaki kodu `startButton_Click`gövdesine kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="6f54b-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="6f54b-160">Kod, uygulamayı yönlendiren yöntemi çağırır, `SumPageSizes`ve denetim `startButton_Click`döndüğünde bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6f54b-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="6f54b-161">Zaman uyumlu çözüm kodu aşağıdaki dört yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="6f54b-161">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="6f54b-162">`SumPageSizes`, `SetUpURLList` Web sayfası URL 'Lerinin bir listesini alır ve sonra her bir URL 'YI işlemek için `GetURLContents` ve `DisplayResults` çağırır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="6f54b-163">`SetUpURLList`, Web adreslerinin bir listesini oluşturan ve döndüren.</span><span class="sxs-lookup"><span data-stu-id="6f54b-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="6f54b-164">Her Web sitesinin içeriğini indiren ve bir bayt dizisi olarak içeriği döndüren `GetURLContents`.</span><span class="sxs-lookup"><span data-stu-id="6f54b-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="6f54b-165">her URL için bayt dizisindeki bayt sayısını görüntüleyen `DisplayResults`.</span><span class="sxs-lookup"><span data-stu-id="6f54b-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="6f54b-166">Aşağıdaki dört yöntemi kopyalayın ve sonra MainWindow. xaml. vb ' de `startButton_Click` olay işleyicisi altına yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="6f54b-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
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

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="6f54b-167">Zaman uyumlu çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="6f54b-167">Test the synchronous solution</span></span>

1. <span data-ttu-id="6f54b-168">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="6f54b-169">Aşağıdaki listeye benzer bir çıktı görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="6f54b-169">Output that resembles the following list should appear:</span></span>

    ```console
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

    <span data-ttu-id="6f54b-170">Sayıları görüntülemenin birkaç saniye sürdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="6f54b-171">Bu süre boyunca, Kullanıcı arabirimi iş parçacığı istenen kaynakların indirilmesini beklerken engellenir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="6f54b-172">Sonuç olarak, **Başlat** düğmesini seçtikten sonra görüntü penceresini taşıyamaz, ekranı kaplamaz, simge durumuna küçültebilir ya da kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="6f54b-173">Bu çalışmalar, bayt sayıları görünene kadar başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6f54b-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="6f54b-174">Bir Web sitesi yanıt vermiyorsa, hangi sitenin başarısız olduğunun belirtii olmaz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="6f54b-175">Beklemeyi durdurup programı kapatmanız zordur.</span><span class="sxs-lookup"><span data-stu-id="6f54b-175">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="6f54b-176">GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6f54b-176">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="6f54b-177">Zaman uyumlu çözümü zaman uyumsuz bir çözüme dönüştürmek için, <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> yöntemine ve <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> yöntemine yapılan çağrılar uygulamanın Web 'e eriştiği yer olduğundan, başlamak için en iyi yer `GetURLContents`.</span><span class="sxs-lookup"><span data-stu-id="6f54b-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="6f54b-178">.NET Framework, her iki yöntemin de zaman uyumsuz sürümlerini sağlayarak dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="6f54b-179">`GetURLContents`' de kullanılan yöntemler hakkında daha fazla bilgi için bkz. <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="6f54b-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6f54b-180">Bu izlenecek yolda bulunan adımları izleyerek bazı derleyici hataları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="6f54b-181">Bunları yoksayabilir ve İzlenecek yol ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-181">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="6f54b-182">`GetURLContents` üçüncü satırındaki `GetResponse` zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> metoduna olan yöntemi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="6f54b-183">`GetResponseAsync` <xref:System.Threading.Tasks.Task%601>döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f54b-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="6f54b-184">Bu durumda, *görev dönüş değişkeni*`TResult`, <xref:System.Net.WebResponse>türü vardır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="6f54b-185">Görev, istenen veriler indirildikten ve görevin tamamlanmasını çalıştırdıktan sonra gerçek bir `WebResponse` nesnesi oluşturmak için bir taahhüddir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="6f54b-186">Görevden `WebResponse` değerini almak için aşağıdaki kodda gösterildiği gibi, `GetResponseAsync`çağrısına bir [await](../../../../visual-basic/language-reference/operators/await-operator.md) işleci uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="6f54b-187">`Await` işleci, beklenen görev tamamlanana kadar, `GetURLContents`geçerli metodun yürütülmesini askıya alır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="6f54b-188">Bu arada, Denetim geçerli yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="6f54b-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="6f54b-189">Bu örnekte, geçerli yöntem `GetURLContents`ve arayan `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="6f54b-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="6f54b-190">Görev tamamlandığında, taahhüt edilen `WebResponse` nesnesi, beklenen görevin değeri olarak üretilir ve `response`değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="6f54b-191">Önceki deyim, ne olacağını açıklamak için aşağıdaki iki ifadeye ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="6f54b-192">`webReq.GetResponseAsync` çağrısı `Task(Of WebResponse)` veya `Task<WebResponse>`döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f54b-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="6f54b-193">Sonra, `WebResponse` değerini almak için göreve bir `Await` işleci uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="6f54b-194">Zaman uyumsuz yönteminizin, görevin tamamlanmasına bağlı olmaması durumunda, zaman uyumsuz metoda yapılan çağrıdan sonra ve Await işleci uygulanmadan önce bu iki deyim arasında bu işe devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="6f54b-195">Örnekler için bkz. [nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task. whenall (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="6f54b-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="6f54b-196">Önceki adımda `Await` işlecini eklediğiniz için bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="6f54b-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="6f54b-197">İşleci yalnızca [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="6f54b-198">`CopyTo` çağrısını `CopyToAsync`çağrısı ile değiştirmek için dönüştürme adımlarını tekrarlarken hatayı yoksayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="6f54b-199"><xref:System.IO.Stream.CopyToAsync%2A>olarak çağrılan metodun adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="6f54b-200">`CopyTo` veya `CopyToAsync` yöntemi, baytları bağımsız değişkenine `content`, ve anlamlı bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="6f54b-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="6f54b-201">Zaman uyumlu sürümde, `CopyTo` çağrısı bir değer döndürmeyen basit bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="6f54b-202">Zaman uyumsuz sürüm `CopyToAsync`, bir <xref:System.Threading.Tasks.Task>döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f54b-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="6f54b-203">Görev, "Task (void)" gibi çalışır ve yöntemin beklenmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f54b-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="6f54b-204">Aşağıdaki kodun gösterdiği gibi, `CopyToAsync`çağrısına `Await` veya `await` uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="6f54b-205">Önceki ifade aşağıdaki iki kod satırını abbreviates.</span><span class="sxs-lookup"><span data-stu-id="6f54b-205">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="6f54b-206">`GetURLContents` her şey, yöntem imzasını ayarlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="6f54b-207">`Await` işlecini yalnızca [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="6f54b-208">Aşağıdaki kodun gösterdiği gibi, yöntemi *zaman uyumsuz bir yöntem*olarak işaretlemek için değiştirici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="6f54b-209">Zaman uyumsuz bir yöntemin dönüş türü yalnızca <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="6f54b-210">Visual Basic, yönteminin bir `Task` veya `Task(Of T)`döndüren bir `Function` olması veya metodun bir `Sub`olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="6f54b-211">Genellikle, bir `Sub` yöntemi yalnızca `Sub` gerekli olduğu zaman uyumsuz olay işleyicide kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="6f54b-212">Diğer durumlarda, tamamlanan yöntemin T türünde bir değer döndüren bir [Return](../../../../visual-basic/language-reference/statements/return-statement.md) ifadesine sahipse ve tamamlanmış Yöntem anlamlı bir değer döndürmezse `Task` kullandığınızda `Task(T)` kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6f54b-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="6f54b-213">Daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="6f54b-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

    <span data-ttu-id="6f54b-214">`GetURLContents` yöntemi bir return ifadesine sahiptir ve ifade bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f54b-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="6f54b-215">Bu nedenle, zaman uyumsuz sürümün dönüş türü görev (T), burada T bir bayt dizisidir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="6f54b-216">Yöntem imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="6f54b-216">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="6f54b-217">Dönüş türünü `Task(Of Byte())`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-217">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="6f54b-218">Kurala göre, zaman uyumsuz metotların "Async" ile biten adları vardır. `GetURLContentsAsync`yöntemi yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="6f54b-219">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-219">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="6f54b-220">Bu az değişiklikle, zaman uyumsuz bir metoda `GetURLContents` dönüştürmesi tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="6f54b-221">Sumpageslikleri zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6f54b-221">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="6f54b-222">`SumPageSizes`için önceki yordamdaki adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="6f54b-223">İlk olarak, `GetURLContents` çağrısını zaman uyumsuz bir çağrıya değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="6f54b-224">Daha önce yapmadıysanız, `GetURLContents` `GetURLContentsAsync`olarak çağrılan metodun adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="6f54b-225">Bayt dizi değerini almak için `GetURLContentsAsync` döndüren göreve `Await` uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="6f54b-226">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-226">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="6f54b-227">Önceki atama, aşağıdaki iki kod satırını abbreviates.</span><span class="sxs-lookup"><span data-stu-id="6f54b-227">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="6f54b-228">Yöntemin imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="6f54b-228">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="6f54b-229">Yöntemi `Async` değiştiricisiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-229">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="6f54b-230">Yöntem adına "Async" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-230">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="6f54b-231">`SumPageSizesAsync` T için bir değer döndürmediğinden, bu kez bir görev dönüş değişkeni yok. (yöntemin hiçbir `Return` bildirisi yok.) Ancak, yönteminin bir `Task` olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="6f54b-232">Bu nedenle, `Sub` yöntem türünü `Function`olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="6f54b-233">İşlevin dönüş türü `Task`.</span><span class="sxs-lookup"><span data-stu-id="6f54b-233">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="6f54b-234">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-234">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="6f54b-235">`SumPageSizes` `SumPageSizesAsync` dönüşümü tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="6f54b-236">StartButton_Click öğesini zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6f54b-236">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="6f54b-237">Daha önce yapmadıysanız, olay işleyicisinde `SumPageSizes` çağrılan yöntemin adını `SumPageSizesAsync`olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="6f54b-238">`SumPageSizesAsync` zaman uyumsuz bir yöntem olduğundan, olay işleyicisindeki kodu, sonucu beklemek için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="6f54b-239">`SumPageSizesAsync` çağrısı, `GetURLContentsAsync``CopyToAsync` çağrısını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="6f54b-240">Çağrı bir `Task(T)`değil `Task`döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f54b-240">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="6f54b-241">Önceki yordamlarda olduğu gibi, çağrıyı tek bir deyim veya iki deyim kullanarak dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="6f54b-242">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-242">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="6f54b-243">İşlemi yanlışlıkla yeniden girmeye engel olmak için, **Başlangıç** düğmesini devre dışı bırakmak üzere `startButton_Click` en üstüne aşağıdaki ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="6f54b-244">Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-244">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="6f54b-245">Yeniden giriş hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="6f54b-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="6f54b-246">Son olarak, `Async` değiştiricisini bildirime ekleyerek olay işleyicisinin `SumPagSizesAsync`bekleymasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="6f54b-247">Genellikle, olay işleyicilerinin adları değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="6f54b-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="6f54b-248">Olay işleyicilerinin Visual Basic `Sub` yordamlar olması gerektiğinden, dönüş türü `Task` olarak değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="6f54b-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="6f54b-249">Projenin zaman uyumlu olarak zaman uyumsuz işlemeye dönüştürülmesi işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="6f54b-250">Zaman uyumsuz çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="6f54b-250">Test the asynchronous solution</span></span>

1. <span data-ttu-id="6f54b-251">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="6f54b-252">Zaman uyumlu çözümün çıktısına benzeyen çıkış görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="6f54b-253">Ancak, aşağıdaki farklılıklara dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-253">However, notice the following differences.</span></span>

    - <span data-ttu-id="6f54b-254">İşlem tamamlandıktan sonra sonuçların hepsi aynı anda gerçekleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="6f54b-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="6f54b-255">Örneğin, her iki program de `startButton_Click` metin kutusunu temizleyen bir çizgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="6f54b-256">Tek bir sonuç kümesi görüntülendikten sonra **Başlat** düğmesini ikinci bir kez seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemek amaç.</span><span class="sxs-lookup"><span data-stu-id="6f54b-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="6f54b-257">Zaman uyumlu sürümde, metin kutusu yalnızca sayımlar ikinci kez görüntülenmeden önce temizlenir, İndirmeler tamamlandığında ve Kullanıcı arabirimi iş parçacığı başka iş yapmak için ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="6f54b-258">Zaman uyumsuz sürümde, **Başlat** düğmesini seçtikten sonra metin kutusu hemen temizlenir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="6f54b-259">En önemlisi, indirme sırasında UI iş parçacığı engellenmiyor.</span><span class="sxs-lookup"><span data-stu-id="6f54b-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="6f54b-260">Web kaynakları indirilirken, sayıldıkça ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="6f54b-261">Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alanda bulunan x) seçerek işlemi iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="6f54b-262">GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin</span><span class="sxs-lookup"><span data-stu-id="6f54b-262">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="6f54b-263">.NET Framework kullanabileceğiniz birçok zaman uyumsuz yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f54b-263">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="6f54b-264">Bunlardan biri, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> yöntemi Bu izlenecek yol için yalnızca ihtiyacınız olanları yapar.</span><span class="sxs-lookup"><span data-stu-id="6f54b-264">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="6f54b-265">Bunu, önceki yordamda oluşturduğunuz `GetURLContentsAsync` yöntemi yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="6f54b-266">İlk adım `SumPageSizesAsync` yönteminde bir <xref:System.Net.Http.HttpClient> nesnesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="6f54b-266">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="6f54b-267">Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-267">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="6f54b-268">`SumPageSizesAsync,` `GetURLContentsAsync` yönteminizin çağrısını `HttpClient` yöntemine yönelik bir çağrı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="6f54b-269">Yazdığınız `GetURLContentsAsync` yöntemi kaldırın veya açıklamayı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6f54b-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="6f54b-270">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="6f54b-271">Projenin bu sürümünün davranışı, "zaman uyumsuz çözümü test etmek Için" yordamının açıklandığı, ancak sizin de daha az çaba gösteren davranışla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="6f54b-272">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f54b-272">Example</span></span>

<span data-ttu-id="6f54b-273">Zaman uyumsuz `GetURLContentsAsync` yöntemini kullanan dönüştürülmüş zaman uyumsuz çözümün tam örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-273">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="6f54b-274">Özgün, zaman uyumlu çözüme kesinlikle benzediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6f54b-274">Notice that it strongly resembles the original, synchronous solution.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
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

<span data-ttu-id="6f54b-275">Aşağıdaki kod, `GetByteArrayAsync``HttpClient` yöntemini kullanan çözümün tam örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="6f54b-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
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
            }
        Return urls
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

## <a name="see-also"></a><span data-ttu-id="6f54b-276">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f54b-276">See also</span></span>

- [<span data-ttu-id="6f54b-277">Zaman uyumsuz örnek: Web Walkthrough 'A erişmeC# (ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f54b-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="6f54b-278">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="6f54b-278">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="6f54b-279">Async</span><span class="sxs-lookup"><span data-stu-id="6f54b-279">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="6f54b-280">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f54b-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="6f54b-281">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f54b-281">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="6f54b-282">Görev tabanlı zaman uyumsuz programlama (TAP)</span><span class="sxs-lookup"><span data-stu-id="6f54b-282">Task-based Asynchronous Programming (TAP)</span></span>](https://go.microsoft.com/fwlink/?LinkId=204847)
- [<span data-ttu-id="6f54b-283">Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f54b-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="6f54b-284">Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f54b-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
