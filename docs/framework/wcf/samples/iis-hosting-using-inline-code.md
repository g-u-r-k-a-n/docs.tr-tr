---
description: 'Hakkında daha fazla bilgi edinin: satır Içi kod kullanarak IIS barındırma'
title: Satır İçi Kod Kullanarak IIS Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 58c2e119ad49f56d015290747ab247bd45ff4d23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631872"
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="996aa-103">Satır İçi Kod Kullanarak IIS Barındırma</span><span class="sxs-lookup"><span data-stu-id="996aa-103">IIS Hosting Using Inline Code</span></span>

<span data-ttu-id="996aa-104">Bu örnek Internet Information Services (IIS) tarafından barındırılan bir hizmetin nasıl uygulanacağını gösterir; burada hizmet kodu bir. svc dosyasında satır içinde bulunur ve isteğe bağlı olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="996aa-104">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="996aa-105">Hizmet kodu Ayrıca, uygulamanın \ App_Code dizininde bulunan kaynak kodu dosyalarında doğrudan uygulanabilir veya \Bin. içinde dağıtılan derlemeye derlenmiş olabilir</span><span class="sxs-lookup"><span data-stu-id="996aa-105">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="996aa-106">Bu örnek, bu teknikleri göstermez.</span><span class="sxs-lookup"><span data-stu-id="996aa-106">This sample does not demonstrate these techniques.</span></span>

> [!NOTE]
> <span data-ttu-id="996aa-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="996aa-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="996aa-108">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="996aa-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="996aa-109">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="996aa-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="996aa-110">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="996aa-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="996aa-111">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="996aa-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

<span data-ttu-id="996aa-112">Örnek, istek-yanıt iletişim modelini tanımlayan bir sözleşmeyi uygulayan tipik bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="996aa-112">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="996aa-113">Hizmet IIS 'de barındırılır ve hizmet kodu tamamen Service. svc dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="996aa-113">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="996aa-114">Hizmet, ana bilgisayar etkinleştirilir ve hizmete gönderilen ilk ileti tarafından isteğe bağlı olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="996aa-114">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="996aa-115">Ön derleme gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="996aa-115">There is no pre-compilation necessary.</span></span> <span data-ttu-id="996aa-116">Hizmet `ICalculator` aşağıdaki kodda tanımlandığı şekilde bir sözleşme uygular:</span><span class="sxs-lookup"><span data-stu-id="996aa-116">The service implements an `ICalculator` contract as defined in the following code:</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="996aa-117">Hizmet uygulama, uygun sonucu hesaplar ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="996aa-117">The service implementation calculates and returns the appropriate result.</span></span>

`<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>`

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="996aa-118">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="996aa-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="996aa-119">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="996aa-119">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="996aa-120">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="996aa-120">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="996aa-121">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="996aa-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="996aa-122">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="996aa-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="996aa-123">Çözüm oluşturulduktan sonra, ServiceModelSamples uygulamasını IIS 7,0 ' de ayarlamak için setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="996aa-123">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="996aa-124">ServiceModelSamples dizini artık bir IIS 7,0 uygulaması olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="996aa-124">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="996aa-125">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="996aa-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="996aa-126">Bu hizmeti çağırasağlayan bir istemci uygulaması oluşturma hakkında bir örnek için bkz. [nasıl yapılır: Istemci oluşturma](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="996aa-126">For an example on how to create a client application that can call this service, see [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="996aa-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="996aa-127">See also</span></span>

- <span data-ttu-id="996aa-128">[AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="996aa-128">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
