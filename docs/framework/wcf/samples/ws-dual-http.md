---
title: WS İkili Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 44fdf6f0b27e15c486afa32f67668e9fd6eeac10
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138682"
---
# <a name="ws-dual-http"></a><span data-ttu-id="7c71b-102">WS İkili Http</span><span class="sxs-lookup"><span data-stu-id="7c71b-102">WS Dual Http</span></span>

<span data-ttu-id="7c71b-103">Çift http örneği, `WSDualHttpBinding` bağlamanın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c71b-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="7c71b-104">Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programından (. exe) ve hizmet kitaplığından (. dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="7c71b-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7c71b-105">Hizmet bir çift yönlü sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="7c71b-105">The service implements a duplex contract.</span></span> <span data-ttu-id="7c71b-106">Sözleşme, matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan `ICalculatorDuplex` arabirimi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7c71b-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="7c71b-107">Bu örnekte, `ICalculatorDuplex` arabirimi istemcinin, oturum üzerinde çalışan bir sonucu hesaplamak için matematik işlemleri gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c71b-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="7c71b-108">Bağımsız olarak, hizmet `ICalculatorDuplexCallback` arabirimindeki sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="7c71b-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="7c71b-109">Bir çift yönlü sözleşme, istemci ve hizmet arasında gönderilen ileti kümesiyle ilişkilendirilmesi için bir bağlam kurulması gerektiğinden oturum gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7c71b-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="7c71b-110">`WSDualHttpBinding` bağlama çift yönlü iletişimi destekler.</span><span class="sxs-lookup"><span data-stu-id="7c71b-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>

> [!NOTE]
> <span data-ttu-id="7c71b-111">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="7c71b-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c71b-112">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c71b-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7c71b-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7c71b-113">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7c71b-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.</span><span class="sxs-lookup"><span data-stu-id="7c71b-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c71b-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7c71b-115">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`

<span data-ttu-id="7c71b-116">`WSDualHttpBinding`bir hizmet uç noktası yapılandırmak için uç nokta yapılandırmasındaki bağlamayı gösterildiği gibi belirtin.</span><span class="sxs-lookup"><span data-stu-id="7c71b-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>

```xml
<endpoint address=""
         binding="wsDualHttpBinding"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
```

<span data-ttu-id="7c71b-117">İstemcisinde, aşağıdaki örnek yapılandırmada gösterildiği gibi sunucunun istemciye bağlanmak için kullanabileceği bir adresi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c71b-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint address=
         "http://localhost/servicemodelsamples/service.svc"
         binding="wsDualHttpBinding"
         bindingConfiguration="Binding1"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
  </client>

  <bindings>
    <!-- Configure a WSDualHttpBinding that supports duplex -->
    <!-- communication. -->
    <wsDualHttpBinding>
      <binding name="Binding1"
               clientBaseAddress="http://localhost:8000/myClient/"
               useDefaultWebProxy="true"
               bypassProxyOnLocal="false">
      </binding>
    </wsDualHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="7c71b-118">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7c71b-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7c71b-119">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c71b-119">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client once the output is displayed.

Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="7c71b-120">Örneği çalıştırdığınızda, hizmetten gönderilen geri çağırma arabirimindeki istemciye döndürülen iletileri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="7c71b-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="7c71b-121">Her ara sonuç görüntülenir ve tüm işlemler tamamlandıktan sonra denklemin tamamı gelir.</span><span class="sxs-lookup"><span data-stu-id="7c71b-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="7c71b-122">İstemcisini kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c71b-122">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7c71b-123">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7c71b-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7c71b-124">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="7c71b-124">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="7c71b-125">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7c71b-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="7c71b-126">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7c71b-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="7c71b-127">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7c71b-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7c71b-128">İstemciyi bir çapraz makine yapılandırmasında çalıştırırken, localhost 'u [\<client > öğesinin\<uç noktası >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) `address` özniteliğinde ve `clientBaseAddress` bağlamasının\<özniteliği ile değiştirdiğinizden emin olun [>](../../configure-apps/file-schema/wcf/bindings.md) [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) öğesinin öğesi, aşağıda gösterildiği gibi uygun makinenin adı ile.</span><span class="sxs-lookup"><span data-stu-id="7c71b-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>

    ```xml
    <client>
        <endpoint name = ""
          address=
         "http://service_machine_name/servicemodelsamples/service.svc"
        />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress=
            "http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```
