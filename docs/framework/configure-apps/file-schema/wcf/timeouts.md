---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: f7e513bb5c486fa5f7c39c9b2e3cfcd26bd7c219
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157102"
---
# \<timeOuts>

<span data-ttu-id="f9631-101">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9631-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="f9631-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9631-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9631-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9631-103">Attributes and Elements</span></span>  

 <span data-ttu-id="f9631-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9631-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9631-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9631-105">Attributes</span></span>  
  
|<span data-ttu-id="f9631-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9631-106">Attribute</span></span>|<span data-ttu-id="f9631-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9631-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f9631-108"><xref:System.TimeSpan>Hizmet ana bilgisayarının kapanması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f9631-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="f9631-109"><xref:System.TimeSpan>Hizmet ana bilgisayarının açması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f9631-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9631-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9631-110">Child Elements</span></span>  

 <span data-ttu-id="f9631-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9631-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9631-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9631-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f9631-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9631-113">Element</span></span>|<span data-ttu-id="f9631-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9631-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="f9631-115">Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="f9631-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9631-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9631-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="f9631-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="f9631-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
