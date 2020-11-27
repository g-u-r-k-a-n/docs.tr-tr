---
title: Yönlendirme Hizmeti ile Merhaba Dünya
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 3d91634d72481427f04e958f6dc2734829b6158b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253862"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="6df8d-102">Yönlendirme Hizmeti ile Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="6df8d-102">Hello World with the Routing Service</span></span>

<span data-ttu-id="6df8d-103">Bu örnek Windows Communication Foundation (WCF) yönlendirme hizmetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6df8d-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="6df8d-104">Yönlendirme hizmeti, uygulamanıza içerik tabanlı bir yönlendirici eklenmesini kolaylaştıran bir WCF bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="6df8d-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="6df8d-105">Bu örnek, yönlendirme hizmetini kullanarak iletişim kurmak için standart WCF Hesaplayıcı örneğine uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="6df8d-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="6df8d-106">Bu örnekte, hesap makinesi istemcisi, yönlendirici tarafından kullanıma sunulan bir uç noktaya ileti gönderecek şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6df8d-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="6df8d-107">Yönlendirme hizmeti, kendisine gönderilen tüm iletileri kabul etmek ve hesap makinesi hizmetine karşılık gelen bir uç noktaya iletmek üzere yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6df8d-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="6df8d-108">Böylece istemciden gönderilen iletiler, yönlendirici tarafından alınır ve gerçek Hesaplayıcı hizmetine yeniden yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6df8d-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="6df8d-109">Hesaplayıcı hizmetinden gelen iletiler yönlendiriciye geri gönderilir, bu da yeniden Hesaplayıcı istemcisine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6df8d-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="6df8d-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6df8d-110">To use this sample</span></span>

1. <span data-ttu-id="6df8d-111">Visual Studio 2012 kullanarak, HelloRoutingService. sln ' yi açın.</span><span class="sxs-lookup"><span data-stu-id="6df8d-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="6df8d-112">F5 veya CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="6df8d-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6df8d-113">F5 tuşuna basarsanız, hesap makinesi Istemcisi otomatik olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="6df8d-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="6df8d-114">CTRL + SHIFT + B 'ye (derleme) basarsanız, aşağıdaki uygulamaları kendiniz başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6df8d-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="6df8d-115">Hesaplayıcı istemcisi (./Hesaplatorclient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="6df8d-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="6df8d-116">Hesaplayıcı hizmeti (./Hesaplayıcı Torservice/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="6df8d-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="6df8d-117">Yönlendirme hizmeti (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="6df8d-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="6df8d-118">İstemcisini başlatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6df8d-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="6df8d-119">Aşağıdaki çıkışı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="6df8d-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="6df8d-120">Kod veya App.Config aracılığıyla yapılandırılabilir</span><span class="sxs-lookup"><span data-stu-id="6df8d-120">Configurable via Code or App.Config</span></span>

 <span data-ttu-id="6df8d-121">Örnek, yönlendirici davranışını tanımlamak için bir App.config dosyası kullanmak üzere yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6df8d-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="6df8d-122">Ayrıca, App.config dosyanın adını başka bir şeye değiştirerek tanınmayacak ve ConfigureRouterViaCode () yöntem çağrısının açıklamasını belirleyebilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6df8d-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="6df8d-123">Her iki yöntem de yönlendiriciden aynı davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="6df8d-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="6df8d-124">Senaryo</span><span class="sxs-lookup"><span data-stu-id="6df8d-124">Scenario</span></span>

 <span data-ttu-id="6df8d-125">Bu örnek, bir temel ileti göndericisi görevi gören yönlendiriciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6df8d-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="6df8d-126">Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış bir hedef uç noktası kümesine geçirmek için yapılandırılmış bir saydam proxy düğümü işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="6df8d-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="6df8d-127">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="6df8d-127">Real World Scenario</span></span>

 <span data-ttu-id="6df8d-128">Contoso, hizmetlerinin adlandırma, adresleme, yapılandırma ve güvenliğine sahip olduğu esnekliği artırmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="6df8d-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="6df8d-129">Bunu yapmak için, genel kullanıma yönelik bir uç nokta olarak görev yapmak üzere hizmetlerinin önüne temel bir ileti göndericisi yerleştirirler.</span><span class="sxs-lookup"><span data-stu-id="6df8d-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="6df8d-130">Bu, gerçek hizmetlerinin önüne ek güvenlik yerleştirmelerini ve daha sonra ölçeklendirilebilir çözüm veya hizmet sürümü oluşturmayı daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6df8d-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6df8d-131">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6df8d-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6df8d-132">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6df8d-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6df8d-133">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6df8d-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6df8d-134">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6df8d-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="6df8d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6df8d-135">See also</span></span>

- <span data-ttu-id="6df8d-136">[AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6df8d-136">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
