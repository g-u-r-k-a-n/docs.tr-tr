---
title: Kendini Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 9077f2b00c97ae2a2106a50780cfd2cd9596c1ec
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716315"
---
# <a name="self-host"></a><span data-ttu-id="33b81-102">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="33b81-102">Self-Host</span></span>
<span data-ttu-id="33b81-103">Bu örnek, bir konsol uygulamasında kendi kendine barındırılan bir hizmetin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="33b81-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="33b81-104">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="33b81-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="33b81-105">Hizmet yapılandırma dosyası, Web. config 'den App. config olarak yeniden adlandırıldı ve konağın kullandığı bir temel adres yapılandırmak üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="33b81-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="33b81-106">Hizmet kaynak kodu, yapılandırılmış temel adresi sağlayan bir hizmet ana bilgisayarı oluşturan ve açan bir statik `Main` işlevi uygulayacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33b81-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="33b81-107">Hizmet uygulamasının her işlem için konsola çıkış yazacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33b81-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="33b81-108">Hizmetin doğru uç nokta adresini yapılandırma dışında, istemci değiştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="33b81-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33b81-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="33b81-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="33b81-110">Örnek, aşağıdaki örnek kodda gösterildiği gibi, verilen `CalculatorService` türü için <xref:System.ServiceModel.ServiceHost> oluşturmak üzere statik Main işlevi uygular.</span><span class="sxs-lookup"><span data-stu-id="33b81-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="33b81-111">Bir hizmet Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) içinde barındırılıyorsa, hizmetin temel adresi barındırma ortamı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="33b81-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="33b81-112">Şirket içinde barındırılan durumda, temel adresi kendiniz belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33b81-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="33b81-113">Bu, aşağıdaki örnek yapılandırmada gösterildiği gibi `add` öğesi, [\<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), [>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) [\<ana bilgisayar](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)\<alt öğesi kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="33b81-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="33b81-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="33b81-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="33b81-115">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="33b81-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="33b81-116">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="33b81-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="33b81-117">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="33b81-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="33b81-118">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="33b81-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="33b81-119">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="33b81-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="33b81-120">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="33b81-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="33b81-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="33b81-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="33b81-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="33b81-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33b81-123">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="33b81-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="33b81-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33b81-124">See also</span></span>

- [<span data-ttu-id="33b81-125">AppFabric barındırma ve kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="33b81-125">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
