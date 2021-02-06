---
description: 'Hakkında daha fazla bilgi edinin: <bindingElementExtensions>'
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 4c1b4b924906b1a6dc143588a057129ca5ce8f40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639425"
---
# \<bindingElementExtensions>

<span data-ttu-id="8cbd7-102">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="8cbd7-102">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="8cbd7-103">Anahtar sözcüğünü kullanarak bu koleksiyona özel bir bağlama öğesi ekleyebilir `add` ve `type` öğesinin özniteliğini bir bağlama öğesi uzantısına ve `name` özniteliği de özel bağlama öğesine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cbd7-103">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="8cbd7-104">Bağlama uzantıları, kullanıcının özel bağlamaların parçası olarak kullanılmak üzere Kullanıcı tanımlı bağlama öğeleri oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cbd7-104">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="8cbd7-105">Programlı olarak, bağlama uzantısı soyut sınıfı uygulayan bir türdür <xref:System.ServiceModel.Channels.BindingElement> .</span><span class="sxs-lookup"><span data-stu-id="8cbd7-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="8cbd7-106">Yapılandırma dosyasında, `bindingElementExtensions` bölümü bir uzantı öğesi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8cbd7-106">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="8cbd7-107">Aşağıdaki örnek, `add` `name` yapılandırma dosyasının bölümüne bir bağlama uzantısı eklemek için öğesini ve özniteliğini kullanır `bindingElementExtensions` .</span><span class="sxs-lookup"><span data-stu-id="8cbd7-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingElementExtensions>
      <add name="udpTransport"
           type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingElementExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="8cbd7-108">Öğeye yapılandırma becerileri eklemek için, kullanıcının bir öğesi yazması ve kaydetmesi gerekir `bindingElementExtensionSection` .</span><span class="sxs-lookup"><span data-stu-id="8cbd7-108">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="8cbd7-109">Bunun hakkında daha fazla bilgi için belgelerine bakın <xref:System.Configuration> .</span><span class="sxs-lookup"><span data-stu-id="8cbd7-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="8cbd7-110">Öğesi ve yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi özel bağlamanın bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8cbd7-110">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>
  <binding name="test2">
    <udpTransport />
    <binaryMessageEncoding maxReadPoolSize="211"
                           maxWritePoolSize="2132"
                           maxSessionSize="3141" />
  </binding>
</customBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="8cbd7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cbd7-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="8cbd7-112">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8cbd7-112">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
