---
description: "Daha fazla bilgi edinin: bulma proxy 'Si uygulama"
title: Keşif Proxy'si Ekleme
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: cfd897e114c99bcacb24e9981ee4a3e99e06636c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734041"
---
# <a name="implementing-a-discovery-proxy"></a>Keşif Proxy'si Ekleme

Bu bölümde, bulma proxy 'si uygulamak için gereken adımlar açıklanmaktadır. Bulma proxy 'si, bir hizmet deposu içeren tek başına hizmettir. İstemciler, proxy 'nin farkında olduğu keşfedilebilir hizmetleri bulmak için bir keşif proxy 'sini sorgulayabilir. Hizmetler ile bir ara sunucu nasıl doldurulur uygulayıcısı. Örneğin, bir bulma proxy 'si var olan bir hizmet deposuna bağlanabilir ve bu bilgileri bulunabilir hale getirebilir, bir yönetici bir ara sunucuya bulunabilir Hizmetleri eklemek için bir yönetim API 'SI kullanabilir veya bir keşif proxy, iç önbelleğini güncelleştirmek için duyuru işlevini kullanabilir.  
  
 WCF uygulama, kolayca bir proxy oluşturmanıza izin veren temel sınıflar sağlar. Bu API 'Leri, mevcut deponuzda bir bulma proxy 'Si oluşturmak için kullanabilirsiniz.  
  
 Burada uygulanan bulma proxy diğer tüm WCF Hizmetleri gibidir, bu da keşif proxy 'sini bulunabilir hale getirebilir ve istemcilerin uç noktalarını bulmasını sağlayabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Nasıl yapılır: Keşif Proxy'si Uygulama](how-to-implement-a-discovery-proxy.md)  
 Bulma proxy 'sinin nasıl uygulanacağını açıklar.  
  
 [Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme](discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Bulma proxy 'sine Kaydolmakta olan keşfedilebilir WCF hizmetinin nasıl uygulanacağını açıklar.  
  
 [Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma](client-app-discovery-proxy-to-find-a-service.md)  
 Bir hizmeti aramak için bulma proxy 'sini kullanan bir WCF istemci uygulamasının nasıl uygulanacağını açıklar.  
  
 [Nasıl yapılır: Keşif Proxy'sini Test Etme](how-to-test-the-discovery-proxy.md)  
 Önceki üç konuda yazılan kodun nasıl test edileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Keşfetme](wcf-discovery.md)
- [Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
