---
description: 'Daha fazla bilgi edinin: NamedPipe etkinleştirme'
title: NamedPipe Etkinleştirme
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 32878b08450b6d4d2d88b3d36c019b3e2138625f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259544"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="5128b-103">NamedPipe Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="5128b-103">NamedPipe Activation</span></span>

<span data-ttu-id="5128b-104">Bu örnekte, adlandırılmış kanallar üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows Işlem etkinleştirme hizmeti (WAS) kullanan bir hizmetin barındırılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5128b-104">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over named pipes.</span></span> <span data-ttu-id="5128b-105">Bu örnek [Başlarken](getting-started-sample.md) ' e dayalıdır ve Windows Vista 'nın çalışmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5128b-105">This sample is based on the [Getting Started](getting-started-sample.md) and requires Windows Vista to run.</span></span>

> [!NOTE]
> <span data-ttu-id="5128b-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="5128b-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5128b-107">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5128b-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5128b-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5128b-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5128b-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5128b-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5128b-110">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5128b-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="5128b-111">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5128b-111">Sample Details</span></span>

<span data-ttu-id="5128b-112">Örnek, bir istemci konsol programından (. exe) ve Windows Işlem etkinleştirme Hizmetleri (WAS) tarafından etkinleştirilen bir çalışan işleminde barındırılan bir hizmet kitaplığından (. dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="5128b-112">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="5128b-113">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="5128b-113">Client activity is visible in the console window.</span></span>

<span data-ttu-id="5128b-114">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="5128b-114">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5128b-115">Sözleşme, `ICalculator` Aşağıdaki örnek kodda gösterildiği gibi matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5128b-115">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

```csharp
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

<span data-ttu-id="5128b-116">İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet uygulamasını hesaplar ve ilgili sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5128b-116">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

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

<span data-ttu-id="5128b-117">Örnek, bir `netNamedPipeBinding` güvenlik olmadan değiştirilmiş bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="5128b-117">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="5128b-118">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5128b-118">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="5128b-119">Hizmetin bağlama türü, `binding` Aşağıdaki örnek yapılandırmada gösterildiği gibi Endpoint öğesinin özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5128b-119">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="5128b-120">Güvenli adlandırılmış kanal bağlamayı kullanmak istiyorsanız, sunucunun güvenlik modunu istediğiniz güvenlik ayarıyla değiştirin ve güncelleştirilmiş bir istemci yapılandırma dosyası almak için istemcide svcutil.exe yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5128b-120">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
        </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="5128b-121">İstemcinin uç nokta bilgileri aşağıdaki örnek kodda gösterildiği gibi yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5128b-121">The client’s endpoint information is configured as shown in the following sample code.</span></span>

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

<span data-ttu-id="5128b-122">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5128b-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5128b-123">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5128b-123">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5128b-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5128b-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5128b-125">IIS 7,0 'nin yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5128b-125">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="5128b-126">WAS etkinleştirmesi için IIS 7,0 gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5128b-126">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="5128b-127">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5128b-127">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="5128b-128">Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="5128b-128">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="5128b-129">**Başlat** menüsünde, **Denetim Masası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="5128b-129">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="5128b-130">**Programlar ve Özellikler '** i seçin.</span><span class="sxs-lookup"><span data-stu-id="5128b-130">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="5128b-131">**Windows bileşenlerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5128b-131">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="5128b-132">**Microsoft .NET Framework 3,0** düğümünü genişletin ve **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5128b-132">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="5128b-133">Windows Işlem etkinleştirme hizmeti 'ni (WAS) adlandırılmış kanal etkinleştirmesini destekleyecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="5128b-133">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="5128b-134">Kolaylık olması halinde, örnek dizinde bulunan AddNetPipeSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5128b-134">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="5128b-135">Net. pipe etkinleştirmesini desteklemek için, önce varsayılan Web sitesinin net. pipe protokolüne bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5128b-135">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="5128b-136">Bu, IIS 7,0 yönetim araç takımı ile yüklenen appcmd.exe kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5128b-136">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="5128b-137">Yükseltilmiş (yönetici) komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5128b-137">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="5128b-138">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="5128b-138">This command is a single line of text.</span></span>

        <span data-ttu-id="5128b-139">Bu komut, varsayılan Web sitesine bir net. pipe site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="5128b-139">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="5128b-140">Bir sitedeki tüm uygulamalar ortak bir net. pipe bağlamasını paylaşır, ancak her uygulama net. pipe desteğini tek tek etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5128b-140">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="5128b-141">/Servicemodelsamples uygulamasının net. pipe ' ı etkinleştirmek için, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5128b-141">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="5128b-142">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="5128b-142">This command is a single line of text.</span></span>

        <span data-ttu-id="5128b-143">Bu komut, hem hem de kullanılarak/servicemodelsamples uygulamasına erişilmesini sağlar `http://localhost/servicemodelsamples` `net.tcp://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="5128b-143">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="5128b-144">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5128b-144">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="5128b-145">Bu örnek için eklemiş olduğunuz net. pipe site bağlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5128b-145">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="5128b-146">Kolaylık olması için aşağıdaki iki adım örnek dizinde yer alan RemoveNetPipeSiteBinding. cmd adlı bir toplu iş dosyasında uygulanır:</span><span class="sxs-lookup"><span data-stu-id="5128b-146">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="5128b-147">Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. TCP ' i kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5128b-147">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="5128b-148">Bu komut tek satırlık bir metin olarak girilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5128b-148">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="5128b-149">Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak net. TCP site bağlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5128b-149">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="5128b-150">Bu komutun tek satırlık bir metin olarak yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5128b-150">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="5128b-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5128b-151">See also</span></span>

- <span data-ttu-id="5128b-152">[AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5128b-152">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
