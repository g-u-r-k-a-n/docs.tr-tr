---
description: 'Daha fazla bilgi edinin: kapsamlar ile bulma örneği'
title: Kapsam ile Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: d2bddb943c5a71b480ac2ab1a436f12703465e9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726552"
---
# <a name="discovery-with-scopes-sample"></a>Kapsam ile Keşif Örneği

Bu örnek, keşfedilebilir uç noktaları kategorilere ayırmak için kapsamların nasıl kullanılacağını ve <xref:System.ServiceModel.Discovery.DiscoveryClient> uç noktalar için zaman uyumsuz bir arama yapmayı nasıl kullanacağınızı gösterir. Hizmette, bu örnek bir uç nokta bulma davranışı ekleyerek ve uç noktaya bir kapsam eklemek ve uç noktanın bulunabilirliğini denetlemek için kullanarak her bir uç nokta için bulmayı özelleştirmeyi gösterir. İstemcide, örnek, istemcilerinin ' a <xref:System.ServiceModel.Discovery.DiscoveryClient> kapsam ekleyerek kapsamları dahil etmek için arama parametrelerini nasıl oluşturup ayarlayaacağına dair bir süre boyunca gider <xref:System.ServiceModel.Discovery.FindCriteria> . Bu örnek ayrıca, bir sonlandırma ölçütü ekleyerek istemcilerin yanıtları nasıl kısıtlayabileceğini gösterir.

## <a name="service-features"></a>Hizmet özellikleri

Bu proje, bir öğesine eklenen iki hizmet uç noktasını gösterir <xref:System.ServiceModel.ServiceHost> . Her uç noktanın kendisiyle <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> ilişkili bir ilişkisi vardır. Bu davranış her iki uç nokta için URI kapsamları eklemek için kullanılır. Bu uç noktaların her birini ayırt etmek için kapsamlar kullanılır, böylelikle istemciler aramayı ince ayarlayabilirler. İkinci uç nokta için, özelliği olarak ayarlanarak bulunabilirliği devre dışı bırakılabilir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> `false` . Bu, bu uç noktayla ilişkili bulgu meta verilerinin herhangi bir bulma iletilerinin parçası olarak gönderilmemesini sağlar.

## <a name="client-features"></a>İstemci özellikleri

`FindCalculatorServiceAddress()`Yöntemi, ' nin nasıl kullanılacağını <xref:System.ServiceModel.Discovery.DiscoveryClient> ve <xref:System.ServiceModel.Discovery.FindCriteria> iki kısıtlama ile nasıl geçirileceğini gösterir. Ölçütlere bir kapsam eklenir ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özellik 1 olarak ayarlanır. Kapsam sonuçları yalnızca aynı kapsamı yayınlayan hizmetlerle sınırlandırır. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>1 olarak ayarlandığında, <xref:System.ServiceModel.Discovery.DiscoveryClient> en çok, 1 uç nokta için beklediği yanıtları sınırlar. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>Çağrı, zaman aşımına ulaşılıncaya veya bir uç nokta bulunana kadar iş parçacığını engelleyen zaman uyumlu bir işlemdir.

### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir. Daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md). Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Komut şu şekilde çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Çözümü derleyin.

3. Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.

4. İstemci yürütülebilir dosyasını çalıştırın. İstemcinin hizmeti bulabileceğini unutmayın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`
