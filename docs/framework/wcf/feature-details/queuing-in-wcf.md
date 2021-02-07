---
description: "Daha fazla bilgi edinin: WCF 'de kuyruğa alma"
title: WCF'de Kuyruğa Alma
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: 21ba3980d7ef5d043a1bf9fed03e0c98ea34a933
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733365"
---
# <a name="queuing-in-wcf"></a>WCF'de Kuyruğa Alma

Bu bölümde Windows Communication Foundation (WCF) ' de sıraya alınmış iletişimin nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="queues-as-a-wcf-transport-binding"></a>WCF Aktarım bağlaması olarak kuyruklar  

 WCF 'de, sözleşmelerin ne değiştirildiğini belirtir. Sözleşmeler, işe bağımlı veya uygulamaya özel ileti değişimlerdir. Bağlamalarda ileti alışverişi yapmak için kullanılan mekanizma (veya "nasıl") belirtilir. WCF 'deki bağlamalar ileti değişimi ayrıntılarını kapsüller. Bu kişiler, kullanıcının taşımanın çeşitli yönlerini veya bağlamaların temsil ettiği Protokolü denetlemesini sağlamak için yapılandırma alt 'lerini kullanıma sunar. WCF 'de kuyruğa alma, birçok sıraya alma uygulaması için büyük bir avantaj olan diğer tüm aktarım bağlamaları gibi davranır. Günümüzde, birçok sıraya alma uygulaması diğer uzak yordam çağrısı (RPC) stili dağıtılan uygulamalardan farklı şekilde yazılmıştır, bu da izlemenizi ve bakımını zorlaştırır. WCF ile, dağıtılmış bir uygulama yazma stili çok aynıdır, daha kolay bir şekilde izlenmesini ve bakımını yapmayı kolaylaştırır. Üstelik, Exchange mekanizmasını iş mantığından ayrı olarak düzenleme, bu da aktarımı yapılandırmak veya uygulamaya özel kodu etkilemeden değişiklikler yapmak kolaydır. Aşağıdaki şekilde, bir WCF hizmeti ve bir istemcinin bir aktarım olarak MSMQ kullanan bir yapısı gösterilmektedir.  
  
 ![Kuyruğa alınmış uygulama diyagramı](media/distributed-queue-figure.jpg "Dağıtılmış kuyruk-şekil")  
  
 Yukarıdaki şekilde görebileceğiniz gibi, istemci ve hizmet yalnızca uygulama semantiğini, yani, sözleşme ve uygulamayı tanımlamalıdır. Hizmet, tercih edilen ayarlarla sıraya alınmış bir bağlamayı yapılandırır. İstemci, hizmete bir WCF istemcisi oluşturmak ve hizmete ileti göndermek için kullanılacak bağlamaları açıklayan bir yapılandırma dosyası oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır. Bu nedenle, sıraya alınmış bir ileti göndermek için istemci bir WCF istemcisi başlatır ve üzerinde bir işlem çağırır. Bu, iletinin iletim kuyruğuna gönderilmesini ve hedef sıraya aktarılmasını sağlar. Sıraya alınan iletişimin tüm karmaşıklıkları, ileti gönderen ve alan uygulamadan gizlenir.  
  
 WCF 'de sıraya alınan bağlama hakkında uyarılar şunlardır:  
  
- WCF 'deki varsayılan sıraya alınmış bağlama kuyrukları kullanarak çift yönlü iletişimi desteklemediğinden tüm hizmet işlemleri tek yönlü olmalıdır. İki yönlü iletişim örneği ([Iki yönlü iletişim](../samples/two-way-communication.md)) kuyrukları kullanarak çift yönlü iletişimi uygulamak için 2 1 yönlü sözleşmeleri nasıl kullanacağınızı gösterir.  
  
- Meta veri değişimi kullanan bir WCF istemcisi oluşturmak için, hizmette ek bir HTTP uç noktası gerekir, böylece doğrudan WCF istemcisini oluşturacak şekilde sorgulanabilir ve kuyruğa alınmış iletişimi uygun şekilde yapılandırmak için bağlama bilgilerini elde edebilirsiniz.  
  
- Sıraya alınan bağlamaya bağlı olarak, WCF dışında ek yapılandırma gerekir. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> WCF ile birlikte gelen sınıf, bağlamaları yapılandırmanızı ve Message Queuing (MSMQ) en az yapılandırmayı gerektirir.  
  
 Aşağıdaki bölümlerde, MSMQ 'YU temel alan WCF ile birlikte gönderilen belirli sıraya alınmış bağlamalar açıklanır.  
  
### <a name="msmq"></a>MSMQ  

 WCF 'deki sıraya alınan aktarım, kuyruğa alınmış iletişimi için MSMQ kullanır.  
  
 MSMQ, Windows ile isteğe bağlı bir bileşen olarak gelir ve NT hizmeti olarak çalışır. İletim kuyruğuna iletim ve hedef sırada teslim için iletileri yakalar. MSMQ kuyruğu yöneticileri, iletilerin iletimde kaybedilmemesi için güvenilir bir ileti aktarımı Protokolü uygular. Protokol yerel veya SOAP tabanlı olabilir; örneğin SOAP güvenilir Ileti Protokolü (SRMP).  
  
 MSMQ 'da kuyruklar işlem veya işlem dışı olabilir. İşlemsel bir kuyruk, iletilerin bir işlem halinde yakalanıp teslim edilmesini ve sonra kuyrukta durda depolanmasını sağlar. İşlem kuyruğuna gönderilen iletiler, sırayla tam olarak bir kez aktarılır. Geçici ve dayanıklı iletileri göndermek için işlemsel olmayan bir kuyruk kullanabilirsiniz. İşlemsel olmayan bir sıraya gönderilen ileti, güvenilir aktarım kesintileri gerçekleştirmez; Bu nedenle iletiler kaybolabilir.  
  
 MSMQ kuyrukları, Active Directory dizin hizmetiyle kaydedilmiş bir Windows kimliği kullanılarak da güvenli hale getirilir. MSMQ yüklenirken, bilgisayarın bir Windows etki alanı ağının parçası olmasını gerektiren Active Directory tümleştirme yükleyebilirsiniz.  
  
 MSMQ hakkında daha fazla bilgi için bkz. [yükleme Message Queuing (MSMQ)](../samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  

 , [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md) Kuyruğa alınan bağlama WCF, MSMQ kullanarak iletişim kurmak için ıkı WCF uç noktası sağlar. Bu nedenle, bağlama, MSMQ 'ya özgü özellikleri gösterir. Ancak, tüm MSMQ özellikleri ve özellikleri içinde gösterilmez `NetMsmqBinding` . Compact, `NetMsmqBinding` çoğu müşterinin yeterince bulması gereken en uygun özellikler kümesiyle tasarlanmıştır.  
  
 , Ana `NetMsmqBinding` sıraya alınan temel sıraya alma kavramlarını, bu nedenle bağlamalardaki Özellikler biçiminde bildirimler. Bu özellikler sırasıyla MSMQ ile iletişim kurar ve iletileri nasıl aktaracağınızla iletişim kurabilir. Özellik kategorilerinin bir tartışması aşağıdaki bölümlerde verilmiştir. Daha fazla bilgi için, belirli özellikleri daha tamamen tanımlayan kavramsal konulara bakın.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce ve dayanıklı Özellikler  

 `ExactlyOnce`Ve `Durable` Özellikleri, iletilerin kuyruklar arasında nasıl aktarılacağını etkiler:  
  
- `ExactlyOnce`: `true` (Varsayılan) olarak ayarlandığında, kuyruğa alınan kanal, teslim edildiğinde iletinin yinelenmemesini sağlar. Ayrıca iletinin kaybolmamasını de sağlar. İleti teslim edilemez veya ileti teslim edilmeden önce Time-To yaşam süresi dolarsa, teslim hatası nedeni ile birlikte başarısız ileti teslim edilemeyen bir sıraya kaydedilir. Olarak ayarlandığında `false` , kuyruğa alınan kanal iletiyi aktarma çabaları yapar. Bu durumda, isteğe bağlı olarak bir atılacak ileti sırası seçebilirsiniz.  
  
- `Durable:``true`(Varsayılan) olarak ayarlandığında, sıraya alınan kanal MSMQ 'nun iletiyi diskte durda depoladığını sağlar. Bu nedenle, MSMQ hizmeti durdurulup yeniden başlatıldığında, diskteki iletiler hedef sıraya aktarılır veya hizmete teslim edilir. Olarak ayarlandığında `false` , iletiler geçici depoda depolanır ve MSMQ hizmetini durdurup yeniden başlatırken kaybedilir.  
  
 `ExactlyOnce`Güvenilir aktarım için, MSMQ kuyruğun işlem olmasını gerektirir. Ayrıca, MSMQ, işlem sırasından okumak için bir işlem gerektirir. Bu şekilde kullandığınızda, olarak `NetMsmqBinding` ayarlandığında ileti göndermek veya almak için bir işlem gerektiğini unutmayın `ExactlyOnce` `true` . Benzer şekilde, MSMQ, ne zaman `ExactlyOnce` `false` ve geçici mesajlaşma için olduğu gibi en iyi çaba kesintileri için kuyruğun işlem dışı olmasını gerektirir. Bu nedenle, `ExactlyOnce` `false` veya dayanıklı olarak ayarlandığında `false` , işlem kullanarak gönderilemez veya alamazsınız.  
  
> [!NOTE]
> Bağlamalardaki ayarlara bağlı olarak doğru sıranın (işlem veya işlem olmayan) oluşturulduğundan emin olun. `ExactlyOnce`İse `true` , bir işlem kuyruğu kullanın; Aksi takdirde, işlemsel olmayan bir kuyruk kullanın.  
  
#### <a name="dead-letter-queue-properties"></a>Dead-Letter kuyruğu özellikleri  

 Teslim edilemeyen iletileri depolamak için atılacak mektup kuyruğu kullanılır. Kullanıcı, iletileri atılacak ileti sırasından okuyan telafi mantığını yazabilir.  
  
 Birçok sıraya alma sistemi, sistem genelinde atılacak bir sıra için sağlanır. MSMQ, işlemsel olmayan sıralara teslim edilemeyen iletiler için sistem genelinde, işlem dışı bir atılacak ileti sırası ve işlem sıralarına teslim edilemeyen iletiler için sistem genelinde bir işlem atılacak mektup sırası sağlar.  
  
 Farklı hedef sıralara ileti gönderen birden çok istemci MSMQ hizmetini paylaşıyorsa, istemciler tarafından gönderilen tüm iletiler aynı atılacak ileti kuyruğuna gider. Bu her zaman tercih edilmez. Windows Vista 'daki WCF ve MSMQ, daha iyi yalıtım için kullanıcının teslim edilemeyen iletileri depolamak üzere belirtebileceğiniz özel bir atılacak mektup kuyruğu (veya uygulamaya özel atılacak ileti sırası) sağlar. Bu nedenle, farklı istemciler aynı atılacak ileti sırasını paylaşmaz.  
  
 Bağlama, ilgilendiğiniz iki özelliğe sahiptir:  
  
- `DeadLetterQueue`: Bu özellik, bir atılacak ileti sırasının istenip istenmediğini belirten bir numaralandırmadır. Sabit Listesi istenirse, atılacak ileti sırası türünü de içerir. Değerleri `None` , `System` , ve `Custom` . Bu özelliklerin yorumu hakkında daha fazla bilgi için bkz. [Ileti aktarımı başarısızlıklarını işlemek için Dead-Letter kuyrukları kullanma](using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue`: Bu özellik, uygulamaya özel atılacak mektup sırasının Tekdüzen Kaynak tanımlayıcısı (URI) adresidir. Bu gereklidir `DeadLetterQueue` .`Custom` seçilir.  
  
#### <a name="poison-message-handling-properties"></a>Zarar Iletisi Işleme özellikleri  

 Hizmet bir işlem altındaki hedef sıradan iletileri okuduğunda, hizmet çeşitli nedenlerle iletiyi işleyemeyebilir. İleti daha sonra tekrar okumak üzere kuyruğa geri konur. Sürekli başarısız olan iletilerle uğraşmak için, bağlamada bir Poison-Message işleme özelliği yapılandırılabilir. Dört özellik vardır: `ReceiveRetryCount` ,, `MaxRetryCycles` `RetryCycleDelay` , ve `ReceiveErrorHandling` . Bu özellikler hakkında daha fazla bilgi için bkz. [zehirli Ileti işleme](poison-message-handling.md).  
  
#### <a name="security-properties"></a>Güvenlik özellikleri  

 MSMQ, bir kuyruktaki erişim denetim listeleri (ACL 'Ler) veya kimliği doğrulanmış iletiler gönderme gibi kendi güvenlik modelini kullanıma sunar. , `NetMsmqBinding` Bu güvenlik özelliklerini taşıma güvenlik ayarlarının bir parçası olarak kullanıma sunar. Aktarım güvenliği için bağlamada iki özellik vardır: `MsmqAuthenticationMode` ve `MsmqProtectionLevel` . Bu özelliklerdeki ayarlar MSMQ 'nun nasıl yapılandırıldığına bağlıdır. Daha fazla bilgi için bkz. [Aktarım güvenliğini kullanarak Iletileri güvenli hale getirme](securing-messages-using-transport-security.md).  
  
 Aktarım güvenliğine ek olarak, gerçek SOAP iletisinin kendisi de ileti güvenliği kullanılarak güvenliği sağlanmış olabilir. Daha fazla bilgi için bkz. [Ileti güvenliği kullanarak Iletileri güvenli hale getirme](securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` Ayrıca iki özelliği de kullanıma `MsmqEncryptionAlgorithm` sunar `MsmqHashAlgorithm` . Bunlar, iletilerin sıraya göre aktarım şifrelemesini ve imzaların karmasını seçmek için farklı algoritmaların numaralandırmalardır.  
  
#### <a name="other-properties"></a>Diğer özellikler  

 Önceki özelliklere ek olarak, bağlamada kullanıma sunulan diğer MSMQ 'ya özgü özellikler şunlardır:  
  
- `UseSourceJournal`: Kaynak günlük kaydı 'nın açık olduğunu belirten bir özellik. Kaynak günlük kaydı, iletim sırasından başarıyla iletilmiş iletileri izlemeye devam eden bir MSMQ özelliğidir.  
  
- `UseMsmqTracing`: MSMQ izlemenin açık olduğunu belirten bir özellik. MSMQ izleme, bir ileti MSMQ kuyruğu Yöneticisi barındıran bir makineye ayrıldığında veya ulaştığında rapor kuyruğuna rapor iletileri gönderir.  
  
- `QueueTransferProtocol`: Kuyruk-kuyruk ileti aktarımları için kullanılacak protokol numaralandırması. MSMQ, yerel bir kuyruk-sıraya Aktarım Protokolü ve SOAP Güvenilir Mesajlaşma Protokolü (SRMP) adlı SOAP tabanlı bir protokol uygular. Queuequeue aktarımları için HTTP taşıması kullanılırken SRMP kullanılır. , Kuyruk-kuyruk aktarımları için HTTPS kullanılırken SRMP güvenli kullanılır.  
  
- `UseActiveDirectory`: Active Directory kuyruk adresi çözümlemesi için kullanılması gerekip gerekmediğini belirten bir Boole değeri. Bu, varsayılan olarak kapalıdır. Daha fazla bilgi için bkz. [hizmet uç noktaları ve sıra adresleme](service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  

 , `MsmqIntegrationBinding` BIR WCF uç noktasının C, C++, com veya System. Messaging API 'lerinde yazılmış mevcut BIR MSMQ uygulamasıyla iletişim kurmasını istediğinizde kullanılır.  
  
 Bağlama özellikleri, ile aynıdır `NetMsmqBinding` . Ancak, aşağıdaki farklar geçerlidir:  
  
- İçin işlem sözleşmesinin, tür `MsmqIntegrationBinding` <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> parametresinin gövde türü olduğu tek bir parametre türünde alınması kısıtlıdır.  
  
- MSMQ yerel ileti özelliklerinin çoğu kullanım için ' de kullanıma sunulur <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> .  
  
- İleti gövdesinin serileştirilmesi ve serisini kaldırma konusunda yardımcı olmak için, XML ve ActiveX gibi serileştiriciler sağlanır.  
  
### <a name="sample-code"></a>Örnek Kod  

 MSMQ kullanan WCF hizmetleri yazma hakkında adım adım yönergeler için aşağıdaki konulara bakın:  
  
- [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 WCF 'de MSMQ kullanımını gösteren tamamlanmış bir kod örneği için aşağıdaki konulara bakın:  
  
- [İşlem Gerçekleştirilmiş MSMQ Bağlama](../samples/transacted-msmq-binding.md)  
  
- [Geçici Kuyruğa Alınmış İletişim](../samples/volatile-queued-communication.md)  
  
- [Teslim Edilemeyen İletiler Sırası](../samples/dead-letter-queues.md)  
  
- [Oturumlar ve Kuyruklar](../samples/sessions-and-queues.md)  
  
- [Çift Yönlü İletişim](../samples/two-way-communication.md)
  
- [SRMP](../samples/srmp.md)  
  
- [İleti Kuyruğa Alma ile İleti Güvenliği](../samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Uç Noktaları ve Kuyruk İşleme](service-endpoints-and-queue-addressing.md)
- [Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma](web-hosting-a-queued-application.md)
