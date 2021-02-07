---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: oturum gerektiren bir hizmet oluşturma'
title: 'Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 362aee23437bb7f45af5a265a9d3ef47bf62915c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734470"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="df9a7-103">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="df9a7-103">How to: Create a Service That Requires Sessions</span></span>

<span data-ttu-id="df9a7-104">Oturumlar, geri çağrılar, çok duraklı güvenlik ve istemciler ile hizmet örnekleri arasındaki ilişkilendirmeler gibi faydalı özellikleri sağlayan iki veya daha fazla uç nokta arasında paylaşılan bir durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df9a7-104">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="df9a7-105">Windows Communication Foundation (WCF) uygulamalarındaki oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanma](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="df9a7-105">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="df9a7-106">Bir sözleşmenin, oturumları desteklemek için bağlamasını gerektirdiğini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="df9a7-106">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="df9a7-107">En az bir işlemle bir hizmet sözleşmesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="df9a7-107">Create a service contract with at least one operation.</span></span> <span data-ttu-id="df9a7-108">Hizmet sözleşmesinin nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: bir hizmet sözleşmesi tanımlama](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="df9a7-108">For an example of how to create a service contract, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="df9a7-109">Özelliği şu <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> şekilde ayarlayarak sözleşmeyi bildiren ' i değiştirin <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="df9a7-109">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="df9a7-110"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Bu sözleşmenin bir oturum içinde çalıştırılması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="df9a7-110"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="df9a7-111"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Bu sözleşme bir oturum içinde çalıştırılabilirler.</span><span class="sxs-lookup"><span data-stu-id="df9a7-111"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="df9a7-112"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Bu sözleşmenin bir oturum içinde çalıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="df9a7-112"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="df9a7-113">Hizmet uç noktanızı oturumları destekleyen bir bağlama kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="df9a7-113">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="df9a7-114">Aşağıdaki yapılandırma örneği, <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> BIR WS ReliableMessaging oturumunu destekleyen öğesinin kullanımını gösterir `-` .</span><span class="sxs-lookup"><span data-stu-id="df9a7-114">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="df9a7-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="df9a7-115">Example</span></span>  

 <span data-ttu-id="df9a7-116">Aşağıdaki örnek kod, bir sözleşme düzeyi oturum gereksinimini belirtmeyi ve bağlamakla bu gereksinimi desteklemek için bir yapılandırma dosyası kullanmayı gösterir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="df9a7-116">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="df9a7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df9a7-117">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
