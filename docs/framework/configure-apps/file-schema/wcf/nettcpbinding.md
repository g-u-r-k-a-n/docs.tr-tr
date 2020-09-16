---
title: <netTcpBinding>
description: Yalnızca TCP kullanan WCF çapraz makine iletişimi için tasarlanan güvenli, güvenilir ve iyileştirilmiş bir bağlamayı temsil eder. Güvenilir Mesajlaşma varsayılan olarak kapalıdır.
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: a366b26d87c8796822e4fbbb2001823c116f2629
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556134"
---
# \<netTcpBinding>

Makineler arası iletişim için güvenli, güvenilir ve iyileştirilmiş bir bağlama belirtir. Varsayılan olarak, ileti güvenliği ve kimlik doğrulaması, ileti teslimi için TCP ve ikili ileti kodlaması için Windows güvenliği ile bir çalışma zamanı iletişim yığını oluşturur.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|`hostNameComparisonMode`|URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür. Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.|  
|`listenBacklog`|Dinleyicide kabul edilmesini bekleyen kanal sayısı üst sınırını belirten pozitif bir tamsayı. Bu sınırın üzerinde olan bağlantılar, sınırın altındaki boşluk kullanılabilir olana kadar sıraya alınır. `connectionTimeout`Öznitelik, bir bağlantı özel durumu oluşturmadan önce istemcinin bağlanması için bekleyeceği süreyi sınırlandırır. Varsayılan değer 10 ' dur.|  
|`maxBufferPoolSize`|Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı. Varsayılan değer 512 * 1024 bayttır. Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır. Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır. Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz. Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.|  
|`maxBufferSize`|İletileri bellekte depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.<br /><br /> `transferMode`Özniteliği öğesine eşitse `Buffered` , bu öznitelik `maxReceivedMessageSize` öznitelik değerine eşit olmalıdır.<br /><br /> `transferMode`Özniteliği öğesine eşitse `Streamed` , bu öznitelik öznitelik değerinden daha fazla olamaz `maxReceivedMessageSize` ve en azından üst bilgilerin boyutu olmalıdır.<br /><br /> Varsayılan değer 65536 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|`maxConnections`|Hizmetin oluşturulacağı/kabul edeceği en fazla giden ve gelen bağlantı sayısını belirten bir tamsayı. Gelen ve giden bağlantılar, bu öznitelik tarafından belirtilen ayrı bir sınıra göre sayılır.<br /><br /> Sınırın üzerindeki gelen bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.<br /><br /> Sınırın üzerindeki giden bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.<br /><br /> Varsayılan değer 10 ' dur.|  
|`maxReceivedMessageSize`|Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı. Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir.|  
|`name`|Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|`openTimeout`|Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|`portSharingEnabled`|Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boolean değer. Bu ise `false` , her bağlama kendi özel bağlantı noktasını kullanır. İstemciler etkilenmediğinden, bu ayar yalnızca hizmetler için geçerlidir.|  
|`receiveTimeout`|<xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:10:00 ' dir.|  
|`sendTimeout`|<xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|`transactionFlow`|Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri. Varsayılan değer: `false`.|  
|`transactionProtocol`|Bu bağlama ile kullanılacak işlem protokolünü belirtir. Geçerli değerler şunlardır<br /><br /> -OleTransactions<br />- WSAtomicTransactionOctober2004<br /><br /> Varsayılan değer OleTransactions 'dir. Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol> .|  
|`transferMode`|<xref:System.ServiceModel.TransferMode>İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirten bir değer.|  
  
### <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.NetTcpSecurityElement> .|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar

Bu bağlama, aktarım güvenliği, ileti teslimi için TCP ve ikili ileti kodlaması kullanan, varsayılan olarak bir çalışma zamanı iletişim yığını üretir. Bu bağlama, bir Intranet üzerinden iletişim kurmak için uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanmış seçenektir.  
  
 İçin varsayılan yapılandırma `netTcpBinding` , tarafından sağlanmış yapılandırmadan daha hızlıdır `wsHttpBinding` , ancak yalnızca WCF iletişimi amaçlıdır. Güvenlik davranışı, isteğe bağlı özniteliği kullanılarak yapılandırılabilir `securityMode` . WS-ReliableMessaging kullanımı, isteğe bağlı özniteliği kullanılarak yapılandırılabilir `reliableSessionEnabled` . Ancak güvenilir mesajlaşma varsayılan olarak kapalıdır. Daha genel olarak, ve gibi HTTP sistem tarafından sağlanmış bağlamalar `wsHttpBinding` , `basicHttpBinding` Varsayılan olarak ' ı açmak üzere yapılandırılmıştır, ancak `netTcpBinding` Örneğin, WS-* belirtimlerinden biri için, destek almak için kabul etmeniz gerekir. Bu, TCP varsayılan yapılandırmasının, HTTP bağlamaları için varsayılan olarak yapılandırılanlardan farklı uç noktalar arasında ileti alışverişi yaparken daha hızlı olduğu anlamına gelir.  
  
## <a name="example"></a>Örnek

Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir. Bağlama türü, `binding` öğesinin özniteliğinde belirtilir `<endpoint>` . NetTcpBinding bağlamasını yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir. Uç noktanın bağlama yapılandırmasına bir özniteliğiyle başvurması gerekir `bindingConfiguration` . Aşağıdaki örnekte, bir bağlama yapılandırması tanımlanmıştır.  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
