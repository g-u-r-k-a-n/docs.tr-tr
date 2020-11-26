---
title: 'Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 05c59bde424049eb5bef8f8bd09c472b58eaa9ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248831"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="ddb0b-102">Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="ddb0b-102">How to: Create a workflow service that consumes an existing service contract</span></span>

<span data-ttu-id="ddb0b-103">.NET Framework 4,5 özelliği, sözleşmenin ilk iş akışı geliştirme biçiminde Web Hizmetleri ve iş akışları arasında daha iyi tümleştirme sunar.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-103">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="ddb0b-104">Sözleşme-ilk iş akışı geliştirme aracı, sözleşmeyi önce kod içinde tasarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="ddb0b-105">Araç daha sonra, sözleşmede bulunan işlemler için araç kutusunda bir etkinlik şablonu otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ddb0b-106">Bu konuda, bir sözleşmenin ilk iş akışı hizmeti oluşturmaya yönelik adım adım yönergeler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="ddb0b-107">Sözleşme-ilk iş akışı hizmeti geliştirme hakkında daha fazla bilgi için bkz. [Ilk Iş akışı hizmeti geliştirmeyi sözleşme](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="ddb0b-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="ddb0b-108">İş akışı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ddb0b-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="ddb0b-109">Visual Studio'da, **Dosya**, **Yeni Proje**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="ddb0b-110">**Şablonlar** ağacındaki **C#** düğümünün altında bulunan **WCF** düğümünü seçin ve **WCF iş akışı hizmeti uygulama** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="ddb0b-111">Yeni projeyi adlandırın `ContractFirst` ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="ddb0b-112">Hizmet sözleşmesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="ddb0b-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="ddb0b-113">**Çözüm Gezgini** projeye sağ tıklayın ve **Ekle**, **Yeni öğe..**. seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="ddb0b-114">Sol taraftaki **kod** düğümünü ve sağ taraftaki **sınıf** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="ddb0b-115">Yeni sınıfı adlandırın `IBookService` ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="ddb0b-116">Görüntülenen kod penceresinin üst kısmında bir using ifadesi ekleyin `System.Servicemodel` .</span><span class="sxs-lookup"><span data-stu-id="ddb0b-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="ddb0b-117">Örnek sınıf tanımını aşağıdaki arabirim tanımına değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="ddb0b-118">**CTRL + SHIFT + B** tuşlarına basarak projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="ddb0b-119">Hizmet sözleşmesini içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="ddb0b-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="ddb0b-120">**Çözüm Gezgini** ' de projeye sağ tıklayın ve **hizmet sözleşmesini içeri aktar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="ddb0b-121">Altında **\<Current Project>** , tüm alt düğümleri açın ve **IBookService**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="ddb0b-122">**Tamam** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="ddb0b-123">Bir iletişim kutusu açılır, işlemin başarıyla tamamlandığını ve oluşturulan etkinliklerin, projeyi oluşturduktan sonra araç kutusu 'nda gözükgörünmediğini size uyaracaktır.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="ddb0b-124">**Tamam** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="ddb0b-125">İçeri aktarılan etkinliklerin araç kutusunda görünmesi için **CTRL + SHIFT + B** tuşlarına basarak projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="ddb0b-126">**Çözüm Gezgini**' de, Service1. xamlx ' yi açın.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="ddb0b-127">İş akışı hizmeti tasarımcıda görünür.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="ddb0b-128">**Sıra** etkinliğini seçin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="ddb0b-129">Özellikler penceresi, **..** . öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="ddb0b-130">düğmesine basın. **ImplementedContract**</span><span class="sxs-lookup"><span data-stu-id="ddb0b-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="ddb0b-131">Görüntülenen tür **koleksiyonu Düzenleyicisi** penceresinde, **tür** açılan listesine tıklayın ve **türlere gözatmayı seçin...**</span><span class="sxs-lookup"><span data-stu-id="ddb0b-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="ddb0b-132">girişte.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-132">entry.</span></span> <span data-ttu-id="ddb0b-133">**Bir .NET türü görüntüle ve Seç** iletişim kutusunda, **\<Current Project>** tüm alt düğümler ' i açın ve **IBookService**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="ddb0b-134">**Tamam** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-134">Click **OK**.</span></span> <span data-ttu-id="ddb0b-135">**Tür koleksiyonu Düzenleyicisi** Iletişim kutusunda **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="ddb0b-136">**ReceiveRequest** ve **SendResponse** etkinliklerini seçin ve silin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="ddb0b-137">Araç kutusundan bir **Buy_ReceiveAndSendReply** ve **Checkout_Receive** etkinliğini **sıralı hizmet** etkinliğine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
