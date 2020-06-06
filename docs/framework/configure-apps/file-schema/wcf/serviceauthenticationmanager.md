---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399702"
---
# \<serviceAuthenticationManager>
<span data-ttu-id="5acfe-101">, Hizmet düzeyinde bir iletim, ileti veya gönderen için geçerliliği belirleyen bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5acfe-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="5acfe-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5acfe-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5acfe-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5acfe-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5acfe-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5acfe-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5acfe-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5acfe-105">Attributes</span></span>  
  
|<span data-ttu-id="5acfe-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5acfe-106">Attribute</span></span>|<span data-ttu-id="5acfe-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5acfe-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5acfe-108">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="5acfe-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="5acfe-109">Geçerli davranış için kimlik doğrulama ilkesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5acfe-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5acfe-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5acfe-110">Child Elements</span></span>  
 <span data-ttu-id="5acfe-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5acfe-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5acfe-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5acfe-112">Parent Elements</span></span>  
  
|<span data-ttu-id="5acfe-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5acfe-113">Element</span></span>|<span data-ttu-id="5acfe-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5acfe-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5acfe-115">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5acfe-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5acfe-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5acfe-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
