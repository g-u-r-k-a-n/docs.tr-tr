---
title: webRequestModules için <remove> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: 65e8b1f2088015b86d4f981f07875d236a11a617
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176194"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="f1f01-102">webRequestModules için \<remove> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="f1f01-102">\<remove> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="f1f01-103">Uygulamadan özel bir Web istek modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f1f01-103">Removes a custom Web request module from the application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**
  
## <a name="syntax"></a><span data-ttu-id="f1f01-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f1f01-104">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1f01-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1f01-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f1f01-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1f01-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1f01-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f1f01-107">Attributes</span></span>  
  
|<span data-ttu-id="f1f01-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="f1f01-108">**Attribute**</span></span>|<span data-ttu-id="f1f01-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f1f01-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="f1f01-110">Bu Web isteği modülü tarafından işlenen istekler için URI ön eki.</span><span class="sxs-lookup"><span data-stu-id="f1f01-110">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1f01-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1f01-111">Child Elements</span></span>  

 <span data-ttu-id="f1f01-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="f1f01-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1f01-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1f01-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f1f01-114">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="f1f01-114">**Element**</span></span>|<span data-ttu-id="f1f01-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f1f01-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f1f01-116">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="f1f01-116">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="f1f01-117">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1f01-117">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1f01-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1f01-118">Remarks</span></span>  

 <span data-ttu-id="f1f01-119">`remove`Öğesi, BELIRTILEN URI ön eki için kayıtlı Web isteği modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f1f01-119">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="f1f01-120">`prefix`Özniteliğin değeri geçerli BIR URI 'nin baştaki karakterleri olmalıdır--örneğin, " `http` " veya " `http://www.contoso.com` ".</span><span class="sxs-lookup"><span data-stu-id="f1f01-120">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f1f01-121">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f1f01-121">Configuration Files</span></span>  

 <span data-ttu-id="f1f01-122">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1f01-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1f01-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1f01-123">Example</span></span>  

<span data-ttu-id="f1f01-124">Aşağıdaki örnek, HTTP için mevcut Web isteği modülünü kaldırır ve ardından HTTP istekleri için yeni bir özel Web istek modülünü kaydeder `www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="f1f01-124">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1f01-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1f01-125">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="f1f01-126">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="f1f01-126">Network Settings Schema</span></span>](index.md)
