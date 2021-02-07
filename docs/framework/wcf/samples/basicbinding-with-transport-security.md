---
description: 'Daha fazla bilgi edinin: taşıma güvenliği ile BasicBinding'
title: Taşıma Güvenliği ile BasicBinding
ms.date: 03/30/2017
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
ms.openlocfilehash: e3d196136fcf91e3e61f82cee7e16421db221192
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755908"
---
# <a name="basicbinding-with-transport-security"></a><span data-ttu-id="3faf1-103">Taşıma Güvenliği ile BasicBinding</span><span class="sxs-lookup"><span data-stu-id="3faf1-103">BasicBinding with Transport Security</span></span>

<span data-ttu-id="3faf1-104">Bu örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3faf1-104">This sample demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="3faf1-105">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="3faf1-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3faf1-106">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3faf1-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3faf1-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3faf1-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3faf1-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3faf1-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3faf1-109">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3faf1-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`

## <a name="sample-details"></a><span data-ttu-id="3faf1-110">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3faf1-110">Sample Details</span></span>

<span data-ttu-id="3faf1-111">Varsayılan olarak, temel bağlama HTTP iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="3faf1-111">By default, the basic binding supports HTTP communication.</span></span> <span data-ttu-id="3faf1-112">Örnek, temel bağlama için taşıma güvenliğinin nasıl etkinleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3faf1-112">The sample shows how to enable transport security for the basic binding.</span></span> <span data-ttu-id="3faf1-113">Örneği çalıştırmadan önce, bir sertifika oluşturmanız ve Web sunucusu Sertifika Sihirbazı 'Nı kullanarak atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3faf1-113">Before you run the sample, you must create a certificate and assign it by using the Web Server Certificate Wizard.</span></span>

> [!NOTE]
> <span data-ttu-id="3faf1-114">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="3faf1-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="3faf1-115">Örnekteki program kodu, [Başlarken](getting-started-sample.md) hizmetindekilerle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3faf1-115">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="3faf1-116">Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi güvenli iletişim sağlamak için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="3faf1-116">The endpoint definition and binding definition in the configuration file settings are modified to enable secure communication, as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
   </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"/>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="3faf1-117">Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızda bir HTTPS: adresine erişmeye çalıştığınızda bir güvenlik uyarısı görünür `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="3faf1-117">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an HTTPS: address in your browser, such as `https://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="3faf1-118">Windows Communication Foundation (WCF) istemcisinin bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenir.</span><span class="sxs-lookup"><span data-stu-id="3faf1-118">To allow the Windows Communication Foundation (WCF) client to work with a test certificate, some additional code is added to the client to suppress the security alert.</span></span> <span data-ttu-id="3faf1-119">Gerçek sertifikalar kullanılırken bu kod ve eşlik eden sınıf gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3faf1-119">This code, and the accompanying class, is not necessary when using real certificates.</span></span>

```csharp
// This code is required only for test certificates such as those
// created by Makecert.exe.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```

<span data-ttu-id="3faf1-120">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3faf1-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3faf1-121">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3faf1-121">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3faf1-122">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3faf1-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3faf1-123">Aşağıdaki komutu kullanarak ASP.NET 4,0 'yi yükler:</span><span class="sxs-lookup"><span data-stu-id="3faf1-123">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="3faf1-124">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3faf1-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="3faf1-125">[Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3faf1-125">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="3faf1-126">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3faf1-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="3faf1-127">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3faf1-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>
