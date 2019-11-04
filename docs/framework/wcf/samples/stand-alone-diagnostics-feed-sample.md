---
title: Bağımsız Tanılama Akış Örneği
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: c8a64c209711734b4915f332e9242346e295ddea
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417037"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="d9e70-102">Bağımsız Tanılama Akış Örneği</span><span class="sxs-lookup"><span data-stu-id="d9e70-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="d9e70-103">Bu örnek, Windows Communication Foundation (WCF) ile dağıtım için bir RSS/Atom akışının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9e70-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="d9e70-104">Nesne modelinin temellerini ve bir Windows Communication Foundation (WCF) hizmeti üzerinde ayarlamayı gösteren temel bir "Merhaba Dünya" programıdır.</span><span class="sxs-lookup"><span data-stu-id="d9e70-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="d9e70-105">WCF modelleri özel bir veri türü döndüren hizmet işlemleri olarak dağıtım akışlarını <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="d9e70-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="d9e70-106"><xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> örnekleri, bir akışı hem RSS 2,0 hem de Atom 1,0 biçimlerine seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9e70-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="d9e70-107">Aşağıdaki örnek kodda kullanılan sözleşme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d9e70-107">The following sample code shows the contract used.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.   
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="d9e70-108">`GetProcesses` işlem, WCF 'nin hizmet işlemlerine HTTP GET isteklerini nasıl dağıtmakta olduğunu denetlemenizi ve gönderilen iletilerin biçimini belirlemenizi sağlayan <xref:System.ServiceModel.Web.WebGetAttribute> özniteliğiyle birlikte açıklanmış.</span><span class="sxs-lookup"><span data-stu-id="d9e70-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="d9e70-109">Herhangi bir WCF hizmeti gibi, dağıtım akışları da herhangi bir yönetilen uygulamada barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9e70-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="d9e70-110">Dağıtım Hizmetleri, doğru şekilde çalışması için belirli bir bağlama (<xref:System.ServiceModel.WebHttpBinding>) ve belirli bir uç nokta davranışı (<xref:System.ServiceModel.Description.WebHttpBehavior>) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d9e70-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="d9e70-111">Yeni <xref:System.ServiceModel.Web.WebServiceHost> sınıfı, belirli bir yapılandırma olmadan bu tür uç noktaları oluşturmak için uygun bir API sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9e70-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="d9e70-112">Alternatif olarak, eşdeğer işlevselliği sağlamak için IIS tarafından barındırılan bir. svc dosyası içinden <xref:System.ServiceModel.Activation.WebServiceHostFactory> kullanabilirsiniz (Bu teknik, bu örnek kodda gösterilmez).</span><span class="sxs-lookup"><span data-stu-id="d9e70-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="d9e70-113">Bu hizmet, standart HTTP GET kullanarak istekleri aldığından, hizmete erişmek için herhangi bir RSS veya ATOM kullanan istemci kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9e70-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="d9e70-114">Örneğin, RSS kullanan bir tarayıcıda `http://localhost:8000/diagnostics/feed/?format=atom` veya `http://localhost:8000/diagnostics/feed/?format=rss` giderek bu hizmetin çıkışını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9e70-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="d9e70-115">Ayrıca, dağıtılmış verileri okumak ve bunu zorunlu kodla işlemek için [WCF dağıtım nesnesi modelinin atom ve RSS 'ye nasıl eşlendiğini](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9e70-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d9e70-116">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d9e70-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d9e70-117">[Windows Communication Foundation Örnekleri Için tek seferlik kurulum yordamında](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)bulunan yönergeleri ayarlama bölümünde açıklandığı gibi, bilgisayarda http ve https için doğru adres kayıt iznine sahip olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d9e70-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d9e70-118">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d9e70-118">Build the solution.</span></span>  
  
3. <span data-ttu-id="d9e70-119">Konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d9e70-119">Run the console application.</span></span>  
  
4. <span data-ttu-id="d9e70-120">Konsol uygulaması çalışırken, RSS kullanan bir tarayıcı kullanarak `http://localhost:8000/diagnostics/feed/?format=atom` veya `http://localhost:8000/diagnostics/feed/?format=rss` gidin.</span><span class="sxs-lookup"><span data-stu-id="d9e70-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d9e70-121">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9e70-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d9e70-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d9e70-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="d9e70-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.</span><span class="sxs-lookup"><span data-stu-id="d9e70-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d9e70-124">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d9e70-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="d9e70-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9e70-125">See also</span></span>

- [<span data-ttu-id="d9e70-126">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="d9e70-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="d9e70-127">WCF Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="d9e70-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
