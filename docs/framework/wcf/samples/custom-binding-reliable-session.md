---
title: Özel Bağlama Güvenilir Oturum
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: bd690f96eea885c4d414f9725125e1918fdffa23
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585149"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="9efd4-102">Özel Bağlama Güvenilir Oturum</span><span class="sxs-lookup"><span data-stu-id="9efd4-102">Custom Binding Reliable Session</span></span>

<span data-ttu-id="9efd4-103">Özel bağlama, farklı bağlama öğelerinin sıralı bir listesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9efd4-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="9efd4-104">Bu örnek, özellikle güvenilir oturumları etkinleştiren çeşitli taşıma ve ileti kodlama öğeleriyle özel bağlamanın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9efd4-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9efd4-105">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9efd4-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9efd4-106">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9efd4-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9efd4-107">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9efd4-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9efd4-108">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9efd4-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a><span data-ttu-id="9efd4-109">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9efd4-109">Sample Details</span></span>

<span data-ttu-id="9efd4-110">Güvenilir Oturumlar, güvenilir mesajlaşma ve oturumlara yönelik özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9efd4-110">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="9efd4-111">Güvenilir Mesajlaşma, hata durumunda iletişim kurmayı yeniden dener ve iletilerin belirli bir sırada gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9efd4-111">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="9efd4-112">Oturumlar, çağrılar arasındaki istemciler için durumu korur.</span><span class="sxs-lookup"><span data-stu-id="9efd4-112">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="9efd4-113">Örnek, istemci durumunun sürdürülmesi için oturumları uygular ve sıralı teslim bildirimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9efd4-113">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="9efd4-114">Örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="9efd4-114">The sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="9efd4-115">Güvenilir oturum özellikleri, istemci ve hizmet için uygulama yapılandırma dosyalarında etkinleştirilir ve yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="9efd4-115">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>

> [!NOTE]
> <span data-ttu-id="9efd4-116">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="9efd4-116">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="9efd4-117">Bağlama öğelerinin sıralaması, her biri kanal yığınındaki bir katmanı temsil ettiğinden (bkz. [Özel Bağlamalar](../extending/custom-bindings.md)) özel bir bağlama tanımlamak açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9efd4-117">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span>

<span data-ttu-id="9efd4-118">Örnek için hizmet yapılandırması, aşağıdaki kod örneğinde gösterildiği gibi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9efd4-118">The service configuration for the sample is defined as shown in the following code example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

<span data-ttu-id="9efd4-119">Bir çapraz makine senaryosunda çalışırken, istemcinin uç nokta adresini hizmetin ana bilgisayar adını yansıtacak şekilde değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9efd4-119">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>

<span data-ttu-id="9efd4-120">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9efd4-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9efd4-121">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9efd4-121">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9efd4-122">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9efd4-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="9efd4-123">Aşağıdaki komutu kullanarak ASP.NET 4,0 'yi yükler:</span><span class="sxs-lookup"><span data-stu-id="9efd4-123">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="9efd4-124">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9efd4-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="9efd4-125">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9efd4-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="9efd4-126">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9efd4-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9efd4-127">İstemciyi bir çapraz makine yapılandırmasında çalıştırırken, `address` Aşağıdaki örnekte gösterildiği gibi, hem öğesinin özniteliğinde hem de ' nin özniteliği için "localhost" [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) öğesini ve `clientBaseAddress` [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) uygun makinenin adını ile değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9efd4-127">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
