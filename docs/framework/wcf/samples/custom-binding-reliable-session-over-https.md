---
title: HTTPS Üzerinden Özel Bağlama Güvenli Oturum
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: aec9bc11fab71a8e3adfe60e0c19b0ac4a9e3699
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241895"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="9fe6d-102">HTTPS Üzerinden Özel Bağlama Güvenli Oturum</span><span class="sxs-lookup"><span data-stu-id="9fe6d-102">Custom Binding Reliable Session over HTTPS</span></span>

<span data-ttu-id="9fe6d-103">Bu örnek, SSL Aktarım güvenliği 'nin güvenilir oturumlarla kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-103">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="9fe6d-104">Güvenilir oturumlar WS-Reliable mesajlaşma protokolünü uygular.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-104">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="9fe6d-105">Güvenilir Oturumlar üzerinde WS-Security oluşturarak güvenli bir güvenilir oturumunuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-105">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="9fe6d-106">Ancak bazen, SSL ile HTTP Transport Security kullanmayı tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-106">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9fe6d-107">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9fe6d-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9fe6d-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9fe6d-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9fe6d-110">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="9fe6d-111">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9fe6d-111">Sample Details</span></span>  

 <span data-ttu-id="9fe6d-112">SSL, paketlerin kendilerine güvenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-112">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="9fe6d-113">Bu, WS-Secure konuşmayı kullanarak güvenilir oturumu güvenli hale getirmenin farklı olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-113">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="9fe6d-114">HTTPS üzerinden güvenilir oturum kullanmak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-114">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="9fe6d-115">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-115">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="9fe6d-116">Güvenilir oturum bağlama öğesi ve kullanılarak özel bir bağlama oluşturulur [\<httpsTransport>](../../configure-apps/file-schema/wcf/httpstransport.md) .</span><span class="sxs-lookup"><span data-stu-id="9fe6d-116">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="9fe6d-117">Aşağıdaki yapılandırma özel bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-117">The following configuration is of the custom binding.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="9fe6d-118">Örnekteki program kodu, [Başlarken](getting-started-sample.md) hizmetindekilerle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-118">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="9fe6d-119">Örneği oluşturmadan önce bir sertifika oluşturmalı ve Web sunucusu Sertifika sihirbazını kullanarak atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-119">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="9fe6d-120">Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, istemci için aşağıdaki örnek yapılandırmada gösterildiği gibi özel bağlamanın kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-120">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="9fe6d-121">Belirtilen adres `https://` düzeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-121">The address specified uses the `https://` scheme.</span></span>  
  
 <span data-ttu-id="9fe6d-122">Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızdan bir https: adresine erişmeye çalıştığınızda bir güvenlik uyarısı görünür `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="9fe6d-122">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="9fe6d-123">Windows Communication Foundation (WCF) istemcisinin bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-123">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="9fe6d-124">Üretim sertifikaları kullanılırken bu kod ve eşlik eden sınıf gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-124">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="9fe6d-125">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9fe6d-126">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-126">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9fe6d-127">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9fe6d-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9fe6d-128">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-128">Install  ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="9fe6d-129">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="9fe6d-130">[Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-130">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="9fe6d-131">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="9fe6d-132">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9fe6d-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
