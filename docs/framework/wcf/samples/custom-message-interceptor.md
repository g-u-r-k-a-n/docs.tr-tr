---
title: Özel İleti Kesici
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 433b14433a7e2dd6edad551a2732e9049a9861ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145092"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="8a2d5-102">Özel İleti Kesici</span><span class="sxs-lookup"><span data-stu-id="8a2d5-102">Custom Message Interceptor</span></span>
<span data-ttu-id="8a2d5-103">Bu örnek kanal genişletilebilirlik modelinin kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="8a2d5-104">Özellikle, çalışma zamanı yığınının belirli bir noktasında gelen ve giden tüm iletileri engellemek için kanal fabrikaları ve kanal dinleyicileri oluşturan özel bir bağlama öğesinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="8a2d5-105">Örnek, bu özel fabrikaların kullanımını gösteren bir istemci ve sunucu da içerir.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="8a2d5-106">Bu örnekte, hem istemci hem de hizmet konsol programlarıdır (.exe).</span><span class="sxs-lookup"><span data-stu-id="8a2d5-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="8a2d5-107">İstemci ve hizmet, özel bağlama öğesini ve ilişkili çalışma zamanı nesnelerini içeren ortak bir kitaplığı (.dll) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a2d5-108">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8a2d5-109">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8a2d5-110">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8a2d5-111">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a2d5-112">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="8a2d5-113">Örnek, kanal çerçevesini kullanarak ve WCF en iyi uygulamalarını izleyerek Windows Communication Foundation'da (WCF) özel katmanlı bir kanal oluşturmak için önerilen yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="8a2d5-114">Özel katmanlı kanal oluşturma adımları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8a2d5-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="8a2d5-115">Kanal şekillerinin hangisinin kanal fabrikanıza ve kanal dinleyicisinin destekleyeceğine karar verin.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="8a2d5-116">Kanal şekillerinizi destekleyen bir kanal fabrikası ve kanal dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="8a2d5-117">Özel katmanlı kanalı kanal yığınına ekleyen bağlayıcı bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="8a2d5-118">Yapılandırma sistemine yeni bağlama öğesi ortaya çıkarmak için bağlayıcı öğe uzantısı bölümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="8a2d5-119">Kanal Şekilleri</span><span class="sxs-lookup"><span data-stu-id="8a2d5-119">Channel Shapes</span></span>  
 <span data-ttu-id="8a2d5-120">Özel katmanlı bir kanal yazmanın ilk adımı, kanal için hangi şekillerin gerekli olduğuna karar vermektir.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="8a2d5-121">İleti denetçimiz için, altımızdaki katmanın desteklediği herhangi bir şekli destekliyoruz <xref:System.ServiceModel.Channels.IOutputChannel> (örneğin, altımızdaki katman oluşturabilir ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>sonra biz de ortaya çıkarız). <xref:System.ServiceModel.Channels.IOutputChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel></span><span class="sxs-lookup"><span data-stu-id="8a2d5-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="8a2d5-122">Kanal Fabrikası ve Dinleyici Fabrikası</span><span class="sxs-lookup"><span data-stu-id="8a2d5-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="8a2d5-123">Özel katmanlı kanal yazmanın bir sonraki adımı, <xref:System.ServiceModel.Channels.IChannelFactory> istemci kanalları ve <xref:System.ServiceModel.Channels.IChannelListener> servis kanalları için bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="8a2d5-124">Bu sınıflar bir iç fabrika ve dinleyici almak `OnCreateChannel` `OnAcceptChannel` ve tüm ama ve iç fabrika ve dinleyici çağırır delege.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="8a2d5-125">Bağlama Öğesi Ekleme</span><span class="sxs-lookup"><span data-stu-id="8a2d5-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="8a2d5-126">Örnek özel bir bağlama öğesi `InterceptingBindingElement`tanımlar: .</span><span class="sxs-lookup"><span data-stu-id="8a2d5-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="8a2d5-127">`InterceptingBindingElement`bir `ChannelMessageInterceptor` girdi olarak alır ve `ChannelMessageInterceptor` içinden geçen iletileri işlemek için bunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="8a2d5-128">Halka açık olması gereken tek sınıf bu.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-128">This is the only class that must be public.</span></span> <span data-ttu-id="8a2d5-129">Fabrika, dinleyici ve kanalların tümü, genel çalışma zamanı arabirimlerinin dahili uygulamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="8a2d5-130">Yapılandırma Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="8a2d5-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="8a2d5-131">Bağlama yapılandırmasıyla tümleştirmek için kitaplık, yapılandırma kesiti işleyicisini bağlayıcı öğe uzantısı bölümü olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="8a2d5-132">İstemci ve sunucu yapılandırma dosyaları bağlayıcı öğe uzantısını yapılandırma sistemine kaydetmelidir.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="8a2d5-133">Bağlama öğelerini yapılandırma sistemine maruz bırakmak isteyen uygulayıcılar bu sınıftan türetilebilir.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="8a2d5-134">İlke Ekleme</span><span class="sxs-lookup"><span data-stu-id="8a2d5-134">Adding Policy</span></span>  
 <span data-ttu-id="8a2d5-135">Politika sistemimizle entegre `InterceptingBindingElement` olmak için, iPolicyExportExtension'ı uygulayarak politika oluşturmaya katılmamız gerektiğini niçin işaret edeceğiz.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="8a2d5-136">Oluşturulan istemcide alma ilkesini desteklemek için, kullanıcı ilke `InterceptingBindingElementImporter` etkin `CreateMessageInterceptor` `ChannelMessageInterceptor` sınıfını oluşturmak için türetilmiş bir sınıf kaydedebilir ve geçersiz kılınabilir ()</span><span class="sxs-lookup"><span data-stu-id="8a2d5-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="8a2d5-137">Örnek: Droppable İleti Denetçisi</span><span class="sxs-lookup"><span data-stu-id="8a2d5-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="8a2d5-138">Örnekte, iletilerin düştüğü bir `ChannelMessageInspector` örnek uygulama da yer alıyor.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="8a2d5-139">Yapılandırmadan aşağıdaki gibi erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8a2d5-139">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="8a2d5-140">İstemci ve sunucu, özel fabrikaları çalışma zamanı kanal yığınlarının en düşük düzeyine (aktarım düzeyinin üzerinde) eklemek için bu yeni oluşturulan yapılandırma bölümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="8a2d5-141">İstemci, `MessageInterceptor` çift numaralı iletilere özel bir üstbilgi eklemek için kitaplığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="8a2d5-142">Diğer taraftan hizmet, `MessageInterceptor` bu özel üstbilgiye sahip olmayan iletileri bırakmak için kitaplığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="8a2d5-143">Hizmeti çalıştırdıktan sonra aşağıdaki istemci çıktısını ve ardından istemciyi görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-143">You should see the following client output after running the service and then the client.</span></span>  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="8a2d5-144">İstemci hizmete 10 farklı rüzgar hızı bildirir, ancak bunların yalnızca yarısını özel üstbilgiyle etiketler.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="8a2d5-145">Hizmette aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8a2d5-145">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8a2d5-146">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8a2d5-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8a2d5-147">Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="8a2d5-148">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="8a2d5-149">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="8a2d5-150">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="8a2d5-151">Önce Service.exe'yi çalıştırın sonra Client.exe'yi çalıştırın ve çıkış için her iki konsol penceresini de izleyin.</span><span class="sxs-lookup"><span data-stu-id="8a2d5-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
