---
title: Eş Adı Çözümleme Protokolü
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428216"
---
# <a name="peer-name-resolution-protocol"></a>Eş Adı Çözümleme Protokolü
Eşler arası ortamlarda, eşler, her birinin ağ konumlarını (adresler, protokoller ve bağlantı noktaları) adlarla veya diğer tanımlayıcı türlerinden çözümlemek için belirli ad çözümleme sistemlerini kullanır. Geçmişte, eş adı çözümlemesi, etki alanı adı sistemi (DNS) içindeki diğer eksikler tarafından da doğal olarak geçici bağlantı tarafından karmaşıktır.  
  
 Microsoft® Windows® Eşler arası ağ platformu, ilk olarak Windows XP için geliştirilmiş ve ardından ' de yükseltilen eş adı çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik bir ad kaydı ve ad çözümleme protokolü ile bu sorunu çözer. Windows Vista™. PNRP geleneksel ad çözümleme sistemlerinden çok farklı çalışır ve uygulama geliştiricileri için heyecan verici yeni olanaklar sunar.  
  
 PNRP ile, eş adları makineye veya makinedeki ayrı uygulamalara veya hizmetlere uygulanabilir. Eş adı çözümlemesi bir adres, bağlantı noktası ve büyük olasılıkla genişletilmiş bir yük içerir. Bu sistemin avantajları arasında hata toleransı, performans sorunu olmaması ve hiçbir şekilde eski adresleri döndürmeyecek ad çözümlemeleri dahildir; Protokolü mobil kullanıcıları bulmaya yönelik harika bir çözüm haline getirme.  
  
 Güvenlik açısından, eş adları güvenli (korumalı) veya güvenli olmayan (korumasız) olarak yayımlanabilir. PNRP güvenli eş adlarını yanıltmaya karşı korumak için ortak anahtar şifrelemeyi kullanır; Her iki bilgisayar ve hizmet da PNRP ile adlandırılabilir.  
  
Eş adı çözümleme protokolü aşağıdaki özellikleri gösterir:  
  
- Dağıtılmış ve neredeyse tamamen sunucusuz. Sunucular yalnızca önyükleme işlemi için gereklidir.  
  
- Üçüncü tarafların katılımı olmadan güvenli ad yayını. DNS ad yayınının aksine, PNRP ad yayını anında ve finans maliyeti olmadan olur.  
  
- PNRP, eski adreslerin çözümlenmesini önleyen gerçek zamanlı olarak güncelleştirilir.  
  
- PNRP aracılığıyla adların çözümlenmesi bilgisayarların ötesinde de hizmetler için ad çözümlemesine izin verir.  
  
## <a name="the-systemnetpeertopeer-namespace"></a>System .net. PeerToPeer ad alanı  
  
- PNRP işlevselliği, .NET Framework sürüm 3,5 içinde <xref:System.Net.PeerToPeer> ad alanı tarafından tanımlanır. Kullanılabilir bir PNRP hizmeti ile eş adlarını kaydetmek ve çözümlemek için kullanılabilecek bir tür kümesi sağlar.  
  
- (PNRP ve özel eşdüzey çözümleyiciler <xref:System.ServiceModel.PeerResolvers> ad alanında belirtilen türler kullanılarak oluşturulabilir ve oluşturulabilir.)  
  
- Kullanılabilir bir PNRP hizmeti ile adları kaydettirmek ve çözümlemek için kullanılan temel türler aşağıdaki gibidir:  
  
- <xref:System.Net.PeerToPeer.Cloud>: kapsamı dahil, kullanılabilir bir PNRP bulutunu açıklayan bilgileri tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerName>: bir bulut içindeki bir eşi kaydettirmek ve daha sonra çözümlemek için kullanılabilecek bir eş adı tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerNameRecord>:, eşe bağlantı kurulabileceği ağ uç noktalarını içeren bir eş için kayıt bilgilerini içeren, PNRP bulutundaki kaydı tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerNameRegistration>: eş adı kaydını başlatma ve durdurma yöntemleri de dahil olmak üzere bir eş adı için kayıt işlemini tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerNameResolver>: bir eş adı çözümleme için hem zaman uyumlu hem de zaman uyumsuz yöntemler de dahil olmak üzere ağ uç noktaları için çözümleme işlemini tanımlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [Ağ Programlama Örnekleri](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
