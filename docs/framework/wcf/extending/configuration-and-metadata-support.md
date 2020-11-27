---
title: Yapılandırma ve Meta Veri Desteği
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: fe7de6fddeccbc83bc81eea69c27c7da5df5c8c3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258003"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="b800e-102">Yapılandırma ve Meta Veri Desteği</span><span class="sxs-lookup"><span data-stu-id="b800e-102">Configuration and Metadata Support</span></span>

<span data-ttu-id="b800e-103">Bu konuda, bağlamalar ve bağlama öğeleri için yapılandırma ve meta veri desteğinin nasıl etkinleştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b800e-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="b800e-104">Yapılandırma ve meta verilere genel bakış</span><span class="sxs-lookup"><span data-stu-id="b800e-104">Overview of Configuration and Metadata</span></span>  

 <span data-ttu-id="b800e-105">Bu konuda, [Kanallar geliştirme](developing-channels.md) görev listesinde 1, 2 ve 4 ' te isteğe bağlı olan aşağıdaki görevler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b800e-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="b800e-106">Bağlama öğesi için yapılandırma dosyası desteği etkinleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="b800e-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="b800e-107">Bağlama için yapılandırma dosyası desteğini etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="b800e-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="b800e-108">Bağlama öğesi için WSDL ve ilke onayları dışarı aktarılıyor.</span><span class="sxs-lookup"><span data-stu-id="b800e-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="b800e-109">Bağlama veya bağlama öğesini eklemek ve yapılandırmak için WSDL ve ilke onayları tanımlama.</span><span class="sxs-lookup"><span data-stu-id="b800e-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="b800e-110">Kullanıcı Tanımlı Bağlamalar ve bağlama öğeleri oluşturma hakkında daha fazla bilgi için, sırasıyla [User-Defined bağlamaları oluşturma](creating-user-defined-bindings.md) ve [bir BindingElement oluşturma](creating-a-bindingelement.md)hakkında bilgi için bkz..</span><span class="sxs-lookup"><span data-stu-id="b800e-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="b800e-111">Yapılandırma desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="b800e-111">Adding Configuration Support</span></span>  

 <span data-ttu-id="b800e-112">Bir kanal için yapılandırma dosyası desteğini etkinleştirmek üzere, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> bağlama öğeleri için yapılandırma desteğinin etkinleştirildiği ve <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> ve <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType> bağlamaları için yapılandırma desteğini etkinleştiren iki yapılandırma bölümü uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b800e-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="b800e-113">Bunu yapmanın daha kolay bir yolu, bağlamalarınız ve bağlama öğeleriniz için yapılandırma kodu oluşturmak üzere [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) örnek aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b800e-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="b800e-114">BindingElementExtensionElement genişletme</span><span class="sxs-lookup"><span data-stu-id="b800e-114">Extending BindingElementExtensionElement</span></span>  

 <span data-ttu-id="b800e-115">Aşağıdaki örnek kod [aktarımdan alınmıştır: UDP](../samples/transport-udp.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="b800e-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="b800e-116">, `UdpTransportElement` <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> `UdpTransportBindingElement` Yapılandırma sistemine yönelik bir ' dır.</span><span class="sxs-lookup"><span data-stu-id="b800e-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="b800e-117">Birkaç temel geçersiz kılmalarla, örnek yapılandırma bölümü adını, bağlama öğesinin türünü ve bağlama öğesinin nasıl oluşturulacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b800e-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="b800e-118">Kullanıcılar daha sonra uzantı bölümünü bir yapılandırma dosyasına aşağıdaki şekilde kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="b800e-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b800e-119">Uzantıya, taşıma olarak UDP 'yi kullanmak için özel bağlamalardan başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="b800e-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="b800e-120">Bağlama için yapılandırma ekleme</span><span class="sxs-lookup"><span data-stu-id="b800e-120">Adding Configuration for a Binding</span></span>  

 <span data-ttu-id="b800e-121">Bu bölüm, `SampleProfileUdpBindingCollectionElement` <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> `SampleProfileUdpBinding` yapılandırma sistemine yönelik bir ' dır.</span><span class="sxs-lookup"><span data-stu-id="b800e-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="b800e-122">Uygulamanın toplu işlemi, `SampleProfileUdpBindingConfigurationElement` ' den türetilen öğesine Temsilcili <xref:System.ServiceModel.Configuration.StandardBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="b800e-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="b800e-123">, `SampleProfileUdpBindingConfigurationElement` Üzerinde özelliklerine karşılık gelen özelliklerine `SampleProfileUdpBinding` ve bağlamadan eşlenecek işlevlere sahiptir `ConfigurationElement` .</span><span class="sxs-lookup"><span data-stu-id="b800e-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="b800e-124">Son olarak, `OnApplyConfiguration` `SampleProfileUdpBinding` Aşağıdaki örnek kodda gösterildiği gibi, yöntemi öğesinde geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="b800e-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                var expectedType = typeof(SampleProfileUdpBinding).AssemblyQualifiedName;
                var typePassedIn = binding.GetType().AssemblyQualifiedName;
                throw new ArgumentException($"Invalid type for binding. Expected type: {expectedType}. Type passed in: {typePassedIn}.");  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="b800e-125">Bu işleyiciyi yapılandırma sistemine kaydetmek için, ilgili yapılandırma dosyasına aşağıdaki bölümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b800e-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="b800e-126">Daha sonra [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma bölümünden başvurulabilirler.</span><span class="sxs-lookup"><span data-stu-id="b800e-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="b800e-127">Bağlama öğesi için meta veri desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="b800e-127">Adding Metadata Support for a Binding Element</span></span>  

 <span data-ttu-id="b800e-128">Bir kanalı meta veri sistemiyle bütünleştirmek için, ilkenin hem içeri ve dışarı aktarılmasını desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b800e-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="b800e-129">Bu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) gibi araçların bağlama öğesinin istemcilerini oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b800e-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="b800e-130">WSDL desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="b800e-130">Adding WSDL Support</span></span>  

 <span data-ttu-id="b800e-131">Bir bağlamadaki aktarım bağlama öğesi, meta verilerde adres bilgilerinin dışarı ve içeri aktarılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="b800e-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="b800e-132">SOAP bağlama kullanılırken, aktarım bağlama öğesi meta verilerde doğru bir taşıma URI 'sini de dışarı aktarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b800e-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="b800e-133">Aşağıdaki örnek kod [aktarımdan alınmıştır: UDP](../samples/transport-udp.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="b800e-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="b800e-134">WSDL dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="b800e-134">WSDL Export</span></span>  

 <span data-ttu-id="b800e-135">Adres bilgilerini dışarı aktarmak için, `UdpTransportBindingElement` arabirimini uygular <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b800e-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="b800e-136"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType>Yöntemi, wsdl bağlantı noktasına doğru adres bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="b800e-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="b800e-137">`UdpTransportBindingElement` <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> Ayrıca, uç nokta bir soap bağlama kullandığında yönteminin uygulanması bir aktarım URI 'si dışarı aktarır:</span><span class="sxs-lookup"><span data-stu-id="b800e-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="b800e-138">WSDL Içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="b800e-138">WSDL Import</span></span>  

 <span data-ttu-id="b800e-139">WSDL içeri aktarma sistemini, adresleri içeri aktarmayı işleyecek şekilde genişletmek için, aşağıdaki yapılandırmayı Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe yapılandırma dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b800e-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </wsdlImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b800e-140">Svcutil.exe çalıştırılırken, WSDL içeri aktarma uzantılarını yüklemeye Svcutil.exe almak için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="b800e-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="b800e-141">' I/SvcutilConfig: kullanarak yapılandırma dosyasına Svcutil.exe \<file> .</span><span class="sxs-lookup"><span data-stu-id="b800e-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="b800e-142">Yapılandırma bölümünü Svcutil.exe aynı dizindeki Svcutil.exe.config ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b800e-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="b800e-143">`UdpBindingElementImporter`Türü, arabirimini uygular <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b800e-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="b800e-144">`ImportEndpoint`YÖNTEMI wsdl bağlantı noktasından adresi içeri aktarır:</span><span class="sxs-lookup"><span data-stu-id="b800e-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="b800e-145">Ilke desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="b800e-145">Adding Policy Support</span></span>  

 <span data-ttu-id="b800e-146">Özel bağlama öğesi, söz konusu bağlama öğesinin yeteneklerini ifade etmek için bir hizmet uç noktası için WSDL bağlamasındaki ilke onaylamalarını dışarı aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="b800e-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="b800e-147">Aşağıdaki örnek kod [aktarımdan alınmıştır: UDP](../samples/transport-udp.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="b800e-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="b800e-148">İlke dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="b800e-148">Policy Export</span></span>  

 <span data-ttu-id="b800e-149">`UdpTransportBindingElement`Türü, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> ilke dışarı aktarma desteği eklemek için uygular.</span><span class="sxs-lookup"><span data-stu-id="b800e-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="b800e-150">Sonuç olarak, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> `UdpTransportBindingElement` onu içeren herhangi bir bağlama için ilke oluşturmaya dahildir.</span><span class="sxs-lookup"><span data-stu-id="b800e-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="b800e-151">' De <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType> kanal çok noktaya yayın MODUNDAYSA UDP ve başka bir onaylama için onay ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b800e-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="b800e-152">Bunun nedeni, çok noktaya yayın modunun iletişim yığınının oluşturulmasını etkilemesi ve bu nedenle her iki taraf arasında koordine olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b800e-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="b800e-153">Özel aktarım bağlama öğeleri, adresleme 'nin işlenmesinden sorumlu olduğundan, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> üzerindeki uygulamanın, `UdpTransportBindingElement` kullanılan WS-Addressing sürümünü göstermek için uygun WS-Addressing ilke onayları vermeyi de işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b800e-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="b800e-154">İlke Içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="b800e-154">Policy Import</span></span>  

 <span data-ttu-id="b800e-155">İlke içeri aktarma sistemini genişletmek için aşağıdaki yapılandırmayı Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe yapılandırma dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b800e-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b800e-156">Ardından, <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> kayıtlı sınıfımızdan () uyguladık `UdpBindingElementImporter` .</span><span class="sxs-lookup"><span data-stu-id="b800e-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="b800e-157">' De <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> , uygun ad alanındaki onayları inceleyin ve taşımayı oluşturma ve çok noktaya yayın olup olmadığını denetleme gibi işlemleri işleyin.</span><span class="sxs-lookup"><span data-stu-id="b800e-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="b800e-158">Ayrıca, içeri aktarıcıların bağlama onayları listesinden işlediği onayları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b800e-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="b800e-159">Svcutil.exe çalıştırılırken, tümleştirme için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="b800e-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="b800e-160">/SvcutilConfig: ile yapılandırma dosyası Svcutil.exe noktası \<file> .</span><span class="sxs-lookup"><span data-stu-id="b800e-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="b800e-161">Yapılandırma bölümünü Svcutil.exe aynı dizindeki Svcutil.exe.config ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b800e-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="b800e-162">Özel standart bağlama Içeri aktarıcı ekleme</span><span class="sxs-lookup"><span data-stu-id="b800e-162">Adding a Custom Standard Binding Importer</span></span>  

 <span data-ttu-id="b800e-163">Svcutil.exe ve <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> türü, varsayılan olarak, sistem tarafından belirtilen bağlamaları tanır ve içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="b800e-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="b800e-164">Aksi takdirde, bağlama bir örnek olarak içeri aktarılır <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b800e-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="b800e-165">Svcutil.exe etkinleştirmek ve <xref:System.ServiceModel.Description.WsdlImporter> içeri aktarmak için `SampleProfileUdpBinding` `UdpBindingElementImporter` özel bir standart bağlama İçeri Aktarıcı işlevi de çalışır.</span><span class="sxs-lookup"><span data-stu-id="b800e-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="b800e-166">Özel standart bağlama İçeri Aktarıcı, `ImportEndpoint` <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> belirli bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> Standart bağlama tarafından oluşturulup oluşturulmadığını görmek için meta verilerden içeri aktarılan örneği incelemek üzere arabirimindeki yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="b800e-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```csharp  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b800e-167">Genellikle, özel bir standart bağlama alma programı uygulamak, yalnızca standart bağlama tarafından ayarlanmış olabilecek özelliklerin değiştiğini ve diğer tüm özelliklerin varsayılan olduğunu doğrulamak için içeri aktarılan bağlama öğelerinin özelliklerinin denetlenmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b800e-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="b800e-168">Standart bağlama İçeri Aktarıcı uygulamaya yönelik temel bir strateji, standart bağlamanın bir örneğini oluşturmaktır, özellikleri bağlama öğelerinden standart bağlamanın desteklediği standart bağlama örneğine yayar ve içeri aktarılan bağlama öğeleriyle standart bağlamalardan bağlama öğelerini karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="b800e-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
