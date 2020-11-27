---
title: DiscoveryClient ve DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 72e5beb1306b679cc3b546d77846b5d1e9bb8bb4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275017"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="91ab6-102">DiscoveryClient ve DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="91ab6-102">DiscoveryClient and DynamicEndpoint</span></span>

<span data-ttu-id="91ab6-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> istemci tarafında Hizmetleri aramak için kullanılan iki sınıftır.</span><span class="sxs-lookup"><span data-stu-id="91ab6-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="91ab6-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> belirli bir ölçüt kümesiyle eşleşen hizmetlerin listesini sağlar ve hizmetlere bağlanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="91ab6-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="91ab6-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> aynı işlemi gerçekleştirir ve ek olarak, bulunan hizmetlerden birine otomatik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="91ab6-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="91ab6-106">Herhangi bir uç nokta bir ile yapılabilir <xref:System.ServiceModel.Discovery.DynamicEndpoint> , arama ölçütleri de de eklenebilir, bu nedenle <xref:System.ServiceModel.Discovery.DynamicEndpoint> çözümünüzde bulmaya ihtiyacınız olduğunda ancak istemci mantığını değiştirmek istemediğinizde yararlı olur; yalnızca uç noktaları değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="91ab6-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> Diğer taraftan, arama işlemi üzerinde daha hassas denetim elde etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="91ab6-108">Her birinin kullanımları ve avantajları aşağıda ayrıntılı.</span><span class="sxs-lookup"><span data-stu-id="91ab6-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="91ab6-109">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="91ab6-109">DiscoveryClient</span></span>  

 <span data-ttu-id="91ab6-110">, <xref:System.ServiceModel.Discovery.DiscoveryClient> Zaman uyumlu ve zaman uyumsuz bulma yöntemlerini <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olaylarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91ab6-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="91ab6-111">Ayrıca, zaman uyumlu ve zaman uyumsuz çözümleme yöntemlerini ve bir <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> olayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91ab6-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="91ab6-112"><xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> Hizmet aramak için veya yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="91ab6-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="91ab6-113">Bu yöntemlerin her ikisi de <xref:System.ServiceModel.Discovery.FindCriteria> sözleşme türü adlarını, kapsamları, istenen en fazla sonuç sayısını ve kapsam eşleştirme kurallarını belirtmenize olanak tanıyan bir örnek alır.</span><span class="sxs-lookup"><span data-stu-id="91ab6-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="91ab6-114"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> Yöntemi çağrılırken ve olayları kullanılabilir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="91ab6-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="91ab6-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> , <xref:System.ServiceModel.Discovery.DiscoveryClient> bir hizmetten her yanıt aldığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="91ab6-116">Bul işleminin ilerleme durumunu gösteren bir ilerleme çubuğunu göstermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="91ab6-117">Ayrıca, alındıkları yanıtları bulmaya çalışmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="91ab6-118"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted>Olay, bulma işlemi tamamlandığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="91ab6-119">Bu durum, en fazla yanıt sayısı alındı veya <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> süresi geçtiğinde oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="91ab6-120">Bulma işlemi tamamlandığında sonuçlar bir örnek içinde döndürülür <xref:System.ServiceModel.Discovery.FindResponse> .</span><span class="sxs-lookup"><span data-stu-id="91ab6-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="91ab6-121">, <xref:System.ServiceModel.Discovery.FindResponse> <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> Eşleşen hizmetlerin adreslerini, sözleşme türü adlarını, uzantıları, dinleme URI 'lerini ve kapsamlarını içeren bir koleksiyon içerir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="91ab6-122">Daha sonra bu bilgileri kullanarak, eşleşen hizmetlerden birine bağlanabilir ve bu hizmetleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ab6-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="91ab6-123">Aşağıdaki örnek, System. ServiceModel. Discovery. DiscoveryClient. Find (System. ServiceModel. Discovery. FindCriteria) yönteminin nasıl çağrılacağını ve bulunan hizmeti çağırmak için döndürülen meta verileri nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="91ab6-124">Kullanmanın bir avantajı <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> , bulduğunuz uç noktaların listesini önbelleğe alabilir ve bunları daha sonra kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ab6-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="91ab6-125">Bu önbellek ile çeşitli hata koşullarını işlemek için özel mantık oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91ab6-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```csharp
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 <span data-ttu-id="91ab6-126">Aşağıdaki örnek, bir bulma işleminin zaman uyumsuz olarak nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```csharp
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));
}
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 <span data-ttu-id="91ab6-127"><xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A>Ve yöntemlerini, <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> uç nokta adresini temel alarak bir hizmeti bulmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="91ab6-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="91ab6-128">Bu, uç nokta adresi ağ adreslenebilir olmadığında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="91ab6-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="91ab6-129">Resolve yöntemleri, <xref:System.ServiceModel.Discovery.ResolveCriteria> çözümlüğiniz hizmetin uç nokta adresini, çözüm işleminin en uzun süresini ve bir dizi uzantıyı belirtmenizi sağlayan bir örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="91ab6-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="91ab6-130">Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> bir hizmeti çözmek için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="91ab6-131">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="91ab6-131">DynamicEndpoint</span></span>  

 <span data-ttu-id="91ab6-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> , standart bir uç noktasıdır (daha fazla bilgi Için, bkz. bulma işlemini gerçekleştiren ve otomatik olarak eşleşen hizmeti seçen [standart uç noktalar](standard-endpoints.md)).</span><span class="sxs-lookup"><span data-stu-id="91ab6-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="91ab6-133">Yalnızca arama yapmak için sözleşmede bir geçiş oluşturun ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> kullanılacak bağlamayı ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> örneği WCF istemcisine geçirin.</span><span class="sxs-lookup"><span data-stu-id="91ab6-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="91ab6-134">Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.DynamicEndpoint> hesap makinesi hizmetini çağırmak için oluşturma ve kullanma işlemlerinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="91ab6-135">Bulma işlemi, istemci her açılışında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="91ab6-136">Yapılandırma içinde tanımlı herhangi bir uç nokta, <xref:System.ServiceModel.Discovery.DynamicEndpoint> `kind ="dynamicEndpoint"` uç nokta yapılandırma öğesine özniteliği eklenerek de bir öğesine açılabilir.</span><span class="sxs-lookup"><span data-stu-id="91ab6-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="91ab6-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91ab6-137">See also</span></span>

- [<span data-ttu-id="91ab6-138">Kapsamlarla Bulma</span><span class="sxs-lookup"><span data-stu-id="91ab6-138">Discovery with Scopes</span></span>](../samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="91ab6-139">Temel</span><span class="sxs-lookup"><span data-stu-id="91ab6-139">Basic</span></span>](../samples/basic-sample.md)
