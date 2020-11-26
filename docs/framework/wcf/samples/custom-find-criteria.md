---
title: Özel Bulma Ölçütleri
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 9271ae1ec4bbd555fe93df24c7d38f0f345a03ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241817"
---
# <a name="custom-find-criteria"></a>Özel Bulma Ölçütleri

Bu örnek, mantığı kullanarak özel bir kapsam eşleşmesi oluşturmayı ve özel bulma hizmetinin nasıl uygulanacağını gösterir. İstemciler, WCF bulmanın sistem tarafından sağlanan bul işlevselliğinin üzerine getirmek ve daha fazla derleme yapmak için özel kapsam eşleştirme işlevlerini kullanır. Bu örneğin kapsamakta olduğu senaryo aşağıdaki gibidir:  
  
1. İstemci, hesap makinesi hizmetini arıyor.  
  
2. İstemcisinin aramasını iyileştirmek için, istemcinin özel bir kapsam eşleştirme kuralı kullanması gerekir.  
  
3. Bu kurala göre, bir hizmet, uç noktası istemci tarafından belirtilen kapsamlarla eşleşiyorsa istemciye geri yanıt verir.  
  
## <a name="demonstrates"></a>Gösteriler  
  
- Özel bir keşif hizmeti oluşturuluyor.  
  
- Algoritmayla özel bir kapsam eşleşmesi uygulama.  
  
## <a name="discussion"></a>Tartışma  

 İstemci "veya" tür eşleştirme ölçütü arıyor. Bir hizmet, uç noktalardaki kapsamlar istemci tarafından belirtilen kapsamlardan biriyle eşleşiyorsa geri yanıt verir. Bu durumda, istemci aşağıdaki listede kapsamlardan herhangi birine sahip bir Hesaplayıcı hizmeti arıyor:  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Bunu gerçekleştirmek için, istemci, bir özel kapsam eşleştirme kuralını URI ile eşleştirerek bir özel kapsam eşleştirme kuralı kullanmaya yönlendirir. Özel kapsam eşleşmesini kolaylaştırmak için, hizmet özel kapsam eşleştirme kuralını anlayan ve ilişkili eşleşen mantığı uygulayan özel bir keşif hizmeti kullanmalıdır.  
  
 İstemci projesinde, Program.cs dosyasını açın. `ScopeMatchBy` `FindCriteria` Nesnesinin alanının belırlı bir URI olarak ayarlandığını unutmayın. Bu tanımlayıcı hizmete gönderilir. Hizmet bu kuralı anlamaz, istemcinin bul isteğini yoksayar.  
  
 Hizmet projesini açın. Özel bulma hizmetini uygulamak için üç dosya kullanılır:  
  
1. **AsyncResult.cs**: Bu, `AsyncResult` bulma yöntemleri tarafından gerekli olan uygulamasıdır.  
  
2. **CustomDiscoveryService.cs**: Bu dosya özel bulma hizmetini uygular. Uygulama, sınıfını genişletir <xref:System.ServiceModel.Discovery.DiscoveryService> ve gerekli yöntemleri geçersiz kılar. Yöntemi uygulamasına göz önünde edin <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> . Yöntemi, kuralla eşleşen özel kapsamın istemci tarafından belirtilmiş olup olmadığını denetler. Bu, istemcinin daha önce belirttiği özel URI 'dir. Özel kural belirtilmişse, "veya" Match mantığını uygulayan kod yolu izlenir.  
  
     Bu özel mantık, hizmetin sahip olduğu uç noktaların her birinde tüm kapsamlardan geçer. Uç noktanın kapsamlarından herhangi biri istemci tarafından sunulan kapsamlardan biriyle eşleşiyorsa, bulma hizmeti bu uç noktayı istemciye geri gönderilen yanıta ekler.  
  
3. **CustomDiscoveryExtension.cs**: Bulma hizmetini uygulamanın son adımı, özel bulma hizmetinin bu uygulamasını hizmet ana bilgisayarına bağlamak. Burada kullanılan yardımcı sınıf `CustomDiscoveryExtension` sınıfı. Bu sınıf, <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> sınıfını genişletir. Kullanıcı, yöntemi geçersiz kılmalıdır <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> . Bu durumda, yöntemi daha önce oluşturulmuş özel bulma hizmetinin bir örneğini döndürür. `PublishedEndpoints`<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, öğesine eklenen tüm uygulama uç noktalarını içeren bir ' dır <xref:System.ServiceModel.ServiceHost> . Özel keşif hizmeti, iç listesini doldurmak için bunu kullanır. Bir kullanıcı diğer uç nokta meta verilerini de ekleyebilir.  
  
 Son olarak, Program.cs öğesini açın. Her ikisinin de <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> `CustomDiscoveryExtension` konağa eklendiğini unutmayın. Bu işlem yapıldıktan ve konakta bulma iletilerinin alınacağı bir uç nokta varsa, uygulama özel bulma hizmetini kullanabilir.  
  
 İstemcinin adresini bilmeden hizmeti bulabildiğinin gözlemleyin.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Projeyi içeren çözümü açın.  
  
2. Projeyi derleyin.  
  
3. Hizmet uygulamasını çalıştırın.  
  
4. İstemci uygulamasını çalıştırın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
