---
description: 'Hakkında daha fazla bilgi edinin: <knownCertificates>'
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 0180db56c775f4f6f17de8da58781c15a412bc81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802235"
---
# \<knownCertificates>

<span data-ttu-id="0d7f1-102">Bir güvenlik belirteci hizmetinden (STS) verilen güvenlik kimlik bilgilerinin kimliğini doğrulamak için verilen bir X. 509.440 sertifikaları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="0d7f1-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d7f1-103">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d7f1-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d7f1-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0d7f1-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="0d7f1-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d7f1-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0d7f1-106">Attributes</span></span>  

 <span data-ttu-id="0d7f1-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0d7f1-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d7f1-108">Child Elements</span></span>  
  
|<span data-ttu-id="0d7f1-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d7f1-109">Element</span></span>|<span data-ttu-id="0d7f1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d7f1-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|<span data-ttu-id="0d7f1-111">Koleksiyona bir X. 509.952 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-111">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d7f1-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d7f1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0d7f1-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d7f1-113">Element</span></span>|<span data-ttu-id="0d7f1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d7f1-114">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="0d7f1-115">Hizmet kimlik bilgisi olarak verilen bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-115">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d7f1-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d7f1-116">Remarks</span></span>  

 <span data-ttu-id="0d7f1-117">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-117">The issued token scenario has three stages.</span></span> <span data-ttu-id="0d7f1-118">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti* denir.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-118">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="0d7f1-119">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-119">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="0d7f1-120">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-120">The client then returns to the service with the token.</span></span> <span data-ttu-id="0d7f1-121">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-121">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="0d7f1-122">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-122">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="0d7f1-123">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Öğesi, bu tür güvenli belirteç hizmeti sertifikalarının depolandığı depodur.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-123">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="0d7f1-124">Sertifika eklemek için [ \<knownCertificates> öğesini](knowncertificates.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-124">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="0d7f1-125">[\<add>](add-of-knowncertificates.md)Aşağıdaki örnekte gösterildiği gibi her sertifika için bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-125">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="0d7f1-126">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-126">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="0d7f1-127">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-127">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="0d7f1-128">Bir istemcinin Federasyon Hizmeti tarafından doğrulanabilmesi ve bu yapılandırma öğesini kullanma hakkında daha fazla bilgi edinmek için, bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="0d7f1-128">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="0d7f1-129">Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="0d7f1-129">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="0d7f1-130">Yapılandırmada koleksiyonun nasıl doldurulacağını gösteren bir örnek için bkz [\<add>](add-of-knowncertificates.md) ..</span><span class="sxs-lookup"><span data-stu-id="0d7f1-130">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7f1-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d7f1-131">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="0d7f1-132">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="0d7f1-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0d7f1-133">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0d7f1-133">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="0d7f1-134">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="0d7f1-134">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="0d7f1-135">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0d7f1-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [<span data-ttu-id="0d7f1-136">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0d7f1-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
