---
description: Daha fazla bilgi için bkz. uç nokta oluşturmaya genel bakış
title: Uç Noktası Oluşturma Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: ff806428922f2097f0d570118d6b5f7836c1797b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756831"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="c6f2a-103">Uç Noktası Oluşturma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6f2a-103">Endpoint Creation Overview</span></span>

<span data-ttu-id="c6f2a-104">Bir Windows Communication Foundation (WCF) hizmeti olan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="c6f2a-105">Uç noktalar, istemcilerin bir WCF hizmetinin sunduğu işlevlere erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-105">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="c6f2a-106">Bu bölüm bir uç noktanın yapısını açıklar ve bir uç noktanın yapılandırma ve kodda nasıl tanımlanacağını özetler.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-106">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="c6f2a-107">Bir uç noktanın yapısı</span><span class="sxs-lookup"><span data-stu-id="c6f2a-107">The Structure of an Endpoint</span></span>

<span data-ttu-id="c6f2a-108">Her uç nokta, uç noktanın nerede bulunacağını belirten bir adres içerir, bir istemcinin uç noktasıyla nasıl iletişim kurabildiğini belirten bir bağlama ve kullanılabilir yöntemleri tanımlayan bir anlaşma.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-108">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>

- <span data-ttu-id="c6f2a-109">**Adres**.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-109">**Address**.</span></span> <span data-ttu-id="c6f2a-110">Adres, uç noktayı benzersiz bir şekilde tanımlar ve hizmetin bulunduğu potansiyel tüketicilere bildirir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-110">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="c6f2a-111"><xref:System.ServiceModel.EndpointAddress>Bir kimlik, bazı Web Hizmetleri Açıklama Dili (wsdl) öğeleri ve isteğe bağlı üstbilgiler koleksiyonu içeren bir Tekdüzen Kaynak tanımlayıcısı (URI) ve adres özellikleri içeren adres tarafından WCF nesne modelinde temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-111">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="c6f2a-112">İsteğe bağlı üstbilgiler, uç noktayı tanımlamak veya bunlarla etkileşime geçmek için ek ayrıntılı adresleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-112">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="c6f2a-113">Daha fazla bilgi için bkz. [uç nokta adresi belirtme](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="c6f2a-113">For more information, see [Specifying an Endpoint Address](specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="c6f2a-114">**Bağlama**.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-114">**Binding**.</span></span> <span data-ttu-id="c6f2a-115">Bağlama, uç noktayla nasıl iletişim kuracağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-115">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="c6f2a-116">Bağlama, hangi Aktarım protokolünün (örneğin, TCP veya HTTP) (örneğin, metin veya ikili) kullanılacağını ve hangi güvenlik gereksinimlerinin gerekli olduğunu (örneğin, Güvenli Yuva Katmanı [SSL] veya SOAP iletisi güvenliği) dahil olmak üzere, uç noktanın dünya ile nasıl iletişim kuracağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-116">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="c6f2a-117">Daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c6f2a-117">For more information, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

- <span data-ttu-id="c6f2a-118">**Hizmet sözleşmesi**.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-118">**Service contract**.</span></span> <span data-ttu-id="c6f2a-119">Hizmet sözleşmesi, uç noktanın istemciye sunduğu işlevselliği özetler.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-119">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="c6f2a-120">Bir anlaşma, bir istemcinin çağırabilecekleri işlemleri, ileti formunu ve giriş parametrelerinin türünü ya da işlemi çağırmak için gereken verileri, istemcinin beklediği işlem veya yanıt iletisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-120">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="c6f2a-121">Üç temel sözleşme türü, temel ileti değişimi desenlerine (MEPs) karşılık gelir: veri birimi (tek yönlü), istek/yanıt ve çift yönlü (çift yönlü).</span><span class="sxs-lookup"><span data-stu-id="c6f2a-121">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="c6f2a-122">Hizmet sözleşmesi, erişim sırasında belirli veri türleri ve ileti biçimleri istemek için veri ve ileti sözleşmeleri de kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-122">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="c6f2a-123">Hizmet sözleşmesinin nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="c6f2a-123">For more information about how to define a service contract, see [Designing Service Contracts](designing-service-contracts.md).</span></span> <span data-ttu-id="c6f2a-124">Bir istemcinin, bir çift yönlü MEP 'de hizmetten ileti almak için, geri arama sözleşmesi olarak adlandırılan hizmet tanımlı bir sözleşmeyi uygulamak için de gerekli olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-124">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="c6f2a-125">Daha fazla bilgi için bkz. [çift yönlü hizmetler](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="c6f2a-125">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>

<span data-ttu-id="c6f2a-126">Bir hizmetin uç noktası, kod kullanılarak veya bildirimli olarak yapılandırma yoluyla imperatively belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-126">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="c6f2a-127">Hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-127">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="c6f2a-128">Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-128">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="c6f2a-129">Genellikle, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha pratik bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-129">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="c6f2a-130">Bağlama ve adresleme bilgilerinin koddan tutulması, uygulamayı yeniden derlemek ve yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-130">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>

> [!NOTE]
> <span data-ttu-id="c6f2a-131">Kimliğe bürünme gerçekleştiren bir hizmet uç noktası eklerken, iki yöntemden birini veya bir yöntemi kullanarak <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> sözleşmeyi doğru bir şekilde yeni bir nesneye yüklemeniz gerekir <xref:System.ServiceModel.Description.ServiceDescription> .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-131">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>

## <a name="defining-endpoints-in-code"></a><span data-ttu-id="c6f2a-132">Koddaki uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="c6f2a-132">Defining Endpoints in Code</span></span>

<span data-ttu-id="c6f2a-133">Aşağıdaki örnek, kodda aşağıdaki gibi bir uç noktanın nasıl belirtildiğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c6f2a-133">The following example illustrates how to specify an endpoint in code with the following:</span></span>

- <span data-ttu-id="c6f2a-134">`IEcho`"Merhaba!" yanıtıyla birisinin adını ve yankısını kabul eden bir hizmet türü için bir sözleşme tanımlayın \<name> .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-134">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>

- <span data-ttu-id="c6f2a-135">`Echo`Sözleşme tarafından tanımlanan türde bir hizmet uygulayın `IEcho` .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-135">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>

- <span data-ttu-id="c6f2a-136">Hizmet için bir uç nokta adresi belirtin `http://localhost:8000/Echo` .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-136">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>

- <span data-ttu-id="c6f2a-137">`Echo`Bir bağlamayı kullanarak hizmeti yapılandırın <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-137">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Use a predefined WSHttpBinding to configure the service.
          WSHttpBinding binding = new WSHttpBinding();

          // Add the endpoint for this service to the service host.
          serviceHost.AddServiceEndpoint(
             typeof(IEcho),
             binding,
             echoUri
           );

          // Open the service host to run it.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Create a ServiceHost for the Echo service.
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)

' Use a predefined WSHttpBinding to configure the service.
Dim binding As New WSHttpBinding()

' Add the endpoint for this service to the service host.
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)

' Open the service host to run it.
serviceHost.Open()
```

> [!NOTE]
> <span data-ttu-id="c6f2a-138">Hizmet ana bilgisayarı bir temel adresle oluşturulur ve ardından temel adrese göre adresin geri kalanı bir uç noktanın parçası olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-138">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="c6f2a-139">Adresin bu bölümlenmesi, birden çok uç noktanın bir konaktaki hizmetler için daha kolay tanımlanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-139">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>

> [!NOTE]
> <span data-ttu-id="c6f2a-140"><xref:System.ServiceModel.Description.ServiceDescription>Hizmet uygulamasındaki özelliklerinin, üzerinde yönteminin ardından değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> <xref:System.ServiceModel.ServiceHostBase> .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-140">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="c6f2a-141">Özelliği ve içindeki yöntemleri gibi bazı üyeler, <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> `AddServiceEndpoint` <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost> o noktadan sonra değiştirilirse bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-141">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="c6f2a-142">Diğerleri bunları değiştirmenize izin verir, ancak sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-142">Others permit you to modify them, but the result is undefined.</span></span>
>
> <span data-ttu-id="c6f2a-143">Benzer şekilde, istemcide, <xref:System.ServiceModel.Description.ServiceEndpoint> üzerine çağrısından sonra değerler değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> <xref:System.ServiceModel.ChannelFactory> .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-143">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="c6f2a-144"><xref:System.ServiceModel.ChannelFactory.Credentials%2A>Özelliği, o noktadan sonra değiştirilirse bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-144">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="c6f2a-145">Diğer istemci açıklama değerleri hata olmadan değiştirilebilir, ancak sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-145">The other client description values can be modified without error, but the result is undefined.</span></span>
>
> <span data-ttu-id="c6f2a-146">Hizmet veya istemci için, çağrılmadan önce açıklamayı değiştirmeniz önerilir <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-146">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>

## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="c6f2a-147">Yapılandırmada uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="c6f2a-147">Defining Endpoints in Configuration</span></span>

<span data-ttu-id="c6f2a-148">Bir uygulama oluştururken, kararları genellikle uygulamayı dağıtan yöneticiye erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-148">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="c6f2a-149">Örneğin, genellikle bir hizmet adresinin (URI) ne olduğunu bilmenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-149">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="c6f2a-150">Bir adresi sabit kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-150">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="c6f2a-151">Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-151">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="c6f2a-152">Ayrıntılar için bkz. [Hizmetleri yapılandırma](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="c6f2a-152">For details, see [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c6f2a-153">[](servicemodel-metadata-utility-tool-svcutil-exe.md) `/config:`  `[,` Yapılandırma dosyalarını hızlıca oluşturmak için dosya adı *dosya adı* anahtarıyla ServiceModel meta veri yardımcı programı aracını (Svcutil.exe) kullanın `]` .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-153">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>

## <a name="using-default-endpoints"></a><span data-ttu-id="c6f2a-154">Varsayılan uç noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="c6f2a-154">Using Default Endpoints</span></span>

<span data-ttu-id="c6f2a-155">Kodda veya yapılandırmada hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-155">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="c6f2a-156">Temel adres kodda veya yapılandırmada belirtilebilir ve varsayılan uç noktalar <xref:System.ServiceModel.ICommunicationObject.Open> , üzerinde çağrıldığında eklenir <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-156">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="c6f2a-157">Bu örnek, önceki bölümden aynı örnektir, ancak hiçbir uç nokta belirtilmediğinden varsayılan uç noktalar eklenir.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-157">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Open the service host to run it. Default endpoints
          // are added when the service is opened.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Open the service host to run it. Default endpoints
' are added when the service is opened.
serviceHost.Open()
```

 <span data-ttu-id="c6f2a-158">Uç noktalar açık olarak sağlanmışsa, çağrılmadan önce ' de çağırarak varsayılan uç noktalar eklenebilir <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> .</span><span class="sxs-lookup"><span data-stu-id="c6f2a-158">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="c6f2a-159">Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-159">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6f2a-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6f2a-160">See also</span></span>

- [<span data-ttu-id="c6f2a-161">Hizmet Sözleşmelerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="c6f2a-161">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
