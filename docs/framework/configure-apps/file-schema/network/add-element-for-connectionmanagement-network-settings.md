---
description: 'Daha fazla bilgi edinin: <add> connectionManagement için öğesi (ağ ayarları)'
title: connectionManagement için <add> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 646d9fcfb73cfd8f4f533672c1a92883274f6e39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729946"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="a5aef-103">connectionManagement için \<add> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="a5aef-103">\<add> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="a5aef-104">Bağlantı yönetimi listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="a5aef-104">Adds an IP address or DNS name to the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="a5aef-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a5aef-105">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5aef-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5aef-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a5aef-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5aef-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5aef-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a5aef-108">Attributes</span></span>  
  
|<span data-ttu-id="a5aef-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="a5aef-109">**Attribute**</span></span>|<span data-ttu-id="a5aef-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a5aef-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="a5aef-111">IP adresini veya DNS adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="a5aef-111">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="a5aef-112">Bir sunucuyla izin verilen en fazla bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="a5aef-112">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="a5aef-113">Sağlanmazsa, varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a5aef-113">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5aef-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5aef-114">Child Elements</span></span>  

 <span data-ttu-id="a5aef-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="a5aef-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5aef-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5aef-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a5aef-117">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="a5aef-117">**Element**</span></span>|<span data-ttu-id="a5aef-118">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a5aef-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a5aef-119">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="a5aef-119">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a5aef-120">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5aef-120">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5aef-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5aef-121">Remarks</span></span>  

 <span data-ttu-id="a5aef-122">`address`Özniteliğin değeri tüm bağlantıları göstermek için bir yıldız işareti ya da formun bir dizesi olmalıdır `<schema>://<idn_hostname>[:<port>]` .</span><span class="sxs-lookup"><span data-stu-id="a5aef-122">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="a5aef-123">Herhangi bir HTTP API 'sine geçirilen URI Unicode içeriyorsa, bu ad dahili olarak dönüştürülür ve bu, <xref:System.Uri.DnsSafeHost%2A> punicode dize (GEÇERLI IDN yapılandırmasına bağımlı davranışlar) döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="a5aef-123">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a5aef-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a5aef-124">Configuration Files</span></span>  

 <span data-ttu-id="a5aef-125">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5aef-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5aef-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5aef-126">Example</span></span>  

 <span data-ttu-id="a5aef-127">Aşağıdaki örnek, bir uygulamayı sunucuya dört bağlantı `www.contoso.com` ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a5aef-127">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5aef-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5aef-128">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="a5aef-129">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="a5aef-129">Network Settings Schema</span></span>](index.md)
