---
title: İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: d3087021c717d6ee055a4a1f5332d9d259f06381
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289600"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma

Sıraya alınan iletiler teslim başarısız olabilir. Bu başarısız iletiler, teslim edilemeyen bir sıraya kaydedilir. Başarısız teslimat, ağ hataları, silinen bir kuyruk, tam sıra, kimlik doğrulama hatası veya zaman içinde teslim etme hatası gibi nedenlerle neden olabilir.  
  
 Alınan uygulama, zaman zaman bir süre sonra kuyruktan okunmayan sırada, sıradaki iletiler kuyrukta kalabilirler. Bu davranış zamana duyarlı iletiler için uygun olmayabilir. Zamana duyarlı iletiler, sıradaki bağlamada ayarlanan yaşam süresi (TTL) özelliğine sahiptir ve bu, iletilerin süresi dolmadan önce kuyrukta ne kadar süreyle kalabileceğini gösterir. Süre dolmayan iletiler, teslim edilemeyen ileti sırası adlı özel bir kuyruğa gönderilir. Ayrıca iletiler, bir kuyruk kotasının aşılması veya kimlik doğrulama hatası nedeniyle diğer nedenlerden dolayı atılacak bir sıraya alınabilir.  
  
 Genellikle, uygulamalar teslim edilemeyen ileti sırasından ve hata nedenlerinden iletileri okumak için maaş mantığı yazar. Dengeleme mantığı, hatanın nedenine bağlıdır. Örneğin, kimlik doğrulama hatası durumunda iletiyle bağlantılı sertifikayı düzeltebilir ve iletiyi yeniden gönderebilirsiniz. Hedef kuyruk kotasına ulaşıldığından, teslim başarısız olursa, kota sorununun çözümlendiğini umuyoruz.  
  
 Çoğu sıraya alma sisteminde, bu sistemdeki tüm başarısız iletilerin depolandığı sistem genelinde bir atılacak ileti sırası vardır. Message Queuing (MSMQ), iki sistem genelinde atılacak ileti sırası sağlar: işlemsel sıraya teslim edilemeyen iletileri depolayan ve işlemsel olmayan sıraya teslim edilemeyen iletileri depolayan, sistem genelinde çok sayıda atılacak bir sıra olmayan bir işlem sistem genelinde atılacak mektup kuyruğu. İki istemci iki farklı hizmete ileti gönderiyorsa ve bu nedenle WCF 'deki farklı kuyruklar, göndermek için aynı MSMQ hizmetini paylaşılıyorsa, sistem teslim edilemeyen ileti kuyruğunda ileti karışımı olması mümkündür. Bu her zaman en uygun değildir. Birkaç durumda (güvenlik, örneğin), bir istemcinin eski ileti sırasından başka bir istemcinin iletilerini okumasını istemeyebilirsiniz. Paylaşılan bir atılacak ileti sırası, istemcilerin gönderdikleri bir iletiyi bulmak için kuyruğa gözatmasını ve teslim edilemeyen ileti sırasındaki ileti sayısına bağlı olarak yüksek maliyetli olabilecek bir şekilde canlı olarak yapılmasını gerektirir. Bu nedenle, WCF `NetMsmqBinding` `MsmqIntegrationBinding,` ve Windows VISTA 'da MSMQ, özel bir atılacak mektup kuyruğu (bazen uygulamaya özgü atılacak mektup kuyruğu olarak adlandırılır) sağlar.  
  
 Özel atılacak mektup kuyruğu, iletileri göndermek için aynı MSMQ hizmetini paylaşan istemciler arasında yalıtım sağlar.  
  
 Windows Server 2003 ve Windows XP 'de Windows Communication Foundation (WCF), sıraya alınan tüm istemci uygulamaları için sistem genelinde bir atılacak ileti sırası sağlar. Windows Vista 'da WCF, her kuyruğa alınan istemci uygulaması için atılacak bir sıra sağlar.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Dead-Letter kuyruğunun kullanımını belirtme  

 Teslim edilemeyen bir sıra, gönderen uygulamanın kuyruk yöneticisidir. Bu, zaman aşımına uğradı veya başarısız aktarım ya da teslim olan iletileri depolar.  
  
 Bağlama, aşağıdaki atılacak ileti sırası özelliklerine sahiptir:  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Dead-Letter kuyruğundan Iletileri okuma  

 Eski bir ileti sırasından gelen iletileri okuyan bir uygulama, aşağıdaki küçük farklılıklar dışında bir uygulama kuyruğundan okuyan bir WCF hizmetine benzerdir:  
  
- Sistem işlem dışı ileti sırasından iletileri okumak için Tekdüzen Kaynak tanımlayıcısı (URI) şu biçimde olmalıdır: net. MSMQ://localhost/System $;D Eadxyasası.  
  
- Bir sistem işlem dışı teslim edilemeyen ileti sırasından iletileri okumak için URI şu biçimde olmalıdır: net. MSMQ://localhost/System $;D eadLetter.  
  
- Özel bir atılacak ileti sırasından iletileri okumak için URI şu biçimde olmalıdır: net. MSMQ://localhost/private/ \<*custom-dlq-name*> burada *Custom-DLQ-Name* özel atılacak ileti sırasının adıdır.  
  
 Kuyrukların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [hizmet uç noktaları ve sıra adresleme](service-endpoints-and-queue-addressing.md).  
  
 Alıcının WCF yığını, hizmetin iletideki adresle dinlediği adreslerle eşleşir. Adresler eşleşiyorsa ileti gönderilir; Aksi takdirde ileti gönderilir. Bu, atılacak ileti sırasındaki iletiler genellikle teslim edilemeyen ileti sırası hizmetine değil hizmete değinilmesi nedeniyle, atılacak ileti sırasından okurken soruna neden olabilir. Bu nedenle, atılacak ileti sırasından okuma hizmeti, yığının, kümeden `ServiceBehavior` bağımsız olarak kuyruktaki tüm iletileri eşleşmesini sağlayan bir adres filtresi yüklemelidir. Özellikle, `ServiceBehavior` <xref:System.ServiceModel.AddressFilterMode.Any> atılacak ileti sırasından iletileri okumak için parametresi ile bir olarak eklemeniz gerekir.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Dead-Letter sırasından zarar Iletisi Işleme  

 Zarar iletisi işleme, bazı koşullarla, atılacak ileti sıralarında kullanılabilir. Sistem kuyruklarından alt sıralar oluşturabilmeniz için, sistem atılacak ileti sırasından okurken `ReceiveErrorHandling` olarak ayarlanamaz `Move` . Özel bir atılacak mektup sırasından okuyorsanız, alt kuyruklara sahip olabilirsiniz ve bu nedenle, `Move` zarar iletisi için geçerli bir değerlendirme olduğunu unutmayın.  
  
 `ReceiveErrorHandling`, Olarak ayarlandığında `Reject` , özel atılacak mektup sırasından okurken, zarar iletisi sistem atılacak ileti kuyruğuna konur. Sistem teslim edilemeyen ileti sırasından okurken ileti bırakılır (temizlendi). MSMQ 'da bir sistem atılacak ileti sırasından reddetme, iletiyi bırakır (temizler).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir atılacak ileti sırasının nasıl oluşturulduğunu ve süre sonu iletileri işlemek için nasıl kullanılacağını gösterir. Örnek, [nasıl yapılır: WCF uç noktaları Ile sıraya alınmış Iletileri Exchange ile](how-to-exchange-queued-messages-with-wcf-endpoints.md)ilgili örneğe dayanır. Aşağıdaki örnek, her bir uygulama için bir atılacak ileti sırası kullanan sipariş işleme hizmetine istemci kodunun nasıl yazılacağını gösterir. Örnek ayrıca, teslim edilemeyen ileti sırasından iletileri nasıl işleyeceğini gösterir.  
  
 Aşağıda, her bir uygulama için atılacak ileti sırası belirten bir istemcinin kodu verilmiştir.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 İstemci yapılandırma dosyasının kodu aşağıda verilmiştir.  

 Aşağıda, bir hizmet işlem iletilerinin atılacak ileti sırasından kodu verilmiştir.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Aşağıda, atılacak ileti sırası hizmeti yapılandırma dosyasının kodu verilmiştir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklar Genel Bakış](queues-overview.md)
- [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Zehirli İleti İşleme](poison-message-handling.md)
