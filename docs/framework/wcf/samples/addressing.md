---
title: Adres Ayarlama
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 77a1321f2babb93ab39eeac944de06fc8c2634c3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249702"
---
# <a name="addressing"></a><span data-ttu-id="c6ead-102">Adres Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c6ead-102">Addressing</span></span>

<span data-ttu-id="c6ead-103">Adresleme örneği, uç nokta adreslerinin çeşitli yönlerini ve özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="c6ead-104">Örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="c6ead-104">The sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="c6ead-105">Bu örnekte, hizmet kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="c6ead-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="c6ead-106">Hem hizmet hem de istemci konsol uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="c6ead-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="c6ead-107">Hizmet, göreli ve mutlak uç nokta adreslerinden oluşan bir birleşimi kullanarak birden fazla uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c6ead-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6ead-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="c6ead-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c6ead-109">Hizmet yapılandırma dosyası bir temel adres ve dört uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="c6ead-110">Temel adres, aşağıdaki örnek yapılandırmada gösterildiği gibi, Service/Host/baseAddresses altında add öğesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="c6ead-111">Aşağıdaki örnek yapılandırmada gösterilen ilk uç nokta tanımı, bir göreli adresi belirtir. Bu, uç nokta adresinin temel adresin bir birleşimi ve URI bileşimi kurallarından sonraki göreli adres olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="c6ead-112">Bu durumda, göreli adres boş ("") olduğundan, uç nokta adresi taban adresle aynı olur.</span><span class="sxs-lookup"><span data-stu-id="c6ead-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="c6ead-113">Gerçek uç nokta adresi `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="c6ead-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="c6ead-114">İkinci uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi göreli bir adresi de belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="c6ead-115">Göreli adres "test", temel adrese eklenir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="c6ead-116">Gerçek uç nokta adresi `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="c6ead-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="c6ead-117">Üçüncü uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi mutlak bir adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="c6ead-118">Taban adresi adreste hiçbir rol oynamıyor.</span><span class="sxs-lookup"><span data-stu-id="c6ead-118">The base address plays no role in the address.</span></span> <span data-ttu-id="c6ead-119">Gerçek uç nokta adresi `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="c6ead-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="c6ead-120">Dördüncü uç nokta adresi, bir mutlak adresi ve farklı bir aktarımı (TCP) belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="c6ead-121">Taban adresi adreste hiçbir rol oynamıyor.</span><span class="sxs-lookup"><span data-stu-id="c6ead-121">The base address plays no role in the address.</span></span> <span data-ttu-id="c6ead-122">Gerçek uç nokta adresi `net.tcp://localhost:9000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="c6ead-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="c6ead-123">İstemci, dört hizmet uç noktasından yalnızca birine erişir, ancak tüm dördü yapılandırma dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c6ead-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="c6ead-124">İstemci, nesneyi oluşturduğunda bir uç nokta seçer `CalculatorProxy` .</span><span class="sxs-lookup"><span data-stu-id="c6ead-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="c6ead-125">Yapılandırma adını `CalculatorEndpoint1` aracılığıyla değiştirerek `CalculatorEndpoint4` , uç noktaların her birini uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6ead-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="c6ead-126">Örneği çalıştırdığınızda hizmet, her bitiş noktası için adresi, bağlama adını ve sözleşme adını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="c6ead-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="c6ead-127">Meta veri değişimi (MEX) uç noktası, ServiceHost 'un perspektifinden, listede görünmesi için yalnızca başka bir uç nokta olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```console  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="c6ead-128">İstemcisini çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c6ead-129">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6ead-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c6ead-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c6ead-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c6ead-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6ead-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c6ead-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c6ead-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c6ead-133">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c6ead-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c6ead-134">Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6ead-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c6ead-135">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c6ead-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6ead-136">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c6ead-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c6ead-137">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c6ead-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6ead-138">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c6ead-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
