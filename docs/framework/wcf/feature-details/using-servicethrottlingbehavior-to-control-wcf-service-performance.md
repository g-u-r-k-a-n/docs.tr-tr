---
title: WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: 44cc924de0c3079bb2f8125a7ac63fa494d4aca1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289418"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a><span data-ttu-id="3b5db-102">WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma</span><span class="sxs-lookup"><span data-stu-id="3b5db-102">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>

<span data-ttu-id="3b5db-103"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior>Sınıfı, uygulama düzeyinde kaç örnek veya oturum oluşturulduğunu sınırlandırmak için kullanabileceğiniz özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="3b5db-103">The <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class exposes properties that you can use to limit how many instances or sessions are created at the application level.</span></span> <span data-ttu-id="3b5db-104">Bu davranışı kullanarak, Windows Communication Foundation (WCF) uygulamanızın performansı üzerinde ince ayar yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b5db-104">Using this behavior, you can fine-tune the performance of your Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a><span data-ttu-id="3b5db-105">Hizmet örnekleri ve eşzamanlı çağrılar denetleniyor</span><span class="sxs-lookup"><span data-stu-id="3b5db-105">Controlling Service Instances and Concurrent Calls</span></span>  

 <span data-ttu-id="3b5db-106"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>Bir sınıf üzerinde etkin olarak işlenen en fazla ileti sayısını <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> hizmette en fazla nesne sayısını belirtmek için özelliğini kullanın <xref:System.ServiceModel.InstanceContext> .</span><span class="sxs-lookup"><span data-stu-id="3b5db-106">Use the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> property to specify the maximum number of messages actively processing across a <xref:System.ServiceModel.ServiceHost> class, and the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> property to specify the maximum number of <xref:System.ServiceModel.InstanceContext> objects in the service.</span></span>  
  
 <span data-ttu-id="3b5db-107">Bu özelliklerin ayarlarının belirlenmesi genellikle uygulamayı yüklere karşı çalıştırmanın gerçek dünya deneyiminden sonra gerçekleştiğinden, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> özelliklerin ayarları genellikle öğesi kullanılarak bir uygulama yapılandırma dosyasında belirtilir [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) .</span><span class="sxs-lookup"><span data-stu-id="3b5db-107">Because determining the settings for these properties usually takes place after real-world experience running the application against loads, the settings for the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> properties is typically specified in an application configuration file using the [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) element.</span></span>  
  
 <span data-ttu-id="3b5db-108">Aşağıdaki kod örneği <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> ,,, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> ve <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> özelliklerini önemsiz bir örnek olarak 1 olarak ayarlayan bir uygulama yapılandırma dosyasından sınıfın kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b5db-108">The following code example shows the use of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class from an application configuration file that sets the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> properties to 1 as a trivial example.</span></span> <span data-ttu-id="3b5db-109">Gerçek hayatta deneyim, belirli bir uygulama için en iyi ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="3b5db-109">Real-world experience determines the optimal settings for any particular application.</span></span>  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 <span data-ttu-id="3b5db-110">Tam çalışma zamanı davranışı, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliklerinin, bir kerede bir işlem içinde nasıl yürütümeyeceğini ve hizmetin yaşam sürelerini <xref:System.ServiceModel.InstanceContext> sırasıyla gelen kanal oturumlarına göre denetleyen ve özelliklerin değerlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b5db-110">The exact run-time behavior depends upon the values of the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> and <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> properties, which control how many messages can execute inside an operation at once and the lifetimes of the service <xref:System.ServiceModel.InstanceContext> relative to incoming channel sessions, respectively.</span></span>  
  
 <span data-ttu-id="3b5db-111">Ayrıntılar için bkz <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> . ve.</span><span class="sxs-lookup"><span data-stu-id="3b5db-111">For details, see <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b5db-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b5db-112">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
