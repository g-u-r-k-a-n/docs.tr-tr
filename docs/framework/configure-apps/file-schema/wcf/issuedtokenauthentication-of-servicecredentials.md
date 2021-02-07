---
description: 'Hakkında daha fazla bilgi <issuedTokenAuthentication> edinin: <serviceCredentials>'
title: <issuedTokenAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 62c60cc467217312c349ecdbe8e98b04dd022ddf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725681"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="26451-103">\<issuedTokenAuthentication> / \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="26451-103">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>

<span data-ttu-id="26451-104">Hizmet kimlik bilgisi olarak verilen özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="26451-104">Specifies a custom token issued as a service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="26451-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="26451-105">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26451-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="26451-106">Attributes and Elements</span></span>  

 <span data-ttu-id="26451-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="26451-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26451-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="26451-108">Attributes</span></span>  
  
|<span data-ttu-id="26451-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="26451-109">Attribute</span></span>|<span data-ttu-id="26451-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26451-110">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="26451-111"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Bir örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin kümesini alır <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="26451-111">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="26451-112">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A> ..</span><span class="sxs-lookup"><span data-stu-id="26451-112">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="26451-113">Güvenilmeyen RSA sertifikası verenler için izin verilip verilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="26451-113">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="26451-114">Sertifikalar, özgünlük doğrulaması için sertifika yetkilileri (CA) tarafından imzalanır.</span><span class="sxs-lookup"><span data-stu-id="26451-114">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="26451-115">Güvenilmeyen bir veren, sertifikaları imzalamak için güvenilmeyecek şekilde belirtilmemiş bir CA 'dır.</span><span class="sxs-lookup"><span data-stu-id="26451-115">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="26451-116"><xref:System.IdentityModel.Tokens.SamlSecurityToken>Güvenlik belirtecinin doğrulanıp doğrulanması gerekip gerekmediğini belirten bir değer alır <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> .</span><span class="sxs-lookup"><span data-stu-id="26451-116">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="26451-117">Bu değer türünde <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="26451-117">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="26451-118">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A> ..</span><span class="sxs-lookup"><span data-stu-id="26451-118">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="26451-119">Sertifika doğrulama modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="26451-119">Sets the certificate validation mode.</span></span> <span data-ttu-id="26451-120">Geçerli değerlerinden biri <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="26451-120">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="26451-121">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="26451-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="26451-122">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="26451-122">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="26451-123">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="26451-123">Optional string.</span></span> <span data-ttu-id="26451-124">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="26451-124">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="26451-125">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="26451-125">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="26451-126">Bir iptal denetiminin oluşup oluşmadığını ve çevrimiçi veya çevrimdışı gerçekleştirildiğini belirten iptal modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="26451-126">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="26451-127">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="26451-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="26451-128">Hizmet kimlik bilgisi için kullanılan SamlSerializer türünü belirten isteğe bağlı bir dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="26451-128">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="26451-129">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="26451-129">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="26451-130">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="26451-130">Optional enumeration.</span></span> <span data-ttu-id="26451-131">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="26451-131">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26451-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="26451-132">Child Elements</span></span>  
  
|<span data-ttu-id="26451-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="26451-133">Element</span></span>|<span data-ttu-id="26451-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26451-134">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="26451-135"><xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>Hizmet kimlik bilgisi için güvenilen verenler belirten bir öğe koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="26451-135">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26451-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="26451-136">Parent Elements</span></span>  
  
|<span data-ttu-id="26451-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="26451-137">Element</span></span>|<span data-ttu-id="26451-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26451-138">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="26451-139">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="26451-139">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26451-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26451-140">Remarks</span></span>  

 <span data-ttu-id="26451-141">Verilen belirteç senaryosunda üç aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="26451-141">The issued token scenario has three stages.</span></span> <span data-ttu-id="26451-142">İlk aşamada, bir hizmete erişmeye çalışan bir istemciye *güvenli bir belirteç hizmeti* denir.</span><span class="sxs-lookup"><span data-stu-id="26451-142">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="26451-143">Güvenli belirteç hizmeti daha sonra istemcinin kimliğini doğrular ve ardından istemciye, genellikle bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteci olarak bir belirteç verir.</span><span class="sxs-lookup"><span data-stu-id="26451-143">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="26451-144">İstemci daha sonra belirtece sahip hizmete geri döner.</span><span class="sxs-lookup"><span data-stu-id="26451-144">The client then returns to the service with the token.</span></span> <span data-ttu-id="26451-145">Hizmet, hizmetin, belirtecin kimliğini doğrulamasına ve dolayısıyla istemcisinde istemciye izin veren verilerin belirtecini inceler.</span><span class="sxs-lookup"><span data-stu-id="26451-145">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="26451-146">Belirtecin kimliğini doğrulamak için, güvenli belirteç hizmetinin kullandığı sertifika hizmet tarafından bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="26451-146">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="26451-147">Bu öğe, bu tür güvenli belirteç hizmeti sertifikalarının deposıdır.</span><span class="sxs-lookup"><span data-stu-id="26451-147">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="26451-148">Sertifika eklemek için öğesini kullanın [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="26451-148">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="26451-149">[\<add>](add-of-knowncertificates.md)Aşağıdaki örnekte gösterildiği gibi her sertifika için bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="26451-149">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="26451-150">Varsayılan olarak, sertifikaların güvenli bir belirteç hizmetinden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="26451-150">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="26451-151">Bu "bilinen" sertifikalar yalnızca meşru istemcilerin bir hizmete erişebilmesini güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="26451-151">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="26451-152">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="26451-152">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26451-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26451-153">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="26451-154">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="26451-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="26451-155">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="26451-155">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
