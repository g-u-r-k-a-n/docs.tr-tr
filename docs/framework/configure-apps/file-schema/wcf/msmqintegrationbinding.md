---
title: <msmqIntegrationBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
ms.openlocfilehash: bc2b1648ad404ba13920d9f276c299756554b5d4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204677"
---
# \<msmqIntegrationBinding>

MSMQ aracılığıyla iletileri yönlendirerek sıraya alma desteği sağlayan bir bağlamayı tanımlar.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqIntegrationBinding>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<msmqIntegrationBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveContextEnabled="Boolean"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           serializationFormat="XML/Binary/ActiveX/ByteArray/Stream"
           timeToLive="TimeSpan"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|closeTimeout|<xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|customDeadLetterQueue|Zaman aşımına uğradı veya başarısız aktarım ya da teslimi olan iletilerin yerleştirildiği, uygulama başına atılacak mektup sırasının konumunu içeren bir URI.<br /><br /> Sahipsiz sıra, teslim edilemeyen süre dolmayan iletiler için gönderen uygulamanın kuyruk yöneticisinde bir sıradır.<br /><br /> Tarafından belirtilen URI 'nin <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> net. MSMQ şemasını kullanması gerekir.|  
|Özelliğinde|Bir <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> . değer varsa, ne tür bir atılacak ileti sırası kullanılacağını belirten.<br /><br /> Atılacak bir sıra, uygulamaya teslim edilemeyen iletilerin aktarılacağı konumdur.<br /><br /> ExactlyOnce güvencesi gerektiren (yani, `exactlyOnce` özniteliği olarak ayarlanmış) iletiler için `true` , bu öznitelik MSMQ 'daki sistem genelinde işlem atılacak mektup kuyruğuna varsayılan olarak ayarlanır.<br /><br /> Herhangi bir değer gerektirmeyen iletiler için, bu öznitelik varsayılan olarak olur `null` .|  
|üretilen|İletinin kuyrukta dayanıklı mi yoksa geçici mi olduğunu belirten bir Boole değeri. Kalıcı bir ileti bir sıra Yöneticisi kilitlenmesiyle çalışır, geçici bir ileti değildir. Geçici iletiler, uygulamalar daha düşük gecikme süresi gerektirdiğinde ve zaman zaman kaybolmuş iletileri kabul edebildiği durumlarda faydalıdır. `exactlyOnce`Özniteliği olarak ayarlandıysa `true` , iletilerin dayanıklı olması gerekir. Varsayılan değer: `true`.|  
|exactlyOnce|Her iletinin yalnızca bir kez teslim edilip edilmediğini belirten Boolean bir değer. Ardından, gönderen teslim arızalarına göre bilgilendirilir. Ne zaman, `durable` `false` Bu öznitelik yok sayılır ve iletiler teslim güvencesi olmadan aktarılır. Varsayılan değer: `true`. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|Değerini|Bu bağlama tarafından işlenen üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı. Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir. İleti boyutu sınırı, hizmet reddi (DoS) saldırılarına maruz kalma olasılığını sınırlandırmaya yöneliktir.|  
|Maxretrydöngüleri|Zarar iletisi algılama özelliği tarafından kullanılan yeniden deneme döngüsü sayısını belirten bir tamsayı. Tüm Döngülerde tüm teslim denemeleri başarısız olduğunda bir ileti bir zarar iletisi haline gelir. Varsayılan değer 2 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|name|Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|openTimeout|Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|receiveErrorHandling|<xref:System.ServiceModel.ReceiveErrorHandling>Zebilen ve dağıtılabilir iletilerin nasıl işleneceğini belirten bir değer.|  
|receiveRetryCount|Sıra yöneticisinin uygulama kuyruğundan uygulamaya bir ileti iletimi başarısız olursa, en fazla çabuk yeniden deneme sayısını belirten bir tamsayı.<br /><br /> En fazla teslim denemesi sayısına ulaşıldığında ve ileti uygulama tarafından erişilmezse, ileti daha sonra yeniden teslim için yeniden deneme kuyruğuna gönderilir. İleti gönderme kuyruğuna geri aktarılmadan önceki zaman miktarı tarafından denetlenir `retryCycleDelay` . Yeniden deneme döngüsü değere ulaştıysanız `maxRetryCycles` , ileti, zarar iletisi kuyruğuna gönderilir ya da bir negatif alındı bildirimi gönderene geri gönderilir.|  
|receiveTimeout|<xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:10:00 ' dir.|  
|receiveContextEnabled|Kuyruklarda iletileri işlemeye yönelik alma bağlamının etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri. Bu olarak ayarlandığında `true` , bir hizmet, işleme başlamak için kuyruktaki bir iletiyi "göz atmayı" ve bir işlem yanlış olursa ve bir özel durum oluşursa, kuyrukta kalır. Hizmetler Ayrıca, daha sonraki bir zamanda işlemeyi yeniden denemek için iletileri "kilitler". ReceiveContext, kuyruktan kaldırılmadan önce iletiyi işlendiğinde "tamamlamak" için bir mekanizma sağlar. İletiler artık ağ üzerinden sıralara okunamaz ve yeniden yazılmaz ve tek tek iletiler, işleme sırasında farklı hizmet örneklerinde geri alınmaz.|  
|retryCycleDelay|Anında teslim edilmemiş bir iletiyi teslim etmeye çalışırken yeniden deneme döngüleri arasındaki gecikme süresini belirten bir TimeSpan değeri. Değer yalnızca en düşük bekleme süresini tanımlar çünkü gerçek bekleme süresi daha uzun olabilir. Varsayılan değer 00:30:00 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|Binding üstündeki SendTimeout|<xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|serializationFormat|İleti gövdesinin serileştirilmesi için kullanılan biçimi tanımlar. Bu öznitelik türü <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat> .|  
|timeToLive|İletilerin süre dolmadan önce ne kadar süreyle geçerli olduğunu belirten bir TimeSpan değeri ve atılacak ileti kuyruğuna yerleştirirsiniz. Varsayılan değer 1.00:00:00 ' dır.<br /><br /> Bu öznitelik, zaman duyarlı iletilerin, alıcı uygulamalar tarafından işlenmeden önce eski hale gelmemesini sağlamak üzere ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki ileti, süresi dolmaya yönelik olarak kabul edilir. Süre dolmayan iletiler, atılacak ileti sırası adlı özel bir kuyruğa gönderilir. Etkin olmayan ileti sırasının konumu, `DeadLetterQueue` özniteliğiyle veya uygun varsayılan değer ile belirlenir.|  
|useMsmqTracing|Bu bağlama tarafından işlenen iletilerin izlenip izlenmeyeceğini belirten bir Boole değeri. Varsayılan değer: `false`. İzleme etkinleştirildiğinde, ileti Message Queuing bilgisayara her ayrıldığında veya ulaştığında rapor iletileri oluşturulur ve rapor kuyruğuna gönderilir.|  
|useSourceJournal|Bu bağlama tarafından işlenen iletilerin kopyalarını belirten bir Boole değeri, kaynak günlüğünde depolanmalıdır. Varsayılan değer: `false`.<br /><br /> Bilgisayarın giden sırasının ayrılmasına sahip bir ileti kaydını tutmak isteyen sıraya alınmış uygulamalar iletileri bir günlük kuyruğuna kopyalayabilir. İleti, giden sırasından ayrıldığında ve iletinin hedef bilgisayarda alındığı bir bildirim alındıktan sonra iletinin bir kopyası gönderen bilgisayarın sistem günlüğü kuyruğunda tutulur.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Özniteliğe  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Xml|XML biçimi|  
|İkili|İkili biçim|  
|ActiveX|ActiveX biçimi|  
|ByteArray|Nesneyi bayt dizisine dizleştirir.|  
|Akış|Akış olarak biçimlendirilen gövde|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<security>](security-of-msmqintegrationbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement> .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu bağlama öğesi, Windows Communication Foundation (WCF) uygulamalarının COM, MSMQ Native API 'Ler veya ad alanında tanımlanan türler kullanan mevcut MSMQ uygulamalarından ileti göndermesini ve iletileri almasını sağlamak için kullanılabilir <xref:System.Messaging?displayProperty=nameWithType> . bu yapılandırma öğesini, kuyruğa yönelik yolları belirtmek, kesintileri aktarmak, iletilerin silinme ve kimlik doğrulamasının yapılıp yapılmayacağını belirlemek için kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamaları Ile Exchange iletileri](../../../wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <msmqIntegrationBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 deadLetterQueue="net.msmq://localhost/blah"
                 durable="true"
                 exactlyOnce="true"
                 maxReceivedMessageSize="1000"
                 maxImmediateRetries="11"
                 maxRetryCycles="12"
                 poisonMessageHandling="Disabled"
                 rejectAfterLastRetry="false"
                 retryCycleDelay="00:05:55"
                 timeToLive="00:11:11"
                 useSourceJournal="true"
                 useMsmqTracing="true"
                 serializationFormat="Binary">
          <security mode="None" />
        </binding>
      </msmqIntegrationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>
- [\<binding>](bindings.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
