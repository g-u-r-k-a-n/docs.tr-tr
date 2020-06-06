---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854932"
---
# \<transportConfigurationTypes>
<span data-ttu-id="07096-101">Belirli bir taşımanın türünü tanımlayan yapılandırma öğelerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07096-101">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="07096-102">Bu, özel WAS protokolleri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07096-102">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="07096-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07096-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07096-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="07096-104">Attributes and Elements</span></span>  
 <span data-ttu-id="07096-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07096-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07096-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07096-106">Attributes</span></span>  
  
|<span data-ttu-id="07096-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="07096-107">Attribute</span></span>|<span data-ttu-id="07096-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07096-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="07096-109">name</span><span class="sxs-lookup"><span data-stu-id="07096-109">name</span></span>|<span data-ttu-id="07096-110">Taşımanın adı</span><span class="sxs-lookup"><span data-stu-id="07096-110">The name of the transport</span></span>|  
|<span data-ttu-id="07096-111">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="07096-111">transportConfigurationType</span></span>|<span data-ttu-id="07096-112">Taşımayı uygulayan tür</span><span class="sxs-lookup"><span data-stu-id="07096-112">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07096-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="07096-113">Child Elements</span></span>  
  
|<span data-ttu-id="07096-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="07096-114">Element</span></span>|<span data-ttu-id="07096-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07096-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="07096-116">Belirli bir taşımanın türünü tanımlayan bir yapılandırma öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="07096-116">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07096-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="07096-117">Parent Elements</span></span>  
  
|<span data-ttu-id="07096-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="07096-118">Element</span></span>|<span data-ttu-id="07096-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07096-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="07096-120">Belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="07096-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07096-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07096-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="07096-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="07096-122">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
