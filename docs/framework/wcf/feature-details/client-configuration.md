---
title: İstemci Yapılandırması
description: Bir hizmete bağlanmak için kullanılan bir uç nokta için adresi, bağlamayı, davranışı ve sözleşmeyi belirtmek üzere WCF istemci yapılandırmasını nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: af9101be0067311fb1a3c0e6e575f186e8ccf161
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265979"
---
# <a name="client-configuration"></a><span data-ttu-id="c43a0-103">İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="c43a0-103">Client Configuration</span></span>

<span data-ttu-id="c43a0-104">İstemcilerin hizmet uç noktalarına bağlanmak için kullanacağı istemci uç noktasının "ABC" özelliklerini, adresi, bağlamayı, davranışı ve sözleşmeyi belirtmek için Windows Communication Foundation (WCF) istemci yapılandırmasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c43a0-104">You can use the Windows Communication Foundation (WCF) client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="c43a0-105">[\<client>](../../configure-apps/file-schema/wcf/client.md)Öğesi, [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) özniteliklerini yapılandırmak için öznitelikleri kullanılan bir öğesi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c43a0-105">The [\<client>](../../configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="c43a0-106">Bu öznitelikler, [uç noktaları yapılandırma](#configuring-endpoints) bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-106">These attributes are discussed in the [Configuring Endpoints](#configuring-endpoints) section.</span></span>  
  
 <span data-ttu-id="c43a0-107">[\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md)Öğesi Ayrıca, [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) verileri içeri ve dışarı aktarmaya yönelik ayarları belirtmek için kullanılan bir öğesi, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) özel adres üst bilgileri koleksiyonu içeren bir öğesi ve bir [\<identity>](../../configure-apps/file-schema/wcf/identity.md) uç noktanın, ileti alışverişi yapan diğer uç noktalara göre kimlik doğrulamasını sağlayan bir öğesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-107">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element also contains a [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata, a [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="c43a0-108">[\<headers>](../../configure-apps/file-schema/wcf/headers.md)Ve [\<identity>](../../configure-apps/file-schema/wcf/identity.md) öğeleri ' ın bir parçasıdır <xref:System.ServiceModel.EndpointAddress> ve [adresler](endpoint-addresses.md) makalesinde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-108">The [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](endpoint-addresses.md) article.</span></span> <span data-ttu-id="c43a0-109">Meta veri uzantılarının kullanımını açıklayan konuların bağlantıları, [meta verileri yapılandırma](#configuring-metadata) bölümünde verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-109">Links to topics that explain the use of metadata extensions are provided in the [Configuring Metadata](#configuring-metadata) section.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="c43a0-110">Uç noktaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c43a0-110">Configuring Endpoints</span></span>  

 <span data-ttu-id="c43a0-111">İstemci yapılandırması, istemcinin her biri kendi adı, adresi ve sözleşmesine sahip olan bir veya daha fazla uç nokta belirtmesini sağlamak üzere tasarlanmıştır [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) ve [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) Bu uç noktayı yapılandırmak için kullanılacak istemci yapılandırmasındaki ve öğelerine başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-111">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="c43a0-112">WCF çalışma zamanının beklediği ad olduğundan, istemci yapılandırma dosyası "App.config" olarak adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-112">The client configuration file should be named "App.config" because this is the name that the WCF runtime expects.</span></span> <span data-ttu-id="c43a0-113">Aşağıdaki örnekte bir istemci yapılandırma dosyası gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-113">The following example shows a client configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
            <!-- Add another endpoint by adding another <endpoint> element. -->
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"
                 bypassProxyOnLocal="false"
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
          <!-- Configure this binding here. -->  
        </binding>  
          </wsHttpBinding>  
     </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="c43a0-114">İsteğe bağlı `name` öznitelik, belirli bir sözleşme için bir uç noktayı benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c43a0-114">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="c43a0-115">Bu, <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> veya tarafından, <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> istemci yapılandırmasındaki hangi uç noktanın hedeflenmekte olduğunu ve hizmet için bir kanal oluşturulduğunda yüklenmesi gerektiğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-115">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="c43a0-116">Joker karakterli bir uç nokta yapılandırma adı " \* " mevcuttur ve <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> isteğe tam olarak bir tane varsa ve bir özel durum oluşturursa, dosyanın herhangi bir uç nokta yapılandırmasını yüklemesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-116">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="c43a0-117">Bu öznitelik atlanırsa, ilgili uç nokta belirtilen anlaşma türüyle ilişkili varsayılan uç nokta olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-117">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="c43a0-118">Özniteliğin varsayılan değeri, `name` diğer ad gibi eşleşen boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-118">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="c43a0-119">Uç noktanın yerini bulmak ve tanımlamak için her uç noktanın kendisiyle ilişkili bir adresi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-119">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="c43a0-120">`address`Özniteliği, uç noktanın konumunu sağlayan URL 'yi belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-120">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="c43a0-121">Ancak bir hizmet uç noktasının adresi bir Tekdüzen Kaynak tanımlayıcısı (URI) oluşturularak kodda de belirtilebilir ve <xref:System.ServiceModel.ServiceHost> metotlardan biri kullanılarak eklenir <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .</span><span class="sxs-lookup"><span data-stu-id="c43a0-121">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="c43a0-122">Daha fazla bilgi için bkz. [adresler](endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="c43a0-122">For more information, see [Addresses](endpoint-addresses.md).</span></span> <span data-ttu-id="c43a0-123">Giriş gösterdiği gibi, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) ve öğeleri ' [\<identity>](../../configure-apps/file-schema/wcf/identity.md) ın bir parçasıdır <xref:System.ServiceModel.EndpointAddress> ve de [adresler](endpoint-addresses.md) konusunda ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-123">As the introduction indicates, the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="c43a0-124">`binding`Özniteliği, uç noktanın bir hizmete bağlanırken kullanması beklenen bağlama türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-124">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="c43a0-125">Başvuruluyorsa, türün kayıtlı bir yapılandırma bölümü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-125">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="c43a0-126">Önceki örnekte, bu, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) uç noktanın bir kullandığını gösteren bölümdür <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="c43a0-126">In the previous example, this is the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="c43a0-127">Ancak, uç noktanın kullanabileceği belirli bir türün birden fazla bağlaması olabilir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-127">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="c43a0-128">Bunların her birinin [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) (Binding) türü öğesinde kendi öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-128">Each of these has its own [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element within the (binding) type element.</span></span> <span data-ttu-id="c43a0-129">`bindingconfiguration`Özniteliği aynı türden bağlamaları ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-129">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="c43a0-130">Değeri, `name` öğesinin özniteliğiyle eşleştirilir [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="c43a0-130">Its value is matched with the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span> <span data-ttu-id="c43a0-131">Yapılandırma kullanarak istemci bağlamasını yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada Istemci bağlaması belirtme](../how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c43a0-131">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="c43a0-132">`behaviorConfiguration`Bu öznitelik, [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) uç noktanın ne kadar kullanılacağını belirtmek için kullanılır [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="c43a0-132">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="c43a0-133">Değeri, `name` öğesinin özniteliğiyle eşleştirilir [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="c43a0-133">Its value is matched with the `name` attribute of the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="c43a0-134">İstemci davranışlarını belirtmek için yapılandırma kullanmayla ilgili bir örnek için bkz. [Istemci davranışlarını yapılandırma](../configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c43a0-134">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="c43a0-135">`contract`Öznitelik, uç noktanın hangi sözleşmeye sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c43a0-135">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="c43a0-136">Bu değer ile eşlenir <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c43a0-136">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="c43a0-137">Varsayılan değer, hizmeti uygulayan sınıfın tam tür adıdır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-137">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="c43a0-138">Meta verileri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c43a0-138">Configuring Metadata</span></span>  

 <span data-ttu-id="c43a0-139">[\<metadata>](../../configure-apps/file-schema/wcf/metadata.md)Öğesi, meta veri içeri aktarma uzantılarını kaydetmek için kullanılan ayarları belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c43a0-139">The [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="c43a0-140">Meta veri sistemini genişletme hakkında daha fazla bilgi için bkz. [veri sistemini genişletme](../extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="c43a0-140">For more information about extending the metadata system, see [Extending the Metadata System](../extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c43a0-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c43a0-141">See also</span></span>

- [<span data-ttu-id="c43a0-142">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="c43a0-142">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="c43a0-143">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c43a0-143">Configuring Client Behaviors</span></span>](../configuring-client-behaviors.md)
