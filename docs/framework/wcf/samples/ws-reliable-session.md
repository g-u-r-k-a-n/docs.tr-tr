---
title: WS Güvenilir Oturum
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: cf3e206724636113646c478407e61dc1c775b620
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267201"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="828d1-102">WS Güvenilir Oturum</span><span class="sxs-lookup"><span data-stu-id="828d1-102">WS Reliable Session</span></span>

<span data-ttu-id="828d1-103">Bu örnek, güvenilir oturumların kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="828d1-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="828d1-104">Güvenilir Oturumlar, güvenilir mesajlaşma ve oturumlar için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="828d1-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="828d1-105">Güvenilir Mesajlaşma, hata durumunda iletişim kurmayı yeniden dener ve mesajların, iletilerin sıralı gelişmesi gibi belirli bir şekilde belirtilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="828d1-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="828d1-106">Oturumlar, çağrılar arasındaki istemciler için durumu korur.</span><span class="sxs-lookup"><span data-stu-id="828d1-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="828d1-107">Örnek, istemci durumunun sürdürülmesi için oturumları uygular ve sıralı teslim bildirimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="828d1-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="828d1-108">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="828d1-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="828d1-109">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="828d1-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="828d1-110">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="828d1-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="828d1-111">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="828d1-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="828d1-112">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="828d1-112">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="828d1-113">Güvenilir oturum özellikleri, istemci ve hizmet için uygulama yapılandırma dosyalarında etkinleştirilir ve yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="828d1-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="828d1-114">Bu örnekte, hizmet Internet Information Services (IIS) içinde barındırılır ve istemci bir konsol uygulaması (. exe).</span><span class="sxs-lookup"><span data-stu-id="828d1-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="828d1-115">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="828d1-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="828d1-116">Örnek öğesini kullanır `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="828d1-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="828d1-117">Bağlama, hem istemci hem de hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="828d1-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="828d1-118">Bağlama türü, `binding` Aşağıdaki örnek yapılandırmada gösterildiği gibi Endpoint öğesinin özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="828d1-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="828d1-119">Uç nokta, `bindingConfiguration` "Binding1" adlı bağlama yapılandırmasına başvuran bir öznitelik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="828d1-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="828d1-120">Bağlama yapılandırması `enabled` , öğesinin özniteliğini olarak ayarlayarak güvenilir oturumlara olanak sağlar [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) `true` .</span><span class="sxs-lookup"><span data-stu-id="828d1-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="828d1-121">Sıralı oturumlar için teslim kesintileri, sıralanmış özniteliği veya olarak ayarlanarak denetlenir `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="828d1-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="828d1-122">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="828d1-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="828d1-123">Hizmet uygulama sınıfı, <xref:System.ServiceModel.InstanceContextMode.PerSession> Aşağıdaki örnek kodda gösterildiği gibi her istemci için ayrı bir sınıf örneği tutmak üzere örnek oluşturma uygular.</span><span class="sxs-lookup"><span data-stu-id="828d1-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="828d1-124">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="828d1-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="828d1-125">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="828d1-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="828d1-126">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="828d1-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="828d1-127">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="828d1-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="828d1-128">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="828d1-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="828d1-129">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="828d1-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="828d1-130">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="828d1-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
