---
title: MSMQ 4.0'da Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: cc4da0deea0de2cd8b3bb8e8f2ba9b8a17e3cc60
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919392"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="3f9bf-102">MSMQ 4.0'da Zehirli İleti İşleme</span><span class="sxs-lookup"><span data-stu-id="3f9bf-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="3f9bf-103">Bu örnek, bir hizmette çok zararlı ileti işlemenin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="3f9bf-104">Bu örnek, [IŞLENEN MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="3f9bf-105">Bu örnek `netMsmqBinding`kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="3f9bf-106">Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="3f9bf-107">Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="3f9bf-108">Daha kesin olarak, istemci iletileri bir kuyruğa gönderir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="3f9bf-109">Hizmet kuyruktaki iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-109">The service receives messages from the queue.</span></span> <span data-ttu-id="3f9bf-110">Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="3f9bf-111">Zararlı ileti, iletiyi okuyan hizmet iletiyi işleyemeyecek ve bu nedenle iletinin okunduğu işlemi sonlandırdığında bir kuyruktan sürekli okunan bir iletidir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="3f9bf-112">Bu gibi durumlarda ileti yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="3f9bf-113">Bu, iletiyle ilgili bir sorun varsa teorik olarak sonsuza kadar devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="3f9bf-114">Bu, yalnızca kuyruktan okumak ve hizmet işlemini çağırmak için işlem kullandığınızda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="3f9bf-115">NetMsmqBinding, MSMQ sürümüne bağlı olarak, zarar iletilerinin tam algılanması için sınırlı algılamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="3f9bf-116">İleti kired olarak algılandıktan sonra, çeşitli yollarla işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="3f9bf-117">MSMQ sürümüne bağlı olarak, NetMsmqBinding, zarar iletilerinin tam işlenmesini sağlamak için sınırlı işlemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="3f9bf-118">Bu örnek, Windows Server 2003 ve Windows XP platformunda ve Windows Vista 'da sunulan tam zararlı tesislerde sunulan sınırlı zarar özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-118">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="3f9bf-119">Her iki örnekte de amaç, zarar mesajını sıradan başka bir kuyruğa taşır ve bu da bir zarar iletisi hizmeti tarafından hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="3f9bf-120">MSMQ v 4.0 zarar Işleme örneği</span><span class="sxs-lookup"><span data-stu-id="3f9bf-120">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="3f9bf-121">Windows Vista 'da, MSMQ, zarar iletilerini depolamak için kullanılabilen bir zarar alt sıra özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-121">In Windows Vista, MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="3f9bf-122">Bu örnek, Windows Vista kullanarak zarar iletileriyle ilgili en iyi yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-122">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="3f9bf-123">Windows Vista 'da zehirli ileti algılama oldukça karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-123">The poison message detection in Windows Vista is quite sophisticated.</span></span> <span data-ttu-id="3f9bf-124">Algılamaya yardımcı olan 3 özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="3f9bf-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A>, belirli bir iletinin kuyruktan yeniden okunduğu ve işlenmek üzere uygulamaya dağıtıldığı sayıdır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="3f9bf-126">İleti uygulamaya dağıtılamadı veya uygulama işlemi hizmet işleminde geri götürüliyorsa, bir ileti sıraya geri alındığında kuyruktan yeniden okunabilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="3f9bf-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>, iletinin yeniden deneme kuyruğuna kaç kez taşındığını sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="3f9bf-128"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> ulaşıldığında, ileti yeniden deneme kuyruğuna taşınır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="3f9bf-129">Özellik <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>, ileti yeniden deneme sırasından ana sıraya geri taşındıktan sonraki zaman gecikmesi olur.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="3f9bf-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 0 ' a sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="3f9bf-131">İleti yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-131">The message is tried again.</span></span> <span data-ttu-id="3f9bf-132">İletiyi okuma denemeleri başarısız olduysa, ileti kired olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="3f9bf-133">İleti kired olarak işaretlendiğinde, ileti <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> Numaralandırmadaki ayarlara göre dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="3f9bf-134">Olası değerleri yeniden yinelemek için:</span><span class="sxs-lookup"><span data-stu-id="3f9bf-134">To reiterate the possible values:</span></span>

- <span data-ttu-id="3f9bf-135">Hata (varsayılan): dinleyiciye ve ayrıca hizmet konağına hata vermek Için.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-135">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="3f9bf-136">Bırakın: iletiyi bırakmak Için.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-136">Drop: To drop the message.</span></span>

- <span data-ttu-id="3f9bf-137">Taşı: iletiyi zarar iletisi alt kuyruğuna taşımak Için.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="3f9bf-138">Bu değer yalnızca Windows Vista 'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-138">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="3f9bf-139">Reddet: iletiyi, gönderenin teslim edilemeyen ileti kuyruğuna geri göndererek iletiyi reddetmek Için.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="3f9bf-140">Bu değer yalnızca Windows Vista 'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-140">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="3f9bf-141">Örnek, zarar iletisi için `Move` eğilimini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="3f9bf-142">`Move`, iletinin zarar alt kuyruğuna taşınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-142">`Move` causes the message to move to the poison sub-queue.</span></span>

 <span data-ttu-id="3f9bf-143">Hizmet sözleşmesi, kuyruklarla birlikte kullanılmak üzere uygun tek yönlü bir hizmeti tanımlayan `IOrderProcessor`.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="3f9bf-144">Hizmet işlemi, sırayı işlediğini belirten bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="3f9bf-145">Zarar iletisi işlevselliğini göstermek için `SubmitPurchaseOrder` hizmeti işlemi, hizmetin rastgele bir çağrısında işlemi geri almak için bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="3f9bf-146">Bu, iletinin sıraya geri alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="3f9bf-147">Sonuç olarak ileti, zarar olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="3f9bf-148">Yapılandırma, zarar iletisini zarar alt kuyruğuna taşımak üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 <span data-ttu-id="3f9bf-149">Hizmet yapılandırması şu zarar iletisi özelliklerini içerir: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`ve `receiveErrorHandling` aşağıdaki yapılandırma dosyasında gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="3f9bf-150">Zarar iletisi kuyruğundan iletileri işleme</span><span class="sxs-lookup"><span data-stu-id="3f9bf-150">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="3f9bf-151">Zarar iletisi hizmeti, son zarar iletisi kuyruğundan iletileri okur ve bunları işler.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="3f9bf-152">Zarar iletisi sırasındaki iletiler, iletiyi işleyen hizmete yönelik mesajlar, bu da zarar iletisi hizmet uç noktasından farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="3f9bf-153">Bu nedenle, zarar iletisi hizmeti sıradaki iletileri okuduğunda, WCF kanal katmanı uç noktalarında uyuşmazlığını bulur ve iletiyi göndermez.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="3f9bf-154">Bu durumda, ileti sipariş işleme hizmetine değinmekte, ancak zarar iletisi hizmeti tarafından alınmakta olur.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="3f9bf-155">İleti farklı bir uç noktaya adreslenmiş olsa bile iletiyi almaya devam etmek için, eşleşme ölçütünün iletinin adreslendiği tüm hizmet uç noktaları ile eşleşmesi durumunda adresleri filtrelemek için bir `ServiceBehavior` eklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="3f9bf-156">Bu, zarar ileti sırasından okunan iletileri başarıyla işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-156">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="3f9bf-157">Zarar iletisi Hizmeti uygulamasının kendisi, hizmet uygulamasına çok benzer.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="3f9bf-158">Sözleşmeyi uygular ve siparişleri işler.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="3f9bf-159">Kod örneği aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-159">The code example is as follows.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 <span data-ttu-id="3f9bf-160">Sipariş sırasından iletileri okuyan sipariş işleme hizmetinin aksine, zarar iletisi hizmeti, zarar alt kuyruğundan iletileri okur.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="3f9bf-161">Poison kuyruğu ana sıranın alt kuyruğudur, "Poison" olarak adlandırılır ve MSMQ tarafından otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="3f9bf-162">Bu durumda, aşağıdaki örnek yapılandırmada gösterildiği gibi ana sıra adını, ardından ";" ve alt sıra adını (Bu örnekte "Poison") belirtin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="3f9bf-163">MSMQ v 3.0 örneğinde, zarar sırası adı, iletiyi taşıdığımız sıra yerine bir alt kuyruk değildir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="3f9bf-164">Örneği çalıştırdığınızda, istemci, hizmet ve zarar iletisi hizmeti etkinlikleri konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="3f9bf-165">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="3f9bf-166">Hizmetleri kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-166">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="3f9bf-167">Hizmet çalışmaya başlar, siparişlerin işlenmesi ve rastgele işlem, işlemeyi sonlandırmaya başlar.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="3f9bf-168">İleti siparişi işlediğini gösteriyorsa, hizmetin gerçekten bir iletiyi sonlandırdığını görene kadar başka bir ileti göndermek için istemciyi yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="3f9bf-169">Yapılandırılan zarar ayarlarına bağlı olarak, ileti son zararlı bir sıraya taşınmadan önce işleme için bir kez denenir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 <span data-ttu-id="3f9bf-170">Zarar sırasından zarar görmüş iletiyi okumak için zarar iletisi hizmetini başlatın.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="3f9bf-171">Bu örnekte, zarar iletisi hizmeti iletiyi okur ve işler.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="3f9bf-172">Sonlandırılan ve zarar veren satın alma sırasının, zarar iletisi hizmeti tarafından okunduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3f9bf-173">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3f9bf-173">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3f9bf-174">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3f9bf-175">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="3f9bf-176">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="3f9bf-177">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="3f9bf-178">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-178">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="3f9bf-179">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-179">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="3f9bf-180">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-180">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="3f9bf-181">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="3f9bf-182">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-182">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="3f9bf-183">Yeni kuyruğun adı olarak `ServiceModelSamplesTransacted` girin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="3f9bf-184">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="3f9bf-185">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için, kuyruk adlarını localhost yerine gerçek ana bilgisayar adını yansıtacak şekilde değiştirin ve [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="3f9bf-186">`netMsmqBinding` bağlama taşıması ile varsayılan olarak güvenlik etkindir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="3f9bf-187">İki özellik, `MsmqAuthenticationMode` ve `MsmqProtectionLevel`birlikte taşıma güvenliği türünü belirleme.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="3f9bf-188">Varsayılan olarak, kimlik doğrulama modu `Windows` olarak ayarlanır ve koruma düzeyi `Sign`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="3f9bf-189">Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ 'nun bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="3f9bf-190">Bu örneği bir etki alanının parçası olmayan bir bilgisayarda çalıştırırsanız, şu hatayı alırsınız: "kullanıcının iç Message Queuing sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="3f9bf-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="3f9bf-191">Örneği çalışma grubuna katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3f9bf-191">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="3f9bf-192">Bilgisayarınız bir etki alanının parçası değilse, aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyini `None` olarak ayarlayarak aktarım güvenliğini kapatın:</span><span class="sxs-lookup"><span data-stu-id="3f9bf-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="3f9bf-193">Uç noktanın bindingConfiguration özniteliğini ayarlayarak, bitiş noktasının bağlama ile ilişkili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="3f9bf-194">Örneği çalıştırmadan önce, Kirmessageserver, sunucu ve istemcideki yapılandırmayı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f9bf-195">`security mode` `None` ayarlanması, `Message` `MsmqAuthenticationMode`, `MsmqProtectionLevel`ve `None`güvenliğini ayarlamaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="3f9bf-196">Meta veri değişimi 'nin çalışması için, http bağlamasıyla bir URL kaydedebiliyoruz.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="3f9bf-197">Bu, hizmetin yükseltilmiş bir komut penceresinde çalıştırılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="3f9bf-198">Aksi takdirde, şöyle bir özel durum alırsınız: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-198">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3f9bf-199">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3f9bf-200">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-200">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3f9bf-201">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3f9bf-202">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3f9bf-202">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
