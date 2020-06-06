---
title: <transport> / <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 49b31a889d192d190125214e89ba09305114eb7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735980"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="2827b-102">\<transport> / \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="2827b-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="2827b-103">Kullanırken aktarım düzeyi güvenliği için ayarları belirtir [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2827b-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="2827b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2827b-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2827b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2827b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2827b-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="2827b-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2827b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2827b-107">Attributes</span></span>  
  
|<span data-ttu-id="2827b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2827b-108">Attribute</span></span>|<span data-ttu-id="2827b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2827b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2827b-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="2827b-110">credentialType</span></span>|<span data-ttu-id="2827b-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2827b-111">Optional.</span></span> <span data-ttu-id="2827b-112">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2827b-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="2827b-113">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="2827b-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="2827b-114">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="2827b-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="2827b-115">Değer</span><span class="sxs-lookup"><span data-stu-id="2827b-115">Value</span></span>|<span data-ttu-id="2827b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2827b-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2827b-117">Sertifika</span><span class="sxs-lookup"><span data-stu-id="2827b-117">Certificate</span></span>|<span data-ttu-id="2827b-118">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2827b-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="2827b-119">Parola</span><span class="sxs-lookup"><span data-stu-id="2827b-119">Password</span></span>|<span data-ttu-id="2827b-120">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2827b-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2827b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2827b-121">Child Elements</span></span>  
 <span data-ttu-id="2827b-122">Yok</span><span class="sxs-lookup"><span data-stu-id="2827b-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2827b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2827b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2827b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="2827b-124">Element</span></span>|<span data-ttu-id="2827b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2827b-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="2827b-126">İçin güvenlik ayarlarını tanımlar [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2827b-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2827b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2827b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="2827b-128">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2827b-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2827b-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2827b-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2827b-130">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2827b-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2827b-131">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="2827b-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
