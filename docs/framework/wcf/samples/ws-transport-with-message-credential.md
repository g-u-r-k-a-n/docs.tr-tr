---
description: Ileti kimlik bilgileri Ile WS aktarımı hakkında daha fazla bilgi edinin
title: İleti Kimlik Bilgileri ile WS Aktarma
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 02514ad4d0bfd103126667f5ecdd21a6bc9151fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668337"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="b6d74-103">İleti Kimlik Bilgileri ile WS Aktarma</span><span class="sxs-lookup"><span data-stu-id="b6d74-103">WS Transport With Message Credential</span></span>

<span data-ttu-id="b6d74-104">Bu örnek, iletide yürütülen istemci kimlik bilgileri ile birlikte SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6d74-104">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="b6d74-105">Bu örnek, `wsHttpBinding` bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b6d74-105">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="b6d74-106">Varsayılan olarak, `wsHttpBinding` bağlama http iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6d74-106">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="b6d74-107">Aktarım güvenliği için yapılandırıldığında bağlama, HTTPS iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="b6d74-107">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="b6d74-108">HTTPS, tel üzerinden iletilen iletiler için Gizlilik ve bütünlük koruması sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6d74-108">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="b6d74-109">Ancak, hizmette istemcinin kimliğini doğrulamak için kullanılabilen kimlik doğrulama mekanizmaları kümesi, HTTPS aktarımının desteklediği ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b6d74-109">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="b6d74-110">Windows Communication Foundation (WCF) `TransportWithMessageCredential` , bu kısıtlamayı aşmak için tasarlanan bir güvenlik modu sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6d74-110">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="b6d74-111">Bu güvenlik modu yapılandırıldığında, aktarım güvenliği, iletilen iletiler için Gizlilik ve bütünlük sağlamak ve hizmet kimlik doğrulamasını gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6d74-111">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="b6d74-112">Ancak istemci kimlik doğrulaması, istemci kimlik bilgisi doğrudan iletiye yerleştirilerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b6d74-112">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="b6d74-113">Bu, aktarım güvenliği modunun performans avantajını korurken istemci kimlik doğrulaması için ileti güvenliği modu tarafından desteklenen herhangi bir kimlik bilgisi türünü kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6d74-113">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="b6d74-114">Bu örnekte, `UserName` istemcinin kimliğini doğrulamak için bir kimlik bilgisi türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6d74-114">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="b6d74-115">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b6d74-115">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="b6d74-116">`wsHttpBinding`Bağlama belirtilir ve istemci ve hizmet için uygulama yapılandırma dosyalarında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b6d74-116">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6d74-117">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b6d74-117">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b6d74-118">Örnekteki program kodu, [kullanmaya](getting-started-sample.md) başlama hizmetindekilerle neredeyse aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b6d74-118">The program code in the sample is almost identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="b6d74-119">Hizmet sözleşmesi tarafından sağlanmış bir ek işlem vardır `GetCallerIdentity` .</span><span class="sxs-lookup"><span data-stu-id="b6d74-119">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="b6d74-120">Bu işlem, arayanın kimliğinin adını çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6d74-120">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="b6d74-121">Örneği oluşturmadan önce bir sertifika oluşturmalı ve Web sunucusu Sertifika sihirbazını kullanarak atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6d74-121">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="b6d74-122">Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, `TransportWithMessageCredential` istemci için aşağıdaki örnek yapılandırmada gösterildiği gibi güvenlik modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b6d74-122">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b6d74-123">Belirtilen adres `https://` düzeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="b6d74-123">The address specified uses the `https://` scheme.</span></span> <span data-ttu-id="b6d74-124">Bağlama yapılandırması güvenlik modunu olarak ayarlar `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="b6d74-124">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="b6d74-125">Hizmetin Web.config dosyasında aynı güvenlik modu belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6d74-125">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="b6d74-126">Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızdan bir https: adresine erişmeye çalıştığınızda bir güvenlik uyarısı görünür  `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="b6d74-126">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="b6d74-127">WCF istemcisinin yerinde bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b6d74-127">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="b6d74-128">Üretim sertifikaları kullanılırken bu kod ve eşlik eden sınıf gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b6d74-128">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="b6d74-129">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b6d74-129">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b6d74-130">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b6d74-130">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:
YourDomainName\YourAccountName  
   Enter password:
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b6d74-131">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b6d74-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b6d74-132">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b6d74-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b6d74-133">[Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b6d74-133">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
3. <span data-ttu-id="b6d74-134">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b6d74-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="b6d74-135">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b6d74-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
