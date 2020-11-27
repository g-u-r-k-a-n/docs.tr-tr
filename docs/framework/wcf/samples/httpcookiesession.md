---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: df29ae84537cdb7cea40abcdb848ffbb8bbd6b9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253823"
---
# <a name="httpcookiesession"></a><span data-ttu-id="459f9-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="459f9-102">HttpCookieSession</span></span>

<span data-ttu-id="459f9-103">Bu örnek, oturum yönetimi için HTTP tanımlama bilgilerini kullanmak üzere özel bir protokol kanalının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="459f9-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="459f9-104">Bu kanal, Windows Communication Foundation (WCF) Hizmetleri ile ASMX istemcileri veya WCF istemcileri ile ASMX hizmetleri arasında iletişime izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="459f9-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="459f9-105">İstemci, oturum tabanlı bir ASMX Web hizmetinde bir Web yöntemi çağırdığında, ASP.NET altyapısı şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="459f9-105">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="459f9-106">Benzersiz bir KIMLIK (oturum KIMLIĞI) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="459f9-106">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="459f9-107">Oturum nesnesini oluşturur ve benzersiz KIMLIK ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="459f9-107">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="459f9-108">Benzersiz KIMLIĞI bir Set-Cookie HTTP yanıt üstbilgisine ekler ve istemciye gönderir.</span><span class="sxs-lookup"><span data-stu-id="459f9-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="459f9-109">İstemciye gönderdiği oturum KIMLIĞINE göre sonraki çağrılarda istemciyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="459f9-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="459f9-110">İstemci, sonraki isteklerinde bu oturum KIMLIĞINI sunucusuna ekler.</span><span class="sxs-lookup"><span data-stu-id="459f9-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="459f9-111">Sunucu, geçerli HTTP bağlamı için uygun oturum nesnesini yüklemek üzere istemcisinden oturum KIMLIĞINI kullanır.</span><span class="sxs-lookup"><span data-stu-id="459f9-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="459f9-112">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="459f9-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="459f9-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="459f9-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="459f9-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="459f9-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="459f9-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="459f9-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="459f9-116">Httppişiriesession kanal Iletisi değişim stili</span><span class="sxs-lookup"><span data-stu-id="459f9-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  

 <span data-ttu-id="459f9-117">Bu örnek, ASMX benzeri senaryolar için oturumları mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="459f9-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="459f9-118">Kanal yığınımızın en altında, ve ' yi destekleyen HTTP taşıdık <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IReplyChannel> .</span><span class="sxs-lookup"><span data-stu-id="459f9-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="459f9-119">Kanal yığınının daha yüksek düzeylerine oturumlar sağlamak için kanal işdir.</span><span class="sxs-lookup"><span data-stu-id="459f9-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="459f9-120">Örnek, oturumları destekleyen iki kanal ( <xref:System.ServiceModel.Channels.IRequestSessionChannel> ve <xref:System.ServiceModel.Channels.IReplySessionChannel> ) uygular.</span><span class="sxs-lookup"><span data-stu-id="459f9-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="459f9-121">Hizmet kanalı</span><span class="sxs-lookup"><span data-stu-id="459f9-121">Service Channel</span></span>  

 <span data-ttu-id="459f9-122">Örnek, sınıfında bir hizmet kanalı sağlar `HttpCookieReplySessionChannelListener` .</span><span class="sxs-lookup"><span data-stu-id="459f9-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="459f9-123">Bu sınıf, <xref:System.ServiceModel.Channels.IChannelListener> arabirimini uygular ve kanalı <xref:System.ServiceModel.Channels.IReplyChannel> kanal yığınında daha düşük bir değerine dönüştürür <xref:System.ServiceModel.Channels.IReplySessionChannel> .</span><span class="sxs-lookup"><span data-stu-id="459f9-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="459f9-124">Bu işlem aşağıdaki bölümlere ayrılabilir:</span><span class="sxs-lookup"><span data-stu-id="459f9-124">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="459f9-125">Kanal dinleyicisi açıldığında, iç dinleyicisinden bir iç kanalı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="459f9-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="459f9-126">İç dinleyici bir veri birimi dinleyicisi olduğundan ve kabul edilen bir kanalın ömrü, dinleyicinin yaşam süresinden ayrıldığından, iç dinleyiciyi kapatabilir ve yalnızca iç kanala sahip olabilir</span><span class="sxs-lookup"><span data-stu-id="459f9-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="459f9-127">Açık işlem tamamlandığında, iç kanaldan ileti almak için bir ileti döngüsü ayarladık.</span><span class="sxs-lookup"><span data-stu-id="459f9-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="459f9-128">Bir ileti geldiğinde hizmet kanalı, oturum tanımlayıcısını inceler ve uygun oturum kanalında aynı şekilde yeniden çoğuller.</span><span class="sxs-lookup"><span data-stu-id="459f9-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="459f9-129">Kanal dinleyicisi, oturum tanımlayıcılarını oturum kanalı örnekleriyle eşleyen bir sözlük tutar.</span><span class="sxs-lookup"><span data-stu-id="459f9-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="459f9-130">`HttpCookieReplySessionChannel`Sınıfı uygular <xref:System.ServiceModel.Channels.IReplySessionChannel> .</span><span class="sxs-lookup"><span data-stu-id="459f9-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="459f9-131">Kanal yığınının daha yüksek düzeyleri, <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> Bu oturum için istekleri okumak üzere yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="459f9-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="459f9-132">Her oturum kanalının, hizmet kanalı tarafından doldurulan bir özel ileti kuyruğu vardır.</span><span class="sxs-lookup"><span data-stu-id="459f9-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="459f9-133">Birisi <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> yöntemi çağırdığında ve ileti kuyruğunda hiç ileti olmadığında kanal, kendisini kapatmadan önce belirtilen miktarda süre bekler.</span><span class="sxs-lookup"><span data-stu-id="459f9-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="459f9-134">Bu, WCF olmayan istemciler için oluşturulan oturum kanallarını temizler.</span><span class="sxs-lookup"><span data-stu-id="459f9-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="459f9-135">`channelMapping`Öğesini izlemek için kullanıyoruz, `ReplySessionChannels` `innerChannel` kabul edilen tüm kanallar kapanana kadar temeldeki sistemimizi kapatmıyoruz.</span><span class="sxs-lookup"><span data-stu-id="459f9-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="459f9-136">Bu şekilde `HttpCookieReplySessionChannel` ömür süresinin ötesinde yer alabilir `HttpCookieReplySessionChannelListener` .</span><span class="sxs-lookup"><span data-stu-id="459f9-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="459f9-137">Ayrıca, kabul edilen kanallar geri çağırma aracılığıyla dinleyiciye bir başvuru tutacağından, atık toplama işlemi konusunda endişelenmenize gerek kalmaz `OnClosed` .</span><span class="sxs-lookup"><span data-stu-id="459f9-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="459f9-138">İstemci kanalı</span><span class="sxs-lookup"><span data-stu-id="459f9-138">Client channel</span></span>  

 <span data-ttu-id="459f9-139">Karşılık gelen istemci kanalı `HttpCookieSessionChannelFactory` sınıfındır.</span><span class="sxs-lookup"><span data-stu-id="459f9-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="459f9-140">Kanal oluşturma sırasında kanal fabrikası, iç istek kanalını bir ile sarmalanmış `HttpCookieRequestSessionChannel` .</span><span class="sxs-lookup"><span data-stu-id="459f9-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="459f9-141">`HttpCookieRequestSessionChannel`Sınıfı, çağrıları temel alınan istek kanalına iletir.</span><span class="sxs-lookup"><span data-stu-id="459f9-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="459f9-142">İstemci proxy 'yi kapattığında, `HttpCookieRequestSessionChannel` kanalın kapatıldığını belirten bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="459f9-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="459f9-143">Bu nedenle, hizmet kanalı yığını kullanımda olan oturum kanalını düzgün şekilde kapatır.</span><span class="sxs-lookup"><span data-stu-id="459f9-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="459f9-144">Bağlama ve bağlama öğesi</span><span class="sxs-lookup"><span data-stu-id="459f9-144">Binding and Binding Element</span></span>  

 <span data-ttu-id="459f9-145">Hizmet ve istemci kanallarını oluşturduktan sonra, bir sonraki adım bunları WCF çalışma zamanına tümleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="459f9-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="459f9-146">Kanallar, bağlamalar ve bağlama öğeleri aracılığıyla WCF 'ye sunulur.</span><span class="sxs-lookup"><span data-stu-id="459f9-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="459f9-147">Bağlama bir veya daha fazla bağlama öğelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="459f9-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="459f9-148">WCF, sistem tarafından tanımlanan birkaç bağlama sunar; Örneğin, BasicHttpBinding veya WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="459f9-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="459f9-149">`HttpCookieSessionBindingElement`Sınıfı, bağlama öğesinin uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="459f9-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="459f9-150">Gerekli kanal dinleyicisini veya kanal fabrikası örneklemesini yapmak için kanal dinleyicisini ve kanal fabrikası oluşturma yöntemlerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="459f9-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="459f9-151">Örnek, hizmet açıklaması için ilke onayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="459f9-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="459f9-152">Bu, örneğin kanal gereksinimlerini hizmeti kullanabilen diğer istemcilere yayımlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="459f9-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="459f9-153">Örneğin, bu bağlama öğesi, olası istemcilerin oturumları desteklediğini bilmesini sağlamak için ilke onayları yayımlar.</span><span class="sxs-lookup"><span data-stu-id="459f9-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="459f9-154">Örnek, `ExchangeTerminateMessage` bağlama öğesi yapılandırmasındaki özelliği sağladığından, hizmetin oturum iletişimini sonlandırmak için ek bir ileti değişimi işlemini desteklediğini göstermek için gerekli onayları ekler.</span><span class="sxs-lookup"><span data-stu-id="459f9-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="459f9-155">İstemciler daha sonra bu eylemi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="459f9-155">Clients can then use this action.</span></span> <span data-ttu-id="459f9-156">Aşağıdaki WSDL kodunda, öğesinden oluşturulan ilke onayları gösterilmektedir `HttpCookieSessionBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="459f9-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="459f9-157">`HttpCookieSessionBinding`Sınıfı, daha önce açıklanan bağlama öğesini kullanan sistem tarafından sağlanmış bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="459f9-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="459f9-158">Kanal yapılandırma sistemine ekleniyor</span><span class="sxs-lookup"><span data-stu-id="459f9-158">Adding the Channel to the Configuration System</span></span>  

 <span data-ttu-id="459f9-159">Örnek, yapılandırma aracılığıyla örnek kanalı kullanıma sunan iki sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="459f9-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="459f9-160">Birincisi <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> , için bir `HttpCookieSessionBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="459f9-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="459f9-161">Uygulamanın toplu işlemi, `HttpCookieSessionBindingConfigurationElement` ' den türetilen öğesine Temsilcili <xref:System.ServiceModel.Configuration.StandardBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="459f9-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="459f9-162">, `HttpCookieSessionBindingConfigurationElement` Üzerindeki özelliklerine karşılık gelen özelliklere sahiptir `HttpCookieSessionBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="459f9-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="459f9-163">Bağlama öğesi uzantı bölümü</span><span class="sxs-lookup"><span data-stu-id="459f9-163">Binding Element Extension Section</span></span>  

 <span data-ttu-id="459f9-164">Bu bölüm, `HttpCookieSessionBindingElementSection` <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> `HttpCookieSessionBindingElement` yapılandırma sistemine yönelik bir ' dır.</span><span class="sxs-lookup"><span data-stu-id="459f9-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="459f9-165">Yapılandırma bölümünün adı birkaç geçersiz kılındığında, bağlama öğesinin türü ve bağlama öğesinin nasıl oluşturulacağı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="459f9-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="459f9-166">Daha sonra uzantı bölümünü bir yapılandırma dosyasına şu şekilde kaydedebiliriz:</span><span class="sxs-lookup"><span data-stu-id="459f9-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>
    <system.serviceModel>
      <extensions>
        <bindingElementExtensions>
          <add name="httpCookieSession"
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,
                    HttpCookieSessionExtension, Version=1.0.0.0,
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>
    </system.serviceModel>
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="459f9-167">Test kodu</span><span class="sxs-lookup"><span data-stu-id="459f9-167">Test Code</span></span>  

 <span data-ttu-id="459f9-168">Bu örnek taşımanın kullanılması için test kodu Istemci ve hizmet dizinlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="459f9-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="459f9-169">İki testten oluşur; bir test `allowCookies` , istemci üzerinde olarak ayarlanmış bir bağlama kullanır `true` .</span><span class="sxs-lookup"><span data-stu-id="459f9-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="459f9-170">İkinci test, bağlama üzerinde açık kapanmaya (sonlandırma iletisi değişimi kullanılarak) izin vermez.</span><span class="sxs-lookup"><span data-stu-id="459f9-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="459f9-171">Örneği çalıştırdığınızda aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="459f9-171">When you run the sample, you should see the following output:</span></span>  
  
```console  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="459f9-172">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="459f9-172">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="459f9-173">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="459f9-173">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="459f9-174">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="459f9-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="459f9-175">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="459f9-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="459f9-176">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="459f9-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
