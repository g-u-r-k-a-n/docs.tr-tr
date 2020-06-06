---
title: <scopedCertificates> Öğesi
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 3c06159709df0afe2a475de1e186b0114af32bc2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399950"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="ee77e-102">\<scopedCertificates> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ee77e-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="ee77e-103">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee77e-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="ee77e-104">Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee77e-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="ee77e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee77e-105">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee77e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee77e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ee77e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee77e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee77e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee77e-108">Attributes</span></span>  
 <span data-ttu-id="ee77e-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee77e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee77e-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee77e-110">Child Elements</span></span>  
  
|<span data-ttu-id="ee77e-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee77e-111">Element</span></span>|<span data-ttu-id="ee77e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee77e-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|<span data-ttu-id="ee77e-113">Kapsamlı sertifikalar koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="ee77e-113">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee77e-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee77e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ee77e-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee77e-115">Element</span></span>|<span data-ttu-id="ee77e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee77e-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="ee77e-117">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee77e-117">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee77e-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee77e-118">Remarks</span></span>  
 <span data-ttu-id="ee77e-119">Bu koleksiyon, istemcinin iletişim kurduğu hizmetin URL 'sini temel alarak kullanılacak hizmet sertifikalarını yapılandırmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee77e-119">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="ee77e-120">Bu özellikle, bir istemcinin birden çok hizmetle (bitiş hizmeti ve aracı güvenlik belirteci Hizmetleri) iletişim kuramadığı verilen belirteç senaryolarında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ee77e-120">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="ee77e-121">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu sertifika hizmete iletileri şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="ee77e-121">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="ee77e-122">Bir bağlama hizmet için bir sertifika gerektiriyorsa ve hizmet URL 'SI için belirli bir sertifika ScopedCertificates içinde bulunmazsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee77e-122">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="ee77e-123">Daha fazla bilgi için bkz. [nasıl yapılır: federe Istemci oluşturma](../../../wcf/feature-details/how-to-create-a-federated-client.md)konusunun "kapsamlı sertifikalar" bölümü.</span><span class="sxs-lookup"><span data-stu-id="ee77e-123">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee77e-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee77e-124">Example</span></span>  
 <span data-ttu-id="ee77e-125">Aşağıdaki örnek, etki alanı adı HTTP protokolünün üzerinde olan uç noktalarla iletişim kurarken İstemcinin kullanacağı bir hizmet sertifikasını belirtir `http://www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="ee77e-125">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="ee77e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee77e-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="ee77e-127">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="ee77e-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ee77e-128">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ee77e-128">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="ee77e-129">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ee77e-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ee77e-130">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ee77e-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
