---
title: Keşif Güvenliği Örneği
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: 0957e8ddaee99e60b205c92319dc2c61e2ab007a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292642"
---
# <a name="discovery-security-sample"></a>Keşif Güvenliği Örneği

Bulma belirtimi, bulma işlemine katılan uç noktaların güvenli olmasını gerektirmez. Bulma iletilerini güvenlikle birlikte geliştirmek, çeşitli saldırı türlerini azaltır (ileti değişikliği, hizmet reddi, yeniden kimlik sahtekarlığı). Bu örnek, sıkıştırılmış imza biçimini kullanarak ileti imzalarını hesaplayan ve doğrulayan özel kanallar uygular (WS-Discovery belirtiminin 8,2 bölümünde açıklanmıştır). Örnek, hem [2005 bulma belirtimini](http://specs.xmlsoap.org/ws/2005/04/discovery/ws-discovery.pdf) hem de [1,1 sürümünü](http://docs.oasis-open.org/ws-dd/discovery/1.1/cs-01/wsdd-discovery-1.1-spec-cs-01.pdf)destekler.  
  
 Özel kanal, bulma ve duyuru uç noktaları için mevcut kanal yığınının üzerine uygulanır. Bu şekilde, gönderilen her ileti için bir imza üst bilgisi uygulanır. İmza, alınan iletilerde doğrulanır ve eşleşmediği zaman veya iletilerde imza yoksa iletiler bırakılır. İletileri imzalamak ve doğrulamak için, örnek sertifikaları kullanır.  
  
## <a name="discussion"></a>Tartışma  

 WCF genişletilebilir ve kullanıcılara kanalları istediğiniz gibi özelleştirme olasılığa izin verir. Örnek, güvenli kanallar oluşturan bir bulgu güvenli bağlama öğesi uygular. Güvenli kanallar, ileti imzalarını uygular ve doğrular ve geçerli yığının üzerine uygulanır.  
  
 Güvenli bağlama öğesi, güvenli kanal fabrikaları ve kanal dinleyicileri oluşturur.  
  
## <a name="secure-channel-factory"></a>Güvenli kanal fabrikası  

 Güvenli kanal fabrikası, ileti üst bilgilerine bir küçük imza ekleyen çıkış veya çift yönlü kanallar oluşturur. Sıkıştırılmış imza biçimi kullanılan iletileri olabildiğince küçük tutmak için. Bir Compact imzasının yapısı aşağıdaki örnekte gösterilmiştir.  
  
```xml  
<d:Security ... >
  [<d:Sig Scheme="xs:anyURI"
         [KeyId="xs:base64Binary"]?  
          Refs="..."  
         [PrefixList]="xs:NMTOKENS"
          Sig="xs:base64Binary"
          ... />]?  
  ...
</d:Security>  
```  
  
> [!NOTE]
> , `PrefixList` 2008 bulma sürümü protokolüne eklenmiştir.  
  
 İmzayı hesaplamak için, örnek genişletilmiş imza öğelerini belirler. `SignedInfo` `ds` WS-Discovery belirtiminin gerektirdiği şekilde ad alanı öneki KULLANıLARAK bir XML imzası () oluşturulur. Bulma ve adresleme ad alanlarındaki gövdeye ve tüm üst bilgilere imza içinde başvuruluyor, bu nedenle üzerinde değişiklik yapılamaz. Başvurulan her öğe, dışlamalı kurallı kullanım () kullanılarak dönüştürülür <http://www.w3.org/2001/10/xml-exc-c14n#> ve ardından BIR SHA-1 Özet değeri hesaplanır ( <http://www.w3.org/2000/09/xmldsig#sha1> ). Başvurulan tüm öğelere ve bunların Özet değerlerine göre imza değeri, RSA algoritması () kullanılarak hesaplanır <http://www.w3.org/2000/09/xmldsig#rsa-sha1> .  
  
 İletiler, istemci tarafından belirtilen sertifikayla imzalanır. Bağlama öğesi oluşturulduğunda depo konumu, ad ve sertifika konu adı belirtilmelidir. Sıkıştırma imzasında, imzalama belirtecinin `KeyId` anahtar tanımlayıcısını temsil eder ve imzalama belirtecinin konu anahtar tanımlayıcısı (kayak) veya imza belirtecinin ortak anahtarının BIR SHA-1 karması vardır.  
  
## <a name="secure-channel-listener"></a>Güvenli kanal dinleyicisi  

 Güvenli kanal dinleyicisi, alınan iletilerde sıkıştırılmış imzayı doğrulayan giriş veya çift yönlü kanallar oluşturur. İmzayı doğrulamak için, `KeyId` iletiye iliştirilmiş, belirtilen depodan bir sertifika seçmek için kullanılan sıkıştır imzasında belirtilen. İletinin imzası yoksa veya imza denetimi başarısız olursa iletiler bırakılır. Güvenli bağlamayı kullanmak için örnek, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> eklenen bulma güvenli bağlama öğesi ile özel ve oluşturan bir fabrika tanımlar. Bu güvenli uç noktalar, bulma duyurusu dinleyicileri ve keşfedilebilir hizmetlerde kullanılabilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntılar  

 Örnek, bir kitaplık ve 4 konsol uygulaması içerir:
  
- **DiscoverySecurityChannels**: güvenli bağlamayı kullanıma sunan bir kitaplık. Kitaplık, giden/gelen iletiler için sıkıştırılmış imzayı hesaplar ve doğrular.  
  
- **Hizmet**: kendi kendine barındırılan bir hizmet olan icalbir hizmet sözleşmesi 'ni kullanıma sunma. Hizmet bulunabilir olarak işaretlendi. Kullanıcı, sertifika için depolama konumunu ve adı ve konu adını ya da diğer benzersiz tanımlayıcıyı ve istemci sertifikalarının bulunduğu mağazayı (gelen iletiler için imzayı denetlemek için kullanılan sertifikalar) belirterek iletileri imzalamak için kullanılan sertifikanın ayrıntılarını belirtir. Bu ayrıntılara dayanarak, ek güvenlik içeren bir UdpDiscoveryEndpoint oluşturulur ve kullanılır.  
  
- **İstemci**: Bu sınıf bir Icalbir torservice bulmaya çalışır ve hizmette yöntemleri çağırabilir. Yine, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> eklenen güvenliği olan bir, iletileri imzalamak ve doğrulamak için oluşturulur ve kullanılır.  
  
- **Announcementlistener**: çevrimiçi ve çevrimdışı duyuruları dinleyen ve güvenli duyuru uç noktasını kullanan kendiliğinden konak bir hizmet.  
  
> [!NOTE]
> Setup.bat birden çok kez çalıştırıldıysanız, Sertifika Yöneticisi yinelenen sertifikalar olduğu için eklemek üzere bir sertifika seçmenizi ister. Bu durumda, Setup.bat iptal edilmelidir ve yinelemeler zaten oluşturulduğundan Cleanup.bat çağrılmalıdır. Cleanup.bat Ayrıca, silinecek bir sertifika seçmenizi ister. Listeden bir sertifika seçin ve hiçbir sertifika geri alınana kadar Cleanup.bat yürütmeye devam edin.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio için Geliştirici Komut İstemi Setup.bat betiğini yürütün. Örnek, iletileri imzalamak ve doğrulamak için sertifikaları kullanır. Betik, Makecert.exe kullanarak sertifikaları oluşturur ve Certmgr.exe kullanarak bunları kurar. Betiğin yönetici ayrıcalıklarıyla çalıştırılması gerekir.  
  
2. Örneği derlemek ve çalıştırmak için, Visual Studio 'da Security. sln dosyasını açın ve **tümünü yeniden derle**' yi seçin. Birden çok proje başlatmak için çözüm özelliklerini güncelleştirin: DiscoverySecureChannels hariç tüm projeler için **Başlat** ' ı seçin. Çözümü normal olarak çalıştırın.  
  
3. Örnekle işiniz bittiğinde, bu örnek için oluşturulan sertifikaları kaldıran Cleanup.bat betiğini yürütün.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
