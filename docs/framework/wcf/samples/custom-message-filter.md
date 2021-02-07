---
description: 'Daha fazla bilgi edinin: özel Ileti filtresi'
title: Özel İleti Filtresi
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 41205badf4d1133dc160fb0b1c4da8e0edb47a16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752489"
---
# <a name="custom-message-filter"></a><span data-ttu-id="17d71-103">Özel İleti Filtresi</span><span class="sxs-lookup"><span data-stu-id="17d71-103">Custom Message Filter</span></span>

<span data-ttu-id="17d71-104">Bu örnek, Windows Communication Foundation (WCF) tarafından uç noktalara ileti göndermek için kullanılan ileti filtrelerinin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="17d71-104">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17d71-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="17d71-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="17d71-106">Bir kanaldaki ilk ileti sunucuya ulaştığında, sunucu bu URI ile ilişkili uç noktaların (varsa) iletiyi alacağını belirlemelidir.</span><span class="sxs-lookup"><span data-stu-id="17d71-106">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="17d71-107">Bu işlem <xref:System.ServiceModel.Dispatcher.MessageFilter> öğesine eklenen nesneler tarafından denetlenir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> .</span><span class="sxs-lookup"><span data-stu-id="17d71-107">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="17d71-108">Bir hizmetin her uç noktası tek bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> .</span><span class="sxs-lookup"><span data-stu-id="17d71-108">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="17d71-109">, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Hem <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a hem de içerir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> .</span><span class="sxs-lookup"><span data-stu-id="17d71-109">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="17d71-110">Bu iki filtrenin birleşimi, bu uç nokta için kullanılan ileti filtresidir.</span><span class="sxs-lookup"><span data-stu-id="17d71-110">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="17d71-111">Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> bir uç nokta için hizmet uç noktası ile eşleşen bir adrese yönelik olan herhangi bir iletiyle eşleşir <xref:System.ServiceModel.EndpointAddress> .</span><span class="sxs-lookup"><span data-stu-id="17d71-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="17d71-112">Varsayılan olarak, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> bir uç nokta için gelen ileti eylemini inceler ve hizmet uç noktası sözleşmesinin işlemlerindeki eylemlerden birine karşılık gelen bir eylemle eşleşen herhangi bir iletiyle eşleşir (yalnızca `IsInitiating` = `true` Eylemler göz önünde bulundurululur).</span><span class="sxs-lookup"><span data-stu-id="17d71-112">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="17d71-113">Sonuç olarak, varsayılan olarak, bir uç nokta için filtre yalnızca, uç noktanın üst bilgisi ise <xref:System.ServiceModel.EndpointAddress> ve ileti eylemi uç nokta işleminin eylemleriyle eşleştiğinde eşleşir.</span><span class="sxs-lookup"><span data-stu-id="17d71-113">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="17d71-114">Bu filtreler bir davranış kullanılarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="17d71-114">These filters can be changed using a behavior.</span></span> <span data-ttu-id="17d71-115">Örnekte, hizmet, <xref:System.ServiceModel.Description.IEndpointBehavior> ve ' nin yerini aldığı bir oluşturur <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> :</span><span class="sxs-lookup"><span data-stu-id="17d71-115">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="17d71-116">İki adres filtresi tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="17d71-116">Two address filters are defined:</span></span>  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 <span data-ttu-id="17d71-117">`FilteringEndpointBehavior`Yapılandırılabilir hale getirilir ve iki farklı çeşitlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="17d71-117">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 <span data-ttu-id="17d71-118">Çeşitleme 1 yalnızca bir ' e ' (herhangi bir eylem) içeren adreslerle eşleşir, ancak değişim 2 yalnızca ' e ' olmayan adreslerle eşleşir:</span><span class="sxs-lookup"><span data-stu-id="17d71-118">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="17d71-119">Yapılandırma dosyasında hizmet yeni davranışı kaydeder:</span><span class="sxs-lookup"><span data-stu-id="17d71-119">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 <span data-ttu-id="17d71-120">Ardından hizmet `endpointBehavior` Her değişim için yapılandırma oluşturur:</span><span class="sxs-lookup"><span data-stu-id="17d71-120">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 <span data-ttu-id="17d71-121">Son olarak, hizmetin uç noktası aşağıdakilerden birine başvurur `behaviorConfigurations` :</span><span class="sxs-lookup"><span data-stu-id="17d71-121">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="17d71-122">İstemci uygulaması uygulaması basittir; hizmetin URI 'sine iki kanal oluşturur (Bu değeri ikinci ( `via` ) parametresi olarak geçirerek <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> her kanalda tek bir ileti gönderir, ancak her biri için farklı uç nokta adresleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="17d71-122">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="17d71-123">Sonuç olarak, istemciden gelen giden iletilerin belirlemeleri farklıdır ve sunucu, istemcinin çıkışıyla gösterildiği gibi buna uygun şekilde yanıt verir:</span><span class="sxs-lookup"><span data-stu-id="17d71-123">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="17d71-124">Sunucunun yapılandırma dosyasındaki varyasyonın değiştirilmesi filtrenin değişmesine neden olur ve istemci karşı davranışı görür ( `urn:e` ileti başarısız olur, bu durum `urn:a` başarısız olur).</span><span class="sxs-lookup"><span data-stu-id="17d71-124">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="17d71-125">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="17d71-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="17d71-126">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="17d71-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="17d71-127">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="17d71-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="17d71-128">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="17d71-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="17d71-129">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="17d71-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="17d71-130">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="17d71-130">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="17d71-131">Örneği tek makineli bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="17d71-131">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="17d71-132">Örneği bir çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md) bölümündeki yönergeleri izleyin ve Client.cs içinde aşağıdaki satırı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="17d71-132">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="17d71-133">Localhost değerini sunucu adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="17d71-133">Replace localhost with the name of server.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
