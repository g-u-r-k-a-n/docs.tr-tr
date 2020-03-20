---
title: WCF Web HTTP biçimlendirme
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: b6c9728fe40e26977366b73337e72b1514a12a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184190"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="bcccc-102">WCF Web HTTP biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="bcccc-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="bcccc-103">WCF Web HTTP programlama modeli, yanıtını geri döndürmek için bir hizmet işlemi için en iyi biçimi dinamik olarak belirlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="bcccc-104">Uygun biçimi belirlemek için iki yöntem desteklenir: otomatik ve açık.</span><span class="sxs-lookup"><span data-stu-id="bcccc-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="bcccc-105">Otomatik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="bcccc-105">Automatic formatting</span></span>  
 <span data-ttu-id="bcccc-106">Etkinleştirildiğinde, otomatik biçimlendirme yanıtı döndürecek en iyi biçimi seçer.</span><span class="sxs-lookup"><span data-stu-id="bcccc-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="bcccc-107">Sırayla aşağıdakileri işaretleyerek en iyi biçimi belirler:</span><span class="sxs-lookup"><span data-stu-id="bcccc-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="bcccc-108">İstek iletisinin Kabul üstbilgisinde ortam türleri.</span><span class="sxs-lookup"><span data-stu-id="bcccc-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="bcccc-109">İstek iletisinin içerik türü.</span><span class="sxs-lookup"><span data-stu-id="bcccc-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="bcccc-110">İşlemdeki varsayılan biçim ayarı.</span><span class="sxs-lookup"><span data-stu-id="bcccc-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="bcccc-111">Web'de varsayılan biçim ayarıHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="bcccc-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="bcccc-112">İstek iletisi bir Üstbilgi içeriyorsa, Windows Communication Foundation (WCF) altyapısı desteklediği bir türü arar.</span><span class="sxs-lookup"><span data-stu-id="bcccc-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="bcccc-113">`Accept` Üstbilgi, ortam türleri için öncelikleri belirtirse, bunlar onurlanır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="bcccc-114">`Accept` Üstbilgide uygun biçim bulunmazsa, istek iletisinin içerik türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="bcccc-115">Uygun içerik türü belirtilmemişse, işlem için varsayılan biçim ayarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="bcccc-116">Varsayılan biçim `ResponseFormat` <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliklerin parametresi ile ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="bcccc-117">İşlemde varsayılan biçim belirtilmemişse, özelliğin <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="bcccc-118">Otomatik biçimlendirme <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> özelliğine dayanır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="bcccc-119">Bu özellik `true`ayarlandığında, WCF altyapısı kullanılacak en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="bcccc-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="bcccc-120">Otomatik biçim seçimi geriye dönük uyumluluk için varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="bcccc-121">Otomatik biçim seçimi programlı olarak veya yapılandırma yoluyla etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bcccc-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="bcccc-122">Aşağıdaki örnekte, kodda otomatik biçim seçiminin nasıl etkinleştirilen gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bcccc-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 <span data-ttu-id="bcccc-123">Otomatik biçimlendirme yapılandırma yoluyla da etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bcccc-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="bcccc-124"><xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> Özelliği doğrudan üzerinde <xref:System.ServiceModel.Description.WebHttpBehavior> ayarlayabilirsiniz veya <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="bcccc-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="bcccc-125">Aşağıdaki örnekte, <xref:System.ServiceModel.Description.WebHttpBehavior>''de otomatik biçim seçiminin nasıl etkinleştirilen</span><span class="sxs-lookup"><span data-stu-id="bcccc-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="bcccc-126">Aşağıdaki örnekte, otomatik biçim seçiminin nasıl etkinleştirilen bir şekilde gösterilmektedir. <xref:System.ServiceModel.Description.WebHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="bcccc-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a><span data-ttu-id="bcccc-127">Açık biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="bcccc-127">Explicit formatting</span></span>  
 <span data-ttu-id="bcccc-128">Adından da anlaşılacağı gibi, açık biçimlendirme geliştirici işlem kodu içinde kullanılacak en iyi biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="bcccc-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="bcccc-129">En iyi biçim XML veya JSON <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> ise <xref:System.ServiceModel.Web.WebMessageFormat.Xml> <xref:System.ServiceModel.Web.WebMessageFormat.Json>geliştirici ya da ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bcccc-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="bcccc-130"><xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> Özellik açıkça ayarlanmazsa, işlemin varsayılan biçimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="bcccc-131">Aşağıdaki örnekte, kullanılacak bir biçim için biçim sorgusu dize parametresini denetler.</span><span class="sxs-lookup"><span data-stu-id="bcccc-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="bcccc-132">Belirtilmişse, 'yi kullanarak <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>işlemin biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bcccc-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="bcccc-133">XML veya JSON dışındaki biçimleri desteklemeniz gerekiyorsa, işleminizi bir geri <xref:System.ServiceModel.Channels.Message>dönüş türüne sahip olmak için tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="bcccc-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="bcccc-134">İşlem kodu içinde, kullanılacak uygun biçimi belirleyin <xref:System.ServiceModel.Channels.Message> ve ardından aşağıdaki yöntemlerden birini kullanarak bir nesne oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bcccc-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="bcccc-135">Bu yöntemlerin her biri içerik alır ve uygun biçimde bir ileti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bcccc-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="bcccc-136">Yöntem, `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` tercihi azaltmak amacıyla istemci tarafından tercih edilen biçimlerin listesini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bcccc-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="bcccc-137">Aşağıdaki örnek, kullanılacak `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` biçimi belirlemek için nasıl kullanılacağını gösterir ve yanıt iletisi oluşturmak için uygun yanıt oluşturma yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bcccc-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcccc-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcccc-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="bcccc-139">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="bcccc-139">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="bcccc-140">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="bcccc-140">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="bcccc-141">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bcccc-141">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="bcccc-142">WCF Web HTTP Programlama Nesnesi Modeli</span><span class="sxs-lookup"><span data-stu-id="bcccc-142">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
