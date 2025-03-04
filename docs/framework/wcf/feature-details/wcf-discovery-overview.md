---
description: 'Daha fazla bilgi edinin: WCF bulgu genel bakış'
title: WCF Keşif Genel Bakış
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: d6acfb86ce0961ea7fbfba7695bece067e3dcec2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779653"
---
# <a name="wcf-discovery-overview"></a>WCF Keşif Genel Bakış

Bulma API 'Leri, WS-Discovery protokolü kullanılarak dinamik yayımlama ve Web Hizmetleri bulma için Birleşik bir programlama modeli sağlar. Bu API 'Ler, hizmetlerin kendilerini ve istemcileri yayımlanmış Hizmetleri bulmak için yayımlamasına olanak sağlar. Bir hizmet bulunabilir hale getirildikten sonra hizmet, duyuru iletileri gönderebilir ve bulma isteklerini dinleyebilir ve bunlara yanıt verebilir. Keşfedilebilir hizmetler, bir ağ üzerinden bir ağı duyurmak üzere bir ağ ve Bye iletileri üzerinde gelişmelerini duyurmak için Merhaba iletiler gönderebilir. İstemcileri, bir hizmeti bulmak için `Probe` ağ üzerinde hizmet sözleşmesi türü, anahtar sözcükler ve kapsam gibi belirli ölçütler içeren bir istek gönderir. Hizmetler, `Probe` isteği alır ve ölçütlere göre eşleşip eşleşmediğine göre belirlenir. Bir hizmet eşleşiyorsa, `ProbeMatch` hizmetle iletişim kurmak için gereken bilgilerle istemciye geri ileti göndererek yanıt verir. İstemciler ayrıca `Resolve` , kendi uç nokta adreslerini değiştirmiş olabilecek Hizmetleri bulmasına izin veren istekleri de gönderebilir. Eşleşen Hizmetler `Resolve` istemciye geri ileti göndererek isteklere yanıt verir `ResolveMatch` .  
  
## <a name="ad-hoc-and-managed-modes"></a>Geçici ve yönetilen modlar  

 Keşif API 'SI iki farklı modu destekler: yönetilen ve geçici. Yönetilen modda, kullanılabilir hizmetler hakkında bilgi tutan bulma proxy 'si adlı merkezi bir sunucu vardır. Keşif proxy 'si, hizmetler hakkında çeşitli yollarla doldurulmuş olabilir. Örneğin, hizmetler bulma proxy 'sine başlama sırasında duyuru iletileri gönderebilir veya proxy, hangi hizmetlerin kullanılabilir olduğunu belirlemek için bir veritabanından veya bir yapılandırma dosyasından verileri okuyabilir. Bulma proxy 'sinin nasıl doldurulduğu, geliştiriciye tamamen tamamen yapılır. İstemciler, kullanılabilir hizmetler hakkında bilgi almak için bulma proxy 'sini kullanır. Bir istemci bir hizmeti aradığında `Probe` , bulma proxy 'sine bir ileti gönderir ve proxy, istemci tarafından aranan hizmetlerden herhangi birinin aradığı hizmetle eşleşip eşleşmediğini belirler. Eşleşmeler varsa bulma proxy 'si istemciye bir yanıt gönderir `ProbeMatch` . İstemci daha sonra doğrudan proxy 'den döndürülen hizmet bilgilerini kullanarak hizmetle iletişim kurabilirler. Yönetilen modun arkasındaki anahtar ilkesi, bulma isteklerinin tek bir yetkiliye, bulma proxy 'sine yönelik bir tek noktaya gönderildiği bir şekilde gönderilir. .NET Framework kendi ara sunucusunu oluşturmanıza izin veren anahtar bileşenleri içerir. İstemciler ve hizmetler Proxy 'yi birden çok yöntemle bulabilir:  
  
- Proxy, geçici iletilere yanıt verebilir.  
  
- Proxy, başlangıç sırasında bir duyuru iletisi gönderebilir.  
  
- İstemciler ve hizmetler, iyi bilinen belirli bir uç noktayı aramak için yazılabilir.  
  
 Geçici modda, merkezi sunucu yoktur. Hizmet duyuruları ve istemci istekleri gibi tüm bulma iletileri çok noktaya yayın biçiminde gönderilir. Varsayılan olarak .NET Framework, UDP protokolü üzerinden geçici bulma desteği içerir. Örneğin, bir hizmet başlangıç sırasında bir Hello duyurusu gönderecek şekilde yapılandırıldıysa, UDP protokolünü kullanarak iyi bilinen bir çok noktaya yayın adresi üzerinden gönderilir. İstemcilerin bu duyuruları etkin bir şekilde dinlemek ve uygun şekilde işlemesi gerekir. İstemci `Probe` bir hizmet için bir ileti gönderdiğinde çok noktaya yayın protokolü kullanılarak ağ üzerinden gönderilir. İsteği alan her hizmet, iletideki ölçütlerle eşleşip eşleşmediğini belirler `Probe` ve `ProbeMatch` hizmet iletide belirtilen ölçütlerle eşleşiyorsa istemciye doğrudan bir iletiyle yanıt verir `Probe` .  
  
## <a name="benefits-of-using-wcf-discovery"></a>WCF bulmayı kullanmanın avantajları  

 WCF bulma WS-Discovery protokol kullanılarak uygulandığından, WS-Discovery uygulayan diğer istemcilerle, hizmetlerle ve proxy 'lerde birlikte çalışabilir. WCF bulma, mevcut WCF API 'Leri üzerine kurulmuştur. Bu, mevcut hizmet ve istemcilerinize bulma işlevselliği eklemenizi kolaylaştırır. Hizmet bulunabilirliği, uygulama yapılandırma ayarları aracılığıyla kolayca eklenebilir. Ayrıca, WCF bulma Ayrıca, Eş ağ, adlandırma kaplaması ve HTTP gibi diğer aktarımlara yönelik bulma protokolünü de destekler. WCF bulma, bir bulma proxy 'sinin kullanıldığı yönetilen işlem modu için destek sağlar. Bu, iletiler tüm ağa çok noktaya yayın iletileri göndermek yerine doğrudan bulma proxy 'sine gönderildiğinde ağ trafiğini azaltabilir. WCF bulma ayrıca Web hizmetleriyle çalışırken daha fazla esneklik sağlar. Örneğin, istemciyi veya hizmeti yeniden yapılandırmak zorunda kalmadan bir hizmetin adresini değiştirebilirsiniz. Bir istemcinin hizmete erişmesi gerektiğinde, `Probe` bir istek aracılığıyla bir ileti verebilir `Find` ve hizmetin geçerli adresiyle yanıt vermesini bekleyebilir. WCF bulma, bir istemcinin sözleşme türleri, bağlama öğeleri, ad alanı, kapsam ve anahtar sözcükler ya da sürüm numaraları gibi farklı ölçütlere göre bir hizmet aramasını sağlar. WCF bulma çalışma zamanı ve tasarım zamanı bulmayı mümkün bir şekilde sunar. Uygulamanıza bulma eklemek, hata toleransı ve otomatik yapılandırma gibi diğer senaryolara olanak tanımak için kullanılabilir.  
  
## <a name="service-publication"></a>Hizmet yayını  

 Bir hizmeti bulunabilir hale getirmek için, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına eklenmelidir ve bulma iletilerinin nerede dinleneceğini belirtmek için bir bulma uç noktası eklenmelidir. Aşağıdaki kod örneği, kendi kendine barındırılan bir hizmetin bulunabilir hale getirmek için nasıl değiştirileceğini gösterir.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Hizmetin keşfedilmesini sağlamak için bir hizmet açıklamasına bir örnek eklenmelidir. Hizmeti <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> bulma isteklerinin nerede dinleneceğini bildirmek için hizmet ana bilgisayarına bir örnek eklenmelidir. Bu örnekte, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> hizmetin UDP çok noktaya yayın aktarımı üzerinden bulma isteklerini dinlemesi gerektiğini belirtmek için bir (öğesinden türetilmiş) bir () eklenir. , <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Tüm iletiler çok noktaya yayın düzeyinde gönderildiğinden, geçici bulma için kullanılır.  
  
## <a name="announcement"></a>Duyuru  

 Varsayılan olarak, hizmet yayını duyuru iletileri göndermez. Hizmetin duyuru iletileri gönderecek şekilde yapılandırılması gerekir. Bu, hizmeti bulma iletilerini dinlemeden ayrı olarak duyurabileceğinden, hizmet yazarları için ek esneklik sağlar. Hizmet duyurusu Ayrıca, Hizmetleri bulma proxy 'si veya diğer hizmet kayıt defterlerine kaydetme mekanizması olarak da kullanılabilir. Aşağıdaki kod, bir hizmetin UDP bağlama üzerinden duyuru iletileri göndermek için nasıl yapılandırılacağını gösterir.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a>Hizmet Bulma  

 İstemci uygulaması, <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri bulmak için sınıfını kullanabilir. Geliştirici, <xref:System.ServiceModel.Discovery.DiscoveryClient> ' ın nereye gönderileceğini belirten bir bulma uç noktasında geçen sınıfının bir örneğini oluşturur `Probe` `Resolve` . İstemci daha sonra <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> bir örnek içinde arama ölçütlerini belirten çağırır <xref:System.ServiceModel.Discovery.FindCriteria> . Eşleşen hizmetler bulunursa, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> bir koleksiyonu döndürür <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> . Aşağıdaki kod, yönteminin nasıl çağrılacağını `Find` ve sonra keşfedilen bir hizmete nasıl bağlanacağını gösterir.  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService())
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a>Bulma ve Ileti düzeyi güvenliği  

 İleti düzeyinde güvenlik kullanırken, <xref:System.ServiceModel.EndpointIdentity> hizmet bulma uç noktasında ve <xref:System.ServiceModel.EndpointIdentity> istemci bulma uç noktasında eşleşen bir değer belirtmeniz gerekir. İleti düzeyi güvenliği hakkında daha fazla bilgi için bkz. [Ileti güvenliği](message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Bulma ve Web 'de barındırılan hizmetler  

 WCF hizmetlerinin keşfedilmesini sağlamak için bunların çalışıyor olması gerekir. IIS 'de barındırılan WCF Hizmetleri, IIS/hizmet için bir ileti alana bağlanana kadar çalıştırılmadığından, varsayılan olarak keşfedilemez.  Web-Hosted hizmetlerini bulunabilir hale getirmek için iki seçenek vardır:  
  
1. Windows Server AppFabric otomatik başlatma özelliğini kullanın  
  
2. Hizmet adına iletişim kurmak için bir bulma proxy 'si kullanın  
  
 Windows Server AppFabric, herhangi bir ileti alınmadan önce bir hizmetin başlatılmasını sağlayacak bir otomatik başlatma özelliğine sahiptir. Bu otomatik başlatma kümesiyle, bir IIS/WAS barındırılan hizmeti bulunabilir olacak şekilde yapılandırılabilir. Otomatik başlatma özelliği hakkında daha fazla bilgi için bkz. [Windows Server AppFabric otomatik başlatma özelliği](/previous-versions/appfabric/ee677260(v=azure.10)). Otomatik başlatma özelliğini açma ile birlikte, hizmeti bulma için yapılandırmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: program aracılığıyla BIR WCF hizmetine bulunabilirliği ekleme ve Istemci](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[yapılandırma dosyasında bulmayı yapılandırma](configuring-discovery-in-a-configuration-file.md).  
  
 Bulma proxy 'si, hizmet çalışmadığı zaman WCF hizmeti adına iletişim kurmak için kullanılabilir. Proxy, araştırmayı dinleyebilir veya iletileri çözümleyebilir ve istemciye yanıt verebilir. İstemci daha sonra iletileri doğrudan hizmete gönderebilir. İstemci hizmete bir ileti gönderdiğinde, iletiye yanıt vermek için örneği oluşturulur. Bulma proxy 'si uygulama hakkında daha fazla bilgi için bkz. [bulma proxy 'Si uygulama](implementing-a-discovery-proxy.md).  
  
> [!NOTE]
> WCF bulmanın düzgün çalışması için tüm NIC 'ler (ağ arabirim denetleyicisi) yalnızca 1 IP adresine sahip olmalıdır.
