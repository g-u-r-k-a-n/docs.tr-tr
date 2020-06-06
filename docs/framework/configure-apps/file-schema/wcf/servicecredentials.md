---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399634"
---
# \<serviceCredentials>
<span data-ttu-id="36ffd-101">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="36ffd-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36ffd-102">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36ffd-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36ffd-103">Attributes and Elements</span></span>  
 <span data-ttu-id="36ffd-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36ffd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36ffd-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36ffd-105">Attributes</span></span>  
  
|<span data-ttu-id="36ffd-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="36ffd-106">Attribute</span></span>|<span data-ttu-id="36ffd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36ffd-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="36ffd-108">Bu yapılandırma öğesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="36ffd-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36ffd-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36ffd-109">Child Elements</span></span>  
  
|<span data-ttu-id="36ffd-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="36ffd-110">Element</span></span>|<span data-ttu-id="36ffd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36ffd-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="36ffd-112">İstemci sertifikası bant dışı kullanılabilir olduğunda kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="36ffd-113">Bu öğe istemci sertifikası doğrulama ayarlarını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="36ffd-114">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="36ffd-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="36ffd-115">Bu hizmet için geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="36ffd-116">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="36ffd-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="36ffd-117">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="36ffd-118">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="36ffd-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="36ffd-119">Güvenli konuşma için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="36ffd-120">Bu öğe türündedir <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="36ffd-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="36ffd-121">Kendisini tanımlamak için bir hizmet tarafından kullanılan bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="36ffd-122">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="36ffd-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="36ffd-123">Kullanıcı adı parola doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="36ffd-124">Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserNameServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="36ffd-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="36ffd-125">Windows kimlik bilgisi doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="36ffd-126">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="36ffd-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36ffd-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36ffd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="36ffd-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="36ffd-128">Element</span></span>|<span data-ttu-id="36ffd-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36ffd-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="36ffd-130">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ffd-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36ffd-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36ffd-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="36ffd-132">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="36ffd-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
