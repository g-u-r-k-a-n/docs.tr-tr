---
title: İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: ea14bc651258684fd31940aa6b88f9731348dcd1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978277"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a><span data-ttu-id="714f3-102">İş Akışı Hizmetlerine İşlemlerin Giriş ve Çıkış Akışını Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="714f3-102">Flowing Transactions into and out of Workflow Services</span></span>
<span data-ttu-id="714f3-103">İş akışı hizmetleri ve istemcileri işlemlere katılabilir.</span><span class="sxs-lookup"><span data-stu-id="714f3-103">Workflow services and clients can participate in transactions.</span></span>  <span data-ttu-id="714f3-104">Bir hizmet işleminin bir ortam işleminin parçası haline gelmesi için, bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliğine <xref:System.ServiceModel.Activities.Receive> etkinlik koyun.</span><span class="sxs-lookup"><span data-stu-id="714f3-104">For a service operation to become part of an ambient transaction, place a <xref:System.ServiceModel.Activities.Receive> activity within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="714f3-105"><xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.TransactedReceiveScope> içindeki bir <xref:System.ServiceModel.Activities.SendReply> etkinliği tarafından yapılan çağrılar, çevresel işlem içinde de yapılır.</span><span class="sxs-lookup"><span data-stu-id="714f3-105">Any calls made by a <xref:System.ServiceModel.Activities.Send> or a <xref:System.ServiceModel.Activities.SendReply> activity within the <xref:System.ServiceModel.Activities.TransactedReceiveScope> will also be made within the ambient transaction.</span></span> <span data-ttu-id="714f3-106">Bir iş akışı istemci uygulaması, <xref:System.Activities.Statements.TransactionScope> etkinliğini kullanarak ve ortam işlemini kullanarak hizmet işlemlerini çağıran bir ortam işlemi oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="714f3-106">A workflow client application can create an ambient transaction by using the <xref:System.Activities.Statements.TransactionScope> activity and call service operations using the ambient transaction.</span></span> <span data-ttu-id="714f3-107">Bu konu, işlemlere katılan bir iş akışı hizmeti ve iş akışı istemcisi oluşturma konusunda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="714f3-107">This topic walks you through creating a workflow service and workflow client that participate in transactions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="714f3-108">Bir iş akışı hizmeti örneği bir işlem içinde yüklenirse ve iş akışı bir <xref:System.Activities.Statements.Persist> etkinlik içeriyorsa, iş akışı örneği işlem zaman aşımına uğrayana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="714f3-108">If a workflow service instance is loaded within a transaction and the workflow contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will block until the transaction times out.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="714f3-109"><xref:System.ServiceModel.Activities.TransactedReceiveScope> kullandığınızda, tüm alma işlemlerini iş akışına <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlikler dahilinde yerleştirmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="714f3-109">Whenever you use a <xref:System.ServiceModel.Activities.TransactedReceiveScope> it is recommended to place all Receives in the workflow within <xref:System.ServiceModel.Activities.TransactedReceiveScope> activities.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="714f3-110"><xref:System.ServiceModel.Activities.TransactedReceiveScope> kullanılırken ve iletileri yanlış sırada geldiğinde, ilk sipariş dışı ileti teslim edilmeye çalışılırken iş akışı iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="714f3-110">When using <xref:System.ServiceModel.Activities.TransactedReceiveScope> and messages arrive in the incorrect order, the workflow will be aborted when trying to deliver the first out of order message.</span></span> <span data-ttu-id="714f3-111">İş akışınızın iş akışı kimliği her zaman tutarlı bir durdurma noktasında olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="714f3-111">You must make sure your workflow is always at a consistent stopping point when the workflow idles.</span></span> <span data-ttu-id="714f3-112">Bu, iş akışını önceki bir Kalıcılık noktasından yeniden başlatmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="714f3-112">This will allow you to restart the workflow from a previous persistence point should the workflow be aborted.</span></span>  
  
### <a name="create-a-shared-library"></a><span data-ttu-id="714f3-113">Paylaşılan kitaplık oluşturma</span><span class="sxs-lookup"><span data-stu-id="714f3-113">Create a shared library</span></span>  
  
1. <span data-ttu-id="714f3-114">Yeni boş bir Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="714f3-114">Create a new empty Visual Studio Solution.</span></span>  
  
2. <span data-ttu-id="714f3-115">`Common`adlı yeni bir sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-115">Add a new class library project called `Common`.</span></span> <span data-ttu-id="714f3-116">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="714f3-116">Add references to the following assemblies:</span></span>  
  
    - <span data-ttu-id="714f3-117">System. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="714f3-117">System.Activities.dll</span></span>  
  
    - <span data-ttu-id="714f3-118">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="714f3-118">System.ServiceModel.dll</span></span>  
  
    - <span data-ttu-id="714f3-119">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="714f3-119">System.ServiceModel.Activities.dll</span></span>  
  
    - <span data-ttu-id="714f3-120">System.Transactions.dll</span><span class="sxs-lookup"><span data-stu-id="714f3-120">System.Transactions.dll</span></span>  
  
3. <span data-ttu-id="714f3-121">`Common` projesine `PrintTransactionInfo` adlı yeni bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-121">Add a new class called `PrintTransactionInfo` to the `Common` project.</span></span> <span data-ttu-id="714f3-122">Bu sınıf <xref:System.Activities.NativeActivity> türetilir ve <xref:System.Activities.NativeActivity.Execute%2A> yöntemini aşırı yükler.</span><span class="sxs-lookup"><span data-stu-id="714f3-122">This class is derived from <xref:System.Activities.NativeActivity> and overloads the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     <span data-ttu-id="714f3-123">Bu, ortam işlem hakkındaki bilgileri görüntüleyen ve bu konuda kullanılan hizmet ve istemci iş akışlarında kullanılan yerel bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="714f3-123">This is a native activity that displays information about the ambient transaction and is used in both the service and client workflows used in this topic.</span></span> <span data-ttu-id="714f3-124">Bu etkinliği **araç kutusunun** **ortak** bölümünde kullanılabilir hale getirmek için çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="714f3-124">Build the solution to make this activity available in the **Common** section of the **Toolbox**.</span></span>  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="714f3-125">İş akışı hizmetini uygulama</span><span class="sxs-lookup"><span data-stu-id="714f3-125">Implement the workflow service</span></span>  
  
1. <span data-ttu-id="714f3-126">`Common` projesine `WorkflowService` adlı yeni bir WCF Iş akışı hizmeti ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-126">Add a new WCF Workflow Service, called `WorkflowService` to the `Common` project.</span></span> <span data-ttu-id="714f3-127">Bunu yapmak için `Common` projesine tıklayın, **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **Iş akışı** ' nı seçin ve **WCF iş akışı hizmeti**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="714f3-127">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **WCF Workflow Service**.</span></span>  
  
     ![Iş akışı hizmeti ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. <span data-ttu-id="714f3-129">Varsayılan `ReceiveRequest` ve `SendResponse` etkinliklerini silin.</span><span class="sxs-lookup"><span data-stu-id="714f3-129">Delete the default `ReceiveRequest` and `SendResponse` activities.</span></span>  
  
3. <span data-ttu-id="714f3-130"><xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip `Sequential Service` etkinliğine bırakın.</span><span class="sxs-lookup"><span data-stu-id="714f3-130">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity into the `Sequential Service` activity.</span></span> <span data-ttu-id="714f3-131">Aşağıdaki örnekte gösterildiği gibi, Text özelliğini `"Workflow Service starting ..."` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-131">Set the text property to `"Workflow Service starting ..."` as shown in the following example.</span></span>  
  
     <span data-ttu-id="714f3-132">! [Sıralı hizmet etkinliğine bir WriteLine etkinliği ekleme (./Media/flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)</span><span class="sxs-lookup"><span data-stu-id="714f3-132">![Adding a WriteLine activity to the Sequential Service activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)</span></span>  
  
4. <span data-ttu-id="714f3-133"><xref:System.Activities.Statements.WriteLine> etkinliğinden sonra bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="714f3-133">Drag and drop a <xref:System.ServiceModel.Activities.TransactedReceiveScope> after the <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="714f3-134"><xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği **araç kutusunun** **mesajlaşma** bölümünde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="714f3-134">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity can be found in the **Messaging** section of the **Toolbox**.</span></span> <span data-ttu-id="714f3-135"><xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği iki bölümden oluşan **istek** ve **gövdeden**oluşur.</span><span class="sxs-lookup"><span data-stu-id="714f3-135">The <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity is composed of two sections **Request** and **Body**.</span></span> <span data-ttu-id="714f3-136">**İstek** bölümü <xref:System.ServiceModel.Activities.Receive> etkinliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="714f3-136">The **Request** section contains the <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="714f3-137">**Gövde** bölümü bir ileti alındıktan sonra bir işlem içinde yürütülecek etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="714f3-137">The **Body** section contains the activities to execute within a transaction after a message has been received.</span></span>  
  
     ![TransactedReceiveScope etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. <span data-ttu-id="714f3-139"><xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliğini seçin ve **değişkenler** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-139">Select the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity and click the **Variables** button.</span></span> <span data-ttu-id="714f3-140">Aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-140">Add the following variables.</span></span>  
  
     ![TransactedReceiveScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > <span data-ttu-id="714f3-142">Varsayılan olarak bulunan veri değişkenini silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714f3-142">You can delete the data variable that is there by default.</span></span> <span data-ttu-id="714f3-143">Ayrıca var olan tanıtıcı değişkenini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714f3-143">You can also use the existing handle variable.</span></span>  
  
6. <span data-ttu-id="714f3-144"><xref:System.ServiceModel.Activities.Receive> etkinliğini <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliğinin **istek** bölümünde sürükleyin ve bırakın.</span><span class="sxs-lookup"><span data-stu-id="714f3-144">Drag and drop a <xref:System.ServiceModel.Activities.Receive> activity within the **Request** section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="714f3-145">Aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="714f3-145">Set the following properties:</span></span>  
  
    |<span data-ttu-id="714f3-146">Özellik</span><span class="sxs-lookup"><span data-stu-id="714f3-146">Property</span></span>|<span data-ttu-id="714f3-147">Değer</span><span class="sxs-lookup"><span data-stu-id="714f3-147">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="714f3-148">CanCreateInstance</span><span class="sxs-lookup"><span data-stu-id="714f3-148">CanCreateInstance</span></span>|<span data-ttu-id="714f3-149">True (onay kutusunu işaretleyin)</span><span class="sxs-lookup"><span data-stu-id="714f3-149">True (check the checkbox)</span></span>|  
    |<span data-ttu-id="714f3-150">OperationName</span><span class="sxs-lookup"><span data-stu-id="714f3-150">OperationName</span></span>|<span data-ttu-id="714f3-151">StartSample</span><span class="sxs-lookup"><span data-stu-id="714f3-151">StartSample</span></span>|  
    |<span data-ttu-id="714f3-152">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="714f3-152">ServiceContractName</span></span>|<span data-ttu-id="714f3-153">Itransactionsample</span><span class="sxs-lookup"><span data-stu-id="714f3-153">ITransactionSample</span></span>|  
  
     <span data-ttu-id="714f3-154">İş akışı şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="714f3-154">The workflow should look like this:</span></span>  
  
     ![Alma etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. <span data-ttu-id="714f3-156"><xref:System.ServiceModel.Activities.Receive> etkinliğinde **tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="714f3-156">Click the **Define...** link in the <xref:System.ServiceModel.Activities.Receive> activity and make the following settings:</span></span>  
  
     ![Alma etkinliği için ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. <span data-ttu-id="714f3-158"><xref:System.Activities.Statements.Sequence> etkinliğini sürükleyip <xref:System.ServiceModel.Activities.TransactedReceiveScope>gövde bölümüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="714f3-158">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the Body section of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="714f3-159"><xref:System.Activities.Statements.Sequence> etkinliği içinde iki <xref:System.Activities.Statements.WriteLine> etkinliği sürükleyip bırakın ve aşağıdaki tabloda gösterildiği gibi <xref:System.Activities.Statements.WriteLine.Text%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-159">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop two <xref:System.Activities.Statements.WriteLine> activities and set the <xref:System.Activities.Statements.WriteLine.Text%2A> properties as shown in the following table.</span></span>  
  
    |<span data-ttu-id="714f3-160">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="714f3-160">Activity</span></span>|<span data-ttu-id="714f3-161">Değer</span><span class="sxs-lookup"><span data-stu-id="714f3-161">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="714f3-162">1\. WriteLine</span><span class="sxs-lookup"><span data-stu-id="714f3-162">1st WriteLine</span></span>|<span data-ttu-id="714f3-163">"Hizmet: alma tamamlandı"</span><span class="sxs-lookup"><span data-stu-id="714f3-163">"Service: Receive Completed"</span></span>|  
    |<span data-ttu-id="714f3-164">2\. WriteLine</span><span class="sxs-lookup"><span data-stu-id="714f3-164">2nd WriteLine</span></span>|<span data-ttu-id="714f3-165">"Hizmet: alındı =" + requestMessage</span><span class="sxs-lookup"><span data-stu-id="714f3-165">"Service: Received = " + requestMessage</span></span>|  
  
     <span data-ttu-id="714f3-166">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="714f3-166">The workflow should now look like this:</span></span>  
  
     ![WriteLine etkinlikleri eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. <span data-ttu-id="714f3-168">`PrintTransactionInfo` etkinliğini <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliğinde **gövdesinde** ikinci <xref:System.Activities.Statements.WriteLine> etkinlikten sonra sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="714f3-168">Drag and drop the `PrintTransactionInfo` activity after the second <xref:System.Activities.Statements.WriteLine> activity in the **Body** in the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span>  
  
     ![PrintTransactionInfo eklendikten sonra sıra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. <span data-ttu-id="714f3-170">`PrintTransactionInfo` etkinliğinden sonra bir <xref:System.Activities.Statements.Assign> etkinliğini sürükleyip bırakın ve aşağıdaki tabloya göre özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-170">Drag and drop an <xref:System.Activities.Statements.Assign> activity after the `PrintTransactionInfo` activity and set its properties according to the following table.</span></span>  
  
    |<span data-ttu-id="714f3-171">Özellik</span><span class="sxs-lookup"><span data-stu-id="714f3-171">Property</span></span>|<span data-ttu-id="714f3-172">Değer</span><span class="sxs-lookup"><span data-stu-id="714f3-172">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="714f3-173">Bitiş</span><span class="sxs-lookup"><span data-stu-id="714f3-173">To</span></span>|<span data-ttu-id="714f3-174">replyMessage</span><span class="sxs-lookup"><span data-stu-id="714f3-174">replyMessage</span></span>|  
    |<span data-ttu-id="714f3-175">Değer</span><span class="sxs-lookup"><span data-stu-id="714f3-175">Value</span></span>|<span data-ttu-id="714f3-176">"Hizmet: Yanıt gönderiliyor."</span><span class="sxs-lookup"><span data-stu-id="714f3-176">"Service: Sending reply."</span></span>|  
  
11. <span data-ttu-id="714f3-177"><xref:System.Activities.Statements.Assign> etkinliğinden sonra bir <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: BEGIN Reply" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-177">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.Activities.Statements.Assign> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Begin reply."</span></span>  
  
     <span data-ttu-id="714f3-178">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="714f3-178">The workflow should now look like this:</span></span>  
  
     ![Assign ve WriteLine eklendikten sonra](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. <span data-ttu-id="714f3-180"><xref:System.ServiceModel.Activities.Receive> etkinliğine sağ tıklayıp **SendReply oluştur** ' u seçin ve son <xref:System.Activities.Statements.WriteLine> etkinliğinden sonra yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="714f3-180">Right click the <xref:System.ServiceModel.Activities.Receive> activity and select **Create SendReply** and paste it after the last <xref:System.Activities.Statements.WriteLine> activity.</span></span> <span data-ttu-id="714f3-181">`SendReplyToReceive` etkinliğinde **tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın.</span><span class="sxs-lookup"><span data-stu-id="714f3-181">Click the **Define...** link in the `SendReplyToReceive` activity and make the following settings.</span></span>  
  
     ![Yanıt iletisi ayarları](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. <span data-ttu-id="714f3-183">`SendReplyToReceive` etkinliğinden sonra bir <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: Reply gönderildi" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-183">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `SendReplyToReceive` activity and set it’s <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Reply sent."</span></span>  
  
14. <span data-ttu-id="714f3-184">İş akışının alt kısmındaki bir <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Service: Workflow bitiyor, çıkmak için ENTER tuşuna basın" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-184">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the bottom of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Service: Workflow ends, press ENTER to exit."</span></span>  
  
     <span data-ttu-id="714f3-185">Tamamlanmış hizmet iş akışı şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="714f3-185">The completed service workflow should look like this:</span></span>  
  
     ![Hizmet Iş akışını doldurun](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a><span data-ttu-id="714f3-187">İş akışı istemcisini uygulama</span><span class="sxs-lookup"><span data-stu-id="714f3-187">Implement the workflow client</span></span>  
  
1. <span data-ttu-id="714f3-188">`Common` projesine `WorkflowClient` adlı yeni bir WCF Iş akışı uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-188">Add a new WCF Workflow application, called `WorkflowClient` to the `Common` project.</span></span> <span data-ttu-id="714f3-189">Bunu yapmak için `Common` projesine tıklayın, **Ekle**, **Yeni öğe...** öğesini seçin, **yüklü şablonlar** altında **iş akışı** ' nı seçin ve **etkinlik**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="714f3-189">To do this right click the `Common` project, select **Add**, **New Item ...**, Select **Workflow** under **Installed Templates** and select **Activity**.</span></span>  
  
     ![Etkinlik projesi ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. <span data-ttu-id="714f3-191"><xref:System.Activities.Statements.Sequence> etkinliğini tasarım yüzeyine sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="714f3-191">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the design surface.</span></span>  
  
3. <span data-ttu-id="714f3-192"><xref:System.Activities.Statements.Sequence> etkinliği içinde <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini `"Client: Workflow starting"`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-192">Within the <xref:System.Activities.Statements.Sequence> activity drag and drop a <xref:System.Activities.Statements.WriteLine> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to `"Client: Workflow starting"`.</span></span> <span data-ttu-id="714f3-193">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="714f3-193">The workflow should now look like this:</span></span>  
  
     ![WriteLine etkinliği ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. <span data-ttu-id="714f3-195"><xref:System.Activities.Statements.TransactionScope> etkinliğini <xref:System.Activities.Statements.WriteLine> etkinliğinden sonra sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="714f3-195">Drag and drop a <xref:System.Activities.Statements.TransactionScope> activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  <span data-ttu-id="714f3-196"><xref:System.Activities.Statements.TransactionScope> etkinliğini seçin, değişkenler düğmesine tıklayın ve aşağıdaki değişkenleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-196">Select the <xref:System.Activities.Statements.TransactionScope> activity, click the Variables button and add the following variables.</span></span>  
  
     ![TransactionScope 'a değişken ekleme](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. <span data-ttu-id="714f3-198"><xref:System.Activities.Statements.Sequence> etkinliğini sürükleyip <xref:System.Activities.Statements.TransactionScope> etkinliğinin gövdesine bırakın.</span><span class="sxs-lookup"><span data-stu-id="714f3-198">Drag and drop a <xref:System.Activities.Statements.Sequence> activity into the body of the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
6. <span data-ttu-id="714f3-199"><xref:System.Activities.Statements.Sequence> içinde `PrintTransactionInfo` etkinliğini sürükleyip bırakma</span><span class="sxs-lookup"><span data-stu-id="714f3-199">Drag and drop a `PrintTransactionInfo` activity within the <xref:System.Activities.Statements.Sequence></span></span>  
  
7. <span data-ttu-id="714f3-200"><xref:System.Activities.Statements.WriteLine> etkinliğini `PrintTransactionInfo` etkinliğinden sonra sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Client: Send başlatılıyor" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-200">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the `PrintTransactionInfo` activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Beginning Send".</span></span> <span data-ttu-id="714f3-201">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="714f3-201">The workflow should now look like this:</span></span>  
  
     ![Istemci ekleniyor: gönderme etkinlikleri başlatılıyor](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. <span data-ttu-id="714f3-203"><xref:System.ServiceModel.Activities.Send> etkinliğini <xref:System.Activities.Statements.Assign> etkinliğinden sonra sürükleyip bırakın ve aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="714f3-203">Drag and drop a <xref:System.ServiceModel.Activities.Send> activity after the <xref:System.Activities.Statements.Assign> activity and set the following properties:</span></span>  
  
    |<span data-ttu-id="714f3-204">Özellik</span><span class="sxs-lookup"><span data-stu-id="714f3-204">Property</span></span>|<span data-ttu-id="714f3-205">Değer</span><span class="sxs-lookup"><span data-stu-id="714f3-205">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="714f3-206">EndpointConfigurationName</span><span class="sxs-lookup"><span data-stu-id="714f3-206">EndpointConfigurationName</span></span>|<span data-ttu-id="714f3-207">workflowServiceEndpoint</span><span class="sxs-lookup"><span data-stu-id="714f3-207">workflowServiceEndpoint</span></span>|  
    |<span data-ttu-id="714f3-208">OperationName</span><span class="sxs-lookup"><span data-stu-id="714f3-208">OperationName</span></span>|<span data-ttu-id="714f3-209">StartSample</span><span class="sxs-lookup"><span data-stu-id="714f3-209">StartSample</span></span>|  
    |<span data-ttu-id="714f3-210">ServiceContractName</span><span class="sxs-lookup"><span data-stu-id="714f3-210">ServiceContractName</span></span>|<span data-ttu-id="714f3-211">Itransactionsample</span><span class="sxs-lookup"><span data-stu-id="714f3-211">ITransactionSample</span></span>|  
  
     <span data-ttu-id="714f3-212">İş akışı artık şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="714f3-212">The workflow should now look like this:</span></span>  
  
     ![Gönderme etkinliği özelliklerini ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. <span data-ttu-id="714f3-214">**Tanımla...** bağlantısına tıklayın ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="714f3-214">Click the **Define...** link and make the following settings:</span></span>  
  
     ![Etkinlik iletisi ayarlarını gönder](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. <span data-ttu-id="714f3-216"><xref:System.ServiceModel.Activities.Send> etkinliğine sağ tıklayın ve **ReceiveReply oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="714f3-216">Right click the <xref:System.ServiceModel.Activities.Send> activity and select **Create ReceiveReply**.</span></span> <span data-ttu-id="714f3-217"><xref:System.ServiceModel.Activities.ReceiveReply> etkinlik <xref:System.ServiceModel.Activities.Send> etkinliğinden sonra otomatik olarak yerleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="714f3-217">The <xref:System.ServiceModel.Activities.ReceiveReply> activity will be automatically placed after the <xref:System.ServiceModel.Activities.Send> activity.</span></span>  
  
11. <span data-ttu-id="714f3-218">Tanımla... öğesine tıklayın ReceiveReplyForSend etkinliğinin bağlantısını yapın ve aşağıdaki ayarları yapın:</span><span class="sxs-lookup"><span data-stu-id="714f3-218">Click the Define... link on the ReceiveReplyForSend activity and make the following settings:</span></span>  
  
     ![ReceiveForSend ileti ayarlarını ayarlama](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. <span data-ttu-id="714f3-220"><xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri arasında <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Client: Send tamamlanmıştır" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-220">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity between the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> activities and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client: Send complete."</span></span>  
  
13. <span data-ttu-id="714f3-221"><xref:System.ServiceModel.Activities.ReceiveReply> etkinliğinden sonra bir <xref:System.Activities.Statements.WriteLine> etkinliğini sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Istemci tarafı: Yanıtla alındı =" + replyMessage olarak ayarlayın</span><span class="sxs-lookup"><span data-stu-id="714f3-221">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity after the <xref:System.ServiceModel.Activities.ReceiveReply> activity and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client side: Reply received = " + replyMessage</span></span>  
  
14. <span data-ttu-id="714f3-222">`PrintTransactionInfo` etkinliğini <xref:System.Activities.Statements.WriteLine> etkinliğinden sonra sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="714f3-222">Drag and drop a `PrintTransactionInfo` activity after the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
15. <span data-ttu-id="714f3-223"><xref:System.Activities.Statements.WriteLine> etkinliğini iş akışının sonuna sürükleyip bırakın ve <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğini "Istemci iş akışı bitişi" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="714f3-223">Drag and drop a <xref:System.Activities.Statements.WriteLine> activity at the end of the workflow and set its <xref:System.Activities.Statements.WriteLine.Text%2A> property to "Client workflow ends."</span></span> <span data-ttu-id="714f3-224">Tamamlanan istemci iş akışı aşağıdaki diyagram gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="714f3-224">The completed client workflow should look like the following diagram.</span></span>  
  
     ![Tamamlanan istemci iş akışı](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. <span data-ttu-id="714f3-226">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="714f3-226">Build the solution.</span></span>  
  
### <a name="create-the-service-application"></a><span data-ttu-id="714f3-227">Hizmet uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="714f3-227">Create the Service application</span></span>  
  
1. <span data-ttu-id="714f3-228">Çözüme `Service` adlı yeni bir konsol uygulaması projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-228">Add a new Console Application project called `Service` to the solution.</span></span> <span data-ttu-id="714f3-229">Aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="714f3-229">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="714f3-230">System. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="714f3-230">System.Activities.dll</span></span>  
  
    2. <span data-ttu-id="714f3-231">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="714f3-231">System.ServiceModel.dll</span></span>  
  
    3. <span data-ttu-id="714f3-232">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="714f3-232">System.ServiceModel.Activities.dll</span></span>  
  
2. <span data-ttu-id="714f3-233">Oluşturulan Program.cs dosyasını ve aşağıdaki kodu açın:</span><span class="sxs-lookup"><span data-stu-id="714f3-233">Open the generated Program.cs file and the following code:</span></span>  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {                
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };         
          }  
    ```  
  
3. <span data-ttu-id="714f3-234">Projeye aşağıdaki App. config dosyasını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-234">Add the following app.config file to the project.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a><span data-ttu-id="714f3-235">İstemci uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="714f3-235">Create the client application</span></span>  
  
1. <span data-ttu-id="714f3-236">Çözüme `Client` adlı yeni bir konsol uygulaması projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-236">Add a new Console Application project called `Client` to the solution.</span></span> <span data-ttu-id="714f3-237">System. Activities. dll dosyasına bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-237">Add a reference to System.Activities.dll.</span></span>  
  
2. <span data-ttu-id="714f3-238">Program.cs dosyasını açın ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="714f3-238">Open the program.cs file and add the following code.</span></span>  
  
    ```csharp
    class Program  
    {  

        private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
        static void Main(string[] args)  
        {  
            //Build client  
            Console.WriteLine("Building the client.");  
            WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
            client.Completed = Program.Completed;  
            client.Aborted = Program.Aborted;  
            client.OnUnhandledException = Program.OnUnhandledException;  
            //Wait for service to start  
            Console.WriteLine("Press ENTER once service is started.");  
            Console.ReadLine();  
  
            //Start the client              
            Console.WriteLine("Starting the client.");  
            client.Run();  
            syncEvent.WaitOne();  
  
            //Sample complete  
            Console.WriteLine();  
            Console.WriteLine("Client complete. Press ENTER to exit.");  
            Console.ReadLine();  
        }  
  
        private static void Completed(WorkflowApplicationCompletedEventArgs e)  
        {  
            Program.syncEvent.Set();  
        }  
  
        private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
        {  
            Console.WriteLine("Client Aborted: {0}", e.Reason);  
            Program.syncEvent.Set();  
        }  
  
        private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
            return UnhandledExceptionAction.Cancel;  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="714f3-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="714f3-239">See also</span></span>

- [<span data-ttu-id="714f3-240">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="714f3-240">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="714f3-241">Windows Communication Foundation İşlemleri Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="714f3-241">Windows Communication Foundation Transactions Overview</span></span>](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
