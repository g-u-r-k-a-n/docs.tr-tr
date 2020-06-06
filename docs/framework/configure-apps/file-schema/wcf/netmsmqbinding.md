---
title: <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: 7456c6373c64e07b73e15e7e2bb229dce4032121
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140738"
---
# \<netMsmqBinding>
Makineler arası iletişim için uygun bir sıraya alınmış bağlamayı tanımlar.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netMsmqBinding>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netMsmqBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxBufferPoolSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           poisonMessageHandling="Disabled/EnabledIfSupported"
           queueTransferProtocol="Native/Srmp/SrmpSecure"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           rejectAfterLastRetry="Boolean"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           timeToLive="TimeSpan"
           useActiveDirectory="Boolean"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/InfoCard" />
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|`customDeadLetterQueue`|Zaman aşımına uğradı veya başarısız aktarım ya da teslimi olan iletilerin yerleştirildiği, uygulama başına atılacak mektup sırasının konumunu içeren bir URI.<br /><br /> Sahipsiz sıra, teslim edilemeyen süre dolmayan iletiler için gönderen uygulamanın kuyruk yöneticisinde bir sıradır.<br /><br /> Tarafından belirtilen URI 'nin <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> net. MSMQ şemasını kullanması gerekir.|  
|`deadLetterQueue`|<xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>Varsa, ne tür bir atılacak ileti sırasının kullanılacağını belirten bir değer.<br /><br /> Atılacak ileti sırası, uygulamaya teslim edilemeyen iletilerin aktarılacağı yerdir.<br /><br /> Güvence gerektiren iletiler `exactlyOnce` (yani, `exactlyOnce` özniteliği olarak ayarlanır `true` ) için, bu öznitelik MSMQ 'daki sistem genelinde işlem atılacak ileti sırasını varsayılan olarak belirler.<br /><br /> Herhangi bir değer gerektirmeyen iletiler için, bu öznitelik varsayılan olarak olur `null` .|  
|`durable`|İletinin kuyrukta dayanıklı mi yoksa geçici mi olduğunu belirten bir Boole değeri. Kalıcı bir ileti bir sıra Yöneticisi kilitlenmesiyle çalışır, geçici bir ileti değildir. Geçici iletiler, uygulamalar daha düşük gecikme süresi gerektirdiğinde ve zaman zaman kaybolmuş iletileri kabul edebildiği durumlarda faydalıdır. `exactlyOnce`Özniteliği olarak ayarlandıysa `true` , iletilerin dayanıklı olması gerekir. Varsayılan değer: `true`.|  
|`exactlyOnce`|Bu bağlama tarafından işlenen her bir iletinin yalnızca bir kez teslim edilip edilmediğini gösteren Boolean bir değer. Ardından, gönderen teslim arızalarına göre bilgilendirilir. Ne zaman, `durable` `false` Bu öznitelik yok sayılır ve iletiler teslim güvencesi olmadan aktarılır. Varsayılan değer: `true`. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı. Varsayılan değer 8 ' dir.|  
|`maxReceivedMessageSize`|Bu bağlama tarafından işlenen üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı. Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir. İleti boyutu sınırı, hizmet reddi (DoS) saldırılarına maruz kalma olasılığını sınırlandırmaya yöneliktir.|  
|`maxRetryCycles`|Zarar iletisi algılama özelliği tarafından kullanılan yeniden deneme döngüsü sayısını belirten bir tamsayı. Tüm Döngülerde tüm teslim denemeleri başarısız olduğunda bir ileti bir zarar iletisi haline gelir. Varsayılan değer 3 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Gerekli öznitelik. Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|`openTimeout`|Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|`QueueTransferProtocol`|<xref:System.ServiceModel.QueueTransferProtocol>Bu bağlamanın kullandığı sıraya alınmış iletişim kanalı aktarımını belirten geçerli bir değer. MSMQ, SOAP Güvenilir Mesajlaşma Protokolü kullanırken Active Directory adreslemeyi desteklemez. Bu nedenle, bu özniteliği özniteliği olarak ayarlandığında veya olarak ayarlamanız gerekir `Srmp` `Srmps` `useActiveDirectory` `true` .|  
|`receiveErrorHandling`|<xref:System.ServiceModel.ReceiveErrorHandling>Zebilen ve dağıtılabilir iletilerin nasıl işleneceğini belirten bir değer.|  
|`receiveRetryCount`|Sıra yöneticisinin yeniden deneme kuyruğuna aktarmadan önce bir ileti göndermek için kaç kez denemesi gerektiğini belirten bir tamsayı.|  
|`receiveTimeout`|<xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:10:00 ' dir.|  
|`retryCycleDelay`|Anında teslim edilmemiş bir iletiyi teslim etmeye çalışırken yeniden deneme döngüleri arasındaki gecikme süresini belirten bir TimeSpan değeri. Değer yalnızca en düşük bekleme süresini tanımlar çünkü gerçek bekleme süresi daha uzun olabilir. Varsayılan değer 00:10:00 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|<xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|`timeToLive`|İletilerin süre dolmadan önce ne kadar süreyle geçerli olduğunu belirten bir TimeSpan değeri ve atılacak ileti kuyruğuna yerleştirirsiniz. Varsayılan değer 1.00:00:00 ' dır.<br /><br /> Bu öznitelik, zaman duyarlı iletilerin, alıcı uygulamalar tarafından işlenmeden önce eski hale gelmemesini sağlamak üzere ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki ileti, süresi dolmaya yönelik olarak kabul edilir. Süre dolmayan iletiler, atılacak ileti sırası adlı özel bir kuyruğa gönderilir. Etkin olmayan ileti sırasının konumu, `DeadLetterQueue` özniteliğiyle veya uygun varsayılan değer ile belirlenir.|  
|`usingActiveDirectory`|Sıra adreslerinin Active Directory kullanılarak dönüştürülmesi gerekip gerekmediğini belirten bir Boole değeri.<br /><br /> MSMQ kuyruğu adresleri, yol adlarından veya doğrudan biçim adlarından oluşabilir. Doğrudan biçim adıyla, MSMQ, DNS, NetBIOS veya IP kullanarak bilgisayar adını çözer. Bir yol adıyla, MSMQ Active Directory kullanarak bilgisayar adını çözer.<br /><br /> Varsayılan olarak, Windows Communication Foundation (WCF) sıraya alınan aktarım, bir ileti sırasının URI 'sini doğrudan biçim adına dönüştürür. `UseActiveDirectory`Özelliği true olarak ayarlayarak, bir uygulama sıraya alınan TAŞıMANıN DNS, NetBIOS veya IP yerine Active Directory kullanarak bilgisayar adını çözmesi gerektiğini belirtebilir.|  
|`useMsmqTracing`|Bu bağlama tarafından işlenen iletilerin izlenip izlenmeyeceğini belirten bir Boole değeri. Varsayılan değer: `false`. İzleme etkinleştirildiğinde, ileti Message Queuing bilgisayara her ayrıldığında veya ulaştığında rapor iletileri oluşturulur ve rapor kuyruğuna gönderilir.|  
|`useSourceJournal`|Bu bağlama tarafından işlenen iletilerin kopyalarını belirten bir Boole değeri, kaynak günlüğünde depolanmalıdır. Varsayılan değer: `false`.<br /><br /> Bilgisayarın giden sırasının ayrılmasına sahip bir ileti kaydını tutmak isteyen sıraya alınmış uygulamalar iletileri bir günlük kuyruğuna kopyalayabilir. İleti, giden sırasından ayrıldığında ve iletinin hedef bilgisayarda alındığı bir bildirim alındıktan sonra iletinin bir kopyası gönderen bilgisayarın sistem günlüğü kuyruğunda tutulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .|  
|[\<security>](security-of-netmsmqbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement> .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `netMsmqBinding`Bağlama, bir taşıma olarak Microsoft Message Queuing (MSMQ) kullanarak sıraya alma desteği sağlar ve gevşek olarak bağlanmış uygulamalar, hata yalıtımı, yük dengeleme ve bağlantısı kesik işlemler için destek sağlar. Bu özelliklerle ilgili bir tartışma için bkz. [WCF 'de kuyruklar](../../../wcf/feature-details/queues-in-wcf.md).  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netMsmqBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 deadLetterQueue="net.msmq://localhost/blah"
                 durable="true"
                 exactlyOnce="true"
                 maxReceivedMessageSize="1000"
                 maxRetries="11"
                 maxRetryCycles="12"
                 poisonMessageHandling="Disabled"
                 rejectAfterLastRetry="false"
                 retryCycleDelay="00:05:55"
                 timeToLive="00:11:11"
                 sourceJournal="true"
                 useMsmqTracing="true"
                 useActiveDirectory="true">
          <security>
            <message clientCredentialType="Windows" />
          </security>
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>
- [\<binding>](bindings.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
