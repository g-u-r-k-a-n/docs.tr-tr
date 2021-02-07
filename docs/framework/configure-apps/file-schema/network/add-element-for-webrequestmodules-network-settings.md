---
description: 'Daha fazla bilgi edinin: <add> webRequestModules için öğesi (ağ ayarları)'
title: webRequestModules için <add> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: 1edb63a1e1095bb4b3c3d749fd389ffaad5ddf9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729906"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="4cdf0-103">webRequestModules için \<add> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="4cdf0-103">\<add> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="4cdf0-104">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-104">Adds a custom Web request module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="4cdf0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4cdf0-105">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cdf0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cdf0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4cdf0-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cdf0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4cdf0-108">Attributes</span></span>  
  
|<span data-ttu-id="4cdf0-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="4cdf0-109">**Attribute**</span></span>|<span data-ttu-id="4cdf0-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="4cdf0-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="4cdf0-111">Bu Web isteği modülü tarafından işlenen istekler için URI ön eki.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-111">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="4cdf0-112"><xref:System.Type.FullName%2A>Bu Web istek modülünü uygulayan, tam tür adı (özelliği tarafından gösterilen) ve derleme adı (özelliği ile belirtilir <xref:System.Reflection.Assembly.FullName%2A> ), virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-112">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cdf0-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cdf0-113">Child Elements</span></span>  

 <span data-ttu-id="4cdf0-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4cdf0-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cdf0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4cdf0-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="4cdf0-116">**Element**</span></span>|<span data-ttu-id="4cdf0-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="4cdf0-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4cdf0-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="4cdf0-118">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="4cdf0-119">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cdf0-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cdf0-120">Remarks</span></span>  

 <span data-ttu-id="4cdf0-121">`prefix`Özniteliği belirtilen Web istek modülünü kullanan URI önekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-121">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="4cdf0-122">Web isteği modülleri, genellikle HTTP veya FTP gibi belirli bir protokolü işlemek için kaydedilir, ancak bir sunucudaki belirli bir sunucuya veya yola yönelik bir isteği işlemek için kayıt yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-122">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="4cdf0-123">Yöntemine bir URI eşleştirme öneki geçirildiğinde Web istek modülü oluşturulur <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4cdf0-123">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="4cdf0-124">`prefix`Özniteliğin değeri geçerli BIR URI 'nin baştaki karakterleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-124">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="4cdf0-125">Örneğin `http` veya `http://www.contoso.com` olabilir.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-125">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="4cdf0-126">Özniteliğin değeri, `type` virgülle ayrılmış olarak geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-126">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="4cdf0-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4cdf0-127">Configuration Files</span></span>  

 <span data-ttu-id="4cdf0-128">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cdf0-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="4cdf0-129">Example</span></span>  

 <span data-ttu-id="4cdf0-130">Aşağıdaki örnek, HTTP için özel bir Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-130">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="4cdf0-131">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-131">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cdf0-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cdf0-132">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="4cdf0-133">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4cdf0-133">Network Settings Schema</span></span>](index.md)
