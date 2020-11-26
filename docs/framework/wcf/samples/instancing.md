---
title: Örnek Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 55042af1e6eec1fe4b3e2cf07d03596e4793575f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237761"
---
# <a name="instancing"></a><span data-ttu-id="ad41e-102">Örnek Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad41e-102">Instancing</span></span>

<span data-ttu-id="ad41e-103">Örnek oluşturma örneği, bir hizmet sınıfı örneklerinin istemci isteklerine yanıt olarak nasıl oluşturulduğunu denetleyen örnek oluşturma davranış ayarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad41e-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="ad41e-104">Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="ad41e-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="ad41e-105">Bu örnek, öğesinden devralan yeni bir sözleşme tanımlar `ICalculatorInstance` `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="ad41e-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="ad41e-106">Tarafından belirtilen sözleşme, `ICalculatorInstance` hizmet örneğinin durumunu incelemek için üç ek işlem sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad41e-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="ad41e-107">Örnek ayarını değiştirerek, istemcisini çalıştırarak değişiklik davranışını gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad41e-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="ad41e-108">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="ad41e-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad41e-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ad41e-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ad41e-110">Aşağıdaki örnek oluşturma modları kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ad41e-110">The following instancing modes are available:</span></span>  
  
- <span data-ttu-id="ad41e-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: Her istemci isteği için yeni bir hizmet örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ad41e-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
- <span data-ttu-id="ad41e-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: Her yeni istemci oturumu için yeni bir örnek oluşturulur ve bu oturumun kullanım ömrü boyunca korunur (oturumu destekleyen bir bağlama gerekir).</span><span class="sxs-lookup"><span data-stu-id="ad41e-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
- <span data-ttu-id="ad41e-113"><xref:System.ServiceModel.InstanceContextMode.Single>: Hizmet sınıfının tek bir örneği, uygulamanın kullanım ömrü boyunca tüm istemci isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="ad41e-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="ad41e-114">Service sınıfı, `[ServiceBehavior(InstanceContextMode=<setting>)]` Aşağıdaki kod örneğinde gösterildiği gibi özniteliği ile örnek oluşturma davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad41e-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="ad41e-115">Hangi satırların açıklama olarak değiştirildiğini değiştirerek, her örnek modunun davranışını gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad41e-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="ad41e-116">Örnek oluşturma modunu değiştirdikten sonra hizmeti yeniden oluşturmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ad41e-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="ad41e-117">İstemcide belirtmek için örnek oluşturma ile ilgili ayarlar yoktur.</span><span class="sxs-lookup"><span data-stu-id="ad41e-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="ad41e-118">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ad41e-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ad41e-119">Hizmetin altında çalıştığı örnek modu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ad41e-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="ad41e-120">Her işlemden sonra örnek KIMLIĞI ve işlem sayısı, örnek oluşturma modunun davranışını yansıtacak şekilde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ad41e-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="ad41e-121">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ad41e-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ad41e-122">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ad41e-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ad41e-123">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ad41e-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ad41e-124">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ad41e-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ad41e-125">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ad41e-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad41e-126">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad41e-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ad41e-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ad41e-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ad41e-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ad41e-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ad41e-129">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ad41e-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
