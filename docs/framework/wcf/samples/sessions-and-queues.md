---
description: 'Daha fazla bilgi edinin: oturumlar ve kuyruklar'
title: Oturumlar ve Kuyruklar
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 94ff58fca628e44b78b002291fa78a39cc10a14f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793018"
---
# <a name="sessions-and-queues"></a>Oturumlar ve kuyruklar

Bu örnek, Message Queuing (MSMQ) taşıması üzerinden sıraya alınmış iletişimde ilgili bir ileti kümesinin nasıl gönderileceğini ve alınacağını gösterir. Bu örnek, `netMsmqBinding` bağlamayı kullanır. Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar. Daha kesin olarak, istemci iletileri bir kuyruğa gönderir. Hizmet kuyruktaki iletileri alır. Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.  
  
 Bazen, bir istemci bir gruptaki birbirleriyle ilgili bir ileti kümesi gönderir. İletilerin birlikte işlenmesi gerektiğinde veya belirtilen sırada, tek bir alan uygulaması tarafından işlenmek üzere bir kuyruk birlikte gruplamak için kullanılabilir. Bu, bir sunucu grubunda birkaç alma uygulaması olduğunda özellikle önemlidir ve bir ileti grubunun aynı alan uygulama tarafından işlenmesini sağlamak için gereklidir. Sıraya alınan oturumlar, hepsi aynı anda işlenmesi gereken ilgili bir ileti kümesi göndermek ve almak için kullanılan bir mekanizmadır. Kuyruğa alınan oturumlar bu kalıbı göstermesi için bir işlem gerektirir.  
  
 Örnekte, istemci tek bir işlem kapsamındaki bir oturumun parçası olarak hizmete bir dizi ileti gönderir.  
  
 Hizmet sözleşmesi, `IOrderTaker` kuyruklarla birlikte kullanılmak üzere uygun tek yönlü bir hizmeti tanımlar. <xref:System.ServiceModel.SessionMode>Aşağıdaki örnek kodda gösterilen sözleşmede kullanılan, iletilerin oturumun bir parçası olduğunu gösterir.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 Hizmet, hizmet işlemlerini ilk işlemin bir işlemde listelediğinden ancak işlemi otomatik olarak tamamladığı şekilde tanımlar. Sonraki işlemler aynı işlemde de listelenmez, ancak otomatik olarak tamamlanmaz. Oturumdaki son işlem işlemi otomatik olarak tamamlar. Bu nedenle, hizmet sözleşmesindeki birkaç işlem etkinleştirmeleri için aynı işlem kullanılır. İşlemlerden herhangi biri bir özel durum oluşturduktan sonra işlem geri alınır ve oturum kuyruğa geri konur. Son işlemin başarıyla tamamlanmasından sonra işlem kaydedilir. Hizmet `PerSession` , <xref:System.ServiceModel.InstanceContextMode> aynı hizmetin aynı örneğindeki bir oturumdaki tüm iletileri almak için olarak kullanır.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 Hizmet kendi kendine barındırılır. MSMQ aktarımını kullanırken kullanılan kuyruğun önceden oluşturulması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte hizmet, <xref:System.Messaging> sıranın varlığını denetlemek için kod içerir ve gerekirse oluşturur. Sıra adı, sınıfı kullanılarak yapılandırma dosyasından okundu <xref:System.Configuration.ConfigurationManager.AppSettings%2A> .  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();
    }  
}  
```

 MSMQ kuyruğu adı, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir. Hizmetin uç noktası, yapılandırma dosyasının System. serviceModel bölümünde tanımlanır ve `netMsmqBinding` bağlamayı belirtir.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 İstemci bir işlem kapsamı oluşturur. Oturumdaki tüm iletiler, işlem kapsamındaki sıraya gönderilir ve tüm iletilerin başarılı veya başarısız olduğu atomik bir birim olarak değerlendirilmesine neden olur. İşlem çağırarak işlenir <xref:System.Transactions.TransactionScope.Complete%2A> .  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
> Oturumdaki tüm iletiler için yalnızca tek bir işlem kullanabilirsiniz ve işlem kaydedilmeden önce oturumdaki tüm iletilerin gönderilmesi gerekir. İstemcinin kapatılması oturumu kapatır. Bu nedenle, oturumdaki tüm iletileri sıraya göndermek için, işlem tamamlanmadan önce istemcinin kapatılması gerekir.  
  
 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir. Hizmetin istemciden ileti alacağını görebilirsiniz. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın. Kuyruk kullanımda olduğundan, istemci ve hizmetin aynı anda çalışıyor olması gerekmez. İstemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir.  
  
 İstemcide.  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 .  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="set-up-build-and-run-the-sample"></a>Örneği kurma, oluşturma ve çalıştırma  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C#, C++ veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
 Varsayılan olarak, <xref:System.ServiceModel.NetMsmqBinding> taşıma güvenliği etkindir. MSMQ aktarım güvenliği için iki ilgili özellik vardır <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve varsayılan olarak, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` kimlik doğrulama modu olarak ayarlanır `Windows` ve koruma düzeyi olarak ayarlanır `Sign` . Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ için, bir etki alanının parçası olması ve MSMQ için Active Directory tümleştirme seçeneğinin yüklü olması gerekir. Bu örneği bu ölçütlere uygun olmayan bir bilgisayarda çalıştırırsanız bir hata alırsınız.  
  
### <a name="run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Örneği çalışma grubuna katılmış bir bilgisayarda çalıştırın  
  
1. Bilgisayarınız bir etki alanının parçası değilse veya Active Directory Tümleştirmesi yüklü değilse, kimlik doğrulama modunu ve koruma düzeyini `None` Aşağıdaki örnek yapılandırmada gösterildiği gibi olarak ayarlayarak aktarım güvenliğini kapatın.  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.  
  
    > [!NOTE]
    > Güvenlik modunun olarak ayarlanması `None` <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , ve ile güvenliğe eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `Message` `None` .  
