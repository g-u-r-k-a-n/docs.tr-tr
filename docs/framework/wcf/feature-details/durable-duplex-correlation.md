---
description: 'Daha fazla bilgi edinin: dayanıklı çift yönlü bağıntı'
title: Dayanıklı Çift Yönlü Bağıntı
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: e30356e03ccb6f8fae7ca735d2ad674bbe2a191d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704959"
---
# <a name="durable-duplex-correlation"></a>Dayanıklı Çift Yönlü Bağıntı

Geri arama bağıntısı olarak da bilinen dayanıklı çift yönlü bağıntı, bir iş akışı hizmeti ilk arayana geri çağrı göndermek için bir gereksinime sahip olduğunda faydalıdır. WCF çift yönlü olarak, geri çağırma gelecekte herhangi bir zamanda gerçekleşebilir ve aynı kanala veya kanal ömrüne bağlı değildir; Tek gereksinim, çağıranın geri çağırma iletisini dinleyen etkin bir uç noktaya sahip olması olabilir. Bu, iki iş akışı hizmetinin uzun süre çalışan bir konuşmada iletişim kurmasına izin verir. Bu konu, dayanıklı çift yönlü bağıntı için bir genel bakış sağlar.  
  
## <a name="using-durable-duplex-correlation"></a>Dayanıklı çift yönlü bağıntı kullanma  

 Dayanıklı çift yönlü bağıntı kullanmak için, iki hizmetin, veya gibi iki yönlü işlemleri destekleyen bir bağlam özellikli bağlama kullanması gerekir <xref:System.ServiceModel.NetTcpContextBinding> <xref:System.ServiceModel.WSHttpContextBinding> . Çağıran hizmet, <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> istemci üzerindeki istenen bağlamayı kaydeder <xref:System.ServiceModel.Endpoint> . Alıcı hizmeti, bu verileri ilk çağrıda alır ve ardından <xref:System.ServiceModel.Endpoint> , <xref:System.ServiceModel.Activities.Send> çağıran hizmete geri çağrı yapan etkinliğin kendi öğesinde kullanır. Bu örnekte, iki hizmet birbirleriyle iletişim kurar. İlk hizmet ikinci hizmette bir yöntemi çağırır ve sonra bir yanıt bekler. İkinci hizmet geri arama yönteminin adını bilir, ancak bu yöntemi uygulayan hizmetin uç noktası tasarım zamanında bilinmez.  
  
> [!NOTE]
> Dayanıklı çift yönlü yalnızca <xref:System.ServiceModel.Channels.AddressingVersion> uç noktanın ile yapılandırıldığı durumlarda kullanılabilir <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A> . Aksi takdirde, <xref:System.InvalidOperationException> aşağıdaki iletiyle bir özel durum oluşturulur: "Ileti [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing)için uç nokta başvurusuna sahip bir geri çağırma bağlamı üst bilgisi içerir. Geri çağırma bağlamı yalnızca AddressingVersion ' WSAddressing10 ' ile yapılandırıldığında aktarılabilir.
  
 Aşağıdaki örnekte, kullanarak bir geri çağırma oluşturan bir iş akışı hizmeti barındırılır <xref:System.ServiceModel.Endpoint> <xref:System.ServiceModel.WSHttpContextBinding> .  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 Bu iş akışı hizmetini uygulayan iş akışı, geri çağırma bağıntısını <xref:System.ServiceModel.Activities.Send> etkinliğiyle başlatır ve <xref:System.ServiceModel.Activities.Receive> ile ilişkili etkinlikten bu geri çağırma uç noktasına başvurur <xref:System.ServiceModel.Activities.Send> . Aşağıdaki örnek, yönteminden döndürülen iş akışını temsil eder `GetWF1` .  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 İkinci iş akışı hizmeti, sistem tarafından sağlanmış, bağlam tabanlı bağlama kullanılarak barındırılır.  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 Bu iş akışı hizmetini uygulayan iş akışı bir etkinlikle başlar <xref:System.ServiceModel.Activities.Receive> . Bu alma etkinliği, bu hizmet için geri çağırma bağıntısını başlatır, uzun süredir çalışan çalışmanın benzetimini yapmak için bir süre gecikmesini sağlar ve ardından hizmete ilk çağrıda geçirilen geri çağırma bağlamını kullanarak ilk hizmete geri çağrı yapar. Aşağıdaki örnek, bir çağrısından döndürülen iş akışını temsil eder `GetWF2` . <xref:System.ServiceModel.Activities.Send>Etkinliğin bir yer tutucu adresine sahip olduğunu `http://www.contoso.com` ; çalışma zamanında kullanılan gerçek adres, sağlanan geri arama adresidir.  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 `StartOrder`Yöntem ilk iş akışında çağrıldığında, iki iş akışı üzerinden yürütme akışını gösteren aşağıdaki çıktı görüntülenir.  
  
```output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 Bu örnekte her iki iş akışı, kullanarak bağıntıyı açıkça yönetir <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> . Bu örnek iş akışlarında yalnızca tek bir bağıntı bulunduğundan, varsayılan <xref:System.ServiceModel.Activities.CorrelationHandle> Yönetim yeterli olacaktır.
