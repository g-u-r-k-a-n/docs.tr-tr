---
description: 'Hakkında daha fazla bilgi edinin: <dynamicEndpoint>'
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 0fe30492e1daeecca5e27aef844f5f6977396049
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725902"
---
# \<dynamicEndpoint>

<span data-ttu-id="8ddc3-102">Bu yapılandırma öğesi, bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8ddc3-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="8ddc3-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="8ddc3-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ddc3-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ddc3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8ddc3-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ddc3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ddc3-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ddc3-106">Attributes</span></span>  

 <span data-ttu-id="8ddc3-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ddc3-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ddc3-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ddc3-108">Child Elements</span></span>  
  
|<span data-ttu-id="8ddc3-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ddc3-109">Element</span></span>|<span data-ttu-id="8ddc3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ddc3-110">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="8ddc3-111">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="8ddc3-111">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ddc3-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ddc3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="8ddc3-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ddc3-113">Element</span></span>|<span data-ttu-id="8ddc3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ddc3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="8ddc3-115">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8ddc3-115">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ddc3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ddc3-116">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
