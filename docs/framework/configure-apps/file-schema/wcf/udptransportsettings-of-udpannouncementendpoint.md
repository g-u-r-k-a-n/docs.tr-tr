---
description: 'Hakkında daha fazla bilgi <udpTransportSettings> edinin: <udpAnnouncementEndpoint>'
title: <udpTransportSettings> / <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
ms.openlocfilehash: 2997004e162728b20daa4f137e1edf132cd33d52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749213"
---
# <a name="udptransportsettings-of-udpannouncementendpoint"></a>\<udpTransportSettings> / \<udpAnnouncementEndpoint>

Bu yapılandırma öğesi için UDP taşıma ayarlarını gösterir [\<udpAnnouncementEndpoint>](udpannouncementendpoint.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpAnnouncementEndpoint>**](udpannouncementendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  

## <a name="syntax"></a>Syntax  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpAnnouncementEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpAnnouncementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Duplicatemessagegeçmişini uzunluğu|Yinelenen iletileri tanımlamak için taşıma tarafından kullanılan en fazla ileti karması sayısını belirten bir tamsayı.  Yinelenen algılama işlemi, TransportManager düzeyinde yapılır. Bu özelliğin 0 olarak ayarlanması yinelenen algılamayı devre dışı bırakır.<br /><br /> Bu öznitelik, sistem yöneticilerinin veya geliştiricilerin yinelenen ileti algılama algoritmalarını kapatmasına izin verir. Kendi yinelenen algılama algoritmanızı uygulamak istiyorsanız bu işlem istenebilir.<br /><br /> Varsayılan değer 4112 ' dir.|  
|maxBufferPoolSize|Taşıma tarafından kullanılan tüm arabellek havuzlarının en büyük boyutunu belirten bir tamsayı.|  
|maxMulticastRetransmitCount|İletinin en fazla kaç kez yeniden gönderilmesi gerektiğini belirten bir tamsayı (ilk gönderme 'ya ek olarak).<br /><br /> Varsayılan değer 2 ' dir.|  
|maxPendingMessageCount|Tek bir kanal örneği için InputQueue öğesinden alınmış ancak henüz kaldırılmayan en fazla ileti sayısını belirten bir tamsayı.  InputQueue, bekleyen ileti sayısı sınırına ulaşmışsa ileti bırakılır.<br /><br /> Varsayılan değer 32 ' dir.|  
|Değerini|Bağlama tarafından işlenebilecek bir iletinin en büyük boyutunu belirten bir tamsayı.<br /><br /> Varsayılan değer 65507 ' dir.|  
|maxUnicastRetransmitCount|İletinin en fazla kaç kez yeniden gönderilmesi gerektiğini belirten bir tamsayı (ilk gönderme 'ya ek olarak).  İleti bir tek noktaya yayın adresine gönderilirse ve karşılık gelen bir RelatesTo üstbilgisiyle yanıt iletisi alındığında, yeniden iletim erken sonlandırılabilir (yapılandırılan sayıda yeniden gönderilmeden önce).<br /><br /> Varsayılan değer 1’dir.|  
|multicastInterfaceId|Çoklu bilgisayarlı makinelerde çok noktaya yayın trafiği gönderirken ve alırken kullanılması gereken ağ bağdaştırıcısını benzersiz şekilde tanımlayan bir dize. Çalışma zamanında, aktarım bu öznitelik değerini, daha sonra `IP_MULTICAST_IF` ve yuva seçeneklerini ayarlamak için kullanılan arabirim dizinini aramak için kullanır `IPV6_MULTICAST_IF` .  Varsa, çok noktaya yayın grubuna katılırken de aynı arabirim dizini kullanılacaktır.<br /><br /> `null` varsayılan değerdir.|  
|socketReceiveBufferSize|Temeldeki WinSock yuvasında Alım arabelleği boyutunu belirten bir tamsayı.<br /><br /> Alma kanalının bir kullanıcısı, verileri alırken sistemin nasıl davranacağını denetlemek için bağlama üzerinde bu özniteliği kullanabilir.  Örneğin, bu öznitelik için daha yüksek bir değere sahip gelen WCF iletilerini kullanan bir uygulama, iletilerin, uygulamanın onları işlemesini beklerken WinSock arabelleğine yığmasını sağlar.  Aynı durumda daha düşük bir değer kullanılması, iletilerin bırakılmasına neden olur. Bu öznitelik, temeldeki WinSock `SO_RCVBUF` yuva seçeneğini gösterir. Bu öznitelik değeri en az boyut olmalıdır `maxReceivedMessageSize` .   Değerinden küçük bir değere ayarlanması `maxReceivedMessageSize` çalışma zamanı özel durumuna neden olur.<br /><br /> Varsayılan değer 65536 ' dir.|  
|timeToLive|Çok noktaya yayın paketinin geçebileceğine yönelik ağ segmenti atlamalarının sayısını belirten bir tamsayı.  Bu öznitelik, `IP_MULTICAST_TTL` ve yuva seçenekleriyle ilişkili işlevselliği gösterir `IP_TTL` .<br /><br /> Varsayılan değer 1’dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|Sabit duyuru sözleşmesine ve UDP aktarım bağlamaya sahip standart bir uç nokta.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
