---
title: NetHttpBinding Kullanma
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 82222dbfa3f35ed00d0173f2bc927c32e9e98470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184239"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="513f9-102">NetHttpBinding Kullanma</span><span class="sxs-lookup"><span data-stu-id="513f9-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="513f9-103"><xref:System.ServiceModel.NetHttpBinding>HTTP veya WebSocket hizmetlerini tüketmek için tasarlanmış bir bağlayıcıdır ve varsayılan olarak ikili kodlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="513f9-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="513f9-104"><xref:System.ServiceModel.NetHttpBinding>bir istek yanıtlama sözleşmesi veya çift yönlü sözleşme ile kullanılıp kullanılmadığını algılar ve davranışını eşleşecek şekilde değiştirir - bu istek yanıtlama sözleşmeleri için HTTP ve çift yönlü sözleşmeler için WebSockets kullanır.</span><span class="sxs-lookup"><span data-stu-id="513f9-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="513f9-105">Bu davranış <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ayarı kullanılarak geçersiz kılınabilir:</span><span class="sxs-lookup"><span data-stu-id="513f9-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="513f9-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>- Bu, WebSockets'i istek-yanıt sözleşmeleri için bile kullanılmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="513f9-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="513f9-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>- Bu, WebSockets'in kullanılmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="513f9-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="513f9-108">Bu ayarile çift yönlü bir sözleşme kullanmaya çalışmak bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="513f9-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="513f9-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>- Bu varsayılan değerdir ve yukarıda açıklandığı gibi şekilde işlem yapılır.</span><span class="sxs-lookup"><span data-stu-id="513f9-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="513f9-110"><xref:System.ServiceModel.NetHttpBinding>hem HTTP modunda hem de WebSocket modunda güvenilir oturumları destekler.</span><span class="sxs-lookup"><span data-stu-id="513f9-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="513f9-111">WebSocket modunda oturumlar aktarım tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="513f9-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="513f9-112">Bağlamanın <xref:System.ServiceModel.NetHttpBinding> Aktarım Modu'nu ve Aktarım Mode'u Kullanarak TransferMode.Streamed olarak ayarlanırsa, büyük akışlar bir kilitlenmeye neden olabilir ve arama zaman alacaktır.</span><span class="sxs-lookup"><span data-stu-id="513f9-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="513f9-113">Bu sorunu çözmek için daha küçük iletiler gönderin veya Aktarım Modu.Arabelleğe Alma'yı kullanın.</span><span class="sxs-lookup"><span data-stu-id="513f9-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="513f9-114">Bir Hizmeti Net'i kullanacak şekilde yapılandırmaHttpBinding</span><span class="sxs-lookup"><span data-stu-id="513f9-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="513f9-115">Diğer <xref:System.ServiceModel.NetHttpBinding> bağlama ile aynı şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="513f9-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="513f9-116">Aşağıdaki yapılandırma snippet nasıl bir WCF hizmeti <xref:System.ServiceModel.NetHttpBinding>ile yapılandırılanın gösteriş gösterir.</span><span class="sxs-lookup"><span data-stu-id="513f9-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 <span data-ttu-id="513f9-117">Aşağıdaki kod snippet kodu eklemek <xref:System.ServiceModel.NetHttpBinding> için nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="513f9-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="513f9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="513f9-118">See also</span></span>

- [<span data-ttu-id="513f9-119">Hizmetler için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="513f9-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="513f9-120">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="513f9-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)
- [<span data-ttu-id="513f9-121">Sistem Destekli Ciltler</span><span class="sxs-lookup"><span data-stu-id="513f9-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="513f9-122">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="513f9-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
