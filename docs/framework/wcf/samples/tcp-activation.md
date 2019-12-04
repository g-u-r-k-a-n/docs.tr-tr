---
title: TCP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: c1a2c0de5fbb666ec3b68ec3da31cc27f8234cbd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716603"
---
# <a name="tcp-activation"></a><span data-ttu-id="0e33c-102">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="0e33c-102">TCP Activation</span></span>

<span data-ttu-id="0e33c-103">Bu örnekte, net. TCP protokolü üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows Işlem etkinleştirme Hizmetleri 'ni (WAS) kullanan bir hizmetin barındırılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0e33c-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="0e33c-104">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="0e33c-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0e33c-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="0e33c-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e33c-106">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e33c-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0e33c-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0e33c-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="0e33c-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="0e33c-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0e33c-109">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0e33c-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="0e33c-110">Örnek, bir istemci konsol programından (. exe) ve tarafından etkinleştirilen bir çalışan işlemde barındırılan bir hizmet kitaplığından (. dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="0e33c-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="0e33c-111">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="0e33c-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="0e33c-112">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="0e33c-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="0e33c-113">Sözleşme, aşağıdaki örnek kodda gösterildiği gibi matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan `ICalculator` arabirimi tarafından tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="0e33c-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

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

<span data-ttu-id="0e33c-114">Hizmet uygulama, uygun sonucu hesaplar ve döndürür:</span><span class="sxs-lookup"><span data-stu-id="0e33c-114">The service implementation calculates and returns the appropriate result:</span></span>

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

<span data-ttu-id="0e33c-115">Örnek, TCP bağlantı noktası Paylaşımı etkin ve güvenlik kapatılmış olan net. TCP bağlamasının bir türevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0e33c-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="0e33c-116">Güvenli bir TCP bağlaması kullanmak istiyorsanız, sunucunun güvenlik modunu istenen ayarla değiştirin ve istemci üzerinde bir güncelleştirme istemci yapılandırma dosyası oluşturmak için Svcutil. exe dosyasını yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0e33c-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="0e33c-117">Aşağıdaki örnekte hizmetin yapılandırması gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0e33c-117">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
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

<span data-ttu-id="0e33c-118">İstemcinin uç noktası aşağıdaki örnek kodda gösterildiği gibi yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="0e33c-118">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="0e33c-119">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0e33c-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0e33c-120">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0e33c-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0e33c-121">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0e33c-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="0e33c-122">IIS 7,0 'nin yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0e33c-122">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="0e33c-123">WAS etkinleştirmesi için IIS 7,0 gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0e33c-123">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="0e33c-124">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0e33c-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="0e33c-125">Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="0e33c-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="0e33c-126">**Başlat** menüsünde, **Denetim Masası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="0e33c-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="0e33c-127">**Programlar ve Özellikler '** i seçin.</span><span class="sxs-lookup"><span data-stu-id="0e33c-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="0e33c-128">**Windows bileşenlerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0e33c-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="0e33c-129">**Microsoft .NET Framework 3,0** düğümünü genişletin ve **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0e33c-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="0e33c-130">TCP etkinleştirmesini destekleyecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="0e33c-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="0e33c-131">Kolaylık olması halinde, örnek dizinde bulunan AddNetTcpSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0e33c-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="0e33c-132">Net. TCP etkinleştirmesini desteklemek için, önce varsayılan Web sitesinin bir net. TCP bağlantı noktasına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e33c-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="0e33c-133">Bu işlem, Internet Information Services 7,0 (IIS) yönetim araç takımı ile yüklenen appcmd. exe kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e33c-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="0e33c-134">Yönetici düzeyindeki bir komut isteminden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0e33c-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="0e33c-135">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="0e33c-135">This command is a single line of text.</span></span> <span data-ttu-id="0e33c-136">Bu komut, TCP bağlantı noktası 808 üzerinde dinleme yapan varsayılan Web sitesine bir net. TCP site bağlamayı herhangi bir ana bilgisayar adı ile ekler.</span><span class="sxs-lookup"><span data-stu-id="0e33c-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="0e33c-137">Bir sitedeki tüm uygulamalar ortak bir net. TCP bağlamasını paylaşır, ancak her uygulama net. TCP desteğini tek tek etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="0e33c-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="0e33c-138">/Servicemodelsamples uygulaması için net. TCP 'yi etkinleştirmek üzere yönetici düzeyinde bir komut isteminden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0e33c-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="0e33c-139">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="0e33c-139">This command is a single line of text.</span></span> <span data-ttu-id="0e33c-140">Bu komut,/servicemodelsamples uygulamasına hem `http://localhost/servicemodelsamples` hem de `net.tcp://localhost/servicemodelsamples`kullanılarak erişilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e33c-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="0e33c-141">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="0e33c-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="0e33c-142">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="0e33c-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    <span data-ttu-id="0e33c-143">Bu örnek için eklemiş olduğunuz net. TCP site bağlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0e33c-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="0e33c-144">Kolaylık olması halinde, örnek dizinde bulunan RemoveNetTcpSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0e33c-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="0e33c-145">Yönetici düzeyinde bir komut isteminden aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. TCP ' i kaldırın:</span><span class="sxs-lookup"><span data-stu-id="0e33c-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="0e33c-146">Bu komut tek satırlık bir metin olarak girilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0e33c-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="0e33c-147">Yönetici düzeyinde bir komut isteminden aşağıdaki komutu çalıştırarak net. TCP site bağlamasını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="0e33c-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="0e33c-148">Bu komutun tek satırlık bir metin olarak yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e33c-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e33c-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e33c-149">See also</span></span>

- [<span data-ttu-id="0e33c-150">AppFabric barındırma ve kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="0e33c-150">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
