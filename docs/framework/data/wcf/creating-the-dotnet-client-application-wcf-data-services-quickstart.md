---
title: .NET Framework Istemci uygulaması oluşturma (WCF Veri Hizmetleri hızlı başlangıç)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 4beaba24e42b15ebc45ece6e5319a2b14df54ab6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975389"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="d1231-102">.NET Framework Istemci uygulaması oluşturma (WCF Veri Hizmetleri hızlı başlangıç)</span><span class="sxs-lookup"><span data-stu-id="d1231-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="d1231-103">Bu, WCF Veri Hizmetleri hızlı başlangıcının son görevidir.</span><span class="sxs-lookup"><span data-stu-id="d1231-103">This is the final task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="d1231-104">Bu görevde, çözüme bir konsol uygulaması ekleyecek, bu yeni istemci uygulamasına açık veri Protokolü (OData) akışına bir başvuru ekleyecek ve oluşturulan istemci veri hizmeti sınıflarını ve istemcisini kullanarak istemci uygulamasından OData akışına erişim elde edersiniz. Kütüphaneler.</span><span class="sxs-lookup"><span data-stu-id="d1231-104">In this task, you will add a console application to the solution, add a reference to the Open Data Protocol (OData) feed into this new client application, and access the OData feed from the client application by using the generated client data service classes and client libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="d1231-105">Bir veri akışına erişmek için .NET Framework tabanlı bir istemci uygulaması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d1231-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="d1231-106">Veri hizmetine OData akışı kullanan herhangi bir uygulama bileşeni erişebilir.</span><span class="sxs-lookup"><span data-stu-id="d1231-106">The data service can be accessed by any application component that consumes an OData feed.</span></span> <span data-ttu-id="d1231-107">Daha fazla bilgi için bkz. [Istemci uygulamasında veri hizmeti kullanma](using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d1231-107">For more information, see [Using a Data Service in a Client Application](using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>

## <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="d1231-108">Visual Studio 'Yu kullanarak istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d1231-108">To create the client application by using Visual Studio</span></span>

1. <span data-ttu-id="d1231-109">**Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**' ye tıklayın ve ardından **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d1231-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="d1231-110">Sol bölmede, **yüklü** > [ **C# Visual** veya **Visual Basic**] > **Windows Desktop**' ı seçin ve ardından **WPF uygulama** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d1231-110">In the left pane, select **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, and then select the **WPF App** template.</span></span>

3. <span data-ttu-id="d1231-111">Proje adı için `NorthwindClient` girin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d1231-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>

4. <span data-ttu-id="d1231-112">MainWindow. xaml dosyasını açın ve XAML kodunu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d1231-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="d1231-113">Projeye veri hizmeti başvurusu eklemek için</span><span class="sxs-lookup"><span data-stu-id="d1231-113">To add a data service reference to the project</span></span>

1. <span data-ttu-id="d1231-114">**Çözüm Gezgini**, NorthwindClient projesine sağ tıklayın, > **hizmet başvurusu** **Ekle** ' ye tıklayın ve ardından **bul**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d1231-114">In **Solution Explorer**, right-click the NorthwindClient project, click **Add** > **Service Reference**, and then click **Discover**.</span></span>

     <span data-ttu-id="d1231-115">Bu, ilk görevde oluşturduğunuz Northwind veri hizmetini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d1231-115">This displays the Northwind data service that you created in the first task.</span></span>

2. <span data-ttu-id="d1231-116">**Ad alanı** metin kutusuna `Northwind`yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d1231-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>

     <span data-ttu-id="d1231-117">Bu, projeye veri hizmeti kaynaklarına erişmek ve bunlarla etkileşim kurmak için kullanılan veri sınıflarını içeren yeni bir kod dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="d1231-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="d1231-118">Veri sınıfları `NorthwindClient.Northwind`ad alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d1231-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>

## <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="d1231-119">WPF uygulamasındaki veri hizmeti verilerine erişmek için</span><span class="sxs-lookup"><span data-stu-id="d1231-119">To access data service data in the WPF application</span></span>

1. <span data-ttu-id="d1231-120">**NorthwindClient**altında **Çözüm Gezgini** , projeye sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d1231-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>

2. <span data-ttu-id="d1231-121">**Başvuru Ekle** iletişim kutusunda, **.net** sekmesine tıklayın, System. Data. Services. Client. dll derlemesini seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d1231-121">In the **Add Reference** dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span>

3. <span data-ttu-id="d1231-122">**NorthwindClient**altındaki **Çözüm Gezgini** , MainWindow. xaml dosyası için kod sayfasını açın ve aşağıdaki `using` ifadesini (`Imports` Visual Basic) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1231-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. <span data-ttu-id="d1231-123">Bu veri hizmetini sorgulayan ve sonucu bir <xref:System.Data.Services.Client.DataServiceCollection%601> `MainWindow` sınıfına bağlayan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d1231-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>

    > [!NOTE]
    > <span data-ttu-id="d1231-124">Ana bilgisayar adı `localhost:12345`, Northwind Data Service örneğinizi barındıran sunucu ve bağlantı noktasıyla değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d1231-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. <span data-ttu-id="d1231-125">`MainWindow` sınıfına değişiklikleri kaydeden aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d1231-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="d1231-126">NorthwindClient uygulamasını derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d1231-126">To build and run the NorthwindClient application</span></span>

1. <span data-ttu-id="d1231-127">**Çözüm Gezgini**, NorthwindClient projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="d1231-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>

2. <span data-ttu-id="d1231-128">Uygulamayı başlatmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d1231-128">Press **F5** to start the application.</span></span>

     <span data-ttu-id="d1231-129">Bu, çözümü oluşturur ve istemci uygulamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="d1231-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="d1231-130">Veriler hizmetten istenir ve konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d1231-130">Data is requested from the service and displayed in the console.</span></span>

3. <span data-ttu-id="d1231-131">Data Grid 'in **Quantity** sütunundaki bir değeri düzenleyin ve ardından **Kaydet**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d1231-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>

     <span data-ttu-id="d1231-132">Değişiklikler veri hizmetine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="d1231-132">Changes are saved to the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d1231-133">NorthwindClient uygulamasının bu sürümü varlıkların eklenmesini ve silinmesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d1231-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d1231-134">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="d1231-134">Next Steps</span></span>

<span data-ttu-id="d1231-135">Örnek Northwind OData akışına erişen istemci uygulamasını başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="d1231-135">You have successfully created the client application that accesses the sample Northwind OData feed.</span></span> <span data-ttu-id="d1231-136">Ayrıca WCF Veri Hizmetleri hızlı başlangıcı 'nı tamamladınız!</span><span class="sxs-lookup"><span data-stu-id="d1231-136">You've also completed the WCF Data Services quickstart!</span></span>

<span data-ttu-id="d1231-137">.NET Framework uygulamasından bir OData akışına erişme hakkında daha fazla bilgi için, bkz. [WCF veri Hizmetleri Istemci kitaplığı](wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="d1231-137">For more information about accessing an OData feed from a .NET Framework application, see [WCF Data Services Client Library](wcf-data-services-client-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1231-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1231-138">See also</span></span>

- [<span data-ttu-id="d1231-139">Başlarken</span><span class="sxs-lookup"><span data-stu-id="d1231-139">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="d1231-140">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d1231-140">Resources</span></span>](wcf-data-services-resources.md)
