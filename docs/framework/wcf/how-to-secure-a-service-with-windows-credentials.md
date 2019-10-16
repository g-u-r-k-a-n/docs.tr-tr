---
title: 'Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: d02e697b23b6c745a59f3c9c37dd9c565f2f710e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320930"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="c604e-102">Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c604e-102">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="c604e-103">Bu konu başlığı altında, bir Windows etki alanında bulunan ve aynı etki alanındaki istemciler tarafından çağrılan bir Windows Communication Foundation (WCF) hizmetinde aktarım güvenliğinin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c604e-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="c604e-104">Bu senaryo hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasıyla taşıma güvenliği](./feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c604e-104">For more information about this scenario, see [Transport Security with Windows Authentication](./feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="c604e-105">Örnek bir uygulama için bkz. [WSHttpBinding](./samples/wshttpbinding.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="c604e-105">For a sample application, see the [WSHttpBinding](./samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="c604e-106">Bu konu başlığı altında, var olan bir sözleşme arabirimi ve uygulamanızın zaten tanımlanmış olduğu varsayılır ve bu uygulamaya eklenir.</span><span class="sxs-lookup"><span data-stu-id="c604e-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="c604e-107">Ayrıca var olan bir hizmeti ve istemciyi de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c604e-107">You can also modify an existing service and client.</span></span>

<span data-ttu-id="c604e-108">Windows kimlik bilgileriyle bir hizmetin güvenliğini tamamen kodda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c604e-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="c604e-109">Alternatif olarak, bir yapılandırma dosyası kullanarak bazı kodları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c604e-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="c604e-110">Bu konuda her iki yol da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c604e-110">This topic shows both ways.</span></span> <span data-ttu-id="c604e-111">Her ikisini değil yalnızca birini kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c604e-111">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="c604e-112">İlk üç yordam, kodu kullanarak hizmetin nasıl güvence altına alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c604e-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="c604e-113">Dördüncü ve beşinci yordam, bir yapılandırma dosyası ile nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c604e-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="c604e-114">Kod kullanma</span><span class="sxs-lookup"><span data-stu-id="c604e-114">Using Code</span></span>

<span data-ttu-id="c604e-115">Hizmetin ve istemcinin tüm kodu, bu konunun sonundaki örnek bölümdür.</span><span class="sxs-lookup"><span data-stu-id="c604e-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="c604e-116">İlk yordam kodda <xref:System.ServiceModel.WSHttpBinding> sınıfı oluşturma ve yapılandırmayı adım adım açıklar.</span><span class="sxs-lookup"><span data-stu-id="c604e-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="c604e-117">Bağlama HTTP aktarımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c604e-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="c604e-118">İstemcide aynı bağlama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c604e-118">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="c604e-119">Windows kimlik bilgileri ve ileti güvenliği kullanan bir WSHttpBinding oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c604e-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="c604e-120">Bu yordamın kodu, örnek bölümünde hizmet kodundaki `Test` sınıfının `Run` yönteminin başına eklenir.</span><span class="sxs-lookup"><span data-stu-id="c604e-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="c604e-121">Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c604e-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="c604e-122">@No__t-1 sınıfının <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğini <xref:System.ServiceModel.SecurityMode.Message> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c604e-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="c604e-123">@No__t-1 sınıfının <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliğini <xref:System.ServiceModel.MessageCredentialType.Windows> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c604e-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="c604e-124">Bu yordamın kodu aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c604e-124">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="c604e-125">Bir hizmette bağlamayı kullanma</span><span class="sxs-lookup"><span data-stu-id="c604e-125">Using the Binding in a Service</span></span>

<span data-ttu-id="c604e-126">Bu, bağlamanın şirket içinde barındırılan bir hizmette nasıl kullanılacağını gösteren ikinci yordamdır.</span><span class="sxs-lookup"><span data-stu-id="c604e-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="c604e-127">Barındırma hizmetleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="c604e-127">For more information about hosting services see [Hosting Services](hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="c604e-128">Bir hizmette bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c604e-128">To use a binding in a service</span></span>

1. <span data-ttu-id="c604e-129">Önceki yordamdan koddan sonra bu yordamın kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c604e-129">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="c604e-130">@No__t-1 adlı <xref:System.Type> değişkeni oluşturun ve arabirimin türünü atayın (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="c604e-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="c604e-131">Visual Basic kullanırken, `GetType` işlecini kullanın; kullanırken C#, `typeof` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="c604e-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="c604e-132">@No__t-1 adlı ikinci bir <xref:System.Type> değişkeni oluşturun ve uygulanan sözleşmenin türünü (`Calculator`) atayın.</span><span class="sxs-lookup"><span data-stu-id="c604e-132">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="c604e-133">Hizmetin temel adresiyle `baseAddress` adlı <xref:System.Uri> sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c604e-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="c604e-134">Temel adres, aktarımdan eşleşen bir şemaya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c604e-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="c604e-135">Bu durumda, aktarım düzeni HTTP olur ve adres özel Tekdüzen Kaynak tanımlayıcısı (URI) "localhost" ve bir bağlantı noktası numarası (8036) ve bir taban bitiş noktası adresi ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/` ' ı içerir.</span><span class="sxs-lookup"><span data-stu-id="c604e-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="c604e-136">@No__t-1 ve `baseAddress` değişkenleriyle <xref:System.ServiceModel.ServiceHost> sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c604e-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="c604e-137">@No__t-0, bağlama ve bir uç nokta adı (secureCalculator) kullanarak hizmete bir uç nokta ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c604e-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="c604e-138">Bir istemcinin, hizmete bir çağrı başlatırken temel adresi ve uç nokta adını birleştirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="c604e-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="c604e-139">Hizmeti başlatmak için <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="c604e-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="c604e-140">Bu yordamın kodu burada gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c604e-140">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="c604e-141">Bir Istemcide bağlamayı kullanma</span><span class="sxs-lookup"><span data-stu-id="c604e-141">Using the Binding in a Client</span></span>

<span data-ttu-id="c604e-142">Bu yordamda hizmeti ile iletişim kuran bir proxy oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c604e-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="c604e-143">Proxy, proxy 'yi oluşturmak için hizmet meta verilerini kullanan [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c604e-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="c604e-144">Bu yordam ayrıca hizmetle iletişim kurmak için <xref:System.ServiceModel.WSHttpBinding> sınıfının bir örneğini oluşturur ve ardından hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="c604e-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="c604e-145">Bu örnek, yalnızca istemciyi oluşturmak için kod kullanır.</span><span class="sxs-lookup"><span data-stu-id="c604e-145">This example uses only code to create the client.</span></span> <span data-ttu-id="c604e-146">Alternatif olarak, bu yordamı izleyen bölümünde gösterilen bir yapılandırma dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c604e-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="c604e-147">Bir istemcide kodla bir bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c604e-147">To use a binding in a client with code</span></span>

1. <span data-ttu-id="c604e-148">Hizmetin meta verilerinden proxy kodunu oluşturmak için SvcUtil. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c604e-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="c604e-149">Daha fazla bilgi için bkz. [nasıl yapılır: Istemci oluşturma](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="c604e-149">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="c604e-150">Oluşturulan proxy kodu, her istemcinin bir WCF hizmetiyle iletişim kurmak için gerekli oluşturucuları, yöntemleri ve özellikleri olmasını sağlayan <xref:System.ServiceModel.ClientBase%601> sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="c604e-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="c604e-151">Bu örnekte, oluşturulan kod, `ICalculator` arabirimini uygulayan `CalculatorClient` sınıfını içerir ve hizmet koduyla uyumluluğu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c604e-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="c604e-152">Bu yordamın kodu, istemci programın `Main` yönteminin başına eklenir.</span><span class="sxs-lookup"><span data-stu-id="c604e-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="c604e-153">@No__t-0 sınıfının bir örneğini oluşturun ve güvenlik modunu `Message` ve istemci kimlik bilgileri türü `Windows` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c604e-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="c604e-154">Örnek, `clientBinding` değişkenini adlandırır.</span><span class="sxs-lookup"><span data-stu-id="c604e-154">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="c604e-155">@No__t-1 adlı <xref:System.ServiceModel.EndpointAddress> sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c604e-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="c604e-156">Uç nokta adıyla birleştirilmiş temel adresi olan örneği başlatın.</span><span class="sxs-lookup"><span data-stu-id="c604e-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="c604e-157">Oluşturulan istemci sınıfının bir örneğini `serviceAddress` ve `clientBinding` değişkenleriyle oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c604e-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="c604e-158">Aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.ClientBase%601.Open%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="c604e-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="c604e-159">Hizmeti çağırın ve sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="c604e-159">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="c604e-160">Yapılandırma dosyasını kullanma</span><span class="sxs-lookup"><span data-stu-id="c604e-160">Using the Configuration File</span></span>

<span data-ttu-id="c604e-161">Yordam kodu ile bağlama oluşturmak yerine, yapılandırma dosyasının bağlamalar bölümü için gösterilen aşağıdaki kodu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c604e-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="c604e-162">Önceden tanımlanmış bir hizmetiniz yoksa, bkz. [Hizmetleri tasarlama ve uygulama](designing-and-implementing-services.md)ve [Hizmetleri yapılandırma](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="c604e-162">If you do not already have a service defined, see [Designing and Implementing Services](designing-and-implementing-services.md), and [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c604e-163">Bu yapılandırma kodu hem hizmet hem de istemci yapılandırma dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c604e-163">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="c604e-164">Yapılandırma kullanarak Windows etki alanındaki bir hizmette aktarım güvenliğini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="c604e-164">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="c604e-165">Yapılandırma dosyasının [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) öğesi bölümüne [\<wshttpbinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c604e-165">Add a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="c604e-166">< @No__t-1 > öğesine < `binding` > öğesi ekleyin ve `configurationName` özniteliğini uygulamanıza uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c604e-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="c604e-167">Bir < `security` > öğesi ekleyin ve `mode` özniteliğini Ileti olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c604e-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="c604e-168">< @No__t-0 > öğesi ekleyin ve `clientCredentialType` özniteliğini Windows 'a ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c604e-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="c604e-169">Hizmetin yapılandırma dosyasında `<bindings>` bölümünü aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c604e-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="c604e-170">Zaten bir hizmet yapılandırma dosyanız yoksa, bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c604e-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

    ```xml
    <bindings>
      <wsHttpBinding>
       <binding name = "wsHttpBinding_Calculator">
         <security mode="Message">
           <message clientCredentialType="Windows"/>
         </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="c604e-171">Bir Istemcide bağlamayı kullanma</span><span class="sxs-lookup"><span data-stu-id="c604e-171">Using the Binding in a Client</span></span>

<span data-ttu-id="c604e-172">Bu yordamda iki dosyanın nasıl oluşturulacağı gösterilmektedir: hizmetle iletişim kuran bir ara sunucu ve bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="c604e-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="c604e-173">Ayrıca, istemci programında, istemcide kullanılan üçüncü dosya olan değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="c604e-173">It also describes changes to the client program, which is the third file used on the client.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="c604e-174">Yapılandırmaya sahip bir istemcide bağlama kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c604e-174">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="c604e-175">Proxy kodunu ve yapılandırma dosyasını hizmetin meta verilerinden oluşturmak için SvcUtil. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c604e-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="c604e-176">Daha fazla bilgi için bkz. [nasıl yapılır: Istemci oluşturma](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="c604e-176">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="c604e-177">Oluşturulan yapılandırma dosyasının [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) bölümünü, önceki bölümdeki yapılandırma kodu ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c604e-177">Replace the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="c604e-178">Yordam kodu, istemci programın `Main` yönteminin başına eklenir.</span><span class="sxs-lookup"><span data-stu-id="c604e-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="c604e-179">Yapılandırma dosyasındaki bağlamanın adını giriş parametresi olarak geçirerek oluşturulan istemci sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c604e-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="c604e-180">Aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.ClientBase%601.Open%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="c604e-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="c604e-181">Hizmeti çağırın ve sonuçları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="c604e-181">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="c604e-182">Örnek</span><span class="sxs-lookup"><span data-stu-id="c604e-182">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="c604e-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c604e-183">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="c604e-184">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="c604e-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="c604e-185">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c604e-185">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="c604e-186">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c604e-186">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="c604e-187">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c604e-187">Security Overview</span></span>](./feature-details/security-overview.md)
