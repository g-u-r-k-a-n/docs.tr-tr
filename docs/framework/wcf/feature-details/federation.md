---
title: Federasyon
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: c31c2612b595e627b0c4c2d7fbb3a359b19ee704
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595498"
---
# <a name="federation"></a><span data-ttu-id="c7cb8-102">Federasyon</span><span class="sxs-lookup"><span data-stu-id="c7cb8-102">Federation</span></span>
<span data-ttu-id="c7cb8-103">Bu konuda, Federe güvenlik kavramıyla ilgili kısa bir genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="c7cb8-104">Federasyon güvenlik mimarilerini dağıtmaya yönelik Windows Communication Foundation (WCF) desteğini de açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="c7cb8-105">Federasyonu gösteren örnek bir uygulama için bkz. [Federasyon örneği](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c7cb8-105">For a sample application that demonstrates federation, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="c7cb8-106">Federal Güvenlik tanımı</span><span class="sxs-lookup"><span data-stu-id="c7cb8-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="c7cb8-107">Federasyon güvenliği, bir istemcinin eriştiği hizmet ile ilişkili kimlik doğrulama ve yetkilendirme yordamlarına kadar temiz ayrım sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="c7cb8-108">Federasyon güvenliği, farklı güven bölgelerinde birden fazla sistem, ağ ve kuruluşta işbirliği yapılmasını de mümkün.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="c7cb8-109">WCF, Federasyon güvenliği kullanan dağıtılmış sistemler oluşturmak ve dağıtmak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="c7cb8-110">Federasyon güvenlik mimarisinin öğeleri</span><span class="sxs-lookup"><span data-stu-id="c7cb8-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="c7cb8-111">Federasyon güvenlik mimarisinin aşağıdaki tabloda açıklandığı gibi üç anahtar öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="c7cb8-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="c7cb8-112">Element</span></span>|<span data-ttu-id="c7cb8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7cb8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7cb8-114">Etki alanı/bölge</span><span class="sxs-lookup"><span data-stu-id="c7cb8-114">Domain/realm</span></span>|<span data-ttu-id="c7cb8-115">Tek bir güvenlik yönetimi veya güven birimi.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="c7cb8-116">Tipik bir etki alanı tek bir kuruluş içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="c7cb8-117">Federasyon</span><span class="sxs-lookup"><span data-stu-id="c7cb8-117">Federation</span></span>|<span data-ttu-id="c7cb8-118">Güvenine sahip bir etki alanı koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="c7cb8-119">Güven düzeyi farklılık gösterebilir, ancak genellikle kimlik doğrulaması içerir ve neredeyse her zaman yetkilendirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="c7cb8-120">Tipik bir Federasyon, bir dizi kaynağa paylaşılan erişim için güven oluşturmuş bir sayıda kuruluş içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="c7cb8-121">Güvenlik Belirteci Hizmeti (STS)</span><span class="sxs-lookup"><span data-stu-id="c7cb8-121">Security Token Service (STS)</span></span>|<span data-ttu-id="c7cb8-122">Güvenlik belirteçleri veren bir Web hizmeti; diğer bir deyişle, bu, güvendiğini ve güvenmesini sağlayan kanıtları temel alarak onaylamaları yapar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="c7cb8-123">Bu, etki alanları arasındaki güven aracılığı temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="c7cb8-124">Örnek Senaryo</span><span class="sxs-lookup"><span data-stu-id="c7cb8-124">Example Scenario</span></span>  
 <span data-ttu-id="c7cb8-125">Aşağıdaki çizimde bir Federasyon güvenliği örneği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c7cb8-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Tipik bir Federasyon güvenlik senaryosunu gösteren diyagram.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="c7cb8-127">Bu senaryo iki kuruluş içerir: A ve B. kuruluş B, kuruluşlardaki bazı kullanıcıların önemli bulabileceği bir web kaynağına (Web hizmeti) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7cb8-128">Bu bölümde, *kaynak*, *hizmet*ve *Web hizmeti* 'nin birbirlerinin yerine kullanıldığı terimler kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="c7cb8-129">Genellikle kuruluş B, bir kullanıcının, hizmet erişmeden önce geçerli bir kimlik doğrulama biçimi sağlamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="c7cb8-130">Ayrıca, kuruluş, kullanıcının söz konusu kaynağa erişmek için yetkilendirilmesini de gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="c7cb8-131">Bu sorunu ele almanın ve kuruluşlardaki kullanıcıların B kuruluşunda kaynağa erişmesi için bir yol aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c7cb8-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="c7cb8-132">Kuruluştaki kullanıcılar, kimlik bilgilerini (Kullanıcı adı ve parola) B kuruluşuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="c7cb8-133">Kaynak erişimi sırasında, kuruluşlardaki kullanıcılar kimlik bilgilerini B kuruluşuna sunmadan, kaynağa erişmeden önce kimlik doğrulamasından geçer.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="c7cb8-134">Bu yaklaşım üç önemli dezavantaja sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c7cb8-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="c7cb8-135">B kuruluşunun, yerel kullanıcılarının kimlik bilgilerini yönetmeye ek olarak, kuruluşlarındaki kullanıcıların kimlik bilgilerini yönetmesi vardır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="c7cb8-136">Kuruluştaki kullanıcıların, normalde bir kuruluş içindeki kaynaklara erişim kazanmak için kullandıkları kimlik bilgilerinden ayrı bir ek kimlik bilgileri (yani, ek Kullanıcı adı ve parola hatırlamaları) olması gerekir. Bu genellikle, çok sayıda hizmet sitesinde aynı Kullanıcı adı ve parolayı kullanma ve zayıf bir güvenlik ölçüsü olan uygulamayı teşvik eder.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="c7cb8-137">Daha fazla kuruluş, B kuruluşunda kaynağı bir değer olduğu gibi algılamaz mimari ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="c7cb8-138">Daha önce bahsedilen dezavantajları ele veren alternatif bir yaklaşım, Federe güvenlik kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="c7cb8-139">Bu yaklaşımda, A ve B kuruluşları bir güven ilişkisi kurar ve kurulan güvenin aracılı hale getirmesini sağlamak için güvenlik belirteci hizmeti (STS) benimseme.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="c7cb8-140">Bir Federasyon güvenlik mimarisinde, kuruluşlardaki kullanıcılar B kuruluşunda Web hizmetine erişmek istiyorlarsa, bu, belirli bir hizmete erişiminin kimliğini doğrulayan ve bu hizmetin kimliğini doğrulayan B kuruluşunda bulunan STS 'den geçerli bir güvenlik belirteci sunması gerektiğini bilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="c7cb8-141">STS B ile iletişim kurulurken, kullanıcılar STS ile ilişkili ilkeden başka bir yöneltme düzeyi alır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="c7cb8-142">STS B 'nin bir güvenlik belirteci vermesini gerektiren STS A 'nın (yani, istemci güven bölgesi) geçerli bir güvenlik belirteci sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="c7cb8-143">Bu, iki kuruluş arasında kurulan güven ilişkisinin bir sahibi olabilir ve B kuruluşunun, A kuruluşundan kullanıcılar için kimlikleri yönetmesi gerekmez. Pratikte STS B genellikle null `issuerAddress` ve içerir `issuerMetadataAddress` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="c7cb8-144">Daha fazla bilgi için bkz. [nasıl yapılır: yerel veren yapılandırma](how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="c7cb8-144">For more information, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="c7cb8-145">Bu durumda, istemci STS A 'nın yerini bulmak için yerel bir ilke danışmanlar. Bu yapılandırma, *Ev bölgesi Federasyonu* olarak ADLANDıRıLıR ve STS B 'nin STS hakkındaki bilgileri saklamak zorunda olmadığından daha iyi ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="c7cb8-146">Kullanıcılar A kurumunda STS ile iletişim kurun ve normal olarak kuruluş içindeki diğer kaynaklara erişim kazanmak için kullandıkları kimlik doğrulama kimlik bilgilerini sunarak bir güvenlik belirteci elde eder. Bu Ayrıca, kullanıcıların birden çok kimlik bilgisi kümesini sürdürmek veya birden çok hizmet sitesinde aynı kimlik bilgilerini kullanmasını sağlamak zorunda konuma almayı azaltır sorununu da ortadan koyar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="c7cb8-147">Kullanıcılar STS A 'dan bir güvenlik belirteci aldıktan sonra, bu belirteci STS 'ye sunar. B. kuruluş, kullanıcıların isteklerini yetkilendirmeyi gerçekleştirmeye devam eder ve kendi güvenlik belirteçleri kümesinden kullanıcılara bir güvenlik belirteci yayınlar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="c7cb8-148">Kullanıcılar daha sonra belirtecini B kuruluşunda kaynağa sunabilir ve hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="c7cb8-149">WCF 'de Federal güvenlik desteği</span><span class="sxs-lookup"><span data-stu-id="c7cb8-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="c7cb8-150">WCF, aracılığıyla Federal Güvenlik mimarileri dağıtmaya yönelik anahtar desteği sağlar [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="c7cb8-151">[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)Öğesi, istek-yanıt iletişim stili için temel alınan aktarım mekanizması olarak http kullanımını gerektiren güvenli, güvenilir ve birlikte çalışabilen bir bağlama sağlar. Bu, kodlama için Tel biçimi olarak metin ve xml kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-151">The [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="c7cb8-152">[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)Bir Federasyon güvenlik senaryosunda kullanımı, aşağıdaki bölümlerde açıklandığı gibi, mantıksal olarak bağımsız iki aşamaya ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-152">The use of [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="c7cb8-153">1. Aşama: Tasarım aşaması</span><span class="sxs-lookup"><span data-stu-id="c7cb8-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="c7cb8-154">Tasarım aşamasında istemci, hizmet uç noktasının açığa çıkardığı ilkeyi okumak ve hizmetin kimlik doğrulama ve yetkilendirme gereksinimlerini toplamak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="c7cb8-155">İstemci üzerinde aşağıdaki Federasyon güvenliği iletişim modelini oluşturmak için uygun proxy 'ler oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="c7cb8-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="c7cb8-156">İstemci güven bölgesindeki STS 'den bir güvenlik belirteci alın.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="c7cb8-157">Belirteci hizmet güven bölgesindeki STS 'ye sunun.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="c7cb8-158">Hizmet güven bölgesindeki STS 'den bir güvenlik belirteci alın.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="c7cb8-159">Hizmete erişmek için belirteci hizmete sunun.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="c7cb8-160">2. Aşama: çalışma zamanı aşaması</span><span class="sxs-lookup"><span data-stu-id="c7cb8-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="c7cb8-161">Çalışma zamanı aşamasında istemci, WCF istemci sınıfının bir nesnesini başlatır ve WCF istemcisini kullanarak bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="c7cb8-162">WCF 'nin temel alınan çatısı, Federasyon güvenliği iletişim düzeninde daha önce bahsedilen adımları işler ve istemcinin hizmeti sorunsuz bir şekilde kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="c7cb8-163">WCF kullanarak örnek uygulama</span><span class="sxs-lookup"><span data-stu-id="c7cb8-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="c7cb8-164">Aşağıdaki çizimde, WCF 'den yerel destek kullanan bir Federasyon güvenlik mimarisine yönelik örnek bir uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Örnek bir Federasyon güvenlik uygulamasını gösteren diyagram.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="c7cb8-166">Örnek hizmetim</span><span class="sxs-lookup"><span data-stu-id="c7cb8-166">Example MyService</span></span>  
 <span data-ttu-id="c7cb8-167">Hizmet `MyService` aracılığıyla tek bir uç nokta sunar `MyServiceEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="c7cb8-168">Aşağıdaki çizimde bitiş noktasıyla ilişkili adres, bağlama ve anlaşma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![MyServiceEndpoint ayrıntılarının gösterildiği diyagram.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="c7cb8-170">Hizmet uç noktası `MyServiceEndpoint` ' nı kullanır [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve `accessAuthorized` STS B tarafından verilen talebe sahip geçerli bir güvenlik onaylama işlemi BIÇIMLENDIRME dili (SAML) belirteci gerektirir. Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="c7cb8-171">İçin gereken talepler hakkında bir hafif nokta not edilmelidir `MyService` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="c7cb8-172">İkinci şekil, `MyService` talebe sahip BIR SAML belirteci gerektirdiğini gösterir `accessAuthorized` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="c7cb8-173">Daha kesin olması için bu, gereken talep türünü belirtir `MyService` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="c7cb8-174">Bu talep türünün tam adı, `http://tempuri.org:accessAuthorized` hizmet yapılandırma dosyasında kullanılan (ilişkili ad alanıyla birlikte).</span><span class="sxs-lookup"><span data-stu-id="c7cb8-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="c7cb8-175">Bu talebin değeri, bu talebin varlığını gösterir ve `true` STS B tarafından ayarlandığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="c7cb8-176">Çalışma zamanında, bu ilke `MyServiceOperationRequirement` öğesinin bir parçası olarak uygulanan sınıfı tarafından zorlanır `MyService` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="c7cb8-177">STS B</span><span class="sxs-lookup"><span data-stu-id="c7cb8-177">STS B</span></span>  
 <span data-ttu-id="c7cb8-178">Aşağıdaki çizimde STS B gösterilmektedir. Daha önce belirtildiği gibi, bir güvenlik belirteci hizmeti (STS) da bir Web hizmetidir ve ilişkili uç noktaları, ilkesi vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Güvenlik belirteci hizmeti B 'yi gösteren diyagram.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="c7cb8-180">STS B, `STSEndpoint` güvenlik belirteçleri istemek için kullanılabilecek adlı tek bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="c7cb8-181">Özellikle STS B, `accessAuthorized` `MyService` servis sitesinde hizmete erişmek için sunulabilen, talebe sahip SAML belirteçleri verir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="c7cb8-182">Ancak STS B, kullanıcıların talebi içeren STS tarafından verilen geçerli bir SAML belirteci sunmasını gerektirir `userAuthenticated` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="c7cb8-183">Bu, STS yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-183">This is declaratively specified in the STS configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="c7cb8-184">`userAuthenticated`Bu talep, STS B için gereken talep türüdür. Bu talep türünün tam adı, `http://tempuri.org:userAuthenticated` STS yapılandırma dosyasında kullanılan (ilişkili ad alanıyla birlikte).</span><span class="sxs-lookup"><span data-stu-id="c7cb8-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="c7cb8-185">Bu talebin değeri, bu talebin varlığını gösterir ve `true` STS A tarafından ayarlandığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="c7cb8-186">Çalışma zamanında, `STS_B_OperationRequirement` sınıfı STS 'nin bir parçası olarak uygulanan bu ilkeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="c7cb8-187">Erişim denetimi net ise STS B, talebe sahip bir SAML belirteci yayınlar `accessAuthorized` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="c7cb8-188">STS A</span><span class="sxs-lookup"><span data-stu-id="c7cb8-188">STS A</span></span>  
 <span data-ttu-id="c7cb8-189">Aşağıdaki çizimde STS A gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="c7cb8-190">![Federasyon](media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="c7cb8-190">![Federation](media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="c7cb8-191">STS B 'ye benzer şekilde, STS A da güvenlik belirteçleri veren ve bu amaçla tek bir uç nokta sunan bir Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="c7cb8-192">Ancak, farklı bir bağlama () kullanır `wsHttpBinding` ve kullanıcıların bir talep ile geçerli bir CardSpace sunmasını gerektirir `emailAddress` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="c7cb8-193">Yanıt ' da, talebe sahip SAML belirteçleri verir `userAuthenticated` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="c7cb8-194">Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-194">This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"
                       storeName="My" />  
       </identity>  
    </endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="c7cb8-195">Çalışma zamanında, `STS_A_OperationRequirement` sınıfı STS 'Nin bir parçası olarak uygulanan bu ilkeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="c7cb8-196">Erişim ise `true` , STS, talebe sahip BIR SAML belirteci yayınlar `userAuthenticated` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="c7cb8-197">Kuruluşunda istemci A</span><span class="sxs-lookup"><span data-stu-id="c7cb8-197">Client at Organization A</span></span>  
 <span data-ttu-id="c7cb8-198">Aşağıdaki çizimde, bir hizmet çağrısı yapma ile ilgili adımlarla birlikte A kuruluşunda istemci gösterilmektedir `MyService` .</span><span class="sxs-lookup"><span data-stu-id="c7cb8-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="c7cb8-199">Diğer işlevsel bileşenler de ayrıca tamamlana için de eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-199">The other functional components are also included for completeness.</span></span>  
  
 ![Bir hizmetim hizmeti çağrısındaki adımları gösteren diyagram.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="c7cb8-201">Özet</span><span class="sxs-lookup"><span data-stu-id="c7cb8-201">Summary</span></span>  
 <span data-ttu-id="c7cb8-202">Federal güvenlik, daha temiz bir sorumluluk bölmesi sağlar ve güvenli, ölçeklenebilir hizmet mimarileri oluşturmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="c7cb8-203">WCF, dağıtılmış uygulamalar oluşturmaya ve dağıtmaya yönelik bir platform olarak, Federasyon güvenliği uygulamak için yerel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7cb8-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7cb8-204">See also</span></span>

- [<span data-ttu-id="c7cb8-205">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c7cb8-205">Security</span></span>](security.md)
