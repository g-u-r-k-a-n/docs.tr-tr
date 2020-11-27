---
title: PNRP Bulutları
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: 60b6fb44116fe2d8af50fb0b310615b3b962977b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263210"
---
# <a name="pnrp-clouds"></a>PNRP Bulutları

Bir PNRP "bulutu" ağ üzerinden birbirleriyle iletişim kurabilen bir düğüm kümesini temsil eder. "Cloud" terimi "eşdüzey ağ" ve "eşler arası Graf" ile eşanlamlıdır.  
  
 Düğümler arasındaki iletişimin asla bir buluttan diğerine çapraz olmaması gerekir. <xref:System.Net.PeerToPeer.Cloud>Örnek, büyük/küçük harfe duyarlı olan adıyla benzersiz bir şekilde tanımlanır. Tek bir eş veya düğüm birden fazla buluta bağlı olabilir.  
  
 Bulutlar ağ arabirimlerine çok yakın bir şekilde bağlanır.  Farklı alt ağlara bağlı iki ağ kartına sahip çoklu bilgisayarlı bir makinede, üç bulut döndürülür: Arabirim başına her bir bağlantı yerel adresi için bir tane ve tek bir genel kapsam bulutu.  
  
 PNRP, bir kapsamın birbirini bulabilen bilgisayarların gruplandırılması olduğu üç bulut "kapsamını" kullanır:  
  
- Genel bulut genel IPv6 adresi kapsamına ve genel adreslere karşılık gelir ve IPv6 Internet 'in tamamında tüm bilgisayarları temsil eder. Yalnızca tek bir genel bulut vardır.  
  
- Bağlantı yerel bulutu bağlantı yerel IPv6 adresi kapsamına ve bağlantı yerel adreslerine karşılık gelir. Bağlantı yerel bulutu, genellikle yerel olarak bağlı alt ağla aynı olan belirli bir bağlantı içindir. Birden çok bağlantı yerel bulutu olabilir.  
  
 Siteye özgü bulut olan üçüncü bulut, site IPv6 adresi kapsamına ve site yerel adreslerine karşılık gelir. Bu bulut kullanım dışı bırakılmıştır, ancak yine de PNRP ' de desteklenir.  
  
## <a name="clouds"></a>Bulutlar  

 PNRP bulutları, sınıfının örnekleriyle temsil edilir <xref:System.Net.PeerToPeer.Cloud> . Bir eşdüzey kullanılan bulut grupları, sıralanabilir sınıfın örnekleri tarafından temsil edilir <xref:System.Net.PeerToPeer.CloudCollection> . Geçerli eş tarafından bilinen PNRP bulutu koleksiyonları statik yöntem çağırarak elde edilebilir <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> .  
  
 Ayrı bulutlar, 256 karakter Unicode dizesi olarak temsil edilen benzersiz adlara sahiptir. Bu adlar, yukarıda bahsedilen kapsamla birlikte, bulut sınıfının benzersiz örneklerini oluşturmak için kullanılır. Bu örnekler kalıcı kullanım için seri hale getirilebilir ve yeniden oluşturulabilir.  
  
 Bir bulut örneği oluşturulduktan veya alındıktan sonra, bir bilinen eşdüzey ağ oluşturmak için eş adları onunla birlikte kaydedilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.Cloud>
- [Eş Adı Çözümleme Protokolü](peer-name-resolution-protocol.md)
