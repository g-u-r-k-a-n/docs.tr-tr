---
description: 'Hakkında daha fazla bilgi edinin: <namespaceTable>'
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 73bfac93fba3247c02c2d86d1482af2563015a76
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684093"
---
# \<namespaceTable>

<span data-ttu-id="ca091-102">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ca091-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="ca091-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca091-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca091-104">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="ca091-104">Attributes and elements</span></span>

<span data-ttu-id="ca091-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca091-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca091-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca091-106">Attributes</span></span>

<span data-ttu-id="ca091-107">Yok</span><span class="sxs-lookup"><span data-stu-id="ca091-107">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca091-108">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ca091-108">Child elements</span></span>

|     | <span data-ttu-id="ca091-109">Description</span><span class="sxs-lookup"><span data-stu-id="ca091-109">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="ca091-110">XPath ifadeleri için kullanılan bir ad alanı ön eki eşlemesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca091-110">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="ca091-111">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="ca091-111">Parent elements</span></span>

|     | <span data-ttu-id="ca091-112">Description</span><span class="sxs-lookup"><span data-stu-id="ca091-112">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="ca091-113">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> . Ayrıca, bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca091-113">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ca091-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca091-114">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
