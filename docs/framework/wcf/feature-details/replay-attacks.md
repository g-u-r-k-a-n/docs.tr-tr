---
title: Yeniden Yürütme Saldırıları
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: 4325b3747074f13cf02752f99b25fa02e4117b4c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239087"
---
# <a name="replay-attacks"></a>Yeniden Yürütme Saldırıları

Bir saldırgan iki taraf arasında bir ileti akışını kopyaladığında veya bir veya daha fazla tarafın akışını yeniden oynadığında bir yeniden *yürütme saldırısı* meydana gelir. Hafiflemediği sürece, saldırıya tabi olan bilgisayarlar akışı meşru iletiler olarak işler ve bu da bir öğenin gereksiz sıraları gibi hatalı sonuçlar oluşmasına neden olur.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Bağlamalar, yansıma saldırılarına maruz kalabilir  

 *Yansıma saldırıları* , yanıt olarak alıcıdan gelmiş gibi iletiler bir gönderene geri yeniden oynatılır. Windows Communication Foundation (WCF) mekanizmasında standart yeniden *yürütme algılaması* bunu otomatik olarak işlemez.  
  
 WCF hizmet modeli istek iletileri için imzalı bir ileti KIMLIĞI eklediğinden ve yanıt iletilerinde imzalı bir üst bilgi beklediği için yansıma saldırıları varsayılan olarak azaltıldığında `relates-to` . Sonuç olarak, istek iletisi yanıt olarak yeniden yürütülemez. Güvenli güvenilir ileti (RM) senaryolarında, şu nedenle yansıma saldırıları azaltıldığında:  
  
- Oluşturma sırası ve sıra oluşturma yanıtı ileti şemaları farklıdır.  
  
- Simpleks dizileri için, istemci gönderdiği sıralı iletiler, istemci bu iletileri anlamadığından bu iletiyi yeniden oynamayabilir.  
  
- Çift yönlü diziler için, iki sıra kimliği benzersiz olmalıdır. Bu nedenle, bir giden sırası iletisi gelen sıralı ileti olarak yeniden oynatılamaz (tüm sıralı üstbilgiler ve gövdeler, çok fazla).  
  
 Yansıma saldırılarına açık olan tek bağlamalar, WS-Addressing olmayan ve WS-Addressing devre dışı olan özel bağlamalardır ve simetrik anahtar tabanlı güvenliği kullanır. <xref:System.ServiceModel.BasicHttpBinding>Varsayılan olarak WS-Addressing kullanmaz, ancak simetrik anahtar tabanlı güvenliği bu saldırıya karşı savunmasız çalışmasına izin verecek şekilde kullanmaz.  
  
 Özel bağlamalar için azaltma, güvenlik bağlamı kurmamalıdır veya WS-Addressing üst bilgileri gerektirmemelidir.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Web grubu: saldırgan birden çok düğüme Isteği yeniden yürütür  

 İstemci bir Web çiftliğinde uygulanan bir hizmeti kullanır. Bir saldırgan gruptaki bir düğüme gönderilen isteği gruptaki başka bir düğüme yeniden yürütür. Ayrıca, bir hizmet yeniden başlatılırsa, yeniden yürütme önbelleği temizlenir ve bu da bir saldırganın isteği yeniden oynamalarına olanak tanır. (Önbellek kullanılan, daha önce görülen ileti imzası değerlerini içerir ve bu imzaların yalnızca bir kez kullanılabilmesi için yeniden oynatılır. Yeniden yürütme önbellekleri bir Web grubu genelinde paylaşılmaz.)  
  
 Azaltmaları şunları içerir:  
  
- Durum bilgisi olan güvenlik bağlamı belirteçleriyle (güvenli konuşma etkin olan veya olmayan) ileti modu güvenliği kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](how-to-create-a-security-context-token-for-a-secure-session.md).  
  
- Hizmeti, aktarım düzeyi güvenliği kullanacak şekilde yapılandırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik konuları](security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](information-disclosure.md)
- [Ayrıcalık Yükseltme](elevation-of-privilege.md)
- [Hizmet Reddi](denial-of-service.md)
- [Kurcalama](tampering.md)
- [Desteklenmeyen Senaryolar](unsupported-scenarios.md)
