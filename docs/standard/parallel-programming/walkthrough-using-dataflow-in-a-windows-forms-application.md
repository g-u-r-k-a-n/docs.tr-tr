---
description: 'Daha fazla bilgi edinin: Izlenecek yol: Windows Forms uygulamasında veri akışı kullanma'
title: "İzlenecek yol: Windows Forms Uygulaması'nda Veri Akışı Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
ms.openlocfilehash: 761f47b3250827a8d5cbee8bb444d172e9ae950f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798049"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a><span data-ttu-id="93f4b-103">İzlenecek yol: Windows Forms Uygulaması'nda Veri Akışı Kullanma</span><span class="sxs-lookup"><span data-stu-id="93f4b-103">Walkthrough: Using Dataflow in a Windows Forms Application</span></span>

<span data-ttu-id="93f4b-104">Bu belgede, Windows Forms uygulamasında görüntü işlemeyi gerçekleştiren bir veri akışı bloğu ağı oluşturma işlemi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-104">This document demonstrates how to create a network of dataflow blocks that perform image processing in a Windows Forms application.</span></span>  
  
 <span data-ttu-id="93f4b-105">Bu örnek, belirtilen klasörden görüntü dosyalarını yükler, bileşik bir görüntü oluşturur ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93f4b-105">This example loads image files from the specified folder, creates a composite image, and displays the result.</span></span> <span data-ttu-id="93f4b-106">Örnek, görüntüleri ağ üzerinden yönlendirmek için veri akışı modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="93f4b-106">The example uses the dataflow model to route images through the network.</span></span> <span data-ttu-id="93f4b-107">Veri akışı modelinde, bir programın bağımsız bileşenleri ileti göndererek birbirleriyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="93f4b-107">In the dataflow model, independent components of a program communicate with one another by sending messages.</span></span> <span data-ttu-id="93f4b-108">Bir bileşen bir ileti aldığında, bazı işlemleri gerçekleştirir ve sonucu başka bir bileşene geçirir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-108">When a component receives a message, it performs some action and then passes the result to another component.</span></span> <span data-ttu-id="93f4b-109">Bunu, bir uygulamanın bir programdaki işlem sırasını denetlemek için denetim yapılarını (örneğin, koşullu deyimler, döngüler vb.) kullandığı denetim akışı modeliyle karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="93f4b-109">Compare this with the control flow model, in which an application uses control structures, for example, conditional statements, loops, and so on, to control the order of operations in a program.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="93f4b-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="93f4b-110">Prerequisites</span></span>  

 <span data-ttu-id="93f4b-111">Bu yönergeyi başlamadan önce [veri akışını](dataflow-task-parallel-library.md) okuyun.</span><span class="sxs-lookup"><span data-stu-id="93f4b-111">Read [Dataflow](dataflow-task-parallel-library.md) before you start this walkthrough.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a><span data-ttu-id="93f4b-112">Bölümler</span><span class="sxs-lookup"><span data-stu-id="93f4b-112">Sections</span></span>  

 <span data-ttu-id="93f4b-113">Bu izlenecek yol aşağıdaki bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="93f4b-113">This walkthrough contains the following sections:</span></span>  
  
- [<span data-ttu-id="93f4b-114">Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="93f4b-114">Creating the Windows Forms Application</span></span>](#winforms)  
  
- [<span data-ttu-id="93f4b-115">Veri akışı ağını oluşturma</span><span class="sxs-lookup"><span data-stu-id="93f4b-115">Creating the Dataflow Network</span></span>](#network)  
  
- [<span data-ttu-id="93f4b-116">Veri akışı ağını Kullanıcı arabirimine bağlama</span><span class="sxs-lookup"><span data-stu-id="93f4b-116">Connecting the Dataflow Network to the User Interface</span></span>](#ui)  
  
- [<span data-ttu-id="93f4b-117">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="93f4b-117">The Complete Example</span></span>](#complete)  
  
<a name="winforms"></a>

## <a name="creating-the-windows-forms-application"></a><span data-ttu-id="93f4b-118">Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="93f4b-118">Creating the Windows Forms Application</span></span>  

 <span data-ttu-id="93f4b-119">Bu bölümde temel Windows Forms uygulamasının nasıl oluşturulacağı ve ana forma nasıl denetim ekleneceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93f4b-119">This section describes how to create the basic Windows Forms application and add controls to the main form.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="93f4b-120">Windows Forms uygulamasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="93f4b-120">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="93f4b-121">Visual Studio 'da, Visual C# veya Visual Basic **Windows Forms uygulama** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="93f4b-121">In Visual Studio, create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="93f4b-122">Bu belgede, proje adlandırılır `CompositeImages` .</span><span class="sxs-lookup"><span data-stu-id="93f4b-122">In this document, the project is named `CompositeImages`.</span></span>  
  
2. <span data-ttu-id="93f4b-123">Ana form için form tasarımcısında, Form1.cs (Visual Basic için Form1. vb), bir <xref:System.Windows.Forms.ToolStrip> denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="93f4b-123">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="93f4b-124"><xref:System.Windows.Forms.ToolStripButton>Denetime denetim ekleyin <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="93f4b-124">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="93f4b-125"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>Özelliğini olarak ayarlayın <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> **klasörü seçin**.</span><span class="sxs-lookup"><span data-stu-id="93f4b-125">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Choose Folder**.</span></span>  
  
4. <span data-ttu-id="93f4b-126">Denetime ikinci bir <xref:System.Windows.Forms.ToolStripButton> denetim ekleyin <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="93f4b-126">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="93f4b-127"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>Özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> , <xref:System.Windows.Forms.ToolStripItem.Text%2A> **iptal** edilecek özelliği ve özelliğini olarak ayarlayın <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> `False` .</span><span class="sxs-lookup"><span data-stu-id="93f4b-127">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="93f4b-128"><xref:System.Windows.Forms.PictureBox>Ana forma bir nesne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="93f4b-128">Add a <xref:System.Windows.Forms.PictureBox> object to the main form.</span></span> <span data-ttu-id="93f4b-129"><xref:System.Windows.Forms.Control.Dock%2A>Özelliğini olarak ayarlayın <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="93f4b-129">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
<a name="network"></a>

## <a name="creating-the-dataflow-network"></a><span data-ttu-id="93f4b-130">Veri akışı ağını oluşturma</span><span class="sxs-lookup"><span data-stu-id="93f4b-130">Creating the Dataflow Network</span></span>  

 <span data-ttu-id="93f4b-131">Bu bölümde, görüntü işlemeyi gerçekleştiren veri akışı ağının nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93f4b-131">This section describes how to create the dataflow network that performs image processing.</span></span>  
  
### <a name="to-create-the-dataflow-network"></a><span data-ttu-id="93f4b-132">Veri akışı ağını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="93f4b-132">To Create the Dataflow Network</span></span>  
  
1. <span data-ttu-id="93f4b-133">Projenize System.Threading.Tasks.Dataflow.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="93f4b-133">Add a reference to System.Threading.Tasks.Dataflow.dll to your project.</span></span>  
  
2. <span data-ttu-id="93f4b-134">Form1.cs (Visual Basic için Form1. vb) 'in aşağıdaki `using` ( `Using` Visual Basic) deyimlerini içerdiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="93f4b-134">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Using` in Visual Basic) statements:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. <span data-ttu-id="93f4b-135">Sınıfına aşağıdaki veri üyelerini ekleyin `Form1` :</span><span class="sxs-lookup"><span data-stu-id="93f4b-135">Add the following data members to the `Form1` class:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. <span data-ttu-id="93f4b-136">Aşağıdaki yöntemini `CreateImageProcessingNetwork` `Form1` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="93f4b-136">Add the following method, `CreateImageProcessingNetwork`, to the `Form1` class.</span></span> <span data-ttu-id="93f4b-137">Bu yöntem, görüntü işleme ağını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93f4b-137">This method creates the image processing network.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. <span data-ttu-id="93f4b-138">Yöntemini uygulayın `LoadBitmaps` .</span><span class="sxs-lookup"><span data-stu-id="93f4b-138">Implement the `LoadBitmaps` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. <span data-ttu-id="93f4b-139">Yöntemini uygulayın `CreateCompositeBitmap` .</span><span class="sxs-lookup"><span data-stu-id="93f4b-139">Implement the `CreateCompositeBitmap` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > <span data-ttu-id="93f4b-140">Yönteminin C# sürümü, `CreateCompositeBitmap` nesneleri verimli bir şekilde işlemeyi sağlamak için işaretçiler kullanır <xref:System.Drawing.Bitmap?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="93f4b-140">The C# version of the `CreateCompositeBitmap` method uses pointers to enable efficient processing of the <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="93f4b-141">Bu nedenle, [unsafe](../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanabilmeniz için projenizdeki **güvenli olmayan koda izin ver** seçeneğini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-141">Therefore, you must enable the **Allow unsafe code** option in your project in order to use the [unsafe](../../csharp/language-reference/keywords/unsafe.md) keyword.</span></span> <span data-ttu-id="93f4b-142">Visual C# projesinde güvenli olmayan kodun nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="93f4b-142">For more information about how to enable unsafe code in a Visual C# project, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="93f4b-143">Aşağıdaki tablo, ağın üyelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="93f4b-143">The following table describes the members of the network.</span></span>  
  
|<span data-ttu-id="93f4b-144">Üye</span><span class="sxs-lookup"><span data-stu-id="93f4b-144">Member</span></span>|<span data-ttu-id="93f4b-145">Tür</span><span class="sxs-lookup"><span data-stu-id="93f4b-145">Type</span></span>|<span data-ttu-id="93f4b-146">Description</span><span class="sxs-lookup"><span data-stu-id="93f4b-146">Description</span></span>|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="93f4b-147">Bir klasör yolunu girdi olarak alır ve <xref:System.Drawing.Bitmap> çıktı olarak bir nesne koleksiyonu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93f4b-147">Takes a folder path as input and produces a collection of <xref:System.Drawing.Bitmap> objects as output.</span></span>|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="93f4b-148">Bir <xref:System.Drawing.Bitmap> nesne koleksiyonunu girdi olarak alır ve çıkış olarak bileşik bir bit eşlem üretir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-148">Takes a collection of <xref:System.Drawing.Bitmap> objects as input and produces a composite bitmap as output.</span></span>|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="93f4b-149">Form üzerinde bileşik bit eşlemi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93f4b-149">Displays the composite bitmap on the form.</span></span>|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="93f4b-150">İşlemin iptal edildiğini belirten bir resim görüntüler ve kullanıcının başka bir klasör seçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="93f4b-150">Displays an image to indicate that the operation is canceled and enables the user to select another folder.</span></span>|  
  
 <span data-ttu-id="93f4b-151">Veri akışı bloklarını bir ağ oluşturacak şekilde bağlamak için bu örnek <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="93f4b-151">To connect the dataflow blocks to form a network, this example uses the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method.</span></span> <span data-ttu-id="93f4b-152"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>Yöntemi, <xref:System.Predicate%601> hedef bloğunun bir iletiyi kabul edip etmeyeceğini belirleyen bir nesneyi alan aşırı yüklenmiş bir sürüm içerir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-152">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method contains an overloaded version that takes a <xref:System.Predicate%601> object that determines whether the target block accepts or rejects a message.</span></span> <span data-ttu-id="93f4b-153">Bu filtreleme mekanizması ileti bloklarının yalnızca belirli değerleri almasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="93f4b-153">This filtering mechanism enables message blocks to receive only certain values.</span></span> <span data-ttu-id="93f4b-154">Bu örnekte, ağ iki şekilde dallandırma yapabilir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-154">In this example, the network can branch in one of two ways.</span></span> <span data-ttu-id="93f4b-155">Ana dal görüntüleri diskten yükler, bileşik görüntüyü oluşturur ve bu görüntüyü form üzerinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93f4b-155">The main branch loads the images from disk, creates the composite image, and displays that image on the form.</span></span> <span data-ttu-id="93f4b-156">Alternatif dal geçerli işlemi iptal eder.</span><span class="sxs-lookup"><span data-stu-id="93f4b-156">The alternate branch cancels the current operation.</span></span> <span data-ttu-id="93f4b-157"><xref:System.Predicate%601>Nesneler, Ana daldaki veri akışı bloklarını, belirli iletileri reddeterek alternatif dala geçiş yapmak üzere etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-157">The <xref:System.Predicate%601> objects enable the dataflow blocks along the main branch to switch to the alternative branch by rejecting certain messages.</span></span> <span data-ttu-id="93f4b-158">Örneğin, Kullanıcı işlemi iptal ederse, veri akışı bloğu `createCompositeBitmap` `null` `Nothing` çıkış olarak (Visual Basic) üretir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-158">For example, if the user cancels the operation, the dataflow block `createCompositeBitmap` produces `null` (`Nothing` in Visual Basic) as its output.</span></span> <span data-ttu-id="93f4b-159">Veri akışı bloğu `displayCompositeBitmap` `null` giriş değerlerini reddeder ve bu nedenle ileti sunulur `operationCancelled` .</span><span class="sxs-lookup"><span data-stu-id="93f4b-159">The dataflow block `displayCompositeBitmap` rejects `null` input values, and therefore, the message is offered to `operationCancelled`.</span></span> <span data-ttu-id="93f4b-160">Veri akışı bloğu `operationCancelled` tüm iletileri kabul eder ve bu nedenle işlemin iptal edildiğini göstermek için bir resim görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93f4b-160">The dataflow block `operationCancelled` accepts all messages and therefore, displays an image to indicate that the operation is canceled.</span></span>  
  
 <span data-ttu-id="93f4b-161">Aşağıdaki çizim görüntü işleme ağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="93f4b-161">The following illustration shows the image processing network:</span></span>  
  
 ![Görüntü işleme ağını gösteren çizim.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 <span data-ttu-id="93f4b-163">`displayCompositeBitmap`Ve `operationCancelled` veri akışı blokları Kullanıcı arabiriminde işlem yaptığından, bu eylemlerin Kullanıcı arabirimi iş parçacığında gerçekleştirilmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-163">Because the `displayCompositeBitmap` and `operationCancelled` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="93f4b-164">Bunu gerçekleştirmek için, oluşturma sırasında, bu nesnelerin her biri, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği olarak ayarlanmış bir nesne sağlar <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="93f4b-164">To accomplish this, during construction, these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="93f4b-165"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>Yöntemi, <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme bağlamında çalışmayı gerçekleştiren bir nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93f4b-165">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="93f4b-166">Yöntemi, `CreateImageProcessingNetwork` Kullanıcı arabirimi iş parçacığında çalışan **Klasör Seç** düğmesinin işleyicisinden çağrıldığı için, `displayCompositeBitmap` ve `operationCancelled` veri akışı blokları için Eylemler kullanıcı arabirimi iş parçacığında da çalışır.</span><span class="sxs-lookup"><span data-stu-id="93f4b-166">Because the `CreateImageProcessingNetwork` method is called from the handler of the **Choose Folder** button, which runs on the user-interface thread, the actions for the `displayCompositeBitmap` and `operationCancelled` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="93f4b-167">Bu örnek, özelliği ayarlamak yerine paylaşılan bir iptal belirteci kullanır, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> çünkü <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> Özellik kalıcı olarak veri akışı blok yürütmeyi iptal eder.</span><span class="sxs-lookup"><span data-stu-id="93f4b-167">This example uses a shared cancellation token instead of setting the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution.</span></span> <span data-ttu-id="93f4b-168">İptal belirteci, Kullanıcı bir veya daha fazla işlemi iptal ettiğinde bile, bu örneğin aynı veri akışı ağını birden çok kez yeniden kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="93f4b-168">A cancellation token enables this example to reuse the same dataflow network multiple times, even when the user cancels one or more operations.</span></span> <span data-ttu-id="93f4b-169"><xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>Bir veri akışı bloğunun yürütülmesini kalıcı olarak iptal etmek için kullanan bir örnek için bkz. [nasıl yapılır: veri akışı bloğunu iptal](how-to-cancel-a-dataflow-block.md)etme.</span><span class="sxs-lookup"><span data-stu-id="93f4b-169">For an example that uses <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> to permanently cancel the execution of a dataflow block, see [How to: Cancel a Dataflow Block](how-to-cancel-a-dataflow-block.md).</span></span>  
  
<a name="ui"></a>

## <a name="connecting-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="93f4b-170">Veri akışı ağını Kullanıcı arabirimine bağlama</span><span class="sxs-lookup"><span data-stu-id="93f4b-170">Connecting the Dataflow Network to the User Interface</span></span>  

 <span data-ttu-id="93f4b-171">Bu bölümde, veri akışı ağının Kullanıcı arabirimine nasıl bağlanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93f4b-171">This section describes how to connect the dataflow network to the user interface.</span></span> <span data-ttu-id="93f4b-172">Bileşik görüntünün ve işlemin iptalinin oluşturulması, **Klasör Seç** ve **iptal** düğmelerinden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="93f4b-172">The creation of the composite image and cancellation of the operation are initiated from the **Choose Folder** and **Cancel** buttons.</span></span> <span data-ttu-id="93f4b-173">Kullanıcı bu düğmelerden birini seçtiğinde, uygun eylem zaman uyumsuz bir şekilde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="93f4b-173">When the user chooses either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="93f4b-174">Veri akışı ağını Kullanıcı arabirimine bağlamak için</span><span class="sxs-lookup"><span data-stu-id="93f4b-174">To Connect the Dataflow Network to the User Interface</span></span>  
  
1. <span data-ttu-id="93f4b-175">Ana form için form tasarımcısında, <xref:System.Windows.Forms.ToolStripItem.Click> **Klasör Seç** düğmesine yönelik olay için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="93f4b-175">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
2. <span data-ttu-id="93f4b-176"><xref:System.Windows.Forms.ToolStripItem.Click> **Klasör Seç** düğmesine yönelik olayı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="93f4b-176">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. <span data-ttu-id="93f4b-177">Ana form için form tasarımcısında, <xref:System.Windows.Forms.ToolStripItem.Click> **iptal** düğmesine yönelik olay için bir olay işleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="93f4b-177">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="93f4b-178"><xref:System.Windows.Forms.ToolStripItem.Click> **İptal** düğmesi için olayı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="93f4b-178">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="93f4b-179">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="93f4b-179">The Complete Example</span></span>  

 <span data-ttu-id="93f4b-180">Aşağıdaki örnekte bu izlenecek yol için tüm kod gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-180">The following example shows the complete code for this walkthrough.</span></span>  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 <span data-ttu-id="93f4b-181">Aşağıdaki çizimde ortak \ örnek resimler \ klasörü için tipik çıkış gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="93f4b-181">The following illustration shows typical output for the common \Sample Pictures\ folder.</span></span>  
  
 <span data-ttu-id="93f4b-182">![Windows Forms uygulaması](media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span><span class="sxs-lookup"><span data-stu-id="93f4b-182">![The Windows Forms Application](media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span></span>  

## <a name="see-also"></a><span data-ttu-id="93f4b-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93f4b-183">See also</span></span>

- [<span data-ttu-id="93f4b-184">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="93f4b-184">Dataflow</span></span>](dataflow-task-parallel-library.md)
